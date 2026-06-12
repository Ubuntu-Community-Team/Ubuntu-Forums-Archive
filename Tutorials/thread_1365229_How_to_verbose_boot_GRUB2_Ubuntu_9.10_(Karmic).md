---
title: "How to verbose boot GRUB2 Ubuntu 9.10 (Karmic)"
date: 2009-12-27
forum: Tutorials
---

### Post by nbx909 on 2009-12-27
I know that you can find this stuff looking around but I did not find a simple tutorial for those of us new to GRUB2 and want verbose boot. There are many reasons for verbose boot, I personally like to make sure my computer hasn't frozen or got stuck on a boot process.


**Here is how you do it:**
[INDENT]Take your favorite editor (nano, vi, gedit) and open up /etc/default/grub 
My favorite editor is gedit so I did:
[INDENT]```
 sudo gedit /etc/default/grub

```[/INDENT]
Find the line that says

[INDENT]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and remove the quiet part so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="splash"
```[/INDENT]
Then save and close out of your editor

Then run this command to finalize it:
[INDENT]```
sudo update-grub
```[/INDENT]
This took a few minutes for me to run so don't panic if you don't see anything happening at first. 
[/INDENT]
After the previous command is finished you should be able to reboot and when you boot up you will have a verbose boot.




***If you also do not want to the splash screen then change **
[INDENT]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to 
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```[/INDENT]



***If you want the bootloader menu you can change **
[INDENT]```
GRUB_HIDDEN_TIMEOUT=0
```
to
```
# GRUB_HIDDEN_TIMEOUT=0
```
[/INDENT]
and change
[INDENT]```
GRUB_HIDDEN_TIMEOUT_QUIET=true 
```
to
```
GRUB_HIDDEN_TIMEOUT_QUIET=false 
```[/INDENT]

and change
[INDENT]```
# GRUB_TIMEOUT=10 
```
to
```
GRUB_TIMEOUT=10 
```[/INDENT]
This says that it will automatically boot the 1st OS (ubuntu) in 10 seconds unless a key stroke is recorded then it will stop the count down. If you don't want it to automatically select the 1st OS set it equal to -1. This will require you to manually select an OS from the list.


**_*Remember to run ```
sudo update-grub
``` after any changes._**

Here is my config:
[INDENT] 
```
 #If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```[/INDENT]


_sources:_
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by marseille on 2010-01-17
thank-you... exactly what i wanted to know:

> GRUB_CMDLINE_LINUX_DEFAULT=""


-     -     -


N o t e s:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://grub.gibibit.com/](http://grub.gibibit.com/)
[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)
[http://ubuntuforums.org/showthread.php?t=1182436](http://ubuntuforums.org/showthread.php?t=1182436)

---

### Post by fat yak on 2011-11-21
Thank you, I had a problem with grub hanging at the Ubuntu logo screen.
By hitting CTRL-ALT-F2 I was able to login and edit the file with vi /etc/default/grub (gedit wouldn't work).
This alllowed me to follow the process and work out that the hang was due to a faulty rules file I had inserted.

P.S. Long live the forums!!!!

---

