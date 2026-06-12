---
title: "Can't install ubuntu thorugh virtual box on windows host"
date: 2008-08-31
forum: Virtualisation
---

### Post by Tyler Zambori on 2008-08-31
hi all,

I have windows xp 32 bit installed as the host on a 64 bit
quad core.  This part is kind of beside the point, but it
happened by accident because of lack of correct presentation
by the reseller. (I am hating windows now). 

But I still need it for the time being, and I want to
install ubuntu as the guest OS. So I downloaded virtual
box, file name: VirtualBox-1.6.4-Win_amd64.msi

So I go to open and install it, and guess what, for some
reason it thinks I have a 32 bit computer.  So I go to 
install the 32 bit version of virtual box, and when I
go to set up the new virtual machine, ubuntu starts the
setup process, and guess what: it won't install because it
thinks my quad core setup is not 64 bit.

yesterday, I installed ubuntu studio as the one and only 
OS by accident, no virtual anything involved, no windows after that, and there was no problem. 

Am I going to have to do it the other way around, and have 
Ubuntu studio be the host?

---

### Post by Tyler Zambori on 2008-08-31
ok, I said the heck with it, and installed regular plain
64 bit ubuntu hardy heron within windows, and there was 
no prob.  I will just stick with that until I learn this
OS.  

So the prob must be with virtualbox for windows.

---

### Post by Pom2122 on 2008-08-31
Tyler:

1) You install the version of VB which matches the version of your Host OS, not the processor. (32 bit VB for 32 bit Windows)

2) VB CANNOT use 64 bit guests - only 32 bit.

3) If you installed Ubuntu 64 bit as the Host you could install 64 bit VB but you still can ONLY install 32 bit guests.

---

### Post by Tyler Zambori on 2008-08-31
Thanks Pom 2122.  That kind of sucks.

What software would let me install a 64 bit OS
as a guest OS? Is there an open source one?

---

