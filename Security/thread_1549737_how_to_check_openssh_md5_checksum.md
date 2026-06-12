---
title: "how to check openssh md5 checksum"
date: 2010-08-10
forum: Security
---

### Post by valugi on 2010-08-10
I have Ubuntu 10.04 and I used my ssh to connect to a webserver.
This is the version that I have installed.
> OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009


Apparently the server was hacked using my user and the server admin suggested the my ssh can be tainted.

On this [post]("http://serverfault.com/questions/167292/how-to-check-for-sniffers-in-ubuntu") people advice me to do a checksum of the ssh, but I cannot find this file on my system.

```
md5sum /usr/sbin/sshd
```

And I will need a md5 hash from a good untainted version and I cannot find that as well on the openssh website.

Thanks for the suggestions.

---

### Post by Bachstelze on 2010-08-10
sshd is the SSH server. You're probably talking about the SSH client, /usr/bin/ssh.

---

### Post by valugi on 2010-08-10
Thanks. Correct. 
How can I get a correct MD5 for comparison?

Mine is b26174c7f4d2d7eebb68dbed3e2b884e.
Thanks.

---

### Post by Bachstelze on 2010-08-10
Download the package from [http://packages.ubuntu.com](http://packages.ubuntu.com), extract it (dpkg -x foo.deb .) and check the md5sum of the file in it.

---

### Post by valugi on 2010-08-10
Thanks again.
I've looked in the repositories here:
[http://packages.ubuntu.com/search?suite=lucid&arch=i386&searchon=names&keywords=OpenSSH](http://packages.ubuntu.com/search?suite=lucid&arch=i386&searchon=names&keywords=OpenSSH)

I cannot seem to find 5.3p1-3ubuntu4, but only 5.3p1-3ubuntu3 and this one has a different MD5.

Is this 5.3p1-3ubuntu3 the same as mine, or it could be updating from somewhere else?
> OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009

---

### Post by Bachstelze on 2010-08-10
Yeah, packages.ubuntu.com seems to be out of sync. The latest version for Lucid is indeed 3ubuntu4, you can get it from here: [http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_5.3p1-3ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_5.3p1-3ubuntu4_i386.deb)

---

### Post by cavalier911 on 2010-08-10
Most packages install an md5sum file which is stored here:
/var/lib/dpkg/info

debsums is a utility that checks your installed files against the md5sum file.

```
sudo apt-get install debsums
```

```
debsums openssh-client
```

To get the updated openssh-client:

```
sudo aptitude download openssh-client
```

I extracted and md5sum matches what you posted.

---

### Post by valugi on 2010-08-10
Thanks a lot guys for the help.
My ssh is not tainted. Same md5: b26174c7f4d2d7eebb68dbed3e2b884e.

---

