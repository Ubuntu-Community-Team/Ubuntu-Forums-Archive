---
title: "OSE -&gt; PUEL virtualbox migration?"
date: 2010-03-12
forum: Virtualisation
---

### Post by Beowulf.1000 on 2010-03-12
Any tips on how not to lose my data and virtualized Windows XP that I have running smoothly in the OSE version of virtualbox on my Ubuntu 9.10 64bit system, as I want to migrate to to the PUEL version of virtualbox? Is there some way to do the crossover and keep my existing virtualized WinXP?

I copied (backed up) everything in ~/.virtualbox to another backup folder-- so I should be good right for not losing anything? I downlaoded PUEL but to install it it wants the OSE virtualbox to be removed first. So I should be able to now remove OSE, then install PUEL, then somehow import my virtual WinXP that I backed up, right?

---

### Post by JKyleOKC on 2010-03-12
While I'm running on 32-bit 8.04.4 host, the procedure should be the same for all Linux hosts. First, uninstall the OSE version; I used Synaptic and clicked Remove, NOT Remove completely. Next, add the VirtualBox repository to your sources.list file as described on the VirtualBox download page and update Synaptic's data (which should happen automagically after you modify the sources list). Then install the Sun VirtualBox version which is now listed.

Your existing VMs and all other content of the original .VirtualBox directory will remain intact, but you should then install the new Guest Additions package for best results. It's version-specific and the version at the VirtualBox site is likely to be newer than then one in the Ubunty repositories.

---

### Post by Beowulf.1000 on 2010-03-12
Okay I backed up all the virtualbox data, I will give a try today or tomorrow change to PUEL as you suggest. I do prefer synaptic over a .deb (I did download a .deb from the Sun Virtualbox site, complete with guest additions, for my AMD 64 bit Ubuntu -- perhaps I could just install that after removing OSE virtualbox?)

---

### Post by JKyleOKC on 2010-03-12
Right. Just double-click on the deb file and it will launch the installer. However it's still best to add the VirtualBox site to your sources.list, since that will get you any update notices automatically.

---

### Post by Beowulf.1000 on 2010-03-12
USB problems, can anybody toss me a bone?

I installed the .deb Sun virtualbox PUEL edition, went great. Then installed guest addition from PUEL menu. Windows XP showed new drivers for usb and usb2 installing after I turned on USB support from the PUEL settings menu.

But when I plug in my flash USB drive I can not access it, it shows it is unavailable. It is listed the the PUEL Devices:USB Devices menu, but is grayed out and listed as unavailable, even after I made sure to unmount it from the linux desktop.

What can I do to get my virtualbox WinXP to access files on my flashdrive for read/write? This was the main reason I changed over from OSE to PUEL.

---

### Post by howefield on 2010-03-12
Did you add your user to the vboxusers group ?

---

### Post by Beowulf.1000 on 2010-03-12
Oops, no I had not. Did that and yes now I have USB support. But... now with the PUEL edition I no longer have fullscreen 1600x900 resolution of my virtualized WinXP filling my screen. Sigh, always something, ugh. With OSE edition I had full screen. I do the Ctrl+f but now I only have about 1100x600 and that is the highest resolution listed in the WinXP display settings. What the heck happened to actual full screen mode? I have the guest addition installed? I believe as best I recall I even had actual full screen just before I added myself to vboxusers group, but I do not know how that would have messed up full screen. Ideas?

EDIT: Solved. I enabled 2D acceleration in the Display settings for the virtual WinXP, and also re-enabled advanced desktop effects on my Ubuntu; now I have full screen virtual WinXP again. Not sure what combo of that is needed or not needed, but one or both of those settings must be needed. 

Thank you all for you help! I love having USB, especially since I hope to get my MIDI keyboard through its USB cable working in my virtual Windows machine for music composition with Sibelius 6 (which is installed and working on the virtual machine).


> **howefield said:**
> Did you add your user to the vboxusers group ?

---

### Post by MrSkrimps on 2010-03-13
I have run into quite a problem with PUEL.  I had OSE running perfectly, attempted to update to PUEL via instructions from virtual box website.  And ran into this error:

Processing triggers for man-db ...
Processing triggers for python-support ...
(Reading database ... 360636 files and directories currently installed.)
Unpacking virtualbox-3.1 (from .../virtualbox-3.1_3.1.4-57640%5fUbuntu%5fkarmic_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/virtualbox-3.1_3.1.4-57640%5fUbuntu%5fkarmic_amd64.deb (--unpack):
 trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso', which is also in package virtualbox-guest-additions 0:3.0.8-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package libsdl-ttf2.0-0.
Unpacking libsdl-ttf2.0-0 (from .../libsdl-ttf2.0-0_2.0.9-1build1_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-3.1_3.1.4-57640%5fUbuntu%5fkarmic_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libsdl-ttf2.0-0 (2.0.9-1build1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

skrimps@Athena:~

I have Ubuntu 9.10 amd64 and can't find any information on the error I'm getting, let alone able to figure out where/what to start looking at to fix the problem.  Any suggestions??

---

### Post by square34 on 2010-04-25
Hi MrSkrimps,

I had the same problem and i solved removing the virtualbox-guest-additions pkg.

try:

apt-get remove virtualbox-guest-additions

and then reinstall:

apt-get install virtualbox-3.1

(After that remenber to add your user to the vboxusers group...)

That worked for me.

Regards

---

