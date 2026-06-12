---
title: "What is the version of openssh installed"
date: 2012-01-26
forum: Security
---

### Post by satimis on 2012-01-26
Hi all,

Ubuntu 1010 server 64bit

Chroot users with OpenSSH
[http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229](http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229)

```

With the release of OpenSSH 4.9p1, you no longer have to rely on third-party hacks or complicated chroot setups to confine users to their home directories or give them access to SFTP services ......
```

# aptitude versions openssh-server```

p   1:5.5p1-4ubuntu4                                                          maverick                                               500 
i   1:5.5p1-4ubuntu6                                                          maverick-updates
```   

# aptitude versions openssh-client```

p   1:5.5p1-4ubuntu4                                                          maverick                                               500 
i   1:5.5p1-4ubuntu6                                                          maverick-updates  
```  

Do I need to install third party hacks such as "Jailkit"?  TIA


B.R.
satimis

---

### Post by Lars Noodén on 2012-01-26
You can [Chroot](http://www.debian-administration.org/articles/590) SFTP users very easily.  Regular shell access is a bit more complex.  The main thing to pay attention to is that [ChrootDirectory](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) requires that the path  not by writable by any other user or group other than root.  No third party hacks are needed.

---

### Post by satimis on 2012-01-26
> **Lars Noodén said:**
> You can [Chroot](http://www.debian-administration.org/articles/590) SFTP users very easily.  Regular shell access is a bit more complex.  The main thing to pay attention to is that [ChrootDirectory](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) requires that the path  not by writable by any other user or group other than root.  No third party hacks are needed.

Hi,

Thanks for your advice and links.  I'll go through them later.

I'm curious to know the version of openssh running on Ubuntu.  They seem different from deb package.  Thanks

satimis

---

### Post by Lars Noodén on 2012-01-26
There's no **-v** option for [sshd](http://manpages.ubuntu.com/manpages/oneiric/en/man8/sshd.8.html).  But if you try it anyway, the error message tells you which version is installed.

```

/usr/sbin/sshd -v

```

You want 4.9 or later for ChrootDirectory:
[http://www.openssh.com/txt/release-4.9](http://www.openssh.com/txt/release-4.9)

---

### Post by CharlesA on 2012-01-26
That install of Ubuntu has openssh-server version 5.5 installed.

Lucid comes with openssh-server 5.3:

```
charles@Lucid:~$ sshd -v
sshd: illegal option -- v
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
usage: sshd [-46DdeiqTt] [-b bits] [-C connection_spec] [-f config_file]
            [-g login_grace_time] [-h host_key_file] [-k key_gen_time]
            [-o option] [-p port] [-u len]

```

---

### Post by satimis on 2012-01-26
> **Lars Noodén said:**
> There's no **-v** option for [sshd](http://manpages.ubuntu.com/manpages/oneiric/en/man8/sshd.8.html).  But if you try it anyway, the error message tells you which version is installed.

```

/usr/sbin/sshd -v

```
# /usr/sbin/sshd -v```

sshd: illegal option -- v
OpenSSH_5.5p1 Debian-4ubuntu6, OpenSSL 0.9.8o 01 Jun 2010
........

```
I got it.

> 
You want 4.9 or later for ChrootDirectory:
[http://www.openssh.com/txt/release-4.9](http://www.openssh.com/txt/release-4.9)
According to the link;
Chroot users with OpenSSH:
[http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229](http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229)

```

With the release of OpenSSH 4.9p1, you no longer have to rely on third-party hacks or complicated chroot setups to confine users to their home directories or give them access to SFTP services.....
```
It refers to "OpenSSH 4.9p1".  I think the later version should also work.

Thanks

B.R.
satimis

---

### Post by satimis on 2012-01-26
> **CharlesA said:**
> That install of Ubuntu has openssh-server version 5.5 installed.

Lucid comes with openssh-server 5.3:

```
charles@Lucid:~$ sshd -v
sshd: illegal option -- v
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
usage: sshd [-46DdeiqTt] [-b bits] [-C connection_spec] [-f config_file]
            [-g login_grace_time] [-h host_key_file] [-k key_gen_time]
            [-o option] [-p port] [-u len]

```
Hi CharlesA,

Advice noted.  Thanks

satimis

---

