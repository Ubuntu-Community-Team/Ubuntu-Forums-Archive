---
title: "vbox have access but no write permission"
date: 2008-04-04
forum: Virtualisation
---

### Post by iansane on 2008-04-04
Hi, I have vbox installed on Ubuntu Hardy AMD64 server. The Vmachine is on a external usb drive with Fedora installed.

I set a shared follder "//home/ian/virtualShare" then "chmod 777 /home/ian/virtualShare" on the host.
created folder "host" on guest desktop
 I used ```

mount -t vboxsf  virtualShare /home/ian/Desktop/host
```
to mount the share to the host directory on my desktop. Since this is for testing and learning, both the host and guest have the same username "ian" so the paths are the same.

I can access the share but get "permission denied" when I try to mkdir, rename a folder, copy a file into the "host" directory or anything besides dealing with .txt files. For some reason the problem doesn't affect .txt

If it makes a difference, of cource the host (Ubuntu) is ext3 file system, but the Vmachine is on usb drive with NTFS file system.

Any suggestions?
Thanks

---

### Post by VitaLiNux on 2008-04-05
If I were you, I'd check the VBOXUSERS GROUP @ System | Administration | Users & Groups. You have to be sure your username belongs to that group. If that's the problem, Come and tell us!

---

### Post by ethos101 on 2008-10-05
I'm getting the same problem. Hardy32 host and XPSP3 guest.  I can access the shared folder ~/Documents in guest network places and see the contents but I can't even copy the files to the guest.  I have my user in vboxusers and 777 on the shared folder.

Am I missing something?

[EDIT]

Yes, apparently I can't share an existing home folder.  What I did was create a new folder under ~ called ~/VBoxShared and added that to the list and everything works as it should.  I don't exactly know why but there it is.

---

