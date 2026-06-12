---
title: "Lotus Symphony Beta 3"
date: 2007-12-19
forum: The Cafe
---

### Post by laser_in_your_eye on 2007-12-19
Has anyone had success with Lotus Symphony Beta 3?  I was able to get it installed using the various guides for Beta 1, but now I can't open the program.  When I click on the icon in the Applications menu, I get the following error:

*There was an error creating the child process for this terminal*

If I try to open it manually via terminal, I get the following error:

/opt/ibm/lotus/Symphony/framework/shared/eclipse/plugins/com.ibm.productivity.tools.standalone.addin_3.0.0.20071213-2212/apps$ IBM\ Lotus\ Symphony
*bash: IBM Lotus Symphony: command not found*

If I manually go into this folder and try to open the Symphony icon, nothing happens.  Does anyone know what I'm doing wrong?

thanks.

---

### Post by Sandlot on 2007-12-21
Do not upgrade in Ubuntu 7.10.  Completely uninstall the previous version before attempting installation of Beta 3

Uninstall completely:

**sudo /opt/ibm/lotus/Symphony/_uninst/uninstaller.bin**

Close the wizard and make sure the ***hidden*** "/home/[user]/.lotus" file is deleted completely. You may have to take ownership of it to delete it: 

**sudo chown -R [user] ~/.lotus/**

Place the bin file in your root directory and use the following commands in order one at a time.

**sudo chmod +x IBM_Lotus_Symphony_linux.bin**

**sudo /IBM_Lotus_Symphony_linux.bin**

Allow the installation to complete and close the wizard.  

Use the following line before trying to launch from the menu:

**sudo chown -R [username] ~/.lotus/**

I have done this on two machines now and it is working well on both.

The OO.org speed tweak also works well.
File>Preferences>Symphony>Memory> change cache size to 128 M.

I hope this helps everybody.

---

### Post by smartboyathome on 2007-12-21
When trying to run the installer, I get this:

```
java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
JVMDUMP006I Processing Dump Event "abort", detail "" - Please Wait.
JVMDUMP007I JVM Requesting System Dump using '/home/aabbott/core.20071221.185351.17530.dmp'
JVMDUMP010I System Dump written to /home/aabbott/core.20071221.185351.17530.dmp
JVMDUMP007I JVM Requesting Snap Dump using '/home/aabbott/Snap0001.20071221.185351.17530.trc'
JVMDUMP010I Snap Dump written to /home/aabbott/Snap0001.20071221.185351.17530.trc
JVMDUMP007I JVM Requesting Java Dump using '/home/aabbott/javacore.20071221.185351.17530.txt'
JVMDUMP010I Java Dump written to /home/aabbott/javacore.20071221.185351.17530.txt
JVMDUMP013I Processed Dump Event "abort", detail "".
Aborted (core dumped)
```

I would like to try beta 3. Please help. Thanks. :)

---

### Post by benjamin1840 on 2007-12-22
Smartboyathome:

I had the same Java Dump problem with Fedora 8, but this is how I got around it:

1) Hit Ctrl-Alt-F1 to exit X.

2) Log in with your name and password at the prompt.

3) Make the .bin file executable, as described by sandlot: "sudo chmod +x IBM_Symphony_Linux.bin"

4) Execute the file in console mode: "./IBM_Symphony_Linux.bin -console"

5) Go through the questions, which offer default responses. (For me, there was a 10-minute gap between each question.)

6) Receive word that installation is complete. 

7) Start X back up. (I actually rebooted my computer at this point, since I do not know the correct command for getting back to gdm.)

8) Cross your fingers that there is a new menu entry: Applications > Office > IBM Lotus Symphony. 

One last note: since you are a Ubuntu user, you might have to start by hitting sudo-Ctrl-Alt-F1. This could be a problem, since very few keyboards have a sudo button nowadays. 

I hope this is helpful.

-Ben

---

### Post by laser_in_your_eye on 2007-12-25
> **Sandlot said:**
> Do not upgrade in Ubuntu 7.10.  Completely uninstall the previous version before attempting installation of Beta 3

Uninstall completely:

**sudo /opt/ibm/lotus/Symphony/_uninst/uninstaller.bin**

Close the wizard and make sure the ***hidden*** "/home/[user]/.lotus" file is deleted completely. You may have to take ownership of it to delete it: 

**sudo chown -R [user] ~/.lotus/**

Place the bin file in your root directory and use the following commands in order one at a time.

**sudo chmod +x IBM_Lotus_Symphony_linux.bin**

**sudo /IBM_Lotus_Symphony_linux.bin**

Allow the installation to complete and close the wizard.  

Use the following line before trying to launch from the menu:

**sudo chown -R [username] ~/.lotus/**

I have done this on two machines now and it is working well on both.

The OO.org speed tweak also works well.
File>Preferences>Symphony>Memory> change cache size to 128 M.

I hope this helps everybody.

Worked for me!  Beta 3 is running...  THANKS!

---

### Post by DeadSuperHero on 2007-12-25
Also, don't forget to navigate to:

/home/username/.lotus

then  sudo chown -R userame:username .lotus

---

### Post by prince_niceguy on 2008-01-28
you can go back to x using ctrl + alt + F7... I am trying to install symphony. Hope this time it works. I have tried in windows and it is impressive.

---

### Post by old_salt on 2008-02-12
I'm unable to get either Beta3 or 4 to install on any of my Ubuntu systems both 64bit and 32bit. 

Here's my error logfile.

---

