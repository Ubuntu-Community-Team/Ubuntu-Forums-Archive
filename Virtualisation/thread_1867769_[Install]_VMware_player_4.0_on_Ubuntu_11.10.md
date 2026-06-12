---
title: "[Install] VMware player 4.0 on Ubuntu 11.10"
date: 2011-10-23
forum: Virtualisation
---

### Post by skybullet_ on 2011-10-23
Hi!

I'm using Oneiric and I try to install VMware Player 4.0 so I can run a WinXP .vmdh file previous created.

Unfortunately I get this error in bash:

[B]One or more of your processors does not have the necessary 64bit extensions to run VMware virtual machines
Installation was unsuccessful![/B]
 [IMG]http://forum.ubuntu-it.org/Smileys/ubuntu-it/angry.gif[/IMG]

I've downloaded 32bit version for linux (VMware-Player-4.0.0-471780.i386.bundle)...so which is the problem??

My notebook is a Dell Inspiron 6000 with Intel Pentium M 1.86Ghz and 2Gb RAM.

Thank you very much for any answers!
 [IMG]http://forum.ubuntu-it.org/Smileys/ubuntu-it/smiley.gif[/IMG] [IMG]http://forum.ubuntu-it.org/Smileys/ubuntu-it/smiley.gif[/IMG] [IMG]http://forum.ubuntu-it.org/Smileys/ubuntu-it/smiley.gif[/IMG]

---

### Post by snovik on 2011-10-24
Version 4.0 requires 64-bit architecture

[http://www.vmware.com/support/player40/doc/releasenotes_player40.html#Installation_Requirements](http://www.vmware.com/support/player40/doc/releasenotes_player40.html#Installation_Requirements)

---

### Post by e79 on 2011-10-24
Your processor does not support virtualization (assuming it is [this one]("http://ark.intel.com/products/27593/Intel-Pentium-M-Processor-750-%282M-Cache-1_86-GHz-533-MHz-FSB%29")). You unfortunately won't be able to virtualize with this machine.

---

### Post by Joshua49 on 2011-12-14
Hi, 
I have the same problem, however, CPU-Z tells me I have the perfect CPU for it : 

```
	Specification		Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
	Instructions sets	MMX, SSE, SSE2, SSE3, SSSE3, SSE4.1, SSE4.2, EM64T, VT-x, AES, AVX

```

Any ideas ? Is VM Player 3 worth it ?

---

### Post by BenB1 on 2011-12-14
Seems I am not alone in trouble with VMWare Player. Tried installing following directions. It hung during install. Searched, found more instructions. Tried those, still hung. Uninstalled it, deleted the downloaded bundle file from root's home. Now unable to log in as regular user.
Going to try a reboot to see if that clears out something. Hopefully it works.

The reboot did not work. Created a user foo to use as a user until able to figure it out. Saw something about using a workaround of moving config files for each user, then replacing them piecemeal seeing what causes issues, or not.

---

### Post by fjgaude on 2011-12-14
> **Joshua49 said:**
> Hi, 
I have the same problem, however, CPU-Z tells me I have the perfect CPU for it : 

```
	Specification		Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
	Instructions sets	MMX, SSE, SSE2, SSE3, SSSE3, SSE4.1, SSE4.2, EM64T, VT-x, AES, AVX

```

Any ideas ? Is VM Player 3 worth it ?

I can't say what you have done, but Player 4.0.1 works perfectly with 11.10 and 11.04. I run 64-bit but I think there is a 32-bit version on the vmware.com site.

---

### Post by d2redneck on 2012-01-15
I am also haveing a problem with 4.0.1 I am really new to Ubuntu and this is one of the last issues I have to figure out before I switch to Ubuntu completely.  It just hangs up during the installation.  don't know what to do.  HELP!!!!!!!

---

### Post by d2redneck on 2012-01-16
ok i figured it out on my system.  

first thing is to make the VMware-Player-4.0.1-528992.x86_64.txt an executable by first getting into the folder directory that you have it in (in my case it was the downloads folder) by typing chmod +rx VMware-Player-4.0.1-538992.x86_64.txt then you type sudo ./VMware-Player-4.0.1-538992.x86_64.txt and it goes from there. All of this is done in the terminal. worked perfectly on my system.  Windows is about to go bye bye

---

### Post by japzone on 2012-01-17
I would just use VirtualBox. It works alot better on a Linux host than VMware does in my expirience, and I've had no trouble booting any Number of OSs on it. VirtualBox is compatible with VMware files too, so no problems there. VirtualBox can be installed via the VirtualBox site here: [https://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by d2redneck on 2012-01-17
I mainly use VMware player for the simple reason that that is what I have to use in school.  After I graduate then I will probably start using virtual box but, for now I am stuck.

---

### Post by japzone on 2012-01-18
> **d2redneck said:**
> I mainly use VMware player for the simple reason that that is what I have to use in school.  After I graduate then I will probably start using virtual box but, for now I am stuck.

I see...

---

### Post by dcstar on 2012-01-20
> **d2redneck said:**
> ok i figured it out on my system.  

first thing is to make the VMware-Player-4.0.1-528992.x86_64.txt an executable by first getting into the folder directory that you have it in (in my case it was the downloads folder) by typing chmod +rx VMware-Player-4.0.1-538992.x86_64.txt then you type sudo ./VMware-Player-4.0.1-538992.x86_64.txt and it goes from there. All of this is done in the terminal. worked perfectly on my system.  Windows is about to go bye bye

VMware Player Linux downloads are .bundle files, so I have no idea where you get ".txt" from:

[https://www.vmware.com/tryvmware/p/activate.php?p=player&lp=1&a=DOWNLOAD_FILE&baseurl=https://download2.vmware.com/software/wkst/&filename=VMware-Player-4.0.1-528992.x86_64.bundle](https://www.vmware.com/tryvmware/p/activate.php?p=player&lp=1&a=DOWNLOAD_FILE&baseurl=https://download2.vmware.com/software/wkst/&filename=VMware-Player-4.0.1-528992.x86_64.bundle)

---

### Post by fjgaude on 2012-01-21
Player 4.0.1 is a .txt file, at least it was for me.

---

### Post by escu on 2012-02-07
Hello, it seems vmware player 4 and above and related products needs a 64-bit capable processor. If your CPU has virtualization extensions as VT-x, may be necessary enable it on BIOS.

Ive just installed vmware player 3.1.5 on P4 without virtualization extensions and it works perfect on ubuntu 10.04LTS but the version 4 of vmware player installation fails due to 64-bit lack support on my cpu.

Cheers

---

### Post by dcstar on 2012-02-08
> **escu said:**
> Hello, it seems vmware player 4 and above and related products needs a 64-bit capable processor. If your CPU has virtualization extensions as VT-x, may be necessary enable it on BIOS.


VMware Player for Linux comes in 64 & 32 bit versions. People need to download the actual version that matches the **host OS** that they are using.

---

### Post by jadedphotographer on 2012-02-14
> **fjgaude said:**
> Player 4.0.1 is a .txt file, at least it was for me.
I'm getting the same .txt file.Renaming it to .bundle and .bin does not work either.

---

### Post by dcstar on 2012-02-15
> **jadedphotographer said:**
> I'm getting the same .txt file.Renaming it to .bundle and .bin does not work either.

Renaming means nothing, set the Execute bit as specified in the other posts.

---

### Post by QuAdS17 on 2012-02-22
> **d2redneck said:**
> ok i figured it out on my system.  

first thing is to make the VMware-Player-4.0.1-528992.x86_64.txt an executable by first getting into the folder directory that you have it in (in my case it was the downloads folder) by typing chmod +rx VMware-Player-4.0.1-538992.x86_64.txt then you type sudo ./VMware-Player-4.0.1-538992.x86_64.txt and it goes from there. All of this is done in the terminal. worked perfectly on my system.  Windows is about to go bye bye

Thank you very much. Works perfectly.

---

### Post by InnerBushman on 2012-03-27
I have downloaded the 32-bit version. I want to virtualise 32-bit guest on 32-bit host. I mean seriously... WTH?

Error says: One or more of your processors does not have the necessary 64bit extensions to run VMware virtual machines.

If i can't run this poo on my 32-bit machine, why do they give me a download for it?! ;[

---

### Post by dcstar on 2012-03-28
> **InnerBushman said:**
> I have downloaded the 32-bit version. I want to virtualise 32-bit guest on 32-bit host. I mean seriously... WTH?

Error says: One or more of your processors does not have the necessary 64bit extensions to run VMware virtual machines.

If i can't run this poo on my 32-bit machine, why do they give me a download for it?! ;[

32-bit **hardware** is only supported up to Workstation 7 and (probably) Player 3:

[http://communities.vmware.com/message/1828239#1828239](http://communities.vmware.com/message/1828239#1828239)

Download the old versions and they should install.

People have to accept that places like VMware aren't going to keep supporting old hardware when they release new products, they exist for commercial users that rarely have hardware more than 3 years old and supporting anything prior to that just isn't worth their while.

---

### Post by agungpw on 2012-04-03
I've actually handle this problem.. for the simple step, u can try this one.

type this script one terminal, it's to download the helper program


wget [http://hacktolive.org/files/app_runner/App_Runner_0.4.9.deb](http://hacktolive.org/files/app_runner/App_Runner_0.4.9.deb)

after that type dpkg -i <name package>.deb to install package.

after its finish, go to file vmware-player.bundle, right klick - script - run - CLI APP as root.

done.

---

### Post by Cajhne on 2012-04-06
> **japzone said:**
> I would just use VirtualBox. It works alot better on a Linux host than VMware does in my expirience, and I've had no trouble booting any Number of OSs on it. VirtualBox is compatible with VMware files too, so no problems there. VirtualBox can be installed via the VirtualBox site here: [https://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads")

If you're running WinXP in Virtualbox, you are better off with VMWare Player. The second you try to define a shared folder in VirtualBox (and the subsequent hours you'll waste trying to figure out why it hasn't worked), will have you longing for a solution that isn't badly hacked together. Check out this thread to save yourself some headache if you're misguided enough to use VirtualBox to run XP:
[http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)

Just reading that work-around should have you running back to VMware with a newfound appreciation, despite some installation difficulties.

---

