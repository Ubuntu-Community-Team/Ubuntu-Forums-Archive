---
title: "[SOLVED] VMWare Server just will not work..."
date: 2008-08-23
forum: Virtualisation
---

### Post by TpyKv on 2008-08-23
Hey Everyone,

I reformatted my laptop as I thought that doing this would help my vmware problem. I was on Gutsy and upgraded to Hardy when it was in Beta, so thought this might be the reason why VMWare stopped working... 

Anyway after re-installing Hardy, and following Bodhizazen's install guide here - [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)
and Intangir's here - [http://ubuntuforums.org/showthread.php?t=791708](http://ubuntuforums.org/showthread.php?t=791708)

I am still unable to run it. The little Vmware starting bar loads up and dissappears... I try do the vmware-config command, it says a few services cannot stop and that's about it. I've tried the any-any update too and still no joy...

Does anyone know of anything else I can try?

Thank you,

Kevin

---

### Post by TpyKv on 2008-08-24
BUMP

:lolflag:

---

### Post by gtdaqua on 2008-08-25
> I try do the vmware-config command, it says a few services cannot stop and that's about it

Post the output of the command here. Without knowing the error message, it will be very difficult to assist.

---

### Post by TpyKv on 2008-08-26
[http://premium1.uploadit.org/mentholist//vmware1.png](http://premium1.uploadit.org/mentholist//vmware1.png)

if you click on the applications - other - system tools - vmware server console, it does nothing. if you type sudo vmware-config.pl then you get all this, it says its ok,and has been configured, but then type vmware and once again you get nothing. Just told to run the config script again and again....

I've reinstalled and still no joy...

any suggestions welcome, I need vmware working or will have to go use virtual box, or a vista dual boot again. anything but that....:(

---

### Post by TpyKv on 2008-08-26
I get this...


The configuration of VMware Server 1.0.6 build-91891 for Linux for this running
kernel completed successfully.

kevin@vaio:~/src/VMWare/vmware-server-distrib$ sudo vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet3                                          done
   NAT service on /dev/vmnet3                                          done
   Host-only networking on /dev/vmnet3                                failed
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

kevin@vaio:~/src/VMWare/vmware-server-distrib$

---

### Post by TpyKv on 2008-08-27
Bump

Sorry to keep bumping! it's just I have less than two weeks to get this working and do loads of work, if it doesn't happen soon I HAVE to go back to Vista. Please don't let this happen.

---

### Post by TpyKv on 2008-08-27
Does anyone know if you can pay for support for VMware in Ubuntu?

---

### Post by TpyKv on 2008-08-27
this tutorial also gives the same problem as stated above

[http://ge.ubuntuforums.com/showthread.php?t=788169](http://ge.ubuntuforums.com/showthread.php?t=788169)

so that's three tutorials, every possible way of installing, with one complete wipe and re install of Hardy, and still no closer to having a resolution. Looking for the 4th tutorial now, please...?

---

### Post by FrooziE on 2008-08-28
Bump

---

### Post by ultrarazen on 2008-08-28
Have you tried running the vmware console from the terminal?
try running the command
```
vmware
```
in a terminal and see what messages it gives

Also make sure you do this (from the first tutorial)

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

---

### Post by jasonhuebert on 2008-08-28
Following the tutorials for installing VMware Server on Ubuntu also gave me problems.  For me, I wasn't installing some of the extra dependencies that already exist on a Ubuntu Desktop installation that don't exist in a Ubuntu Server installation.

```
sudo apt-get install libx11-6 libxtst6 libice-dev libsm-dev libxt6 libxrender1
```

Following the tutorial with the addition of the above line worked for me.

---

### Post by TpyKv on 2008-08-29
> **ultrarazen said:**
> Have you tried running the vmware console from the terminal?
try running the command
```
vmware
```
in a terminal and see what messages it gives

Also make sure you do this (from the first tutorial)

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

Yep I've tried that, thank you...

---

### Post by TpyKv on 2008-08-29
> **jasonhuebert said:**
> Following the tutorials for installing VMware Server on Ubuntu also gave me problems.  For me, I wasn't installing some of the extra dependencies that already exist on a Ubuntu Desktop installation that don't exist in a Ubuntu Server installation.

```
sudo apt-get install libx11-6 libxtst6 libice-dev libsm-dev libxt6 libxrender1
```

Following the tutorial with the addition of the above line worked for me.

Brilliant, thanks, this is the one thing I have not yet tried... although I'm not sure how successful it will be - the thing is I'm installing it on a laptop, the desktop edition, so these should already be there. I'll give it another whirl.. with fingers crossed. 

Can you tell me which tutorial you followed? waaaaay too many available...



Thanks again..

---

### Post by TpyKv on 2008-09-04
> **jasonhuebert said:**
> Following the tutorials for installing VMware Server on Ubuntu also gave me problems.  For me, I wasn't installing some of the extra dependencies that already exist on a Ubuntu Desktop installation that don't exist in a Ubuntu Server installation.

```
sudo apt-get install libx11-6 libxtst6 libice-dev libsm-dev libxt6 libxrender1
```

Following the tutorial with the addition of the above line worked for me.

I cannot thank you enough, this works!!

PROBLEM SOLVED! Thanks to everyone... and Jason you ROCK!

:guitar:

---

### Post by TpyKv on 2008-09-04
Solved:

Woot ...:guitar:

---

