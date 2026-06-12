---
title: "OUs not showing with Ubuntu / Samba?"
date: 2008-07-23
forum: Server Platforms
---

### Post by mspake on 2008-07-23
We run a Windows 2003 AD domain.  I set up Ubuntu 8.04.1 using Gnome and Samba 3.0.28a.  Everything seems to work properly, but I'm unable to find out how to do what I'm looking for.  (I'm new to Linux, but can follow instructions that are broken down potato head style.) "wbinfo -u" shows all the users (win and linux), but "wbinfo -g" only shows the linux groups.

What I'm looking to do is for the Windows groups/OUs to also show on the Linux box (and only be managed on the win server), where I can do NTFS folder & file permissions adding Windows OUs & groups, not just the individual users. (Like on a Win Server.) I don't know if this is possible, but any help would be very appreciated.

---

### Post by silverglade00 on 2008-07-23
I am dealing with some of the same issues. Some of the things that I have come across, such as adding an AD group to sudoers say to use
%DOMAINNAME\\group^name

The % says that it refers to a group.
The DOMAINNAME is the short domain name and does not have to be in caps.
The two backslashes are an escaped single backslash.
The ^ is used when there is a space in the group name, such as Domain^Admins.

---

