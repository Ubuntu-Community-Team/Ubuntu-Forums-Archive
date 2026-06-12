---
title: "Where to put script to shut down VBox VM's when shutting down Ubuntu"
date: 2009-02-01
forum: Virtualisation
---

### Post by Jose Catre-Vandis on 2009-02-01
I generally run a VM with XP on a separate desktop, and consistently forget I have it open when shutting down, which causes my laptop to freeze up.

Writing a script is no great problem using:
```
VBoxManage controlvm XP poweroff
```
but where do I put it so that it is run prior to the shutdown command?

---

### Post by Tomatz on 2009-02-01
> **Jose Catre-Vandis said:**
> I generally run a VM with XP on a separate desktop, and consistently forget I have it open when shutting down, which causes my laptop to freeze up.

Writing a script is no great problem using:
```
VBoxManage controlvm XP poweroff
```
but where do I put it so that it is run prior to the shutdown command?

Im not great at scripting but the easiest way i can think of doing it would be:

```
VBoxManage controlvm XP poweroff

sleep 20

gnome-session-save --kill
```

Put the code above it in a **text file on your desktop** and all it **shutdown-script**, then:

Open a terminal

```
cd ~/Desktop
```

```
sudo chmod 777 /shutdown-script
```

```
sudo cp /shutdown-script /usr/bin/shutdown-script
```


Now just run the command **shutdown-script** or add it to a launcher.  Also i have only allowed **20 seconds till shutdown (for xp)**. You may need to alter this ;)

---

### Post by Jose Catre-Vandis on 2009-02-01
Thanks Tomatz

It's not that part I have a problem with, I want to automate it as a part of the normal shut down routine (because I keep forgetting)

We have a nice place for start up programs, but not for shut down scripts ;)

---

### Post by Tomatz on 2009-02-01
The folder **/etc/rc6.d** holds all the scripts for shutdown BUT any script you make will have to watch for vbox to shutdown your guest OS before continuing with the host shutdown process. This could be problematic and is far beyond my experience.

Maybe you should ask in the programing forum?

---

### Post by Jose Catre-Vandis on 2009-02-17
bump?

---

### Post by markba on 2009-02-18
You can use VBoxTool (see my sig) for controlled saving when the host goes down. It makes use of the init-system (as suggested above). It is doing much more, like autostarting sessions at boot, check the website if you'd like....

---

### Post by Jose Catre-Vandis on 2009-02-18
Thanks markba

vboxtool is great, but I don't always want VMs to start when I boot up. Any way to block the autostart function? (I'll have a look in the scripts)

---

### Post by markba on 2009-02-18
Blocking autostart is easy, just empty /etc/vboxtool/machines.conf: vboxtool will only autostart the sessions named in machines.conf. As an alternative, you can also comment them out by preceding the line by '#'.

Autosave sessions does not depend on machines.conf, so even with an empty machines.conf, all sessions will be saved automatically on shutdown.

---

### Post by Jose Catre-Vandis on 2009-02-18
I'll need to rephrase what I said about vboxtool... it's a great idea....

can't get it to work for love nor money.

Won't start or stop or run any VM's with  or without a GUI

Not enough patience here this evening to perservere with it, but it has given me some ideas about how I can code to achieve what I want to do, using my original command.

---

### Post by markba on 2009-02-19
Installation should not be that difficult, just follow these instructions: [http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/readme.txt?view=markup](http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/readme.txt?view=markup)

But nevertheless, you can also implement your own solution, as allways: by studying code, you'll learn a lot. If you have any questions about vboxtool, just drop them here.

---

### Post by Jose Catre-Vandis on 2009-02-19
Yes, I followed these instructions to the letter. vboxtool did not start any VMs on boot up, even with the right info in machines.conf and vboxtool.conf. when I opened up a machine and tried to close it down (shutdown) whilst still open (the VM) I was returned to a login prompt, after loggin back in xVM Virtualbox window was open and my VM was listed as "aborted". Same applied when the two config files were empty. Nothing worked either when trying to manually start/stop/restart vboxtool from a terminal, although it did seem to pick up on one of my VMs that was in a saved state, though didn't start it. Nothing in System Monitor and no vbox proggies running. Am on Xubuntu 8.10 if that makes any difference and using v0.3 from Sourceforge. Should I try the SVN 0.41 you mention on virtualbox.org forums?

---

### Post by markba on 2009-02-19
Using 0.3 should be no problem nor should running under Xubuntu. vboxtool is running on production systems on Ubuntu, Debian, OpenSuse, Centos, etc. so Xubuntu should be no problem I guess (not tested though).

The aborted state after shutdown is normal, when vboxtool is not 'active'. Probably (my assumption) by some configuration error. To see, what goes wrong and where, we have to go through your setup, step by step. As an example, say you have a session called 'Windows XP'.

First: you are able to start, save and stop sessions from the VBox GUI?

Next, try:

```
vboxtool show
```

This should give info about all registered sessions.

Next, start a session with the VBox GUI and try:

```
vboxtool showrun
```

This should give info about all registered sessions which are currently running.

Now you can try:

```
vboxtool save
```

This will save all running sessions. The command gives feedback about which sessions it is saving.

Now you start a session by vboxtool:

```
vboxtool start "Windows XP"
```

Check with the 'vboxtool showrun'-command if it's running. Save session with 'vboxtool save'

Until now, vboxtool does not make use of vboxtool.conf or machines.conf, so it does not matter if they exist or what's in it.

If this all works well, you can edit /etc/vboxtool/machines.conf:

```
Windows XP,,
```

Now you can start all sessions from machines.conf by one command:

```
vboxtool autostart
```

I'll leave it from here, just let me know if all commands work (or not), then we can take the next step (look into the init-system).

---

### Post by Jose Catre-Vandis on 2009-02-19
> **markba said:**
> Using 0.3 should be no problem nor should running under Xubuntu. vboxtool is running on production systems on Ubuntu, Debian, OpenSuse, Centos, etc. so Xubuntu should be no problem I guess (not tested though).

The aborted state after shutdown is normal, when vboxtool is not 'active'. Probably (my assumption) by some configuration error. To see, what goes wrong and where, we have to go through your setup, step by step. As an example, say you have a session called 'Windows XP'.

First: you are able to start, save and stop sessions from the VBox GUI?

**YES**

Next, try:

```
vboxtool show
```



This should give info about all registered sessions.

**YES**

Next, start a session with the VBox GUI and try:

```
vboxtool showrun
```

This should give info about all registered sessions which are currently running.

**YES**

Now you can try:

```
vboxtool save
```



This will save all running sessions. The command gives feedback about which sessions it is saving.

**YES**

Now you start a session by vboxtool:

```
vboxtool start "Windows XP"
```

**YES?**

Check with the 'vboxtool showrun'-command if it's running. 

**NO!**

Here is the output from terminal after all these commands

```
jose@ibex:~$ vboxtool show
XP (vrdp=): powered-off
jose@ibex:~$ vboxtool showrun
XP (vrdp=): running (cpu=2.0%, mem=407m)
jose@ibex:~$ vboxtool save
Saving "XP"
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
jose@ibex:~$ vboxtool start "XP"
Starting "XP" (vrdp=)
Waiting for the remote session to open...
Remote session has been successfully opened.
jose@ibex:~$ vboxtool showrun
jose@ibex:~$ 
```




So problems start when trying to use vboxtool start on a saved VM ?
System Monitor is not showing any Vbox programs running. Although if I watch whilst running the start command all the right things happen then they close down again
Anything to do with the location of my VMs - they are not in the default location?
And do the Vms need a VDRP port setting away from 3389?

I ran vboxtool start and of three VMs in a saved state, one started up headless and I was able to access via rdesktop. headless is no good for what I want.

---

### Post by markba on 2009-02-19
> **Jose Catre-Vandis said:**
> Anything to do with the location of my VMs - they are not in the default location?

Well, maybe. vboxtool should be robust enough to manage this. But nevertheless, what's that location?

---

### Post by Jose Catre-Vandis on 2009-02-19
```
/media/VMS/VirtualBox/VDI
```

Same drive, different partition, and as you see no . before the V in VirtualBox. Machines are in the same place but in a machines directory.

All the other commands worked OK up to this point

---

### Post by Jose Catre-Vandis on 2009-02-20
Update

Things seemed to have improved a bit after some tinkering! I had another VM with VRDP settings in place, this was causing problems as it was starting up but preventing my chosen VM from starting due to port conflicts. With all VMs now having no settings from within the XVM GUI, I can now start my chosen VM with the vboxtool start command.

However, it starts and saves headlessly ( I guess this is by design) from command line

But things aren't all working as they are supposed to.

If I open up the VM with the GUI, then save it using "vboxtool save VM", I cannot open it up again using "vboxtool start VM".

If I try to shutdown with the VM open, I only get back to the login gdm, and the VM then shows as aborted.

Spooky ;)

---

### Post by markba on 2009-02-20
> **Jose Catre-Vandis said:**
> Update

Things seemed to have improved a bit after some tinkering! I had another VM with VRDP settings in place, this was causing problems as it was starting up but preventing my chosen VM from starting due to port conflicts. With all VMs now having no settings from within the XVM GUI, I can now start my chosen VM with the vboxtool start command.


Nice find. I was thinking is this direction also (saw the your vboxtool-output where vrdp was empty), tested it without a vrdp-port, but that all worked OK. I could not have guessed several (running) sessions with the same vrsp-port. 

Problem is that vboxtool, due to the usage of VBoxManage (instead of VBoxHeadless) does not report the error. I going to report a bug for this one, because it is very annoying and time consuming (like this case shows).

> **Jose Catre-Vandis said:**
> 
However, it starts up as headless ( I guess this is by design)

You're right. Sessions are started on the background, and can be accessed by rdp, e.g. rdpclient. As this is not what you need, it is not of any interest.

When I'm at home (I don't have a vboxtool environment at hand), I'll prepare a CLI-statement in which we can check your init-system.

---

### Post by markba on 2009-02-20
> **Jose Catre-Vandis said:**
> 
But things aren't all working as they are supposed to.

If I open up the VM with the GUI, then save it using "vboxtool save VM", I cannot open it up again using "vboxtool start VM".

If I try to shutdown with the VM open, I only get back to the login gdm, and the VM then shows as aborted.

Spooky ;)

Maybe vboxtool is indeed issueing the save-command on shutdown, but is not capable of saving the session. This should mean the init-system is correct, but there's something wrong with the save-command...

1. If you save the session by GUI (instead of vboxtool), it does work as expected?
2. What is the output of 'vboxtool save' (resulting in the aborted session)?

---

### Post by Jose Catre-Vandis on 2009-02-20
OK, after further testing, I can see that vboxtool is working fine for a headless environment, start, stop, save, shutdown, restart, autostart.

But as I don't want to autostart VMs, and I want to use my XP VM on the desktop and not through rdp, and vboxtool won't shutdown a "GUI" VM, not sure where to go next?

Thanks for all your support markba :)

---

### Post by markba on 2009-02-20
> **Jose Catre-Vandis said:**
> OK, after further testing, I can see that vboxtool is working fine for a headless environment, start, stop, save, shutdown, restart, autostart.

But as I don't want to autostart VMs, and I want to use my XP VM on the desktop and not through rdp, and vboxtool won't shutdown a "GUI" VM, not sure where to go next?

vboxtool is capable of *only* saving sessions on shutdown (so without autostart or using rdp), just as you wanted. So I still think vboxtool can help you, we just have to resolve the save-problem.

> **Jose Catre-Vandis said:**
> If I open up the VM with the GUI, then save it using "vboxtool save VM", I cannot open it up again using "vboxtool start VM".

If I try to shutdown with the VM open, I only get back to the login gdm, and the VM then shows as aborted.

Spooky ;)

So this seems to be the problem: a session opened by the GUI, cannot be saved by vboxtool reliable. If that same session is started by vboxtool, saving is working as expected.

Can you open a session by GUI and try the following:

```
VBoxManage controlvm <session name> savestate
```

---

### Post by Jose Catre-Vandis on 2009-02-20
Here is the terminal output from doing a savestate, startvm and savestate again:
```
jose@ibex:~$ VBoxManage controlvm XP savestate
VirtualBox Command Line Management Interface Version 2.1.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
jose@ibex:~$ VBoxManage startvm XP
VirtualBox Command Line Management Interface Version 2.1.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Waiting for the remote session to open...
Remote session has been successfully opened.
jose@ibex:~$ VBoxManage controlvm XP savestate
VirtualBox Command Line Management Interface Version 2.1.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
jose@ibex:~$
```

It all worked as expected. I had the VM open in seamless mode too, it saved and closed down, then opened back up on command to its saved and seamless state, then happily saved and closed again.

---

### Post by Jose Catre-Vandis on 2009-02-21
OK, I have made some progress, can get shutdown from the desktop with a VM open, although not through using vboxtool, but this might help in getting where we want to be. It struck me that running a VM in GUI mode required the logged in user / vboxuser to open it up, so by starting the VM with sudo and using the home environment of my logged in user I should be able to shutdown more cleanly. This is different from running headless which I do not believe requires a user to be logged in in order to run the vm. I also found that the vboxdrv script had some options to help out here, and by creating a file called /etc/default/virtualbox with some options tells vboxdrv to close all vms. I am not getting a savestate, just aborted, but seem to be on the right lines. Actions as follows:

```
sudo touch /etc/default/virtualbox
sudo nano /etc/default/virtualbox
```
add the following entries:
```
SHUTDOWN_USERS="jose"
SHUTDOWN=savestate
```
save out of /etc/default/virtualbox. vboxdrv picks up this information.
Now just to prove that it is vboxdrv doing the work, remove vboxtoolinit from rc.d
```
sudo update-rc.d -f vboxtoolinit remove
```

Next start your VM with this command:
```
sudo -H -u jose VBoxManage startvm XP
```
This overcomes the problem of trying to run a VM as root, as it cannot find the VM. No password is needed?

Try shutting down or restarting, should take you all the way instead of back to gdm.

Not sure why I am not getting a savestate?

You can use
```
sudo -H -u jose VBoxManage controlvm XP savestate
``` in the same way.

---

### Post by markba on 2009-02-21
First, some comments. 

The init-file /etc/init.d/vboxdrv does *not* look at /etc/virtualbox. This is stated in comments in the code but, if you look closely, you can see that /etc/virtualbox is never read. I actually made a bug report on this:
[http://www.virtualbox.org/ticket/1037](http://www.virtualbox.org/ticket/1037)

Next, the different init systems (vboxdrx and vboxtoolinit) do not interfere with each other. Removing one or the other from the init system can not have any effect.

My guess is, that the problem in your setup is due to an non standard installation method, this was discussed earlier, but details were sparse.

> **Jose Catre-Vandis said:**
> 
It struck me that running a VM in GUI mode required the logged in user / vboxuser to open it up, so by starting the VM with sudo and using the home environment of my logged in user I should be able to shutdown more cleanly.

Probably, the user under which you created the VM's is not the same user ('jose') that is using the VM's. I think that is the reason, you have to resort to the following command:

```
sudo -H -u jose VBoxManage startvm XP
```

Note that this is not standard, any VM should be started without using sudo/su etc. This indicates that something is wrong (or: not standard) with your setup. This also explains all the strange effects you mentioned above (not being able to save/start sessions etc.).

For solving your problem, it is imperative to do a structured research, leaving out all elements which have no influence on the problem at hand. Until this is sorted out, IMO it's not effective to look into vboxtool or any other method for a proper VM shutdown.

---

### Post by Jose Catre-Vandis on 2009-02-21
Hmmm....

Bog standard Xubuntu 8.10 installation
Bog standard VBox installation aside from custom directory for VMs/Machines
All features of VirtualBox work
All VMs created by jose, only one user on the PC, jose (other than root)
Agree that a user is needed, even for headless
[This chap]("http://www.glump.net/howto/virtualbox_as_a_service") must be getting "stoppage" from his script then

Time to setup a clean new environment to do some testing......

---

### Post by Jose Catre-Vandis on 2009-02-21
OK, just done a clean install of Xubuntu 8.10 in a separate partition. Added VBox 2.1_2.1.4, and installed a brand new VM. Following that installed vboxtool v3 as per instructions. Created empty files in /etc/vboxtool for machines.conf and vboxtool.conf

vboxtool show works
vboxtool showrun works
vboxtool save works
vboxtool stop works
vboxtool start does not work (yes I checked with showrun)

When rebooting or shutting down vboxtool does not savestate, and I am sent to the gdm login

Didn't try vboxtool autostart.

So do I still have a non- standard install somewhere?

#######################################################

Also have been trying out my own simple script as per the first post, ```
#!/bin/sh
VBoxManage controlvm XP savestate
```then using update-rc.d to create the links```
sudo update-rc.d shutVM start 01 0 6 .
```but have stumbled across what appears to be a real issue. [This page]("http://www.iitk.ac.in/LDP/LDP/lfs/LFS-BOOK-6.1.1-HTML/chapter07/usage.html") says that > Links that start with an S in the rc0.d and rc6.d directories will not cause anything to be started. They will be called with the parameter stop to stop something. The logic behind this is that when a user is going to reboot or halt the system, nothing needs to be started. The system only needs to be stopped. This is no real help to me because I need a script to "start" / run when shutdown or reboot is called. I suppose the answer is to write a full script using skeleton as a template that is started when the system starts, and activated when the system shuts down. How would I do this? Seems like the long way round ;)

( I guess this is what vboxtool does well for a headless environment but it won't work for me in gui mode)

---

### Post by Jose Catre-Vandis on 2009-02-23
Solution to my challenge coming up, script writing and requiring a little testing :)

---

### Post by Jose Catre-Vandis on 2009-02-23
Solved, by me
HOWTO: Gracefully Shutdown VirtualBox VMs on Reboot or Shutdown of Ubuntu

[http://bimma.me.uk/2009/02/23/howto-gracefully-shutdown-virtualbox-vms-on-reboot-or-shutdown-of-ubuntu/](http://bimma.me.uk/2009/02/23/howto-gracefully-shutdown-virtualbox-vms-on-reboot-or-shutdown-of-ubuntu/)

or on Ubuntuforums in tutorials & tips

[http://ubuntuforums.org/showthread.php?t=1078689](http://ubuntuforums.org/showthread.php?t=1078689)

---

