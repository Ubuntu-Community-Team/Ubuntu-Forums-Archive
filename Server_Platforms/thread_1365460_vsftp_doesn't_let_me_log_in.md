---
title: "vsftp doesn't let me log in"
date: 2009-12-27
forum: Server Platforms
---

### Post by karimone on 2009-12-27
Hi all. I have a little local machine with ubuntu server 9.10 on it. I had there vsftpd working properly but now, maybe after the ehcp installation there is no way to log in. Every time vsftpd say that login or pwassword is incorrect.

Any suggestion?

---

### Post by karimone on 2009-12-29
I noted that I can login only if I use the SFTP protocol. Better than nothing :-)

---

### Post by Lars Noodén on 2009-12-29
> **karimone said:**
> I noted that I can login only if I use the SFTP protocol. Better than **ftp** or **ftps** :-)

There fixed that for you. ;)

You can probably do a lot more tith the sftp built into openssh.  It's certainly easier.  You can use GUI-based SFTP clients to transfer files:  Filezilla,  Konqueror, Dolphin, Nautilus, Cyberduck, Fugu, or Fetch all work with sftp.  For example, in Konqueror, just type in the URL to the sftp server like this: *sftp://karimone-server.example.org/var/www/*

You can also use [sshfs](http://packages.ubuntu.com/karmic/sshfs) to make some directories on the remote machine available as a folder on your local machine.

If you want to limit access to specific directories, openssh server is very easy to configure with chroot.

---

### Post by karimone on 2009-12-29
You're right. I guess I can use the server in many ways with sftp. Do you know also how I can reactivate the old ftp?

---

### Post by Lars Noodén on 2009-12-29
Why, specifically, use FTP?  From the example in the main question, it looks like it is being used to log in to an account to transfer files.  Using FTP to do that guarantees that the username, password and data are transmitted over the Internet unencrypted.  If that is the case, then SFTP is the correct method.  

You should be able to see this using tcpdump:
```

sudo tcpdump -c 10 -qnp -A -s 0 -i eth0 "port 20 or port 21"

```

If that is not the case and you need read-only FTP,
for Anonymous FTP, you probably have something like this in your config file.

```

local_enable=NO
anonymous_enable=YES
write_enable=NO
anon_root=/var/ftp

```

1) make sure that vsftp is still installed
2) double check your vsftp config file
3) if you are launching ftpd via xinetd or inetd, 
  check the config files for those to make sure they are correct
4) make sure that there is a use 'ftp'
5) check the ftp directory permissions for anonymous ftp

---

### Post by karimone on 2009-12-29
Thanks a lot!

---

