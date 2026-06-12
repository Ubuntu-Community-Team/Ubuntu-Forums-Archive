---
title: "[SOLVED] Vanished HD space from virtual machines?"
date: 2007-11-07
forum: Virtualisation
---

### Post by Kymus on 2007-11-07
Alright, I understand pre-allocation of HD space. It pre-allocates, that space disappears, no problem.

My problem, is that I've been messing with VMWare Server and I've made virtual drives and then got rid of them, but the space doesn't free up. I've got 40GB or more in limbo.

I've thus far used VMWare, Virtual Box, and QEmu. I know VMWare has atleast 40GB of preallocated space floating around somewhere. The others, it's possible but I'm not 100% sure.

I just want to get back all the preallocated space and start over again...

---

### Post by Kymus on 2007-11-07
bump.

---

### Post by Kymus on 2007-11-07
I hate bumping my own posts, but I'm running out of space here :(

---

### Post by Kymus on 2007-11-07
bump

[img]http://s11.divshare.com/files/2007/10/06/2244922/PandaPic.jpg[/img]

:-D

---

### Post by Kymus on 2007-11-08
[img]http://www.kreyol.com/panda.jpg[/img]

---

### Post by Kymus on 2007-11-08
[img]http://spatula-city.org/~im14u2c/images/dilbert-unix-512px.png[/img]

---

### Post by bodhi.zazen on 2007-11-08
Well, the files have to be somewhere, have you checked the trash ?

My only other thought is to release the hard drive from your virtual machines.

---

### Post by Kymus on 2007-11-08
> **bodhi.zazen said:**
> Well, the files have to be somewhere, have you checked the trash ?

I'm not sure how I'd find allocated space in the trash :confused:

> My only other thought is to release the hard drive from your virtual machines.

That's what got me into the mess lol :P. I wiped the HD from the menu and then redid everything. Now, beforehand I made sure to take note of the free space and after wiping the virtual HD and creating a new one, I had even less space :eek:

---

### Post by gb64 on 2007-11-08
VM machines are usually file containers. You need to delete the actual container files on your Ubuntu file system. Maybe sort files by size? They should have a .vmdk extension for VMware, .vdi for VirtualBox.

---

### Post by Kymus on 2007-11-08
> **gb64 said:**
> VM machines are usually file containers. You need to delete the actual container files on your Ubuntu file system. Maybe sort files by size? They should have a .vmdk extension for VMware, .vdi for VirtualBox.

=D> woo that did it! I had 50+ gigs of that stuff sittin around :eek:

thanks a lot ;)

---

