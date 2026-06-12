---
title: "Fully encrypted disk on VMWare install on Windows"
date: 2013-10-09
forum: Security
---

### Post by ThomWilhelm on 2013-10-09
Hi there,

At work I have to use Windows (*sigh*). However I can easily install VMWare player and run Ubuntu, and with VMWare tools it runs really nicely in full screen mode, I almost forget I'm using a virtual machine.

Anyway, my question is mainly about security, in particular disk encryption. I have a couple of personal SSH keys and such on the Ubuntu install, usually if it was a laptop I'd fully encrypt the disk. I see this option is still available during install of 12.10 on VMWare, however I just wanted to confirm this means that the disk image will be completely encrypted. I.e if a colleague took a raw copy of my HDD, it wouldn't be possible to access any sensitive data.

Thanks! :popcorn:

---

### Post by Amorphous Serendipity on 2013-10-09
Hi ThomWilhelm,

Yes, if you do an encrypted install it will  completely encrypt your VM. If you are still worried afterwards, you can  install TrueCrypt in the VM and create an encrypted container to store  the SSH keys.

---

### Post by ThomWilhelm on 2013-10-10
Hey thanks. Following some experimentation today I've confirmed this. I noticed before (using an ugly Windows grep tool called astrogrep) that I could search the VMWare disk files and find the raw data inside them, or even just open some of the smaller files with a text editor and see random parts of the disk, which bugged me in-case my drive was stolen/copied. I created a new VM using the encrypted disk option, then copied all the contents over to the new machine, then booted with a live CD against the old VM and ran:
[B]
sudo shred -vf /dev/sda1[/B]

To completely nuke the old disk files, before deleting them from the host machine (this step prevents those undelete tools from getting the data). Now have searched the new VM disk files and nothing is found as it all encrypted nicely.

Thanks again! :D

---

