---
title: "Is Server 7.04 Command-line Only?"
date: 2007-05-10
forum: Server Platforms
---

### Post by galume on 2007-05-10
Team- Is server 7.04 command-line only? :confused:  If there's a GUI how to you initate it from the command-line?  Thanks in advance! (posted in Absolute Beginner Talk before finding this forum...:-p)

---

### Post by ohgod on 2007-05-10
Yes, all the 'server' versions don't come with a gui.

If you want a gui, you can install one like so:  (be warned it'll take quite a while)
```

sudo apt-get install ubuntu-desktop

```

---

### Post by galume on 2007-05-10
Thanks!  It is installing, and it IS taking a while like you said.  Will the GUI start automatically upon restart, or is there a command to start the GUI once installed?

The reason we're going GUI is that we don't have a need for security on this server- it's internal testing only.

Thanks :)

---

### Post by ohgod on 2007-05-10
Glad it's working out for you.

Yeah, the GUI should start up automatically when it's all done (you'll probably have to reboot).

---

### Post by galume on 2007-05-10
OK, it's done and I'm at the command prompt again.  Tried all the commands I could dream up...what's the restart command? :-k

---

### Post by galume on 2007-05-10
Hey...nevermind, got it...'shutdown now -r'  I rebooted, and am still at the command prompt logged in.  Any ideas on a command to start the desktop interface?

Thanks!

---

### Post by StarMonkee on 2007-05-10
Try running 'startx'

---

### Post by galume on 2007-05-10
That got me this:
Fatal Server Error
No Screens Found
x10 fatal IO erro 104 (connection reset by peer) on X server ":0.0"
After 0 requests (0 known processed) with 0 events remaining
user@computer:~$

back to the prompt

---

### Post by Pro_D on 2007-05-11
I am new to ubuntu (see my registration date) and running 6.06 myself but this might help.

I remember getting some error messages durring the install of ubuntu-desktop and the commands that the failed install instructed me to run didn't work (typo? I don't remember the command).  I remembered comming across something called xserver-xorg in earlier searches.  I decided to type in "sudo apt-get install xserver-xorg".  After that was done I tried "sudo apt-get install ubuntu-desktop" again and it worked.  Also if you are wanting the computer to always boot to a gui and it doesn't automaticaly take you to one on your next reboot you will want to type in "sudo apt-get install gdm" (which is supposed to get installed with ubuntu-desktop package).  The gdm is the desktop manager for gnome.

The above is what I did to get the install that I am typing this in with.

Another thought is if somehow the desktop package is installed badly (damaged?) you could try "sudo apt-get --reinstall install ubuntu-desktop".  I would try this last if the above still fails.  Pretty sure that --reinstall will uninstall and then install the ubuntu-desktop again.

Hopefully that is helpful.

---

### Post by agamum on 2007-05-12
hi!

I'm in a similar case, just installed lamp server and after installed a gui (xfce) and it starts automatically after reboot, but I dont like that.

I want to boot only in command line and starts X server only when I really need.

But dont know how to get this done... :( somebody can help me please???

I have searched for this and cant find anything for this exactly in the forum.

I run command "runlevel" after start and says "2",  I read something about if I do chmod -x in the rc2.d over the xserver it will stop to run next reboot, but this doesnt works for me...

I got this in the rc2.d directory:

                       S19cupsys        S89anacron
S05vbesave                   S19hplip         S89atd
S10acpid                     S19mysql         S89cron
S10powernowd.early           S20apmd          S91apache2
S10sysklogd                  S20apport        S98usplash
S10xserver-xorg-input-wacom  S20hotkey-setup  S99acpi-support
S11klogd                     S20makedev       S99rc.local
S12dbus                      S20powernowd     S99rmnologin
S13gdm                       S20rsync         S99stop-readahead
S17mysql-ndb-mgm             S20ssh
S18mysql-ndb                 S50proftpd

So I chmoded -x to S10xserver-xorg-input-wacom but this dont do nothing, when I reboot the X server is automatically started again.


Any help please??

---

### Post by Pro_D on 2007-06-02
It's probably too late by now but I thought I would throw this up anyway.  I have been away from my only linux computer for 3 weeks (and missing it while using windows).

I also didn't want to have my server booting a gui on startup.  Luckily for a while I took lots of notes and so I have this little thing for ya: sysv-rc-conf.  That is how it shows up in the synaptic package manager .  Once you have that installed then open up a terminal and use sudo sysv-rc-conf.  Once there you will want to disable (un-x) gdm entries.  Since I didn't realy know what I was doing precisely I disabled gdm at runlevel 2, 3, 4, and 5 but I honestly don't know just how many run levels you are 'supposed' to kill.

The result of this is when my test server boots up I get the nice graphical start sequence like an Ubuntu desktop install, when that is finished I get a regular text prompting me for a username and a password.  After I input those I get a nice simple text prompt like we got before we installed the desktop on top.

When you type startx (don't need or want to sudo that and it doesn't matter what environment you use, I think) you get a desktop rather quickly much faster than I expected.  The place you would go to reboot/shutdown the computer now have those options removed. Log off now simply shuts off whatever graphical desktop you picked, you remain loged into your user account that you typed on the text prompt at boot though.

From reading apparently this doesn't disable the shutdown scripts, just the startup ones. I haven't seen any error messages yet, but then I haven't gone through all the logs either.

One other thing, I did not expect the GUI admin programs to work with the text admin programs but so far they do, for example, changes you make in synaptic package manager get reflected in the apt-get so don't worry to much about not being able to make changes in different environments (like I did).  I guess I got used to programs not really talking to eachother.

---

