---
title: "[SERVER] Samba sharing"
date: 2011-03-13
forum: Server Platforms
---

### Post by FreiheitPT on 2011-03-13
Hello Ubuntu friends,

Well, I installed rtorrent + rutorrent in my server, and all the stuff that rtorrent downloads goes to, let's say, folder = FOLDER

I would like to share this folder on the LAN, for some users only, but not for all, and one of them, has write permissions.

I would prefer, at least, that the users without write capabilities do not have to login to access the folder.

this configs, do almost what I want:


[SHARE]
   comment = Share folder
   path = /FOLDER
   browsable = yes
   read only = yes
   guest ok = yes
   write list = USERX
   hosts allow = ip1, ip2, ip3

NOTE: ip1~3 are LAN ips

But it seams, with these configs, that it does not ask for login details.

The idea was that the system would ask for login details, but if the user does not input anything, the system would consider this user as a guest (as i think it should happen).

NOTE: Ubuntu + Windows users are on this lan.

Thanks in advance!


EDIT:
forgot something: when rtorrent downloads stuff to that folder, it seems that even the user with write capabilities on FOLDER, has no permissions to delete folders/files that rtorrent creates, but alk other files, created by this user, are (obviously as expected) deletable. Does someone knows what I have to do? Thanks!

---

