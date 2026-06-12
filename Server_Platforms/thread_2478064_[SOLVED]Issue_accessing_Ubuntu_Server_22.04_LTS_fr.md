---
title: "[SOLVED]Issue accessing Ubuntu Server 22.04 LTS from windows workstations"
date: 2022-08-15
forum: Server Platforms
---

### Post by stannellc on 2022-08-15
[COLOR=#232629][FONT=-apple-system]I'm working with a new installation and have 3 users. Two of the users have no issues. One user can't access the data. If you try to open a folder from the windows machine it says that the user might not have permissions.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Right click and go to properties, and it says you must have read permissions to view the properties of the object. If I go to advanced and try to change the owner, it brings me to the same dialog box you get if you right click on the folder, go to properties, and then go to the security tab.
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I'm unfamiliar with Ubuntu, but familiar with this process of adding someone on a windows machine so they can access a folder. Under select user or group, I can click on advanced and then click find now, it will list all the users from "this location" which is my server.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The two working accounts are in this list, but the third is not. All 3 users are in the same groups, and all have the same rights. I have deleted the users and added them again. I have gone through the same steps for all users, yet I can't get it to work for this one. I'm thinking I'm missing something simple, but I can't find it.
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]What I want to do is find a way to list all permissions for a single user so I can compare them. I've been all over Google, and all I can find is how to tell file permissions and folder permissions, but not a way to find everything a single user has been granted.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]If there is a way to do that, maybe it would point me in the right direction. Though I'm not sure about that as I have gone through the exact same steps for all users. I'd appreciate any insight on this.
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I only have 2 samba shares:

[/FONT][/COLOR]```

[MEDIA]
path = /media
valid users = @editors
browsable = yes
writable = yes
read only = no
guest ok = no

[USB]
path = /mnt/usb
valid users = @editors
browsable = yes
writable = yes
read only = no
guest ok = no

```
Thanks.

---

### Post by stannellc on 2022-08-15
My bad, sorry.  Thought I had gone through all the same steps, but that user was not added in samba.

---

