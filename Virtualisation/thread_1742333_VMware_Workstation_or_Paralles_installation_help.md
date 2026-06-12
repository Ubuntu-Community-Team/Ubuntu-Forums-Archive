---
title: "VMware Workstation or Paralles installation help"
date: 2011-04-28
forum: Virtualisation
---

### Post by =Spider_Man= on 2011-04-28
[B][SIZE=3]Hello this is my second post asking for help.

Again I am a complete noob so sorry for this if it sounds dumb.

I wanted to install either VMware Workstation or Parallels on my Ubuntu 10.10 mav but I do not know how its done or if I am even downloading the right versions.

One guy from Parallels help center gave me a .exe to install Parallels in Ubuntu.

Now im not sure that he gave me the right link.

VMware gives me a linux link to download and install but i think that its also the wrong one. I believe its meant for version 9.04 and down.

Again I may be wrong about a lot of this because I am a noob.

If anyone can help me please let me know. Thank you very much

[/SIZE][/B]

---

### Post by bhaverkamp on 2011-04-28
Obviously the exe link is wrong. Which version of Workstation are you trying to install. Version 7 will run on Lucid and older; have not yet had a chance to try it on 11.04.

---

### Post by =Spider_Man= on 2011-04-28
> **bhaverkamp said:**
> Obviously the exe link is wrong. Which version of Workstation are you trying to install. Version 7 will run on Lucid and older; have not yet had a chance to try it on 11.04.


Ok I downloaded this exact version, and yes its the 64bit because I have 64bit:

VMware-Workstation-Full-7.1.4-385536.x86_64.bundle

That is VMware Workstation 7

I have Ubuntu 10.10 mav 64bit

I dunno how to install this 

Im sorry but I am a noobie to Ubuntu

I appreciate the help :D

---

### Post by bhaverkamp on 2011-04-29
This is actually a cake walk. From the command line issue

sudo sh VMware-Workstation-Full-7.1.4-385536.x86_64.bundle

... and away you go. It will ask you some question during the install.

---

### Post by =Spider_Man= on 2011-04-30
> **bhaverkamp said:**
> This is actually a cake walk. From the command line issue

sudo sh VMware-Workstation-Full-7.1.4-385536.x86_64.bundle

... and away you go. It will ask you some question during the install.


It wont let me install. I cd into the folder where it is located and I get this message:

joel@joel-ThinkPad-Edge:~/Documents$ sudo sh VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
VMware-Workstation-Full-7.1.4-385536.x86_64.bundle: 110: Syntax error: newline unexpected


Im not sure why

---

### Post by defis on 2011-06-20
Here is a site which has the 32bit and the 64bit VMware workstation full 7.1.4 . There is also a video for the installation but is in greek.

[http://greekddl.com/programms/linux-programs/120782-VMWare-Workstation-7-1-4-385536-(Linux).html](http://greekddl.com/programms/linux-programs/120782-VMWare-Workstation-7-1-4-385536-(Linux).html)

> Originally posted by =Spider_Man=
It wont let me install. I cd into the folder where it is located and I get this message:

joel@joel-ThinkPad-Edge:~/Documents$ sudo sh VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
VMware-Workstation-Full-7.1.4-385536.x86_64.bundle: 110: Syntax error: newline unexpected


Im not sure why

Did you make the .bundle executable? To do so, right click the .bundle go to Permissions and check "Make this file executable"

---

### Post by bhaverkamp on 2011-06-21
Cool. It really is in greek.

---

### Post by bhaverkamp on 2011-06-21
> **=Spider_Man= said:**
> It wont let me install. I cd into the folder where it is located and I get this message:

joel@joel-ThinkPad-Edge:~/Documents$ sudo sh VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
VMware-Workstation-Full-7.1.4-385536.x86_64.bundle: 110: Syntax error: newline unexpected


Im not sure why

Perhaps the file has been corrupted. My direction should work. No need to make the file executable. sh is the executeable on the commandline and it is already executable.

---

### Post by bhaverkamp on 2011-06-21
> **defis said:**
> Here is a site which has the 32bit and the 64bit VMware workstation full 7.1.4 . There is also a video for the installation but is in greek.

[http://greekddl.com/programms/linux-programs/120782-VMWare-Workstation-7-1-4-385536-(Linux).html](http://greekddl.com/programms/linux-programs/120782-VMWare-Workstation-7-1-4-385536-(Linux).html)



Did you make the .bundle executable? To do so, right click the .bundle go to Permissions and check "Make this file executable"
I just tried this myself and it worked. I generated the md5sum for you to check.


>bernieh@bernieh-lx:~/Desktop$ md5sum VMware-Workstation-Full-7.1.4-385536.x86_64.bundle 
>68b424f836f63c12b071a791f80b1593  VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
>bernieh@bernieh-lx:~/Desktop$ sudo sh VMware-Workstation-Full-7.1.4-385536.x86_64.bundle 
>Extracting VMware Installer...done.
>bernieh@bernieh-lx:~/Desktop$

---

### Post by DAB4970 on 2011-06-25
> **bhaverkamp said:**
> Obviously the exe link is wrong. Which version of Workstation are you trying to install. Version 7 will run on Lucid and older; have not yet had a chance to try it on 11.04.

I might be trying Workstation on my 32bit laptop (wish I had a 64bit laptop, though).  I currently have VMware Player installed, but it doesn't seem to want to install Win2K8 Server Guest.  I've tried with and without Legacy Emulation.
The laptop has 10.04 installed.  Depending on how much $ to purchase Workstation, I might wait til next LTS comes out.

---

