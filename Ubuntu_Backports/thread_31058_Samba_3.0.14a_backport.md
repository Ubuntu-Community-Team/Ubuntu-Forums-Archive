---
title: "Samba 3.0.14a backport"
date: 2005-05-01
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-01
I've packaged and am uploading Samba 3.0.14a from Sid to Hoary Staging Backports. Since Samba is a daemon and in the 'main' repository, I felt like I needed to explain a bit:

I'm samba domain networking my home network (XP and Linux and 2000), after reading into the flexibility and control of such a setup. Typically, Samba point releases have plenty of little bugfixes, and from 3.0.10 to 14a is no exception. Among the most annoying is missing files from XP listings.

---

### Post by spacemonkey on 2005-05-09
I got the samba backport today and now it seems my samba shares are not working, people can't access my shared folders.  When I type sudo /etc/init.d/samba restart it doesn't look like it used to either.  Instead of saying:

stopping:    [ok]
starting:      [ok]


it says 

Stopping Samba daemons: nmbd smbd.
Starting Samba daemons: nmbd smbd.

I'm not really sure what this means.  Any help would be appreciated. Thanks.

---

### Post by jdong on 2005-05-09
Check /etc/samba/smb.conf -- it may have been replaced by the installer.


Try using smb://localhost/ , see if it's a network problem or Samba configuration problem.


The start/stop message will be different because this is a Debian package.

---

### Post by spacemonkey on 2005-05-09
I got it.  For some reason the updated samba config has a browsable modifier, and it was turned off by default, so no one could browse my folders.  I turned it on and it works fine now.

Thanks.

---

