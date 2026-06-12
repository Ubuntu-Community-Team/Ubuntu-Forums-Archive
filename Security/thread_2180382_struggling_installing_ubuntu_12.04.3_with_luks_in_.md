---
title: "struggling installing ubuntu 12.04.3 with luks in a dedicated partition"
date: 2013-10-12
forum: Security
---

### Post by chpnp on 2013-10-12
I used the alternate 64bit CD
Not full disk install, I have W7 and another linux already happily running;  i went to manual partition,  added / and swap partition in the luks partition LV.

Everything looks good after installation but problems start at reboot.

1- grub was no installed to mbr; which was unexpected for me, but is fine, i wanted to chainload from the grub legacy installed in the mbr
Rebooted in recovery mode, mounted the luks partition (sorry for the shortcut) and /boot (unencrypted) partition
the problem is that there is NO core.img in /boot (other files seemingly there but i am no grub2 expert)
update-grub works but does not create core.img. How can I solve that ??
(I can see that the command modified some files in /boot though)

2- In my investigations, I went to that manual [http://askubuntu.com/questions/293028/how-can-i-install-ubuntu-encrypted-with-luks-with-dual-boot](http://askubuntu.com/questions/293028/how-can-i-install-ubuntu-encrypted-with-luks-with-dual-boot)
this was just a prior investigation, since grub2 will not even start at that stage.

I am assuming, from that documentation, that i need to follow the instruction to create /etc/crypttab and edit /etc/default/grub to update the GRUB_CMDLINE_LINUX variable as described there (with my data of course)

Is this correct ?

I have no experience with Luks or encrypted ubuntu (but have played with it as well as with encfs and truecrypt), so apologies if that looks trivial to others.

Thanks you for hints. 
At this time I reverted to a non encrypted installation to first sort out the core.imb issue and ensure grubs chainloading works properly before trying luks again.

---

