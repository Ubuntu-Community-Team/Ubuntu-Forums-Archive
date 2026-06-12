---
title: "After upgrade to 14.04 samba file list is very slow if using ACL"
date: 2014-08-26
forum: Server Platforms
---

### Post by Bu83KQdr on 2014-08-26
Hi All,

I used to use ACLs to fine tune permissions in access to my samba shares. It works nicely, however browsing files became very slow after upgrade to 14.04. I can visually see how an explorer window connected to the share updates one file by one, slowly showing the directory listing.

It worked fine in 13.10, but it was the same slow in 13.04. So whatever was fixed in 13.10 got broken in 14.04 again.

What should I do?

---

### Post by arjenzwerver on 2014-12-29
I found a post from Grzegorz Karwowski with a solution working in my case.

[https://plus.google.com/+GrzegorzKarwowski/posts/hqJ2V9ZCC1U](https://plus.google.com/+GrzegorzKarwowski/posts/hqJ2V9ZCC1U)

> Slow access to public Samba shares in Kubuntu 14.04 - solution

In Dolphin and Konqueror listing shares' content with "smb://host/" takes very long time (minutes) and causes kwalletd to run 100% CPU.

Fix: add any username and password in "System Settings -> Sharing". Log out and log back in. Disabling KDE Wallet subsystem will work too. 

Noticed on i386 and amd64 (both upgrades from earlier versions)&#65279;

---

