---
title: "Launch guest application from host script"
date: 2012-09-22
forum: Virtualisation
---

### Post by VeeDubb on 2012-09-22
I'm working on setting up a script to launch an internet explorer, installed in Windows XP through virtualbox, from my ubuntu desktop, and I have most of the pieces.  

(I know that explorer can be installed through wine or playonlinux, but my wife needs to be able to access one site for her job that simply will not let her in if we're using Wine, but works fine through a VM.)


I can start the VM with ```
VBoxManage startvm "WindowsXP"
```


I can launch explorer with ```
VBoxManage guestcontrol WindowsXP exec --image c:\\program\ files\\Internet\ Explorer\\IEXPLORE.EXE --username owner --password password
```


And I can check whether or not the VM is already running with ```
VBoxManage showvminfo "WindowsXP" | grep State
```


What I'm missing is how to use grep state in a logic check so that it will only try to launch the VM if it isn't already running.

The other thing I'd like to do, which is probably WAY more trouble than it's worth, is set it up so that the VM will savestate and exit when internet explorer is closed.  That would be nice, but is not required.

---

### Post by VeeDubb on 2012-09-22
I was able to do everything except automatically savestate and close the VM when explorer closes using the following saved as a shell script.  For sanity sake, I make a launcher in ~/.local/share/Applications

```
#!/bin/bash
if [ $( VBoxManage list runningvms | wc -l ) != "0" ]
then
VBoxManage guestcontrol WindowsXP exec --image c:\\program\ files\\Internet\ Explorer\\IEXPLORE.EXE --username owner --password password
else
VBoxManage startvm "WindowsXP" && VBoxManage guestcontrol WindowsXP exec --image c:\\program\ files\\Internet\ Explorer\\IEXPLORE.EXE --username owner --password password
fi
```


If anyone can point me in the right direction on saving the machine state when explorer closes, that would be fantastic.  I suspect it might be something that has to be set up in the guest OS, but I'd rather not do that because I only want closing explorer to close the VM if it's launched using this script, an I'd rather not set up a separate VM just for that.

---

### Post by JKyleOKC on 2012-09-25
Have a look at the --wait-for option to VBoxManage guestcontrol. It looks as if it just **might** do exactly what you want, returning an error code and/or information that your script could use...

---

### Post by VeeDubb on 2012-09-26
Thanks for the tip, and I think you may be right.

Unfortunately, it seems to be an obscure option (or my google-foo has weakened) because I can't find any useful information online.

I've checked the man page, but like most man pages, it's staggeringly unhelpful to anyone who didn't write the program.  All it says is:

```
VBoxManage guestcontrol      

exec[ute] <vmname>|<uuid> <path    to program> --username <name> --password <password>
[--arguments    "<arguments>"]    [--environment    "<NAME>=<VALUE>
[<NAME>=<VALUE>]"] [--flags <flags>] [--timeout <msec>] [--ver-
bose] [--wait-for exit,stdout,stderr||]
```

Not only does that not tell me how to use it, but anywhere I try to invoke --wait-for it seems to fail with an error that says it's not a valid argument.

---

### Post by VeeDubb on 2012-09-26
Scratch that.  I just got it!  You're a lifesaver.

You don't use --wait-for.  You use --wait-exit, --wait-stdout or --wait-stderr.


I tried ```
VBoxManage startvm "WinXP" && VBoxManage guestcontrol WinXP exec --image c:\\program\ files\\Internet\ Explorer\\IEXPLORE.EXE --username owner --password password --wait-exit && VBoxManage controlvm "WinXP" savestate
```

and also tried ```
VBoxManage startvm "WinXP" && VBoxManage guestcontrol WinXP exec --image c:\\program\ files\\Internet\ Explorer\\IEXPLORE.EXE --username owner --password password --wait-exit && VBoxManage controlvm "WinXP" savestate
```

Both of those fire up the VM, launch explorer, and return to a prompt once explorer closes, but neither of them actually savestate.


My next step was to modify the original shell script and place ```
VBoxManage controlvm "WinXP" savestate
``` to it's own line.  That actually did the trick.  It does take about 5 seconds to shut down the VM after I close XP, but that's about the same as doing a manual savestate.

For anyone else who wants to do the same thing, the solution was fairly simple.

1. Make sure your installation of windows requires a login.  This will not work with a system that is logged in automatically.

2. Shut down your VM (not just a savestate.  Shut it down) 

3. Boot it up, log in, switch to seemless mode, and exit saving machine state.

4. Make a script with the following somewhere in your path.

```
#!/bin/bash
if [ $( VBoxManage list runningvms | wc -l ) != "0" ]
then
VBoxManage guestcontrol WinXP exec --image c:\\program\ files\\Internet\ Explorer\\IEXPLORE.EXE --username owner --password password
VBoxManage controlvm "WinXP" savestate
else
VBoxManage startvm "WinXP" && VBoxManage guestcontrol WinXP exec --image c:\\program\ files\\Internet\ Explorer\\IEXPLORE.EXE --username owner --password password --wait-exit
VBoxManage controlvm "WinXP" savestate
fi
```

Be sure to change WinXP to the name of your virtual machine, and change the username and password accordingly.  Also, don't forget to make it executable.

4. (Optional) Make a launcher for it and save to ~/.local/share/applications  This will make it show up in the unity menus and allow you to put it in your quick launch bar if you're so inclined.

My launcher is just a text file called "Internet Explorer.desktop" with the following contents:

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/stephen/Icons/1920940448.png
Name[en_US]=Internet Explorer
Exec=/home/stephen/bin/vbie.sh
Comment[en_US]=MS Internet Explorer through VirtualBox
Name=Internet Explorer
Comment=MS Internet Explorer through VirtualBox
Icon=/home/stephen/Icons/1920940448.png
```

Just change /home/stephen/bin/vbie.sh to the location and name of your script, and change the Icon line to the location of whatever icon you feel like downloading off the net to use.  And of course, make the launcher executable as well.  You'll be left with a wife-approved solution.


I'm sure the same process could be applied to just about any application that can be launched directly from an executable.

---

### Post by JKyleOKC on 2012-09-26
Glad to know it worked. I wouldn't have thought to try what you did; the author of that man page failed to follow the usual conventions for alternating options. He should have provided examples...

Anyway it's a good script. Congratulations on solving the problem and making the solution available to all of us!

---

