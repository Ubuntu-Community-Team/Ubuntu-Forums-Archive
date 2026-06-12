---
title: "VMWare won't work..."
date: 2010-11-18
forum: Virtualisation
---

### Post by camn on 2010-11-18
Hello... I just tried installing VMWare but it gave me this...
```
sudo perl /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 

/usr/bin/vmware-config.pl: can't open EULA file: No such file or directory
Execution aborted.
``` What do I do? D:

---

### Post by ENigma885 on 2010-11-18
It sounds like the installer is trying to stop some services but failed. Also it cannot access the End User License Agreement file. 

Why VMWare, basically? I have had a horrible experience using it. I recommend [COLOR="RoyalBlue"]VirtualBox[/COLOR] instead. Downloadable form [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by stefangr1 on 2010-11-18
You probably started the wrong script. /usr/bin/config.pl is to reconfigure vmware when its already installed. You have to run the install script provided with the version of vmware that you downloaded.

The fact that the config.pl script failed to stop some services probably means that they aren't running in the first place...

---

### Post by camn on 2010-11-18
> **ENigma885 said:**
> It sounds like the installer is trying to stop some services but failed. Also it cannot access the End User License Agreement file. 

Why VMWare, basically? I have had a horrible experience using it. I recommend [COLOR="RoyalBlue"]VirtualBox[/COLOR] instead. Downloadable form [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.virtualbox.org/wiki/Linux_Downloads").

Trying to install Windows 7 on my computer, I don't have any CDs big enough to put the ISO on, and unetbootin is being mean... Someone said you can use a physical HD instead of a virtual one in VMware.

---

### Post by camn on 2010-11-18
> **stefangr1 said:**
> You probably started the wrong script. /usr/bin/config.pl is to reconfigure vmware when its already installed. You have to run the install script provided with the version of vmware that you downloaded.

The fact that the config.pl script failed to stop some services probably means that they aren't running in the first place...

I installed from the RPM...

---

### Post by CharlesA on 2010-11-18
> **camn said:**
> I installed from the RPM...

What host OS are you using? You can't use RPMs in Ubuntu without converting them (which is messy).

---

### Post by camn on 2010-11-18
> **CharlesA said:**
> What host OS are you using? You can't use RPMs in Ubuntu without converting them (which is messy).

I'm using Ubuntu... I used ```
sudo alien -i -c (nameofrpm).rpm
``` How would I go about uninstalling the messed up RPM installation to install from the .tar.gz?

---

### Post by CharlesA on 2010-11-18
You could try removing it from Synaptic or using apt-get, but I don't know if that'll work or not.

As a general rule of thumb, it's better to install from source then convert a rpm to a deb and install it that way.

---

### Post by camn on 2010-11-18
> **CharlesA said:**
> You could try removing it from Synaptic or using apt-get, but I don't know if that'll work or not.

As a general rule of thumb, it's better to install from source then convert a rpm to a deb and install it that way.

Okay, I'm installing it from the .tar.gz... It's asking me "What is the location of the directory of C header files that match your running
kernel?" And I have no idea what to answer... I'm running Ubuntu 10.10...

---

### Post by CharlesA on 2010-11-19
See here: [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by camn on 2010-11-21
> **CharlesA said:**
> See here: [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

```
There is a problem compiling the vmnet module after it was patched. :(
``` Error D: What does that mean? :/

---

### Post by CharlesA on 2010-11-21
I'm not sure. I haven't really used VMware on Ubuntu since it's such a royal pain in the butt to get installed.

---

### Post by fjgaude on 2010-11-22
> **CharlesA said:**
> I'm not sure. I haven't really used VMware on Ubuntu since it's such a royal pain in the butt to get installed.

come on. That's certainly not true of VMware Player 3.1.3.

---

### Post by CharlesA on 2010-11-22
> **fjgaude said:**
> come on. That's certainly not true of VMware Player 3.1.3.

I haven't used VMware Player on Ubuntu, only server, and the whole installation process is a huge mess.

I do, however, use VirtualBox with no problems. *shrugs*

---

### Post by fjgaude on 2010-11-22
Well, as you likely know, server is no longer supported by VMware... Player seems to be the one for individuals requiring virtual OSs. Player is still free but closed source code.

---

### Post by CharlesA on 2010-11-22
> **fjgaude said:**
> Well, as you likely know, server is no longer supported by VMware... Player seems to be the one for individuals requiring virtual OSs. Player is still free but closed source code.

What are you talking about?

VMWare Server 2.02 is still listed on VMware's site.

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

---

### Post by fjgaude on 2010-11-22
Let's see if there is ever a 2.03. <smile>

---

### Post by dcstar on 2010-11-28
> **camn said:**
> Hello... I just tried installing VMWare but it gave me this...
```
sudo **perl** /usr/bin/vmware-config.pl
.........
/usr/bin/vmware-config.pl: can't open EULA file: No such file or directory
Execution aborted.
``` What do I do? D:

This instructions clearly say:

```
sudo vmware-config.pl
```

Why did you add in "perl"?

---

