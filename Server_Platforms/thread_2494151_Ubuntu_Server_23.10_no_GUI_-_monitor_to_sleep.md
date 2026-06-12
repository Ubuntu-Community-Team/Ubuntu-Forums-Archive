---
title: "Ubuntu Server 23.10 no GUI - monitor to sleep"
date: 2024-01-07
forum: Server Platforms
---

### Post by kein90 on 2024-01-07
Hi everyone, this is my fist post on this forum. I have a Ubuntu Server 23.10 with no GUI, that I use for photos backup, Jellyfin and other similar stuff. 
Once I've configured everything I really don't have much use for the monitor staying on 24/7 and listing me the login information. So my question is: how can I set up so that my monitor only (not the server itself mind you) goes to sleep after 10 minutes of inactivity, and I can then wake it by typing something on the keyboard. 

So far I've tired using an xset command. 

```
xset dpms 600

```
And create a file [COLOR=#FFFFFF][FONT=&amp]activare_monitor.sh[/FONT][/COLOR] with the following information: 


```
#!/bin/bash
xset dpms force on
xdotool key "a"



```

Also set the script's permision with 

```
chmod +x activare_monitor.sh

```


and finally tried to ran this script:

```
xautolock -time 10 -locker "./activare_monitor.sh" -notify 30 -notifier "notify-send 'Monitor will go to sleep in 30 seconds'"

```

My issue is that no matter what I try I get this message on the first step: 
[COLOR=#ECECF1][FONT=Söhne]xset:  unable to open display ""[/FONT][/COLOR] even though I tried to specify the display with the command as such: ```
DISPLAY=:0 xset dpms 600

```

I'm using a HUAWEI MateView GT 34-inch Standard Edition monitor with a display port connection to a HP Elitedesk 800 g3 SFF (if by chance the hardware components are relevant). 
Any help would be greatly appriciated.

---

### Post by howefield on 2024-01-07
Welcome to the forums, thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by MAFoElffen on 2024-01-07
Server Edition's default behavior is to blank, since servers are usually managed reomtely via ssh.

If I don't want that behavior, then I add "consoleblank=0" as a kernel boot parameter to file /etc/default/grub, and pick up the changes with update-grub... I do this to ll my machines, because I want them not to blank or go to sleep before a login. This sucks when your machine reboots fro some reason, you don't notice, then you can't ssh into it. This setting prevents that.

Then add "setterm -blank 0" to a script called by a unit file "WantedBy=multi-user.target"...

I would say probably, instead of creating another unit file, to just edit unit file /usr/lib/systemd/system/rc-local.service and add a second ExecStart= line like this
```

#
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
# This unit gets pulled automatically into multi-user.target by
# systemd-rc-local-generator if /etc/rc.local is executable.
[Unit]
Description=/etc/rc.local Compatibility
Documentation=man:systemd-rc-local-generator(8)
ConditionFileIsExecutable=/etc/rc.local
After=network.target
[Service]
Type=forking
ExecStart=/etc/rc.local start
[COLOR=#ff0000]ExecStart=/usr/bin/setterm -blank 0[/COLOR]
TimeoutSec=0
RemainAfterExit=yes
GuessMainPID=no

```
Save & exit
```

sudo systemctl daemon-reload
sudo systemctl status rc-local.service

```
To refresh the changes and check the status of if is loaded. It would not take affect until the user logged out, and logged back in.

---

### Post by kein90 on 2024-01-08
Thank you for the input but mine never blanked out on me, for whatever reason. I'm actually trying to get a feature similar to what Windows offers where the screen goes black and then comes back when you press a key for example.

---

### Post by MAFoElffen on 2024-01-10
Sorry, the opposite of what I thought you wanted.

Set the boot parameter to "consoleblank=60"

Set the/a second ExecStart line in  rc-local.service to
```

ExecStart=/usr/local/bin/activare_monitor.sh

```
Then change your script to something like this:
```

#!/bin/bash
#
# activare_monitor.sh
#
# Inspired by: https://superuser.com/a/621891
#

INACTIVITY_TIME='1m'

INACTIVITY_CMD="echo -e 'Monitor will go to sleep in 60 seconds'"

function inactivity-start-timer () {
    (sleep "$INACTIVITY_TIME"; $INACTIVITY_CMD) &
    INACTIVITY_PID=$!
    disown
}

function inactivity-stop-timer () {
    kill $INACTIVITY_PID > /dev/null 2>&1
}

PROMPT_COMMAND=inactivity-start-timer

preexec () {
    inactivity-stop-timer
}

preexec_invoke_exec () {
    [ -n "$COMP_LINE" ] && return  # do nothing if completing
    [ "$BASH_COMMAND" = "$PROMPT_COMMAND" ] && return # don't cause a preexec for $PROMPT_COMMAND
 local this_command=`history 1 | sed -e "s/^[ ]*[0-9]*[ ]*//g"`;
 preexec "$this_command"
}

trap 'preexec_invoke_exec' DEBUG

xset --blank 1

```

---

### Post by QIII on 2024-01-10
I run my servers headless (no monitor, no keyboard/mouse) after installation and administer them via SSH.  Why waste hardware on something that doesn't need it?

Oh.  And by the way, I use LTS releases for servers rather than having to upgrade so often.

---

### Post by TheFu on 2024-01-10
I have 2 monitors for all my systems and use a KVM switch for the second one. Most of the time, the 2nd monitor is powered off. Pretty easy.

The main monitor is connected to a workstation that is set to dim in 5 minutes and power off in 10 minutes and lock in 60 minutes.  This is controlled by xscreensaver, but that's part of my GUI setup. I don't use any DE, so YMMV.

---

