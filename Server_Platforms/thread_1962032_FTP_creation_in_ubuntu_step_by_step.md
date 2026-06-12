---
title: "FTP creation in ubuntu step by step"
date: 2012-04-20
forum: Server Platforms
---

### Post by atultiwari on 2012-04-20
I am very new in ubuntu ..
i need to configure FTP server.

I need to create 5 ftp users and they all are having access of their own folders, no one can access others FTP_Folders assigned by me,   Also I need to block them to SSH to the Linux Server.

Thanks in Advance...

AT

---

### Post by MakOwner on 2012-04-20
> **atultiwari said:**
> I am very new in ubuntu ..
i need to configure FTP server.

I need to create 5 ftp users and they all are having access of their own folders, no one can access others FTP_Folders assigned by me,   Also I need to block them to SSH to the Linux Server.

Thanks in Advance...

AT

Can you use sftp instead?  It's incredibly easy to enable on ubuntu.
```

sudo apt-get install openssh-server 

```
Any new or existing users will now have shell and sftp access to their home directory.

It's not ftp, but I find it incredibly more useful.

---

### Post by Habitual on 2012-04-20
> **MakOwner said:**
> ...Any new or existing users will now have shell and sftp access to their home directory.

It's not ftp, but I find it incredibly more useful.

and **secure**

---

### Post by anonymouschief on 2012-04-20
> **atultiwari said:**
> 
I need to create 5 ftp users and they all are having access of their own folders, no one can access others FTP_Folders assigned by me,   Also I need to block them to SSH to the Linux Server.


Your requirements are:
- ftp users with access to their own folders
- no-one can access others' FTP folders assigned by you
- These ftp users should not have SSH/shell access

As has already been suggested by other users, SFTP is the way to go, as opposed to ftp, because it leverages SSH, which is very secure. The following is a url that shows how to chroot sftp users, and jail them into their own home folders; they will not be able to access any folders other than their own; they will not have shell/ssh access.

Please note that the following url contains insteructions that i have not tested myself. Please backup any configuration files before you make changes to them.

[http://www.serverubuntu.it/SFTP-chroot](http://www.serverubuntu.it/SFTP-chroot)

Because this suggestion applied sftp, as opposed to ftp, you will have to lookup sftp clients that your users will have to use to access their home folders on your server. Check [https://www.google.ca/search?rlz=1C1GGGE_enCA396CA396&sourceid=chrome&ie=UTF-8&q=windows+sftp+clients#hl=en&rlz=1C1GGGE_enCA396CA396&sclient=psy-ab&q=sftp+clients&oq=sftp+clients&aq=f&aqi=g4&aql=&gs_nf=1&gs_l=serp.3..0l4.112297.112297.0.112586.1.1.0.0.0.0.115.115.0j1.1.0.VNP8UXo0bfQ&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=d5de7793dde30a36](https://www.google.ca/search?rlz=1C1GGGE_enCA396CA396&sourceid=chrome&ie=UTF-8&q=windows+sftp+clients#hl=en&rlz=1C1GGGE_enCA396CA396&sclient=psy-ab&q=sftp+clients&oq=sftp+clients&aq=f&aqi=g4&aql=&gs_nf=1&gs_l=serp.3..0l4.112297.112297.0.112586.1.1.0.0.0.0.115.115.0j1.1.0.VNP8UXo0bfQ&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=d5de7793dde30a36)

---

### Post by Lars Noodén on 2012-04-20
SFTP clients include Nautilus and FileZilla.

The following example would limit users in the group 'webmasters' to only the folders 'public_html' within their home directories:

```

Subsystem sftp internal-sftp

Match Group webmasters
  **ChrootDirectory** %h/public_html/
  AllowTCPForwarding no
  X11Forwarding no
  **ForceCommand** internal-sftp

```

Note that one gotcha with chroot in OpenSSH-server is that the chrooted directory must be owned by root.  So that may take a bit of planning to figure out how to give the users the access you want yet still have the target writable only by root.

See the manual page for sshd_config for more details:
[http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html)

---

