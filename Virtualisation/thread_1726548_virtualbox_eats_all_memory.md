---
title: "virtualbox eats all memory"
date: 2011-04-11
forum: Virtualisation
---

### Post by orcomza on 2011-04-11
Dear list,

I'm using Ubuntu Lucid. Since a month ago Virtualbox eats all memory turning my desktop unusable. It happens seconds after I log in WinXP.

¿Any known bug/solution for this?

TIA,

--
Roberto

---

### Post by Kirboosy on 2011-04-11
Welcome to the Forums! :D

Have you checked the Virtual Machine RAM settings? If you are giving your virtual machine to much RAM the host computer will fail often times.


Does it give any errors that I should know about?


~Caboose

---

### Post by drewsus on 2011-04-11
Yes. Please tell us your system specs and what you have allocated to the virtual system.

---

### Post by orcomza on 2011-04-11
Well... the original WinXP can't be booted again... VM reboots before showing login dialog. So I tried installing Win7 in a new VM and got the same problem: when installing (extracting files) real memory was fully used up until virtualbox hanged.

Checking swap memory, I discovered it wasn't activated (!!!!) I added a 2nd hard disk some weeks ago and disks changed order (PATA and SATA) As I wasn't using UUID for swap partition it didn't get activated :-)

Shame on me, I was blaming Ubuntu and thinking to switch to Debian :-(

Regards,

--
Roberto

---

