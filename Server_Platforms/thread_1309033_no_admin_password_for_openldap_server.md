---
title: "no admin password for openldap server"
date: 2009-11-01
forum: Server Platforms
---

### Post by Jarod42 on 2009-11-01
Hi,
I am running Ubuntu 9.10 x86_64 Server and installed slapd the other day. The problem I ran into is a missing admin password for the directory. I've been trying to make the LDAP directory fly for 2 days now, with no luck.
I took a look at the documentation for Ubuntu 9.04 under:[https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html)

It clearly states > The installation process will prompt you for the LDAP directory admin password and confirmation., but it didn't. 
I also tried > sudo dpkg-reconfigure slapd, but no luck either.
Obviously something must have changed from 9.04 to 9.10, but I have found no source of documentation so far.
If someone could point me into the right direction, I'd very much appreciate it.

Regards.
 Jarod

---

### Post by bradjinks81 on 2009-11-01
I am having the same problem. The setup never prompted for a password. Same with reconfigure...

---

### Post by catdevrandom on 2009-11-02
Hello,

I have the same problem. This thread here: [http://ubuntuforums.org/showthread.php?t=1295934](http://ubuntuforums.org/showthread.php?t=1295934) has a solution, but it didn't really work for me.

You might also want to check the bug reports that have been filed related to the outdated documentation:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/459403](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/459403)
[https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/442498](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/442498)

I'll keep trying, and if I get anything I'll post it here.

Cheers!

---

### Post by catdevrandom on 2009-11-02
Now I found out what was going wrong for me. I was having problems because I tried to change the directory for the database. Should just leave the default directory (/var/lib/ldap); even symlinks don't seem to work.

The package slapd now comes with minimal configuration (see [https://lists.ubuntu.com/archives/ubuntu-server/2009-August/003182.html](https://lists.ubuntu.com/archives/ubuntu-server/2009-August/003182.html)). You have to create the first database yourself. The post in [http://ubuntuforums.org/showpost.php?p=8161118&postcount=6](http://ubuntuforums.org/showpost.php?p=8161118&postcount=6) explains in detail how to do it.

Another difference is that now there is no admin username for connecting to LDAP anymore. You can now connect to change configurations using the following options: **-Y EXTERNAL -H ldapi:///**. You'll have to run as root or use sudo for it to work.

For example, instead of following the instructions of the Ubuntu Documentation like this: 

```
ldapadd -x -D cn=admin,dc=example,dc=com -W -f example.com.ldif
```

you'll do it like this:

```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f example.com.ldif
```

Once you've added the database as explained [in the other post]("http://ubuntuforums.org/showpost.php?p=8161118&postcount=6"), you'll have the user "cn=admin,dc=home,dc=local" as manager of the database. Then you can just follow the [instructions in the official documentation]("https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html") as before, authenticating using that as username and password.

Hope that helps!

---

