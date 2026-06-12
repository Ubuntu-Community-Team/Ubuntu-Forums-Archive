---
title: "Samba passwords"
date: 2011-11-14
forum: Server Platforms
---

### Post by radek_42 on 2011-11-14
Hi,

I already did web search to find answers with no luck so far. This is what I'd like to do:

> Server running (cli) ubuntu w/ samba service.

> The server has user "adam" with password "adam"

> I'd like to connect to it from Win/Mac/Linux machines to do back ups as user "adam"

Now, I can do all this, but I always need to do:
smbpasswd -a adam
and set password for the samba user. 

Since I often change passwords on the server I'd like samba to use the same database. In another words, is there a way to skip adding samba user (smbpasswd -a) and simply use server's users authentication. 

It seemed that PAM was way to go, but I cannot set it up properly.

I would really appreciate you help, because it starts to drive me crazy!!!

Thanks, Radek

---

### Post by SeijiSensei on 2011-11-14
Take a look at force_user and force_group in the man page for smb.conf.  You can tell Samba to write to the operating system as a specific user that's different from the users accessing the share.  Perhaps "force_user = adam" might do the trick.

---

### Post by radek_42 on 2011-11-16
That sounds like a nice trick, but not quite what I was looking for.

I was playing with in again after some time and found this link
[http://jaka.kubje.org/infodump/2007-05-14-unix-samba-password-sync-on-debian-etch/]("http://jaka.kubje.org/infodump/2007-05-14-unix-samba-password-sync-on-debian-etch/")
which deals with this exact issue. Unfortunately config file in new Ubuntu as well as Debian Squeeze look different so this tutorial does not quite work. After several trials (bless virtual machines) it appears to work more-less out of the box. I believe the trick is to login to the server via e.g. ssh to "activate" password syncing. 

If somebody would like to chime in and explain this a bit more I would really appreciate it (it's still not quite clear what made it work at the end and it bugs me :-)

Cheers,
Radek

> **SeijiSensei said:**
> Take a look at force_user and force_group in the man page for smb.conf.  You can tell Samba to write to the operating system as a specific user that's different from the users accessing the share.  Perhaps "force_user = adam" might do the trick.

---

### Post by Morbius1 on 2011-11-16
libpam-smbpass automatically makes the samba password equal to the server user's login password.

You can change it using smbpasswd but after a reboot of the machine it automatically sets it back to the login password.

Of course you have to actually create a user on the server with a login password so if you create a user using something like this: "sudo useradd -s /bin/true user-name" you're out of luck.

---

