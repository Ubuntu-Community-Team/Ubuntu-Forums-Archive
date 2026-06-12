---
title: "Running Linux-From-Scratch on top of a Guest OS in Virtualbox-OSE"
date: 2009-07-31
forum: Virtualisation
---

### Post by Dananjaya86 on 2009-07-31
I don't know whether this is possible but I think it would be nice if we can make this work. I'm planning to build  Linux From Scratch (6.4) in my home PC,which Ubuntu 9.04 and VirtualBox-OSE is  installed. 

I thought rather than dedicating a separate partition to work on, its better and if not at-least faster to build it on top of a guest Linux OS in Virtualbox. Use of a virtualization software to build the OS rather than restarting the machine each time a new component is installed is suggested by the LFS book also. but the book or Linux from Scratch Site doesn't provide much details on that. 

I though of installing a lightweight distro like Damn Small Linux as the guest and installing necessary software to it (e.g:make,bash,binutils,m4,gawk..etc.etc.) then building LFS on top. Can anybody kindly give me some suggestion or provide me with some pointers regarding this? or plainly whether this is possible or not..and of course fill me in about the pitfalls of doing it this way...

Thanks in Advance

---

### Post by UbuNoob001 on 2010-05-11
Hi there. I will be embarking on the same project. Have you checked out the (3) tutorials on youtube on LFS in Virtual Box? Also, have you read the essential pre-reading list for LFS? 


[http://www.linuxfromscratch.org/hints/downloads/files/essential_prereading.txt](http://www.linuxfromscratch.org/hints/downloads/files/essential_prereading.txt)


Ill subscribe to this thread so we can share any particular difficulties in hosting LFS on VB

---

### Post by BobVila on 2010-05-13
I did this very thing with LFS 6.3 - the virtual platform worked great. I'd recommend booting the VM from the LFS liveCD until you get the LFS system up just to keep things in line with the LFS book. One false move will probably leave you scratching your head, so it's nice to keep things as close to their baseline as possible. 

The other great thing about this approach is SNAPSHOTS! If you near a section you're not sure of, take a snapshot. If you get through it and things aren't working the way they should be, you can roll back and give it another pass. It's a nice safety net even if you don't end up needing it.

---

