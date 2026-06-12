---
title: "Ubuntu Server --configure -a error"
date: 2009-02-09
forum: Server Platforms
---

### Post by bradsh04 on 2009-02-09
I did a search for dpkg --configure -a and did not find any relevant posts on the forum.  So here goes my post:

I am new to the Ubuntu community and I cannot install or remove or run any commands.  Anytime I try to run an install command, like sudo apt-get install ubuntu-desktop, or sudo apt-get install gdm, Ubuntu returns and tells me to use this command:

sudo dpkg --configure -a

When I try that command, this is the error message that is returned:  
 Failed to parse default value `??????????? ?????? ;gtk-theme-selector.desktop,
???????????? ??????????? ???;default-applications.desktop,??????????? ????;gnome
-cups-manager.desktop]' for schema (/schemas/apps/control-center/cc_actions_list).

I can't run any commands without Ubuntu telling me to use dpkg --configure -a, and everytime I use that command I get the parse error and the remote terminal shuts down.

I have searched all over other linux forums and googled this a million times.  I can't seem to find a solution, and the server won't let me run anything until I use dpkg --configure -a successfully.  

Any help you guys can provide me with will be GREATLY APPRECIATED.  I will probably be checking this post everyday.

RB

---

### Post by bryanl on 2009-02-09
What I did to fix this one was to figure out which packages are being complained about. Then remove them completely, update, and get everything working with no complaints, then re-install the removed packages.

I found that the complaints were about much more than the problem package. I used Synaptic to remove the packages.

---

### Post by jimv on 2009-02-09
If I had to guess, you need to go into gconf-editor (press alt+f2 and type 'gconf-editor) and make the values for /apps/control-center/cc_actions_list look like this:

[IMG]http://www.jimvernon.com/images/Screenshot-Edit Key.png[/IMG]

---

### Post by bradsh04 on 2009-02-09
Excellent responses guys, and super fast too.  The only issue is I don't know how to apply them.

> **bryanl said:**
> What I did to fix this one was to figure out which packages are being complained about. Then remove them completely, update, and get everything working with no complaints, then re-install the removed packages.

I found that the complaints were about much more than the problem package. I used Synaptic to remove the packages.

How do I determine which packages are being complained about?  There is a schemas file in the error and when I do a find on that file it returns with a no such file or directory.  

> **jimv said:**
> If I had to guess, you need to go into gconf-editor (press alt+f2 and type 'gconf-editor) and make the values for /apps/control-center/cc_actions_list look like this:

[IMG]http://www.jimvernon.com/images/Screenshot-Edit Key.png[/IMG]

I have not even gotten the gui to work for the server edition yet.  I was trying to do a list of commands to get the GNOME desktop for the server version, or whatever GUI the Ubuntu distribution uses.  

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

Maybe it is not possible for me to get a GUI for ubuntu server.   From what I read these were the steps I were to follow to get the GUI to work, after I completed sudo apt-get install ubuntu-desktop I got this error message.  Now I can't do anything!!  I can't install or remove files, or perform any commands without getting the error about the sudo dpkg --configure -a autocrash command.

Thank you very much for the responses so far, as informative as they are I am still a lost newbie.  Hopefully I can get somewhere soon with this server.

RB

---

### Post by jimv on 2009-02-09
Ok, try these commands:

sudo mv ~/.gconf ~/.gconf.old 
sudo mv /etc/gconf /etc/gconf.old
sudo mv /usr/share/gconf /usr/share/gconf.old
sudo mv /var/lib/gconf /var/lib/gconf.old
sudo dpkg --configure -a

---

### Post by bradsh04 on 2009-02-10
Excellent, those commands seemed to work.  What exactly do they do? Restore the old gconf file before it was corrupted??

Now when I try to install applications, I get errors like this:

dpkg: ../../src/packages.c:265: process_queue: Assertion `!queue.length' failed.
No apport report written because MaxReports is reached already
                                                              E: Sub-process /usr/bin/dpkg exited unexpectedly

At least now I can run sudo dpkg --configure -a  and try again, but I still can't install anything.  I tried installing ubuntu desktop (for the GUI???), lynx, and nmap.  Is there something I am doing critically wrong?

---

