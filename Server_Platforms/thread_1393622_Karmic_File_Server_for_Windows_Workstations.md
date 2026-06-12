---
title: "Karmic File Server for Windows Workstations"
date: 2010-01-29
forum: Server Platforms
---

### Post by mebunto on 2010-01-29
Hello,

I am busy working on configuring a Karmic server with a drobopro (ISCSI) attached so that my home laptops and desktops can save files to the drobopro.
I understand that I can use ext3/ext4 volumes on the drobo, which the server will present to the windows boxes in a way that they can read.
My objective is to have a very efficient file store which is quick and transparent to the users on the Windows boxes.  I'd also like to stream video from the NAS.

Am I right in assuming the following?

[LIST=1]
[*]the ext3/4 file system will be more efficient and faster than ntfs
[*]samba isn't the way to go if doing large file transfers
[/LIST]
Could someone point me in the right direction for advice and guidance for this too?

thanks very much

---

