---
title: "Setting up a Distributed Web Host (Testing/Learning)"
date: 2009-11-29
forum: Server Platforms
---

### Post by dummptyhummpty on 2009-11-29
I have an old Dell PowerEdge 700 that I want to use to experiment with web hosting (and IPv6). I plan to load a bare install of Ubuntu Server and use VMware Server to virtualize separate machines for hosting (Apache, Mail, DNS, SQL, etc). 

[LIST=1]
[*]Are there any good guides or references for doing something like that? What's the best way to manage all these separate servers? I looked into Webmin, but didn't know if there was a better option.
[*]Is there a way to tie all of the machines users together so that I don't have to change my password on each VM?
[*]Lastly, I have one 80gb SATA drive and a 500GB Raid-1 (FakeRaid) drive. Any suggestions how to store things?
[/LIST]
Thank you!

---

### Post by Josh1 on 2009-11-29
> **dummptyhummpty said:**
> I have an old Dell PowerEdge 700 that I want to use to experiment with web hosting (and IPv6). I plan to load a bare install of Ubuntu Server and use VMware Server to virtualize separate machines for hosting (Apache, Mail, DNS, SQL, etc). 

[LIST=1]
[*]Are there any good guides or references for doing something like that? What's the best way to manage all these separate servers? I looked into Webmin, but didn't know if there was a better option.
[*]Is there a way to tie all of the machines users together so that I don't have to change my password on each VM?
[*]Lastly, I have one 80gb SATA drive and a 500GB Raid-1 (FakeRaid) drive. Any suggestions how to store things?
[/LIST]
Thank you!

Have a play around with ESXI, it's a free vmserver install for Linux, that runs directly off a custom fedora.

---

### Post by Denbert on 2009-11-29
> **dummptyhummpty said:**
> I have an old Dell PowerEdge 700 that I want to use to experiment with web hosting (and IPv6). I plan to load a bare install of Ubuntu Server and use VMware Server to virtualize separate machines for hosting (Apache, Mail, DNS, SQL, etc). 



It's a great idea as I have the same setup :-)

First of all, you might consider using Debian Lenny for HOST OS as this distro is very conservative regarding packages. The Ubuntu 8.04 LTS is another solution. Remember to choose a 64-bit system, as this will give you the ability to make 64-bit virtual machines. Both will work with this [great howto]("http://www200.pair.com/mecham/raid/raid1.html"), where you also will try to exchange a fail drive. (I've done it on a real production server and it works)

After the install of a base system with a working raid, I only install ssh and openssh-server.

Now you have a perfect RAID server with a small footprint for hosting your VMWare Server 2.02

Then you install the VMware Server 2.02.

First gain root access and then install necessary dependencies:
```
#aptitude install linux-headers-`uname -r` build-essential xinetd
```

Then go to folder with the downloaded VMware and do this to unpack:

```
#tar xvfz VMware-server-*.tar.gz
#cd vmware-server-distrib
#./vmware-install.pl
```

If you install on ubuntu you can enable root access with this:

```
#sudo passwd root
```

I have 3 servers with this setup and it's powerful, flexible and very easy to backup with a cronjob.

---

### Post by dummptyhummpty on 2009-11-29
> **Josh1 said:**
> Have a play around with ESXI, it's a free vmserver install for Linux, that runs directly off a custom fedora.

Thanks, I was planning to use ESXi, but it's not supported on my PowerEdge.

> **Denbert said:**
> It's a great idea as I have the same setup :-)

First of all, you might consider using Debian Lenny for HOST OS as this distro is very conservative regarding packages. The Ubuntu 8.04 LTS is another solution. Remember to choose a 64-bit system, as this will give you the ability to make 64-bit virtual machines. Both will work with this [great howto]("http://www200.pair.com/mecham/raid/raid1.html"), where you also will try to exchange a fail drive. (I've done it on a real production server and it works)

Thanks for the guide and suggestions. I'd love to do 64-bit, but my PowerEdge has an early P4 processor and doesn't support 64-bit :(

Now that I seem to be ok on the host setup, are there any good guides for setting up all the web hosting services in separate Virtual Machines?

---

### Post by Denbert on 2009-11-29
> **dummptyhummpty said:**
> Thanks, I was planning to use ESXi, but it's not supported on my PowerEdge.

ESXi is not as easy to backup as the VMware 2.0.2 server running on Linux

> **dummptyhummpty said:**
> 
Now that I seem to be ok on the host setup, are there any good guides for setting up all the web hosting services in separate Virtual Machines?

There are tons of great howto's out there. Most Web2.0 setups asks for webserver and MySgl setup, for webserver i Personally prefer the [Lighty]("http://www.lighttpd.net/") webserver as it's fast, has a small footprint and I find configuration less complicated than the Apache Server.

Lighty howtos:

Ubuntu Distro: [http://www.howtoforge.com/installing-lighttpd-with-php5-and-mysql-support-on-ubuntu-9.04](http://www.howtoforge.com/installing-lighttpd-with-php5-and-mysql-support-on-ubuntu-9.04)

Debian Lenny: [http://www.howtoforge.com/installing-lighttpd-with-php5-and-mysql-support-on-debian-lenny](http://www.howtoforge.com/installing-lighttpd-with-php5-and-mysql-support-on-debian-lenny)

these servers will you able to use Drupal, Wordpress or any other type of database driven web2.0 website.

Setup a VM machine with 6 gb. disk 512 mb. ram and bridge network, setup static IP and you are having a fast and rock steady webserver.

---

