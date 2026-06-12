---
title: "VSFTP configuration for a web server"
date: 2008-07-01
forum: Server Platforms
---

### Post by flip79 on 2008-07-01
Hello!

(I'm using Ubuntu @home, but CentOS for my web server).

I'm trying to correctly configure VSFTPD for a web server that I manage. I'd like to have several users that can upload files on their web spaces. I succeded in:

- add a local user and enable him in vsftpd;
- automatically mount its web directory in his home and so let him upload, delete etc. files in his site.

My problem is that every file users upload takes their user/group: I think the correct behavior should be: every file that a user upload automatically take his ownership as user, and "apache" group as group.

Do I have to manually assign "apache" group as the default (primary) group for every new ftp (local) user I add? Now I have them with "apache" set as secondary group and "user name" as primary (for example, user "alice" is part of "alice" group as primary, and "apache" as secondary.

Thank you in advance!!!

---

### Post by flip79 on 2008-07-02
Up :KS

---

### Post by windependence on 2008-07-02
I don't know if you are aware of this but Konqueror and I think nautilus will do sftp right in their browser window, just drag and drop from your Ubuntu box. No ftp server necessary.

For me, I use WinSCP to push my web files from a Windoze box and Fugu from my Mac.

-Tim

---

### Post by flip79 on 2008-07-03
> **windependence said:**
> I don't know if you are aware of this but Konqueror and I think nautilus will do sftp right in their browser window, just drag and drop from your Ubuntu box. No ftp server necessary.

For me, I use WinSCP to push my web files from a Windoze box and Fugu from my Mac.

-Tim
Thank you, windependence, but I'm talking about vsftpd configuration (the server side) not the client side (from my ubuntu box). I already use with success Gnome to manage ftp files on remote systems :)

---

