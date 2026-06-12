---
title: "Virtual Machines and Security"
date: 2009-10-17
forum: The Cafe
---

### Post by niallabrown on 2009-10-17
This is just a simple questions and I don't want to start a war.  I am trying to set up a virtual machine with a very secure Linux distro to sit on top of my Windows install for web tasks that require better security.  I was wondering what distro and what browser people think would provide the most secure experience.  I do love Ubuntu for my every day stuff but if anyone wants to make a case for Ubuntu or another distro that is simply to maintain (i.e. a gui to install updates) I would love to hear it.  I also use firefox now but I have heard the Konqueror is very secure also.

Any thoughts?

---

### Post by Sporkman on 2009-10-17
Any linux distro would be perfectly fine (except, of course, for [DVL]("http://ubuntuforums.org/showthread.php?t=1094200")).

---

### Post by Rainstride on 2009-10-17
> **niallabrown said:**
> This is just a simple questions and I don't want to start a war.  I am trying to set up a virtual machine with a very secure Linux distro to sit on top of my Windows install for web tasks that require better security.  I was wondering what distro and what browser people think would provide the most secure experience.  I do love Ubuntu for my every day stuff but if anyone wants to make a case for Ubuntu or another distro that is simply to maintain (i.e. a gui to install updates) I would love to hear it.  I also use firefox now but I have heard the Konqueror is very secure also.

Any thoughts?

ubuntu is probably just as secure as any other distro, if not more so. keep in mind though your virtual machine will only be as secure as the windows machine you are installing atop.

---

### Post by Dr. C on 2009-10-17
The danger here is that if the host OS gets compromised by say a keyboard logger the security of the uber secure OS in the virtual machine will get compromised by the very same keyboard logger. It makes more sense to have the most secure OS and the host and the least secure OS as the guest.

---

### Post by Frak on 2009-10-17
Debian stable probably. BSD would be a good choice too.

---

### Post by niallabrown on 2009-10-17
I see.  I was under the impression that using a VM would solve most security issues that but I can see how a virtual machine wouldn't fix a problem like key logging.  So maybe a dual boot with Ubuntu or Debian on that machine would be the best option.

Any considerations with browsers?  Is firefox the most secure or would another browser be better?  I assume Firefox is targeted quit a bit being a very popular browser but I know it also receives many fixes and updates from having a big community.   Should I stick with that?

---

### Post by HappyFeet on 2009-10-18
> **Rainstride said:**
> ubuntu is probably just as secure as any other distro, if not more so. keep in mind though your virtual machine will only be as secure as the windows machine you are installing atop.

True. You are better off installing ubuntu and running windows in a VM.

---

### Post by carnagex420x on 2009-10-18
Try a Virtual Appliance, [http://www.vmware.com/appliances/directory/80]("http://www.vmware.com/appliances/directory/80"). The only down side is, you are running on Ubuntu 5.10, so you miss out on newer updates, fixes and features. There is also an older version of firefox installed leaving you with the same problem. But still not bad...

---

### Post by carnagex420x on 2009-10-18
ALSO,
> **HappyFeet said:**
> True. You are better off installing ubuntu and running windows in a VM.

Truth! Unless you need to run games on the machine, theres no reason for windoze in my opinion.

---

### Post by Rainstride on 2009-10-18
> **niallabrown said:**
> I see.  I was under the impression that using a VM would solve most security issues that but I can see how a virtual machine wouldn't fix a problem like key logging.  So maybe a dual boot with Ubuntu or Debian on that machine would be the best option.

Any considerations with browsers?  Is firefox the most secure or would another browser be better?  I assume Firefox is targeted quit a bit being a very popular browser but I know it also receives many fixes and updates from having a big community.   Should I stick with that?

a duel boot is a lot safer. but there is a chance if the windows partition is infected with something, it could messup the MBR. but the up side is the mal-ware can't read the ubuntu partition. so you don't really have to worry at all with a duel boot.

> **HappyFeet said:**
> True. You are better off installing ubuntu and running windows in a VM.
that's what I do, though I do it because im bored. not because i need windows.:)


> **carnagex420x said:**
> ALSO,


Truth! Unless you need to run games on the machine, theres no reason for windoze in my opinion.

sometimes not even for games:).

---

### Post by earthpigg on 2009-10-18
the thing that i personally would not like about full-blown ubuntu in a VM with a Windows host OS is overhead... the hard drive and ram use required, in addition to CPU cycles being eaten up by background services that will likely serve you no purpose. remote desktop viewer in your vm? et cetera.

all you need for your task is:

1) GNU/Linux
2) [X Window System]("http://en.wikipedia.org/wiki/X_Window_System")
3) the lightest window manager possible
4) firefox
5) not an obsene amount of hassle

here is how i personally would do it, using ubuntu tools...

do an ubuntu command line only install.

```
sudo apt-get install gdm xorg openbox firefox
```

gdm will make the virtual machine automatically boot to a graphical environment.

xorg is the X Window System.

openbox is a popular window manager.

firefox is firefox.



a 2gb virtual hard disk and 256mb of ram will be PLENTY for that virtual machine.


if that is to much of a hassle, pick your lightweight ubuntu derivative, download it's .iso, and go with that.

---

### Post by hessiess on 2009-10-18
> **HappyFeet said:**
> True. You are better off installing ubuntu and running windows in a VM.

this.

---

### Post by niallabrown on 2009-10-18
I was trying to simplify the request but let me explain.  I run Ubuntu and Kubuntu full-time on 3 machines but my fiance wont touch them.  The idea was if I could have her windows machine boot into a Linux distro that just pops up firefox or another browser she wouldn't know the difference. If the install is still vulnerable to key loggers on VM, I think what I`ll do is get a light weight ubuntu derivative and install it beside her windows.  I can just make firefox pop up on start up and show her how to select the right grub entry and how to shut down.

> 2) X Window System
3) the lightest window manager possible
I think that a light weight ubuntu derivative will work fine but I will also look into your first suggestion further.

---

### Post by carnagex420x on 2009-10-18
sounds like you need something along the lines of Splashtop, or the Google Chrome OS. Something to get you straight online and is separate from windows all together. If you are going to do a dual boot and need a light ubuntu distro check out Lubuntu, [http://www.linux-mag.com/cache/7520/1.html]("http://www.linux-mag.com/cache/7520/1.html"). It uses "LXDE (Lightweight X11 Desktop Environment), which is in-turn based on Openbox."

---

### Post by earthpigg on 2009-10-18
though LXDE uses openbox by default, it is not *based on* openbox.

in fact, you can use LXDE *without* openbox.

---

