---
title: "How to know when screen is locked/unlocked in ubuntu 17.10"
date: 2017-11-08
forum: Ubuntu Application Development
---

### Post by inigoD on 2017-11-08
I have try to ask this also in stackoverflow but I am not able to achieve nothing:
[URL="https://https://askubuntu.com/questions/974199/how-to-run-a-script-at-screen-lock-unlocks-in-ubuntu-17-10?noredirect=1#comment1562164_974199"]
https://askubuntu.com/questions/974199/how-to-run-a-script-at-screen-lock-unlocks-in-ubuntu-17-10?noredirect=1#comment1562164_974199[/URL]

I want to run an script on screen lock and another one on unlock... How can I know when this occurs?

I've try using dbus-monitor


#!/bin/bash

dbus-monitor --session "type='signal',interface='org.gnome.ScreenSaver'" | \
( while true
    do read X
    if echo $X | grep "boolean true" &> /dev/null; then
        echo "locking at $(date)" >> $HOME/time_xprofile
    elif echo $X | grep "boolean false" &> /dev/null; then
        echo "unlocking at $(date)" >> $HOME/time_xprofile
    fi
    done )

But doesn't work; that signal often doesn't appear at all (neither true nor false)

And also I have try to find which process is running while screen is locked which is not running while unlocked. So I could use 'ps' command to know when it happens using this script with that procname (seems that is not '[COLOR=#7D2727][FONT=inherit]gnome-screensaver-dialog[/FONT][/COLOR]')

[COLOR=#858C93][FONT=inherit]#!/usr/bin/env python3[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]import[/FONT][/COLOR][COLOR=#303336][FONT=inherit] psutil
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]import[/FONT][/COLOR][COLOR=#303336][FONT=inherit] time
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]import[/FONT][/COLOR][COLOR=#303336][FONT=inherit] subprocess

procname [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"gnome-screensaver-dialog"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
lock_command [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"/path/to/lockscript"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
unlock_command [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"/path/to/unlockscript"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

lock1 [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#101094][FONT=inherit]None[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

[/FONT][/COLOR][COLOR=#101094][FONT=inherit]while [/FONT][/COLOR][COLOR=#101094][FONT=inherit]True[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
--time[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]sleep[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]2[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
--lock2 [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] procname [/FONT][/COLOR][COLOR=#101094][FONT=inherit]in[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]p[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]name[/FONT][/COLOR][COLOR=#303336][FONT=inherit]()[/FONT][/COLOR][COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit] p [/FONT][/COLOR][COLOR=#101094][FONT=inherit]in[/FONT][/COLOR][COLOR=#303336][FONT=inherit] psutil[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]process_iter[/FONT][/COLOR][COLOR=#303336][FONT=inherit]())[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#101094][FONT=inherit]--if[/FONT][/COLOR][COLOR=#303336][FONT=inherit] lock2 [/FONT][/COLOR][COLOR=#303336][FONT=inherit]!=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] lock1[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#101094][FONT=inherit]----if[/FONT][/COLOR][COLOR=#303336][FONT=inherit] lock2[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
------subprocess[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Popen[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]lock_command[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
            [/FONT][/COLOR][COLOR=#101094][FONT=inherit]------print[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"locked"[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#101094][FONT=inherit]----else[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
------subprocess[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Popen[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]unlock_command[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
            [/FONT][/COLOR][COLOR=#101094][FONT=inherit]------print[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"unlocked"[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
--lock1 [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] lock2
[/FONT][/COLOR]
But I cannot find any new process while locked... the only process that I see relevant is gsd-screensaver-proxy, which is allways running...

So, I cannot find a way to do it. 

How can I know when the screen flips to locked/unlocked in ubuntu 17.10 with xserver and ubuntu-gnome?

---

### Post by Bryan76 on 2018-01-05
I too am trying to figure out how to run a command on screen lock and unlock.  Have you made any progress?

---

