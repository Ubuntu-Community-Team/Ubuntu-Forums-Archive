---
title: "[SOLVED] No-IP?"
date: 2007-12-24
forum: Server Platforms
---

### Post by Syndacate on 2007-12-24
Yeah, I'm getting sick of going to [http://www.whatismyip.com/](http://www.whatismyip.com/) every 5 minutes when somebody wants a file.

I had no-ip DUC on my Windows machine, and I want to put it on here, but some of the installation files are kind of ambiguous.

I downloaded the tar and extracted it, but I don't know what to do with it...

I typed:

```

sudo apt-get install no-ip

```

And it gave me an error:
```

The following NEW packages will be installed:
  no-ip
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.4kB of archives.
After unpacking 135kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/universe no-ip 2.1.3-3build1 [21.4kB]
Fetched 21.4kB in 0s (36.2kB/s)
Selecting previously deselected package no-ip.
(Reading database ... 147455 files and directories currently installed.)
Unpacking no-ip (from .../no-ip_2.1.3-3build1_i386.deb) ...
Setting up no-ip (2.1.3-3build1) ...
Starting dynamic address update: Can't locate configuration file /etc/no-ip.conf. (Try -c). Ending!

```

I'm not entirely sure what it wants me to do...?

Any help?

(I'm not smart when it comes to servers and such, Windows was easy because it had the task bar thing and was an executable and such.  I'm finding these .tar.gz files a bit hard to install with in Ubuntu).

Like ex.  Anybody know any information on how to get apache status?  Like current connections, or the logs, or anything?

---

### Post by p_quarles on 2007-12-24
The package is already installed, but there's a bug which causes it to fail to install the configuration file correctly:
[https://bugs.launchpad.net/ubuntu/+source/no-ip/+bug/134411](https://bugs.launchpad.net/ubuntu/+source/no-ip/+bug/134411)

According to that bug report, the newest package in Debian will work correctly:
[http://packages.debian.org/sid/noip2](http://packages.debian.org/sid/noip2)

Once you've downloaded the correct version of the package, you'll be able to install it using
```
sudo dpkg -i *package-name*
```
By the way, you didn't actually need to get that source package (the .tar.gz). The "apt-get" command automatically downloads packages from the Ubuntu repositories, and that's exactly how it install the package you selected.

---

### Post by Syndacate on 2007-12-24
> **p_quarles said:**
> The package is already installed, but there's a bug which causes it to fail to install the configuration file correctly:
[https://bugs.launchpad.net/ubuntu/+source/no-ip/+bug/134411](https://bugs.launchpad.net/ubuntu/+source/no-ip/+bug/134411)

According to that bug report, the newest package in Debian will work correctly:
[http://packages.debian.org/sid/noip2](http://packages.debian.org/sid/noip2)

Once you've downloaded the correct version of the package, you'll be able to install it using
```
sudo dpkg -i *package-name*
```
By the way, you didn't actually need to get that source package (the .tar.gz). The "apt-get" command automatically downloads packages from the Ubuntu repositories, and that's exactly how it install the package you selected.

Yeah, I know I didn't need to get the .tar.gz to use apt-get.  I was originally just gonna download that and dpkg -i it, but then I said 'screw it' and just ran apt-get while I was in console.

Umm, thanks for the info, but I'm not sure which one I need to download, there.

I downloaded the one in .tar.gz format but when I went to install it it told me it's not a debian format archive.

I'm not sure which one to download at that second link...  

Any info on that?

---

### Post by p_quarles on 2007-12-24
Sure. Based on the output of the apt-get command you ran, you're using the i386 version of of Ubuntu, so get that version of the package from the Debian packages page.

---

### Post by selmore on 2007-12-24
try

service /etc/init.d/no-ip/ start

---

### Post by Syndacate on 2007-12-24
> **p_quarles said:**
> Sure. Based on the output of the apt-get command you ran, you're using the i386 version of of Ubuntu, so get that version of the package from the Debian packages page.

Seems as though the fun never ends.

I went to the site listed above, downloaded the version for i386 (in .deb format) - typed **"sudo dpkg -i filename"** - and cmae up with this joyous error:

```

syndacate@syndacate-desktop:~/Desktop$ sudo dpkg -i noip2_2.1.7-5_i386.deb
[sudo] password for syndacate:
Selecting previously deselected package noip2.
(Reading database ... 147464 files and directories currently installed.)
Unpacking noip2 (from noip2_2.1.7-5_i386.deb) ...
dpkg: dependency problems prevent configuration of noip2:
 noip2 depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.6.1-1ubuntu10.
dpkg: error processing noip2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 noip2

```

No idea what that means.

Do you want more information or are you sure it's i386?

Maybe it's "hurd-i386" instead?

[quote=selmore]try

service /etc/init.d/no-ip/ start[/quote]

It just tells me that "services" is not a valid command.

---

### Post by p_quarles on 2007-12-24
Oops. You're right: the Debian version uses a newer version of libc6 than is currently available for Ubuntu. Sorry for overlooking that.

Anyway, make sure the version you installed from the repositories is still there:
```
dpkg --get-selections no-ip
```
It should return this line:
```
no-ip                   install
```
If it doesn't do that, run the following. If it did return the state as "install," you can skip this step:
```
sudo apt-get remove --auto-remove no-ip
sudo apt-get install no-ip
```
Next step: I think selmore's command was just a typo. Here's what should work:
```
sudo /etc/init.d/no-ip start
```
If that fails, try the fix listed on the bug report page:
```
sudo no-ip -C
```
This is supposed to automatically generate the config file for the program. After that, run the "start" command from the previous step again.

---

### Post by Syndacate on 2007-12-24
> **p_quarles said:**
> Oops. You're right: the Debian version uses a newer version of libc6 than is currently available for Ubuntu. Sorry for overlooking that.

Anyway, make sure the version you installed from the repositories is still there:
```
dpkg --get-selections no-ip
```
It should return this line:
```
no-ip                   install
```
If it doesn't do that, run the following. If it did return the state as "install," you can skip this step:
```
sudo apt-get remove --auto-remove no-ip
sudo apt-get install no-ip
```
Next step: I think selmore's command was just a typo. Here's what should work:
```
sudo /etc/init.d/no-ip start
```
If that fails, try the fix listed on the bug report page:
```
sudo no-ip -C
```
This is supposed to automatically generate the config file for the program. After that, run the "start" command from the previous step again.

Wow, I really have no idea how you guys rememeber all these "off-standard" commands for UNIX - but yeah, thanks man, it worked, it didn't create it the first time, only asked for UN/PW, then it wouldn't work, then I tried creating it again and it set up the config file 100%, 5 min later my no-ip account works.

You rule - thanks.

---

### Post by p_quarles on 2007-12-24
Heh. The command line seems confusing at first (I remember that feeling well), but it's actually a really well-organized system. Once you get the basics down, you start to see the logic behind the whole system. For what it's worth, I got my real introduction to the shell from Scott Granneman's *Linux Phrasebook*. 

Glad I could help.

---

### Post by Syndacate on 2007-12-24
> **p_quarles said:**
> Heh. The command line seems confusing at first (I remember that feeling well), but it's actually a really well-organized system. Once you get the basics down, you start to see the logic behind the whole system. For what it's worth, I got my real introduction to the shell from Scott Granneman's *Linux Phrasebook*. 

Glad I could help.

The basic commands make sense, but then each program has it's "call" name (ie. "apt-get") and each program has its options which just gets confusing...

---

### Post by SemperNoob on 2008-01-24
Really excellent tutorial on how to get set up with No-IP here: 

[http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html](http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html)

Followed it on gutsy and seem to be up and running.

---

