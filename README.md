## Overview

We already have [Vim-Task](https://github.com/samsonw/vim-task "Vim Task Plugin"), now we need one task plugin for Sublime Text 2.

##ScreenShot

### SublimeTask with Monaco font

<a href="http://blog.samsonis.me/wp-content/uploads/2012/02/SublimeTask.png"><img style="border: medium none;" title="SublimeTask with Monaco font" src="http://blog.samsonis.me/wp-content/uploads/2012/02/SublimeTask.png" alt="SublimeTask with Monaco font" width="300" height="216"></a>

##Installation

I assume you have git installed, if not, you can download the latest source from Github Downloads then copy the whole directory into the Packages directory.

The location of the “Packages” packages directory depends on the OS you’re using, below is a possible location that you may find your Packages directory:

* OS X:
  *  ~/Library/Application Support/Sublime Text 2/Packages
* Linux:
  *  ~/.config/sublime-text-2/Packages
* Windows:
  * %APPDATA%/Sublime Text 2/Packages

Take OS X for example:

    $ cd ~/Library/Application\ Support/Sublime\ Text\ 2/Packages/
    $ git clone git@github.com:samsonw/SublimeTask.git

~~TODO: add this Package to [sublime_package_control](https://github.com/wbond/sublime_package_control), so later we can install it directly in editor via package control.~~

UPDATE: This package has already been accepted by [sublime_package_control](https://github.com/wbond/package_control_channel/pull/157), now you can install it directly in the editor, the package name there is just called “Task”.

##Shortcut Key & Key Binding

By default, I mapped Command+Ctr+Enter (OS X) and Ctrl+Shift+Alt+Enter (Windows, Linux) for toggling the task status, you can simply remap to what’s the most comfortable for you in your Default User keymap file.

* OS X:

        [
            { "keys": ["super+ctrl+enter"], "command": "task"}
        ]

* Linux, Windows:

        [
            { "keys": ["ctrl+shift+alt+enter"], "command": "task"}
        ]

##Customization

To change the task display color, you need to edit a file called Task.tmLanguage bundled together with this SublimeTask package.

    $ subl ~/Library/Application\ Support/Sublime\ Text\ 2/Packages/SublimeTask/Task.tmLanguage

(you may need to enable [sublime command line invocation](http://www.sublimetext.com/docs/2/osx_command_line.html) to execute above command)

    <dict>
        <key>comment</key>
        <string>Completed Tasks</string>
        <key>match</key>
        <string>^\s*✓[^\[\]]*</string>
        <key>name</key>
        <string>string</string>
    </dict>

As you can see above, I use “string” scope for the Completed Tasks by default, which will be mapped to green in my color scheme file. If it doesn’t look good in your color scheme, you can simply customize it by changing “string” to something appropriate to your color scheme.

You can find the scope name in your color scheme file.

##File Format & Syntax

The Task grammar and commands by default apply to file todo.txt and files with extension .task, .tasks, .todo and .todolists. You can also customize this by editing SublimeTask/Task.tmLanguage:

    <key>fileTypes</key>
        <array>
        <string>task</string>
        <string>tasks</string>
        <string>todo.txt</string>
        <string>todo</string>
        <string>todolists</string>
    </array>

All the formats and syntax is similar, quoted below for your references:

>     Headers end with a colon (“:”).
>     Pending (uncompleted) tasks start with a hyphen (“-”). Completed tasks start with a checkmark (“✓”).
>     Headers and tasks can be indented for grouping/hierarchy, as seen in the screenshot above.

##Bug & Feedback

Please report bugs and issues to github: <https://github.com/samsonw/SublimeTask/issues>, any feedback and suggestion is welcome.

