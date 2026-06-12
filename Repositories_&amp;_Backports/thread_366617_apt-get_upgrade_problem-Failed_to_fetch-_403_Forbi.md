---
title: "apt-get upgrade problem-Failed to fetch- 403 Forbidden"
date: 2007-02-21
forum: Repositories &amp; Backports
---

### Post by metalhippyrich on 2007-02-21
I am getting the following upgrade problem on edgy.

[FONT="Courier New"]Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu4_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu4_i386.deb)  403 Forbidden[/FONT]

Is this something I'm doing wrong, or is it an external error?  Help!
I have run apt-get update.  It's doing it on more than one machine here, but surely if it was happening to everyone there'd be something else about it.

When I use Firefox to navigate to that location I get the slightly more detailed error:

[FONT="Arial"]While trying to retrieve the URL: [http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu4_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu4_i386.deb)

The following error was encountered:

    * The request or reply is too large.

      If you are making a POST or PUT request, then your request body (the thing you are trying to upload) is too large. If you are making a GET request, then the reply body (what you are trying to download) is too large. These limits have been established by the Internet Service Provider who operates this cache. Please contact them directly if you feel this is an error. [/FONT]


The exact output, followed by my sources.list is below:

[FONT="Courier New"]root@frog:/etc/apt# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-style-default
  openoffice.org-style-industrial openoffice.org-writer python-uno
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.1MB/69.9MB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main openoffice.org-core 2.0.4-0ubuntu4
  403 Forbidden
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main openoffice.org-common 2.0.4-0ubuntu4
  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu4_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu4_i386.deb)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.0.4-0ubuntu4_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.0.4-0ubuntu4_all.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/FONT]


sources.list

[FONT="Courier New"]
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# debian.scribus.net - Primary repository
deb [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) edgy main restricted

# debian.tagancha.org - Backup repository
deb [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) edgy main restricted
[/FONT]

---

### Post by bapoumba on 2007-02-21
Hello,
the repository may be down for now.
You can edit your sources.list and choose another mirror or just remove for now the gb. Open a terminal (> Accessories > Terminal)
**sudo nano -B /etc/apt/sources.list** to edit the lines, CTRL-O to save (same name), CTRL-X to exit. Then **sudo aptitude update**.

edit : I can access the repo and dl the files.

---

### Post by metalhippyrich on 2007-02-21
Hum- thanks for your quick reply.  Tried with another mirror, did apt-get update, then apt-get upgrade and get the same error:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main openoffice.org-core 2.0.4-0ubuntu4
  403 Forbidden [IP: 195.248.90.38 80]


I notice that another computer is doing the same thing, but with different files.
I'm puzzled.

---

### Post by bapoumba on 2007-02-21
Is the other computer on the same network ?
Do you have a proxy ? If so, what is the output to **cat /etc/apt/apt.conf** ?
Some other user having the same problems often resolve it accessing repositories via ftp rather than http (in sources.list file).

---

### Post by metalhippyrich on 2007-02-21
Marvellous!  Changing the lines in /etc/apt/sources.list
from:  deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
to:      deb [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

worked round it fine.  Thanks!

Yes, all computers are on the same network and we're not using a proxy; there is no file /etc/apt/apt.conf.  I guess I have to put it down to problems with our network, our possibly our ISP.

---

### Post by dr.jackal on 2007-02-26
Hi,
I'm encountering the same problem only that with me changing http to fpt in sources.list doesn't work but just results in a different failure (see attachment)

this is my sources.list:
#Ubuntu
deb [ftp://de.archive.ubuntu.com/ubuntu/](ftp://de.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

#Ubuntu Updates
deb [ftp://de.archive.ubuntu.com/ubuntu/](ftp://de.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [ftp://de.archive.ubuntu.com/ubuntu/](ftp://de.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

#Ubuntu Backports
deb [ftp://de.archive.ubuntu.com/ubuntu/](ftp://de.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [ftp://de.archive.ubuntu.com/ubuntu/](ftp://de.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

#Ubuntu Security (Orig)
#deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

#Ubuntu Security (deutscher Mirror)
deb [ftp://de.archive.ubuntu.com/ubuntu/](ftp://de.archive.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [ftp://de.archive.ubuntu.com/ubuntu/](ftp://de.archive.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse

#Von EasyUbuntu
deb [ftp://packages.freecontrib.org/ubuntu/plf/](ftp://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

#VIM, Gaim2, etc.
deb [ftp://www.freshnet.org/debian/](ftp://www.freshnet.org/debian/) dapper/

#nur VIM7
#deb [http://hassers.fi/ubuntu](http://hassers.fi/ubuntu) dapper vim
#deb-src [http://hassers.fi/ubuntu](http://hassers.fi/ubuntu) dapper vim


Help would be very much appreciated!

---

### Post by bapoumba on 2007-02-26
> **dr.jackal said:**
> 
#Von EasyUbuntu
deb [ftp://packages.freecontrib.org/ubuntu/plf/](ftp://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

#VIM, Gaim2, etc.
deb [ftp://www.freshnet.org/debian/](ftp://www.freshnet.org/debian/) dapper/

#nur VIM7
#deb [http://hassers.fi/ubuntu](http://hassers.fi/ubuntu) dapper vim
#deb-src [http://hassers.fi/ubuntu](http://hassers.fi/ubuntu) dapper vim


First, please remove the freecontrib repositories (the ones you have are for breezy, and freecontrib does not maintain ubuntu packages anymore) and the comment the other freshnet repo.
You can also try to use the general repositories (ie remove the "de." in the url).

Switching from http to ftp usually helps when there are problems with ISP for examples (some proxies that do not allow http requests, from what I understood).

Sorry not to be of much help :/

---

### Post by kleinlappies on 2007-11-17
Hi there

I changed my repo links from http to ftp.
I also got some other error message BUT my packages downloaded and installed without any hassles. 
So what i would do is change the http to ftp. do sudo apt-get update and sudo apt-get upgrade. Then change the ftp's back to http.

Thanks for the info bapoumba

---

### Post by ppetrovic on 2011-09-12
Same annoying problem here.
it was that /etc/apt/apt.conf file
- it contained some proxy.

This is a nasty bug of apt-get.

the proxy was inserted there automatically when
the computer connected to wifi, but it was not removed
automatically later on, when it connected over cable :-(

I have even disabled wifi in bios setup, and still the same problem, until I found the post above in this forum, thanks... :)

---

