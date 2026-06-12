---
title: "Ubuntu Server Config"
date: 2006-04-09
forum: Server Platforms
---

### Post by gymsmoke on 2006-04-09
I've successfully setup a workstation and a laptop on 5.10, and now I want to make the leap to setup a production server using Breezy Badger...
So far, I know I want the following:
Ubuntu 5.10 server
SSH
postfix mail (Need to find out if pop3 or imap is a better choice here)
spamassassin
dns (bind9)
ftp
clamav / freshclam
firestarter
openssl
Apache2
mysql5
php5
phpMyAdmin

I have 3 domains (each with its own ip) that I will setup.  The main domain will be the box itself, and two others for live web sites.  Each of these live sites will also have a virtual host under it for development and testing.

All services to listen on alternate ports (not default), if possible.
Traffic should be whitelist (all is denied unless specifically listed).
Postfix needs to have relay set up since I need to smtp forward mail to and from the mail server.
Also, would like to have VServers set up ... looks very cool... I really like the idea, but am not sure how much work this is in getting it right...  Apparently, I would need to patch the kernel to allow it, so that means installing kernel sources...  I'm ok with reconfiguring a kernel, it would just require more testing to make sure that the box is sound before going 'hot' ...

Any input on what else is a "nice to have" or that will make administering the box less legwork is greatly appreciated.  This is my first shot at this, so all help is appreciated.

---

### Post by John.Michael.Kane on 2006-04-09
[http://www.gideonsoftworks.com/SSHHOWTO/SSH-HOWTO.html](http://www.gideonsoftworks.com/SSHHOWTO/SSH-HOWTO.html)
[http://www.arches.uga.edu/~pkeck/ssh/](http://www.arches.uga.edu/~pkeck/ssh/)

[http://johnny.chadda.se/2005/04/30/postfix-howto/](http://johnny.chadda.se/2005/04/30/postfix-howto/)
[http://homex.subnet.at/~max/mail/mailman.php](http://homex.subnet.at/~max/mail/mailman.php)

[http://www.madboa.com/geek/openssl/](http://www.madboa.com/geek/openssl/)
[http://www.openssl.org/docs/HOWTO/](http://www.openssl.org/docs/HOWTO/)

[http://www.linuxjava.net/howto/webapp/](http://www.linuxjava.net/howto/webapp/)
[http://httpd.apache.org/docs/1.3/misc/howto.html](http://httpd.apache.org/docs/1.3/misc/howto.html)
[http://www.tldp.org/HOWTO/Apache-Overview-HOWTO.html](http://www.tldp.org/HOWTO/Apache-Overview-HOWTO.html)
[http://tomcat.apache.org/tomcat-3.2-doc/tomcat-apache-howto.html](http://tomcat.apache.org/tomcat-3.2-doc/tomcat-apache-howto.html)

[http://www.lamphowto.com/](http://www.lamphowto.com/)

Hope it offers some help.

---

### Post by gymsmoke on 2006-04-12
SD~
Thanks for the links.  I've read through a few, and am still going through the rest...

Would I be better served at this point going with 5.10 and upgrading to Dapper on release, or installing Dapper at this point and patching through the release cycle?

I've already put the plan in place for moving my existing sites and mail to a temp home while I do this, and I'll have about a month to get the server up and fully functional, so there is time for some experimentation (but not alot)...

Any input would be very much appreciated.

---

### Post by gymsmoke on 2006-04-14
SD~
Ok.  Read through the links...  (Apache will definitely be 2.0, though, not 1.3)...
I like the list I came up with (OP).  Should be a strong setup for a server.
I'm definitely going with 5.10 for the moment... I don't want to push the envelope with Dapper until I'm a little more comfortable (and experienced).
mysql5 / php5 seem to be possible stumbling areas, since it looks as though I'll have to compile these from source.
In order to compile these (and probably others in the future), I know that I'll need to
sudo apt-get install build-essentials, but Id also like to have the kernel headers and source on hand, as well.
Any input as to what these are called in the apt world?

We're starting the install tomorrow around 9am (EDT), so any input is greatly appreciated.  I'm going to be up late tonight studying up, reviewing my configuration notes, etc., so there are no surprises.  I'm very excited at the prospect of having my first production server install of Ubuntu running!

---

### Post by fdoving on 2006-04-15
I would strongly recommend using Ubuntu packages for most if not all applications. Compiling yourself makes upgrading and doing security fixes more time consuming and complicated.
It's preferable to use packages from the apt repositories. To make updating fast, secure and easy.

That's my opinion.
I would consider getting mysql5 and php5 from dapper (using apt pinning to only get the needed packages) before considering compiling yourself.

- Frode

---

### Post by gymsmoke on 2006-04-15
Frode~
I tend to agree with you, but I'm not familiar with how to "pin" repositories, unless you're referring to the adding of them to /etc/apt/sources temporarily.

Also, do you know which repo's I would need to add in order to get mysql/php5 ?

Thanks.  The base install is underway, which means that I should be ready to start looking for these apps in about an hour or so...

---

### Post by LordHunter317 on 2006-04-15
Why do you want to run of all this stuff on the same box?

---

### Post by CrustyDOD on 2006-04-15
[QUOTE=LordHunter317]Why do you want to run of all this stuff on the same box?[/QUOTE]
Its called, entry server configuration :D Not the best but for start is good..

I will also run similar stuff (without Gnome) on 1 box for start and after sometime, new boxes will be installed..

You got any better solution LordHunter317? Second server is not an option yet..

---

### Post by gymsmoke on 2006-04-15
LH~
Due to the fact that I only have 1 physical box at the moment, it's my only resource.
Ultimately, yes, it would be better to have segregated servers for db, mail, web...

The base system is installed, and openssh-server is set, so I can now get in...
The drive is parted out as:
/ = 7Gb
/boot = 100Mb
/swap = 1Gb
/var = 7Gb
/home = 24.9Gb

Before I move on, do you have any suggestions as to a better layout based on the OP (which is what I want to end up with) ?

bind9 is installed now and working... i'm up to installation of mysql... I'd like to mysql5, but can't seem to find it anywhere, and I would rather not use source installs, if possible... Any suggestions ? (I know that it's available under Dapper, but I don't know how to access those repo's)

got no replies, didn't want to get too far ahead of the curve, so mysql 4 and php4 are both up and running, along with postfix, proftpd, apache2... so far, so good... now to get down to the nuts and bolts of configuring...

---

### Post by jinacio on 2006-04-16
hmm firestarter?!?

why don't use use shorewall? it's an interface to iptables, easy enough to set up and imho MUCH better than using firestarter... (wich is nice for desktops though)

just my 0.02&#8364;

BTW: use [dovecot]("http://www.dovecot.org") for a light, fast, secure pop3 and imap server. very easy to set up too!

another edit:
if you need another cheap host, imho a xen vps is a nice solution
i have an extremely cheap one thats running all of that and more, with lots of bandwidth :)

---

### Post by LordHunter317 on 2006-04-16
> **gymsmoke]The base system is installed, and openssh-server is set, so I can now get in...
The drive is parted out as:
/ = 7Gb
/boot = 100Mb
/swap = 1Gb
/var = 7Gb
/home = 24.9Gb

Before I move on, do you have any suggestions as to a better layout based on the OP (which is what I want to end up with) ?[/quote]I would, unless you have a reason to, create two partitions: /boot and /.  Place a swapfile on / as big as you like.

The only other partition I would create at this point is /home, for personal data.  As this is a server and most of the data will be in /var (except for possibly shared files via Samba or NFS), you may want to make a huge /var that is the remainder of the disk.

At anyrate, that balance may be fine.  It's your call, really.  

>  Any suggestions ? (I know that it's available under Dapper, but I don't know how to access those repo's)Add dapper to sources.list:```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe
```Then create a file in /etc/apt/apt.conf.d called '99user' with the following line:```
APT::Default-Release "breezy" said:**
> so far, so good... now to get down to the nuts and bolts of configuring...You are, in my mind, going about this the wrong way.

You do one service at a time, until it's completely configured and secure.  Then you install the next service and repeat.  This minimizes your exposure and your risk during installation.

---

### Post by LordHunter317 on 2006-04-16
Also, I wouldn't bother with a firewall at all unless you have a need.  Most services listen locally by default.  If you don't want any inboudn connections in the meanwhile, run this, as root:```
iptables -F
iptables -P INPUT DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
```Which only allows incoming connections on your loopback interface.  This isolates the servers on the box to only listen themselves.  You can then just run:```
iptables -P INPUT ACCEPT
iptables -F
```to undo it.

I am very anti-shorewall, and especially anti-firestarter as they tend to generate excessively complicated and unnecessary rules.

---

### Post by gymsmoke on 2006-04-16
LH~
thank you very much for the solid information.  I have all the packages I need installed, and, because I lack the experience necessary (and also due to the fact that there are more people out there that say they know what they're doing than actually do), I installed a control panel to get me over the hump of setting up the mail server and dns entries correctly... 

I'm really beginning to regret it... lack of documentation, sloppy coding, and a number of other things that I won't go into here aside, I haven't really learned anything more about setting up the server than I have by searching and reading articles for the last 2+ days and nights...

Since the production mail and website are all securely running on a shared host right now (I moved them before I ever started any of this), is there a way that I can take the colo server back to just the base install and openssh-server and start again without having to have the isp just re-install the base system again?

At this point, I'd feel comfortable doing that, and taking your suggestion of installing each component, securing it, and then moving on...

Your input is greatly appreciated...

---

### Post by LordHunter317 on 2006-04-17
[QUOTE=gymsmoke]LH~
thank you very much for the solid information.[/quote]Well, I wasn't totally clear in my partitioning above.  I mean either have a huge /home or a huge /var, if necessary.  Probably not even required unless you need the flexibility to reinstall.

> is there a way that I can take the colo server back to just the base install and openssh-server and start again without having to have the isp just re-install the base system again?If they'll do reinstalls, sure.

---

### Post by gymsmoke on 2006-04-17
yes, they'll do re-installs... for $150 ... I meant, is there a way to back everything off of the box except the base layout and openssh-server without their intervention?

---

### Post by LordHunter317 on 2006-04-17
Assuming you had the list of packages in the base install, you could do something like:```
dpkg --get-selections | grep -vf base.list | sudo xargs apt-get remove --purge
```Which should schedule everything for removal that wasn't in the base list.  Be careful with this, though.

May not get you 100% clean results, either.  Be careful.  Could leave your system in a bad state.

---

### Post by gymsmoke on 2006-04-17
LH~
dpkg --get-selections produces a list of (i believe) all the packages installed so far...
i looked for a base.list file, and found these
/var/lib/dpkg/info/alsa-base.list
/var/lib/dpkg/info/courier-base.list
/var/lib/dpkg/info/gcc-4.0-base.list
/var/lib/dpkg/info/gettext-base.list
/var/lib/dpkg/info/groff-base.list
/var/lib/dpkg/info/language-pack-en-base.list
/var/lib/dpkg/info/linux-sound-base.list
/var/lib/dpkg/info/lsb-base.list
/var/lib/dpkg/info/ncurses-base.list
/var/lib/dpkg/info/netbase.list
/var/lib/dpkg/info/perl-base.list

none of these appear to be what you were referring to, nor do they appear to be what I would consider a 'base install' ...
I'm going to look around a bit to see if there's another file of that type somewhere...

I did find a file in /var/lib/dpkg/info/ called base-files.list, but
dpkg --get-selections | grep -vf /var/lib/dpkg/info/base-files.list produces the same list as 
dpkg --get-selections without any arguments ...

---

### Post by LordHunter317 on 2006-04-17
base.list would be a file you generate, with the package list of a base install.  I'm not sure how the best way to generate that is.  Probably from a clean install elsewhere.  Add to that list any packages you don't removed, like openssh-server.

On a clean install, you can do it via:```
dpkg --get-selections | grep [[:space:]]install$ |cut -f1 > base.list
```

---

### Post by gymsmoke on 2006-04-17
hrmmm - what about this?
/var/cache/apt/archives/base-config_2.67ubuntu20_all.deb

This file is dated 12-March-2006
(it's a file of type: Debian binary package (format 2.0) )

 dpkg-deb --info base-config_2.67ubuntu20_all.deb
 new debian package, version 2.0.
 size 291224 bytes: control archive= 170241 bytes.
      29 bytes,     1 lines      conffiles
     798 bytes,    17 lines      control
    8257 bytes,   112 lines      md5sums
    2550 bytes,    64 lines   *  postinst             #!/bin/sh
     484 bytes,    16 lines   *  postrm               #!/bin/sh
  453717 bytes,  8564 lines      templates
 Package: base-config
 Version: 2.67ubuntu20
 Section: base
 Priority: important
 Architecture: all
 Depends: debconf (>= 1.4.56), apt (>= 0.6.40), adduser, console-data (>= 2002.12.04dbs-16), console-tools, passwd (>= 20000902-6), bsdutils (>= 1:2.11l), debianutils (>= 1.6), gettext-base
 Conflicts: tasksel (<< 2.25)
 Installed-Size: 1472
 Maintainer: Debian Install System Team <debian-boot@lists.debian.org>
 Description: Debian base system configurator
  This package handles setting up the Debian base system. It contains the
  configuration program you see when you install Debian for the first time
  and boot up your new Debian system.
  .
  It can be removed with no ill effects -- once your Debian system is
  installed, this package's only useful function is to allow you to
  reconfigure some things.

---

