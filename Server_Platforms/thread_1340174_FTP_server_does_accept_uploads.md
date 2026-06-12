---
title: "FTP server does accept uploads?"
date: 2009-11-28
forum: Server Platforms
---

### Post by gian on 2009-11-28
hello All,

I setup an FTP server on a Jaunty server box in order to collect frames sent from ip cameras.

I enclose the vsftpd.conf in attachment.

The camera, an AXIS M1011, is setup to log as myself, local user, and the connection test reports OK. The destination folder is in my home.

The log reports the upload of files:

Sat Nov 28 12:17:38 2009 [pid 28947] [gian] OK UPLOAD: Client "192.168.1.153", "/home/gian/camera/hurco/image09-05-31_13-50-27-38.jpg", 60215 bytes, 749.58Kbyte/sec
Sat Nov 28 12:17:38 2009 [pid 28947] [gian] OK UPLOAD: Client "192.168.1.153", "/home/gian/camera/hurco/image09-05-31_13-50-27-42.jpg", 60113 bytes, 938.45Kbyte/sec

but there is no trace of them, nothing, zero.

Must have done something wrong, but I double checked everything...

thanks for your time and advice,
-Gian

---

### Post by gian on 2009-11-28
sorry, wrong path in camera setup

---

### Post by Vegan on 2009-11-28
snicker

---

### Post by JT9161 on 2009-11-28
[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

Look for **write_enable**

---

### Post by Lars Noodén on 2009-11-29
Having an account that can log in and upload via FTP is asking for eventual trouble.  Not only is the data transferred unencrypted, but also the passwords and usernames.  It is much safer to use SFTP, which happens to be built-in to your ssh server.  It's even very easy to chroot so that the account can read and write only to specific directories.


```

# specify how to activate the sftp server when needed
Subsystem sftp internal-sftp

# chroot any account in the group "cameras" to their home directory
Match Group cameras
	ChrootDirectory %h
	AllowTCPForwarding no
	X11Forwarding 
	ForceCommand internal-sftp

```

Note that [ssh server](http://packages.ubuntu.com/karmic/openssh-server) is not mutually exclusive with FTP.  You can leave your vsftp running as is while you test SFTP.  

The era of unencrypted logins ended 10 years ago.

---

### Post by gian on 2009-11-30
thank all of you for your kind help.

As soon as I posted the question, I realized that the problem lied in the folder setting of the camera, so now it is solved.

If I knew how to delete a post, if possible at all, I would have done so.

Thanks for the SFTP hint.

---

### Post by Vegan on 2009-11-30
Mark this as solved.

---

### Post by gian on 2009-11-30
well if you look at the first post, you'll see it's already [solved]

---

