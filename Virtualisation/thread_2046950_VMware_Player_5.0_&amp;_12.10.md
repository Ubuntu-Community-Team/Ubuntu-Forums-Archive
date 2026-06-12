---
title: "VMware Player 5.0 &amp; 12.10"
date: 2012-08-23
forum: Virtualisation
---

### Post by fjgaude on 2012-08-23
Has anyone tried to use Player 5.0 with the latest updates to Ubuntu 12.10, beyond Alpha3?

---

### Post by dcstar on 2012-08-30
> **fjgaude said:**
> Has anyone tried to use Player 5.0 with the latest updates to Ubuntu 12.10, beyond Alpha3?

Which way? I have 12.10 as a VM inside Player 5 (actually had it running inside 4 before the recent Player upgrade).

---

### Post by fjgaude on 2012-08-30
Ubuntu 12.10 host and VMware running, no VM. The last upgrade to 12.10 permitted VMware 5.0 to build but it would exit whenever I pointed to an appliance on another partition. I haven't tried to create a new VM with it.

I wait! <smile>

---

### Post by dcstar on 2012-09-01
> **fjgaude said:**
> Ubuntu 12.10 host and VMware running, no VM. The last upgrade to 12.10 permitted VMware 5.0 to build but it would exit whenever I pointed to an appliance on another partition. I haven't tried to create a new VM with it.

I wait! <smile>

Given VMware's usual timetable it takes them at least 2 months after an Ubuntu release to have a version of Player/Workstation that is officially compatible with it (usually the kernel version problem).

There might be a patch done by someone in the VMware forums before then, worth keeping an eye out for this sort of thing.

---

### Post by fjgaude on 2012-09-02
Yes, but Player 5.0 compiles just fine. I think 12.10, still in Alpha, has issues with cross partitions.

Will wait and see. Not long now.

Thanks for your advise.

---

### Post by svenole on 2012-09-21
See that you got vmware player to compile. How? Just tried to get it compiled on 12.10 beta, but it keeps complaining about lacking 3.5.0.15 header files which are installed... (/usr/src/linux-headers-3.5.0.15-generic). How ever I can se that I lack the pae directory of header files. Is that the problem here ?

---

### Post by josephmills on 2012-09-21
What is the Player ? 

sorry I am new to vmware trying to figure it out. this is what I get(attachments) installed via software center

---

### Post by fjgaude on 2012-09-21
> **josephmills said:**
> What is the Player ? 

sorry I am new to vmware trying to figure it out. this is what I get(attachments) installed via software center

VMware Player is the software that permits creating and reading virtual machines, like a guest OS. You can download it free from the vmware.com site:

[https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0)

Good luck!

---

### Post by josephmills on 2012-09-21
Ok I will DL and try. Is it different then the client ? also I will post how I got it to install. I am on 
```
~$ lsb_release -a && uname -r 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu quantal (development branch)
Release:	12.10
Codename:	quantal
3.5.0-15-generic

```
all of my software is bleeding edge or so I think.

---

### Post by fjgaude on 2012-09-21
> **svenole said:**
> See that you got vmware player to compile. How? Just tried to get it compiled on 12.10 beta, but it keeps complaining about lacking 3.5.0.15 header files which are installed... (/usr/src/linux-headers-3.5.0.15-generic). How ever I can se that I lack the pae directory of header files. Is that the problem here ?

I'm using 64-bit OS, not pae. I can't say if that is your problem. You are using Player 5.0? I have yet to get it to be able to read an existing VM made on 12.04. It's close but still something wrong... likely VMware will fix it after 12.10 is released, like they usually do.

---

### Post by josephmills on 2012-09-21
> **fjgaude said:**
> VMware Player is the software that permits creating and reading virtual machines, like a guest OS. You can download it free from the vmware.com site:

[https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0)

Good luck!


But what is the difference between the "client" and the "Player"
Thanks

---

### Post by josephmills on 2012-09-21
Ok it installed Fine and dandy. 
Steps,,

1) download the .txt file.
2) make exacudable as it is just a bash script, in my case I downloaded it to my ~/Desktop so 
```
cd ~/Desktop 
```
```
chmod +x VMware-Player-5.0.0-812388.x86_64.txt
```

3) rename the file so there is no txt at the end 

```
 mv VMware-Player-5.0.0-812388.x86_64.txt VMware-Player-5.0.0-812388.x86_64

```

4) run the script as super user 

```
sudo ./VMware-Player-5.0.0-812388.x86_64 
```

5) follow the gtk windows  and let install  


6) have fun

---

### Post by fjgaude on 2012-09-21
> **josephmills said:**
> But what is the difference between the "client" and the "Player"
Thanks

The Player permits you to access the client. The host is your OS. You install the Player. Then you create the client which is like installing an OS using the Player.

The client is the VM, virtual machine, creating by the Player and is nothing more than a file used as you install the OS which you wish to virtualize, like Windows XP or Vista, or even another Linux system.

---

### Post by josephmills on 2012-09-21
I think that I will stick with 
Qemu 
[http://wiki.qemu.org/Main_Page](http://wiki.qemu.org/Main_Page)

or Virtual Box

seems like there is some cool options though for vmware

---

### Post by rsborn on 2012-10-22
Just upgraded to 12.10 release and have found that vmplayer is broken as highlighted in this thread.

As an added note, 4.04 did work but required me to compile kernel modules at each and every start, it seems the vmware blocking filesystem failed. Upgrading to 5.0 was my attempt to fix this, I should have searched for issues first it appears.

Waiting patiently for a release from VMWare I suppose.

Rick

---

### Post by tuX9th on 2012-10-23
is there no workaround?

---

### Post by fjgaude on 2012-10-23
> **tuX9th said:**
> is there no workaround?

Not until VMware comes out with a fix for use with 12.10, at least none that I know of.

---

### Post by dcstar on 2012-10-24
> **fjgaude said:**
> Not until VMware comes out with a fix for use with 12.10, at least none that I know of.

This may be worth a try:

[http://forums.fedoraforum.org/showpost.php?p=1599022&postcount=4](http://forums.fedoraforum.org/showpost.php?p=1599022&postcount=4)

---

### Post by cprov on 2012-10-25
> **dcstar said:**
> This may be worth a try:

[http://forums.fedoraforum.org/showpost.php?p=1599022&postcount=4](http://forums.fedoraforum.org/showpost.php?p=1599022&postcount=4)
Thanks, dcstar!

This patch worked for me with vmplayer 5.0 & 12.10 (including the lsb_release recent fix)

---

### Post by JP Android on 2012-11-02
it works for me too. tks

---

### Post by dcstar on 2012-11-11
The Player/Workstation update of a couple of days ago now officially supports 12.10 - so I assume it now supports the current kernels.

Someone can now try and see if it works on 13.04 Alpha........

---

