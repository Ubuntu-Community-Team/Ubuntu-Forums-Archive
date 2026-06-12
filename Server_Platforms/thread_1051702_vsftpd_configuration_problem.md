---
title: "vsftpd configuration problem"
date: 2009-01-27
forum: Server Platforms
---

### Post by pmulgaonkar on 2009-01-27
I have set up vsftpd and want to enable anonymous users to download files. However, I seem to have  messed up the file permissions. In my vsftpd.conf file, I have anon_root=/home/ftp/

/home/ftp has the following permissions:
dr_xr_xrwx   3   root   nogroup

I have one file copied into the /home/ftp/ folder with permissions
_r_xr_xr_x and this file is not owned by root

It also has a subdirectory /home/ftp/opendir with permissions
drwxrwxrwx owned by root (probably the wrong thing to do).

However, when I log in as anonymous, all I see in the directory window is "/"

I don't see either the file or the directory. What am I doing wrong?

Thanks for any help.

---

### Post by pmulgaonkar on 2009-01-28
--bump--
No one?

---

