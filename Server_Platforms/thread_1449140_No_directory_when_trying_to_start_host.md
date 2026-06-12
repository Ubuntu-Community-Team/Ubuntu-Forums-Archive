---
title: "No directory when trying to start host?"
date: 2010-04-07
forum: Server Platforms
---

### Post by 1serveyou on 2010-04-07
Hey guys, I know this is a dumb question, but this is probably the 6th reformat of Ubuntu server and I believe this is my first time getting this error.

I type in /etc/init.d/hostname.sh start

and I receive
bash: /etc/init.d/hostname.sh: No such file directory

For hostname I've use "hostname" and my actual hostname, and both receive the same error.

Although when I do hostname is shows the correct hostname but without the the comcast part of it , and when I type in hostname -f, I get the correct hostname with the comcast part of it. 

I'm just not sure what I'm doing wrong. I appreciate any help!

---

### Post by KB1JWQ on 2010-04-07
/etc/init.d/hostname is the command.  There's no .sh there.

---

### Post by cdenley on 2010-04-07
[http://changelogs.ubuntu.com/changelogs/pool/main/s/sysvinit/sysvinit_2.87dsf-4ubuntu11/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/s/sysvinit/sysvinit_2.87dsf-4ubuntu11/changelog)
> 
sysvinit (2.87dsf-4ubuntu3) karmic; urgency=low

  FFE LP: #427356.

  * Various initscripts have been replaced by Upstart jobs shipped in
    other packages, the following have been removed:
    - **hostname.sh**
    - mountkernfs.sh
    - mountdevsubfs.sh
    - checkroot.sh
    - mtab.sh
    - checkfs.sh
    - mountall.sh
    - mountall-bootclean.sh
    - mountoverflowtmp
    - mountnfs.sh
    - mountnfs-bootclean.sh
    - bootmisc.sh
    - bootlogs
    - rmnlogin

 -- Scott James Remnant <scott@ubuntu.com>  Tue, 15 Sep 2009 02:45:59 +0100

```

sudo service hostname start

```
or you can just do
```

sudo hostname -b -F /etc/hostname

```

---

### Post by 1serveyou on 2010-04-07
I still get the same response. I think I will reformat again haha, I deleted out the nameservers after I got that last error, but can't remember what was there.

---

### Post by 1serveyou on 2010-04-07
> **cdenley said:**
> [http://changelogs.ubuntu.com/changelogs/pool/main/s/sysvinit/sysvinit_2.87dsf-4ubuntu11/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/s/sysvinit/sysvinit_2.87dsf-4ubuntu11/changelog)

```

sudo service hostname start

```or you can just do
```

sudo hostname -b -F /etc/hostname

```


I receive "unrecognized service"

I just reinstalled ubuntu 9.10 server, and getting the same error. I'm following [http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

Also does comcast normally have a "." at the end of its address? 

Thanks again in advance

---

### Post by cdenley on 2010-04-07
> **1serveyou said:**
> I receive "unrecognized serve"

I'm assuming you get that output for the first command. All that "service" does is run the second command I posted. Both commands are installed by the hostname package, which I'm pretty sure is installed by default.
```

sudo apt-get install hostname
sudo service hostname start

```

---

### Post by 1serveyou on 2010-04-07
> **cdenley said:**
> I'm assuming you get that output for the first command. All that "service" does is run the second command I posted. Both commands are installed by the hostname package, which I'm pretty sure is installed by default.
```

sudo apt-get install hostname
sudo service hostname start

```

I'm sorry I'm not sure which one you mean by first command. I ran "sudo service hostname start", I receive "hostname stop/waiting." Also when you are saying hostname you mean for me to write "hostname" not what I'm using for a hostname right?

---

### Post by cdenley on 2010-04-07
> **1serveyou said:**
> I'm sorry I'm not sure which one you mean by first command. I ran "sudo service hostname start", I receive "hostname stop/waiting." Also when you are saying hostname you mean for me to write "hostname" not what I'm using for a hostname right?
I didn't give you anything that should be substituted. That is the correct output. As I said, all it does is run "hostname -b -F /etc/hostname".

---

### Post by 1serveyou on 2010-04-11
Thanks guys, after playing around with it, I ended up getting it to work. I think I had an IP off or something like that. I've been playing around with Ubuntu Server all weekend(injured my knee so I can't move around too much!).

I finally have working folders that I can view, edit, and execute!

---

