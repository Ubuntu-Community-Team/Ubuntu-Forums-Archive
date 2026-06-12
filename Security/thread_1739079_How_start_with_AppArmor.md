---
title: "How start with AppArmor ?"
date: 2011-04-25
forum: Security
---

### Post by Borneq on 2011-04-25
I am beginner in Linux Security Modules. I want to reach maximum security.
I have Ubuntu 10.10. If I call "apt-get install apparmor", it error:
AppArmor not available as kernel LSM
AppArmor is already installed or I must install? How call it? Command "apparmor" not found...

---

### Post by bodhi.zazen on 2011-04-25
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by Borneq on 2011-04-25
> **bodhi.zazen said:**
> [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

sudo apt-get install apparmor-profile
I try but can't found package apparmor-profile

and 
> 
borneq@borneq-VirtualBox:~$ sudo /etc/init.d/apparmor status
 * AppArmor not available as kernel LSM.
   ...fail!

AppArmor not available as kernel LSM - why?

---

### Post by bodhi.zazen on 2011-04-25
```
sudo apt-get install apparmor-profile**[color=darkred]s**[/color]
```

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apparmor-profile&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apparmor-profile&searchon=name&subword=1&version=all&release=all)

---

### Post by Borneq on 2011-04-25
> **bodhi.zazen said:**
> ```
sudo apt-get install apparmor-profile**[COLOR=darkred]s[/COLOR]**
```[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apparmor-profile&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apparmor-profile&searchon=name&subword=1&version=all&release=all)
Yes, I have already installed but "AppArmor not available as kernel LSM" means that my kernel is not adapted to AppArmor ?
(I have Polish Ubuntu 10.10 Malinowa Mandarynka)

---

### Post by bodhi.zazen on 2011-04-25
What kernel are you running ?

What is the exact command you are running and what is the exact output ?

copy-paste from your terminal here.

If it is the default ubuntu kernel, and not a custom kernel, try another kernel and file a bug report on launchpad.

---

### Post by Borneq on 2011-04-25
Release 10.10 (maverick)
Kernel 2.6.35-28-generic
GNOME 2.32.0

Command: "sudo /etc/init.d/apparmor status"
I am beginner, how can use another kernel, where is launchpad?

---

### Post by bodhi.zazen on 2011-04-25
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

It seems there is a significant problem with that kernel. Did you install the virtualbox additions ? Wonder if they changed the kernel.

When you boot Ubuntu, at the boot menu, you can select various kernels.

---

### Post by Borneq on 2011-04-25
> **bodhi.zazen said:**
> [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

It seems there is a significant problem with that kernel. Did you install the virtualbox additions ? Wonder if they changed the kernel.

When you boot Ubuntu, at the boot menu, you can select various kernels.

Yes, You guess. I am Windows user and I use Linux only in virtual machine (VirtualBox), VirtualBox additions is necessary to communicate between Windows and Linux
I will create launchpad account

---

### Post by bodhi.zazen on 2011-04-25
The virtualbox additions are not necessary at all (you can use any number of network protocols without them such as samba), but that is another discussion. 

The additions should not interfere with apparmor, but you might wish to re-install and try apparmor without the additions. Probably the first thing you will be asked to do when you file a bug on launchpad.

In addition, you can install the (open source) additions via apt-get.

[http://packages.ubuntu.com/maverick/virtualbox-ose-guest-utils](http://packages.ubuntu.com/maverick/virtualbox-ose-guest-utils)

[http://packages.ubuntu.com/maverick/virtualbox-ose-guest-x11](http://packages.ubuntu.com/maverick/virtualbox-ose-guest-x11)

Those packages are, IMO, easier to install and maintain then compiling them from the VirtualBoxAdditions.iso

---

### Post by Borneq on 2011-04-25
How can uninstall additions? I install new system without Virtualbox additions and is OK.

---

### Post by bodhi.zazen on 2011-04-25
> **Borneq said:**
> How can uninstall additions? I install new system without Virtualbox additions and is OK.

You can, but it is not so easy and it will not likely fix your problem.

Run the installer again, add "uninstall" to the end , without quotes.

Or you can remove it by running the script in /opt

```
/opt/VBoxGuestAdditions-4.0.6/uninstall.sh
```

Replace "4.0.6" with the proper version (if needed).

EDIT You can probably install the packages I gave you earlier for the guest additions (using apt-get) if needed or learn how to use samba.

---

### Post by Borneq on 2011-04-26
> **bodhi.zazen said:**
> 
[http://packages.ubuntu.com/maverick/virtualbox-ose-guest-utils](http://packages.ubuntu.com/maverick/virtualbox-ose-guest-utils)
[http://packages.ubuntu.com/maverick/virtualbox-ose-guest-x11](http://packages.ubuntu.com/maverick/virtualbox-ose-guest-x11)


Is OK for this packages!

---

### Post by Borneq on 2011-04-26
I start.
After command "sudo genprof gedit" (without run Gedit) it creates small usr.bin.gedit file:
> 
# Last Modified: Tue Apr 26 09:05:40 2011

#include <tunables/global>



/usr/bin/gedit flags=(complain) {

  #include <abstractions/base>



}
in /etc/apparmor.d/
and Gedit can't correctly run. 
I can delete /etc/apparmor.d/usr.bin.gedit with root privilege or is any tool for deleting?
I run "sudo aa-complain gedit" and run Gedit but /etc/apparmor.d/usr.bin.gedit not changes...

---

### Post by rookcifer on 2011-04-26
> **Borneq said:**
> I start.
After command "sudo genprof gedit" (without run Gedit) it creates small usr.bin.gedit file:
in /etc/apparmor.d/
and Gedit can't correctly run. 
I can delete /etc/apparmor.d/usr.bin.gedit with root privilege or is any tool for deleting?
I run "sudo aa-complain gedit" and run Gedit but /etc/apparmor.d/usr.bin.gedit not changes...

You need to run 

```
sudo aa-logprof
```

and answer the questions in order to create the profile.  Actually when you first ran aa-genprof it automatically puts the profile in complain mode and will pop-up questions on the terminal screen until you click "Finished."

---

### Post by bodhi.zazen on 2011-04-26
> **Borneq said:**
> I start.
After command "sudo genprof gedit" (without run Gedit) it creates small usr.bin.gedit file:
in /etc/apparmor.d/
and Gedit can't correctly run. 
I can delete /etc/apparmor.d/usr.bin.gedit with root privilege or is any tool for deleting?
I run "sudo aa-complain gedit" and run Gedit but /etc/apparmor.d/usr.bin.gedit not changes...

Keep going with the apparmor sticky. 

genprof generates a minimal set of rules, you will need to add a ton of paths for something like gedit running in X =)

---

