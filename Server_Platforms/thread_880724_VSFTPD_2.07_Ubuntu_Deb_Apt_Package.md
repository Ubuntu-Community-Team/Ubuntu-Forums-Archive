---
title: "VSFTPD 2.07 Ubuntu Deb Apt Package"
date: 2008-08-05
forum: Server Platforms
---

### Post by JpMaxMan on 2008-08-05
I'm not sure if any of you have been caught up in this TLS FTPES debacle where filezilla has updated their client and thus broken backward support w/ older FTPS servers not compliant w/ the latest libTLS package (this is my summary from reading this: [http://forum.filezilla-project.org/viewtopic.php?f=2&t=7465&st=0&sk=t&sd=a](http://forum.filezilla-project.org/viewtopic.php?f=2&t=7465&st=0&sk=t&sd=a) ).

Point being, apparently this is fixed in the latest VSFTPD 2.07 - however, this version does not seem to be distributed via the apt-get nor can I find a .deb package for it.  In fact it seems to be on version 2.05. I'm fine to simply download and compile the latest, but in terms of "management" it'd be nice to keep the package support. My sources list is set to the standard Gutsy updates.

Does anybody know when this will be pushed? Is there a more "aggressive" source list I can migrate to?  Any other creative solutions here.  Basically I have an FTP user base and have had to allow non-ssl connections to FTP again because the latest filezilla won't work unless i upgrade the server.

Thanks!

---

### Post by JpMaxMan on 2008-08-05
Update: I upgraded to Ubuntu 8.04 and now I'm on vsftpd 2.06 - but still not 2.07 : (

---

### Post by hux on 2008-08-28
I'm in exactly the same boat as you so I'll be paying attention to this thread.

FWIW, a bug report about this has been filed on Launchpad (although it's not really a bug):

[https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/254905](https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/254905)

Hopefully, v2.0.7 will eventually show up on apt. Until then it's a rather large pain in the rear. :(

---

### Post by ludw on 2008-09-10
I would also like to push for this. Can't be that hard to make a new package, now can it?

---

### Post by ludw on 2008-09-12
I finally tried compiling it from sources and it's actually not that hard. Try this on your own risk, I don't know if it breaks stuff for you or whatever.

So, here what I did to get vsftpd 2.0.7 working under hardy:

First install vsftpd 2.0.6 from apt-get and configure it.
Download the 2.0.7 tarball from [ftp://vsftpd.beasts.org/users/cevans/](ftp://vsftpd.beasts.org/users/cevans/) and untar it.

Enter the untared dir.

Install the deps:
```

sudo apt-get install libcurl3-openssl-dev libc6-dev libcap-dev libpam0g-dev

```

You can add stuff like SSL-support by editing builddefs.sh. I Changed the following:
```

#define VSF_BUILD_SSL

```

Build with make and hope it will work :)
```

make

```

Replace the previously installed vsftpd with the new one.
You might want to keep a copy of the old file around just in case.
```

sudo mv vsftpd /usr/sbin/vsftpd

```

And that's it! Start vsftpd and it should be working properly with TLS and FileZilla.

---

### Post by crumble6 on 2008-09-12
Thanks ever so much ludw, that worked perfectly!

---

### Post by tazeat on 2008-09-28
Thanks ludw, awesome work.

For anyone that wants the i386 I compiled it (Hardy 8.04) according to ludw's directions with ssl enabled [http://tazeat.com/misc/vsftpd.rar](http://tazeat.com/misc/vsftpd.rar).

Just unrar and replace the old one:
```

unrar e vsftpd.rar
sudo mv vsftpd `which vsftpd`

```

Thanks!

---

### Post by minordemocritus on 2009-02-11
Anything you build yourself should go into the /usr/local filesystem. As Flannel put it in #ubuntu-offtopic, overwriting the binary with a compiled one is "not happy".

Compile the source with make, then:
```

$ sudo cp vsftpd /usr/local/sbin/vsftpd

```

Then edit the init script:
```

$ sudo nano -w /etc/init.d/vsftpd

replace:

DAEMON=/usr/sbin/vsftpd

with:

DAEMON=/usr/local/sbin/vsftpd

```

This will point the init script to the new binary.

---

