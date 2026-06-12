---
title: "Maverick has suddenly Unity installed and home folder empty! o.O Have I been hacked?"
date: 2011-08-21
forum: Security
---

### Post by Holker on 2011-08-21
I have posted this before in another category, but I do not get any replies, so once more:
> **Holker said:**
> A couple of days ago I checked for updates and installed Playonlinux 4.0.2 from 4.0.1 and shut down my laptop after that. The following morning I started up my laptop with dualboot; in Grub I selected to start up with Maverick OS and it started loading it up; Ubuntu 10.10 loading screen was normal; Login screen normal too; typed in password and pressed enter and then I get the following error message: > Could not update ICEauthority file /home/holker/.ICEauthority
[Close] I closed the error message and then I get the following error message: [QUOTE]There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)
[Close] Closed that error message as well and then suddenly I have a Unity desktop, which I *NEVER* installed or asked for! o_O And of course another error message appears: > **Nautilus could not create the following required folders: /home/holker/Desktop, /home/holker/.nautilus**
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.
[Ok]                      I closed this, tried to start up Firefox, but it wont... I can open terminal and also text editor... I checked my directory /home/holker/ and there are just 2 files in there;
Access-Your-Private-Data.desktop containing the following text:
```
[Desktop Entry]
_Name=Access Your Private Data
_GenericName=Access Your Private Data
Exec=/usr/bin/ecryptfs-mount-private
Terminal=true
Type=Application
Categories=System;Security;
X-Ubuntu-Gettext-Domain=ecryptfs-utils

```and a README.txt file containing text: ```
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
"Access Your Private Data"

or

From the command line, run:
ecryptfs-mount-private
```I have been looking in this forum for possible solutions and I found this thread: [http://ubuntuforums.org/showthread.php?t=1366173&highlight=ICEauthority](http://ubuntuforums.org/showthread.php?t=1366173&highlight=ICEauthority)
I tried the following things
```
sudo chown holker:holker .ICEauthority
```Then I tried the next advise in the thread:
```
sudo apt-get remove nautilus
sudo shutdown -r now
sudo apt-get install nautilus
sudo shutdown -r now
```it reinstalled nautilus (now idea what kind of program it is btw), but nothing changed... so the next tip in the thread:
```
ls -la /home/
sudo chown holker:holker /home/holker
```nothing... next thing:
```
sudo apt-get install gnome-panel
```Latest version already installed... so I then tried the command in the README.txt file...
```
sudo ecryptfs-mount-private
```...which didnt work either.
All I got now is an extra error in the Ubuntu 10.10 loading screen, before the login screen, so all in all I think I just made matters worse... 
What is going on in my Ubuntu Maverick OS??? Have I been hacked? Because I did not install Unity and it isn't some default setting in Maverick, is it? And how do I get things back to normal? I had a lot of back-ups and new updates saved for my website in my /home/holker directory, which is lost now; how do I get this back?
Can anyone help me out please?[/QUOTE]

---

### Post by An Sanct on 2011-08-21
If you did not use encryption, then you can access your home folder from a Live USB.

Maybe you partially upgraded to natty (check if this is disabled in the update manager settings) If so ... then ... you can hardly turn back.

edit: the probability, that you where hacked are somewhere about 1,3% ... I'm not saying it is impossible, rather hard to believe. (have you got enemies? :))

---

### Post by kerry_s on 2011-08-21
10.10 netbook is the first version of unity desktop, if you were running 10.04 then you must have done a distro update(sudo apt-get dist-upgrade) or excepted the update from update-manager telling you there was a newer version.

---

### Post by Holker on 2011-08-21
> **An Sanct said:**
> If you did not use encryption, then you can access your home folder from a Live USB.

Maybe you partially upgraded to natty (check if this is disabled in the update manager settings) If so ... then ... you can hardly turn back.

edit: the probability, that you where hacked are somewhere about 1,3% ... I'm not saying it is impossible, rather hard to believe. (have you got enemies? :))Well, they say; you aren't somebody until you have made an enemy... but then again; I can be pretty paranoid. ;)

I am pretty sure I have encrypted my home directory at the installation of Ubuntu 10.10 Netbook. I did not install or run 10.04 and upgrade from there. At the moment this is how my home directory looks like:```
ls -la
total 12
dr-x------ 3 holker holker 4096 2011-08-01 20:23 .
drwxr-xr-x 4 root   root   4096 2011-08-01 20:17 ..
lrwxrwxrwx 1 holker holker   56 2011-08-01 20:17 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwx------ 7 holker holker 4096 2011-08-18 12:41 .cache
lrwxrwxrwx 1 holker holker   32 2011-08-01 20:17 .ecryptfs -> /home/.ecryptfs/holker/.ecryptfs
lrwxrwxrwx 1 holker holker   31 2011-08-01 20:17 .Private -> /home/.ecryptfs/holker/.Private
lrwxrwxrwx 1 holker holker   52 2011-08-01 20:17 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
```When I do the following command, I get the following error:```
ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
```This is probably duh-huh and pretty obvious for you guys:```
sudo chown holker:holker .ICEauthority
chown: cannot access `.ICEauthority': No such file or directory
```"sudo chown holker:holker /home/holker" doesnt change any permission.

I have checked the Update Manager Settings and tried to make screenshots, but that doesnt work either, along with Firefox browser, Empathy webbrowser, internet, and Download Software Center among other things...
Anyway; in the "Ubuntu Software" tab of the Update Manager Settings the first 4 options are checked (main, universe, restricted and multiverse). 'Source code' option is not checked. In the "Updates" tab the Important Security - and Recommended Updates are checked, Proposed - and Unsupported Updates are not checked. All 4 say they are maverick btw.

So... what has really happened and what can I do about it? :confused: Can I somehow look into some installation logs or update/upgrade logs? (please don't tell me they are in my home directory :( ) And how do I setup my encrypted private directory properly?

---

### Post by Holker on 2011-08-24
All is lost? :(

---

### Post by westie457 on 2011-08-24
Hi, having stumbled across this thread there is something you can try to save the files that you want. This is a not very elegant way and might not work, however no harm in trying.

Remove the hard drive and hook it up to a Windows machine running Vista or 7 or even XP.
Boot into a LiveCD Desktop and copy the contents of the /home folder including the hidden files (hit <Ctrl>+h to show hidden files) to a NTFS partition. When that has completed shut down the Computer and remove your harddrive. Start Windows and check to see which files you can now look at. You might be able to see those in the encrypted folder.

Windows does not understand Ubuntu file permissions so usually removes them.

Hope this is some help for you.

---

### Post by FatalMessenger on 2011-08-24
Okay, by the looks of it you have set up an encrypted home folder, in which case follow the link below to a guide written by Dustin Kirkland on how to recover your data.
[URL="http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html"]
[/URL][http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

EDIT: Sorry, wrong link.

---

### Post by Holker on 2011-08-25
Tried copying the home directory from the live cd to Windows, but it cannot be done because I do not have permission to read it.  How do I log out of the "ubuntu" username and log in with my "holker" username on the live cd? That way I would have permission I think...
Also tried the steps of Dustin, but my home/.ecryptfs/holker/ directory is completely empty and therefore this does not work either. :(

What now? Is my Maverick OS with Unity installed now unrepairable? Is there no way to fix it?
Am I one of the 77 people who got hacked? Because I really did not install Unity or do some partial upgrade; I just updated the Playonlinux application before all this happened... so odd...

---

### Post by westie457 on 2011-08-25
Sorry in my last post I forgot to say that using in a terminal the command ```
gksudo nautilus
``` will allow you to copy/move/delete anything you want from your hard drive. So be very careful what you do while this particular instance of nautilus is open. Any error messages that appear in the terminal window can be ignored.

The nautilus window will open showing /root and other things in the left pane and a Desktop icon in the right.
Navigate to your home folder by starting with the name of your internal hard drive > File System > home folder > (whatever).

---

### Post by Holker on 2011-08-26
> **westie457 said:**
> Sorry in my last post I forgot to say that using in a terminal the command ```
gksudo nautilus
``` will allow you to copy/move/delete anything you want from your hard drive. So be very careful what you do while this particular instance of nautilus is open. Any error messages that appear in the terminal window can be ignored.

The nautilus window will open showing /root and other things in the left pane and a Desktop icon in the right.
Navigate to your home folder by starting with the name of your internal hard drive > File System > home folder > (whatever). This works, thank you. But unfortunately my "99problems" folder wasn't in there, so I guess all my work is lost...

Anyways, next problem, how do I fix my Maverick OS? Or should I consider this OS also as lost on that partition and just reinstall another OS on top of it?

---

### Post by westie457 on 2011-08-28
> **Holker said:**
> This works, thank you. But unfortunately my "99problems" folder wasn't in there, so I guess all my work is lost...

Anyways, next problem, how do I fix my Maverick OS? Or should I consider this OS also as lost on that partition and just reinstall another OS on top of it?

Apologies for the late reply and hopefully it is not too late.

Personally I would just reinstall maverick to the original folder and partition with out formatting anything. This resets the system files without removing any of the stuff in your home folder. If reinstalling and there are things you do not want to use, before running the set up open nautilus hit Ctrl+H to show hidden files and delete the stuff not required. 99 times out of 100 personal files are left alone so to be safe make a back-up of what you want to keep.

After the reinstall Update Manager will run, un-check the updates you do not want and everything should be fine.

---

### Post by Holker on 2011-08-29
> **westie457 said:**
> Apologies for the late reply and hopefully it is not too late.

Personally I would just reinstall maverick to the original folder and partition with out formatting anything. This resets the system files without removing any of the stuff in your home folder. If reinstalling and there are things you do not want to use, before running the set up open nautilus hit Ctrl+H to show hidden files and delete the stuff not required. 99 times out of 100 personal files are left alone so to be safe make a back-up of what you want to keep.

After the reinstall Update Manager will run, un-check the updates you do not want and everything should be fine.

Last weekend I found my 31 digit/letter passphrase... isn't there something I can do with that?

---

