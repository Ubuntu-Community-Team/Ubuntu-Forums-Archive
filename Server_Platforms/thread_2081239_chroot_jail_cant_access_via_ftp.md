---
title: "chroot jail cant access via ftp"
date: 2012-11-06
forum: Server Platforms
---

### Post by bigmonmulgrew on 2012-11-06
I'm trying to setup a chroot jail for a new user

I've got this working on a vpc but cant get it working on my real server although as far as I am aware they are software identical.

I created the new user with

```
sudo useradd -G webuser -s /bin/false username
```

I'm trying to connect with fireftp in firefox but I've tried with filezilla too and neither will connect

FireFTP is giving me this output
```
Connected (version 2.0, client OpenSSH_5.9p1NaNDebian-5ubuntu1)
Authentication (password) successful!
```

Filezilla gives me this
```
Error:	Network error: Software caused connection abort
Error:	Could not connect to server
```

This is on a ubuntu 12.04 server, updates are installed.
Its a LAMP server.
The vpc I have working is software identical. I've checked everything I can and all seems identical.

New users not in the "webuser" groups can connect fine and if I comment out the following in sshd_config then the new user can connect fine but obviously no jail.

```
Match Group webuser                                                                                                                                                                                                                                                           
     ChrootDirectory %h                                                                                                                                                                                                                                                       
     ForceCommand internal-sftp  
```

You guys are my last hope before I reinstall the server from scratch, any ideas?

---

### Post by Lars Noodén on 2012-11-06
Does the home directory referenced by "ChrootDirectory %h" exist?  useradd by itself won't make a home directory.  If it exists, is it owned by root and writable only by root?  It won't work if it is writable by any other user or group.

---

### Post by bigmonmulgrew on 2012-11-06
> **Lars Noodén said:**
> Does the home directory referenced by "ChrootDirectory %h" exist?  useradd by itself won't make a home directory.  If it exists, is it owned by root and writable only by root?  It won't work if it is writable by any other user or group.

yes the directory exists, it is owned by root, and is only writable by root.

Just double checked

---

### Post by Lars Noodén on 2012-11-06
Ok.  

Can you stop the server, start it in debug mode and try connecting?  That usually gives the information needed.

```

sudo service ssh stop
sudo /usr/sbin/sshd -Dd

```

---

### Post by bigmonmulgrew on 2012-11-06
> **Lars Noodén said:**
> Ok.  

Can you stop the server, start it in debug mode and try connecting?  That usually gives the information needed.

```

sudo service ssh stop
sudo /usr/sbin/sshd -Dd

```

Cracking problem solved

I had changed the ownership and modes of the parent directory, forgot that with chroot jails the directory AND its parent directories must only be writable by root I have changed the parent directories and now its workign fine

Thanks a lot

---

