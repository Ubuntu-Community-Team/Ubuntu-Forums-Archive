---
title: "Where is man?"
date: 2013-10-08
forum: Server Platforms
---

### Post by Karl_Sandfort on 2013-10-08
I just installed Ubuntu Server 12.04.3. I type, for example, **man ls** to look at the man page for the **ls** command. Does the default install not include **man**?

---

### Post by Iowan on 2013-10-08
I just checked a couple of my servers (apparently, I don't have 12.04 on them yet...) - they have **man**.

---

### Post by bab1 on 2013-10-09
> **Karl_Sandfort said:**
> I just installed Ubuntu Server 12.04.3. I type, for example, **man ls** to look at the man page for the **ls** command. Does the default install not include **man**?

What happens that makes you think the man pages (in particular ls) is not installed?

Here is my version```
 lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

```

Here is the man page in question```

man ls


[COLOR="#FF0000"]LS(1) [/COLOR]                                    User Commands                                     LS(1)

NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List  information about the FILEs (the current directory by default).  Sort entries alpha&#8208;
       betically if none of -cftuvSUX nor --sort is specified.

       Mandatory arguments to long options are mandatory for short options too.
       ...
```
Here is where those pages are located> 
/usr/share/man/man1/ls.1.gz

Note that the file is [COLOR="#FF0000"]ls.1.gz[/COLOR] and the man page is actually*** man 1 ls ***  See the [COLOR="#FF0000"]red comments[/COLOR] above.  If you had a series of man pages that where spread over multiple pages (files) you would have to call the number unless you only wanted the default first page.

Thee man pages are really there.  The only thing that gets installed without the man pages or some big well known applications.  If you check you will find the non-installed man pages.  I use apt or Synaptic to find the actual package name for the man pages.

---

### Post by Karl_Sandfort on 2013-10-09
Thank you Iowan and Bab1. I do not even have the **man **executable available. When I execute **whereis man** or **which man** I get no results. When I just type **man **it gives me an error. Interestingly enough, there are **man **directories in my search path (/usr/share and /usr/bin, I think), but no **man **and no **man **symlink. Very strange. I have never seen this, and I'm wondering if anyone knows if this is intentional. If not, then I have to assume I messed up during the install.

---

### Post by Doug S on 2013-10-09
> **Karl_Sandfort said:**
> ... Very strange. I have never seen this, and I'm wondering if anyone knows if this is intentional. If not, then I have to assume I messed up during the install.It is not intentional. Yes, I would assumed you somehow messed up during the install. (Although, I am curious as to how.)

---

### Post by papibe on 2013-10-09
Hi Karl_Sandfort.

Did you install the server using a USB stick or CD/DVD?

In case you used a USB, how did you install the ISO on the USB?

Regards.

---

### Post by bab1 on 2013-10-09
> **Karl_Sandfort said:**
> Thank you Iowan and Bab1. I do not even have the **man **executable available. When I execute **whereis man** or **which man** I get no results. When I just type **man **it gives me an error. Interestingly enough, there are **man **directories in my search path (/usr/share and /usr/bin, I think), but no **man **and no **man **symlink. Very strange. I have never seen this, and I'm wondering if anyone knows if this is intentional. If not, then I have to assume I messed up during the install.

What do you get with this command```
ls -l /usr/bin/man
```

It should return this```
-rwxr-xr-x 1 root root 102880 Dec 28  2012 /usr/bin/man
```

What is the return from just typing *man*?  It should return this```
What manual page do you want?
```

All Ubuntu versions I have installed over the years have had the manual pages included. I thing something when wrong with your install.  I assume this is easy fix.  I would just reinstall the package.  To simulate this before trying it you can use this```
sudo apt-get --simulate --reinstall install man-db
```...then just drop the --simulate.  This package includes the man executable.

---

### Post by Karl_Sandfort on 2013-10-10
> **papibe said:**
> Hi Karl_Sandfort.

Did you install the server using a USB stick or CD/DVD?

In case you used a USB, how did you install the ISO on the USB?

Regards.

I downloaded the ISO, burned it to a DVD, and booted from that. On what looks like a gui Aptitude, there was a short list of packages that you can check off if you want them installed:

OpenSSH Server
DNS Server
LAMP Server
Mail Server
PostGreSQL Server
Print Server
Samba file server
Tomcat Java server
Virtual Machine Host
Manual package selection

I checked off all of them. Other than that, I allowed the install program to proceed with the defaults.

---

### Post by Karl_Sandfort on 2013-10-10
Thanks, bab1. I think that by checking off "Manual package selection" I caused the problem myself. I'm going to try the install again, this time without checking anything. I suspect man will be included by default, as one would expect. If not, I will follow your advice and use apt-get.

---

### Post by bab1 on 2013-10-10
> **Karl_Sandfort said:**
> Thanks, bab1. I think that by checking off "Manual package selection" I caused the problem myself. I'm going to try the install again, this time without checking anything. I suspect man will be included by default, as one would expect. If not, I will follow your advice and use apt-get.

Good man.  Once you have success mark this thread as **solved**.

---

### Post by Karl_Sandfort on 2013-10-11
Reporting back. Here's what happened: When I checked "Manual package selection" it means just that: the **man** package must be installed manually. Thanks for the help, everyone. My question has been answered.

---

