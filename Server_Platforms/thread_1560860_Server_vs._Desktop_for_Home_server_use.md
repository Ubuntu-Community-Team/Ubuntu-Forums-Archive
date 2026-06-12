---
title: "Server vs. Desktop for Home server use?"
date: 2010-08-25
forum: Server Platforms
---

### Post by jfaberna on 2010-08-25
I prefer to use GUI admin tools instead of command line for most management function. I know that you can install the LAMP server stack on Ubuntu Desktop. I also know that Ubuntu Server doesn't enable X11 so everything is command line.

So I'm wondering what are the advantages of running Ubuntu Server versus Ubuntu Desktop with the server packages installed?

Sorry for the dumb question, but I figure I'm missing some key point that everyone else already knows about Server and ease of management.

Jim A

---

### Post by kaldor on 2010-08-25
I'd say server. It's lighter than the Desktop and you can install a GUI that is much less heavier than GNOME anyway.

It's also more secure for servers I believe. Less stuff altered for home use.

---

### Post by sikander3786 on 2010-08-25
If you know how to work on the command line, you should go with the Server Edition. As mentioned it is lighter and will allow you to use your system resources more efficiently. If you need a gui tool, [Webmin]("http://www.webmin.com/") is the way to go. It has almost all the necessary modules and many more are available for custom integration.

Desktop Edition is either not a bad choice but ultimately the choice is Server Edition if you decide between GUI and CLI.

---

### Post by arrrghhh on 2010-08-25
This [ServerGUI](https://help.ubuntu.com/community/ServerGUI) article kinda goes over the disadvantages of installing a GUI on a server.

Honestly if you feel the rig is going to be used for any desktop purposes, I would install the desktop version - like looking at pictures, creating documents, listening to music... etc.

If however you're going to setup the server and it's just going to chug along and provide these services - like LAMP, media/file serving, etc - then I would go for the server edition because it is optimized to do these tasks.  I don't think it's inherently more secure, other than the lack of a GUI - it just runs better because there's less stuff like document creation software, picture viewing software - you get my point.

+1 to Webmin as well.  It won't solve all your problems, but it does help with pesky things like Samba configs :D

---

### Post by dtoronto on 2010-08-25
You are correct, you can install anything that you would want on your server on a desktop version of ubuntu.  It all breaks down to if you want to use the command line or not and if you need the extra resources somewhere else.  If you don't need the resources and don't really want to get to know the command line then I would recommend going with the desktop and then installing the LAMP stack.  Personally I prefer the server version of Ubuntu as I don't have physical access to many of my servers and therefore don't have use for the desktop GUI, but it's up to you.

---

### Post by jfaberna on 2010-08-25
Thanks, all for the great advice and opinions. I'm going to mark this one solved :p

---

### Post by Charlietje on 2010-08-25
+1 to Webmin

---

### Post by jfaberna on 2010-08-25
I just install Webmin and it works great. Seems to be some issue with libmd5-perl not being easily installable with apt-get, but plenty of searchable answers for that problem.

Thanks all, again.

Jim A

---

### Post by CharlesA on 2010-08-25
> **jfaberna said:**
> I just install Webmin and it works great. Seems to be some issue with libmd5-perl not being easily installable with apt-get, but plenty of searchable answers for that problem.

Thanks all, again.

Jim A

Just FYI:

libmd5-perl is used on webmin 1.500, not 1.510-2.

1.510-2 has all the correct dependencies for Ubuntu 10.04. :)

@OP: It all depends on what you want to do, I run the server edition since I run VMs and have already done most of the configuration as it is. :)

---

### Post by quietas on 2010-08-25
Also take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1075599"), it's loaded with good tips on what to use on your home server. Most are using Server with web based tools. Command line with Ebox was a good option and more recommended than Webmin, at least by the Ubuntu folks.

---

### Post by jfaberna on 2010-08-26
[QUOTE=CharlesA;9765883]Just FYI:

libmd5-perl is used on webmin 1.500, not 1.510-2.

1.510-2 has all the correct dependencies for Ubuntu 10.04. :)

QUOTE]

If 1.510-2 has all the correct dependencies, it's well hidden. I downloaded the "current" version of Webmin and it failed to install with the libmd5-perl dependency. It will be good if it gets fixed for simplicity. Either way, I'm good to go. :-)

---

### Post by CharlesA on 2010-08-26
> **jfaberna said:**
> 
If 1.510-2 has all the correct dependencies, it's well hidden. I downloaded the "current" version of Webmin and it failed to install with the libmd5-perl dependency. It will be good if it gets fixed for simplicity. Either way, I'm good to go. :-)

The dependencies are listed [here]("http://www.webmin.com/deb.html").

They are: perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl

I've always installed those dependencies first then install the webmin deb using dpkg.

It also works if you try to install webmin first, then fix the broken dependencies by using **sudo apt-get install -f**

This is what dpkg returns for me:

```
charles@atlantis:~$ dpkg -I webmin_1.510-2_all.deb
 new debian package, version 2.0.
 size 14504260 bytes: control archive= 54844 bytes.
  188821 bytes,  3364 lines      changelog
      18 bytes,     1 lines      conffiles
    1662 bytes,    17 lines      control
    1810 bytes,    38 lines      copyright
    2184 bytes,    85 lines   *  postinst             #!/bin/sh
     284 bytes,     9 lines   *  postrm               #!/bin/sh
     868 bytes,    33 lines   *  preinst              #!/bin/sh
     571 bytes,    15 lines   *  prerm                #!/bin/sh
 Package: webmin
 Version: 1.510-2
 Section: admin
 Priority: optional
 Architecture: all
 Essential: no
 Depends: **[COLOR="Red"]bash, perl, libnet-ssleay-perl, openssl, libauthen-pam-perl, libpam-runtime, libio-pty-perl, apt-show-versions[/COLOR]**
 Pre-Depends: bash, perl
 Installed-Size: 88076
 Maintainer: Jamie Cameron <jcameron@webmin.com>
 Provides: webmin
 Replaces: webmin-adsl, webmin-apache, webmin-bandwidth, webmin-bind, webmin-burner, webmin-cfengine, webmin-cluster, webmin-core, webmin-cpan, webmin-dhcpd, webmin-exim, webmin-exports, webmin-fetchmail, webmin-firewall, webmin-freeswan, webmin-frox, webmin-fsdump, webmin-grub, webmin-heartbeat, webmin-htaccess, webmin-inetd, webmin-jabber, webmin-ldap-netgroups, webmin-ldap-user-simple, webmin-ldap-useradmin, webmin-lilo, webmin-logrotate, webmin-lpadmin, webmin-lvm, webmin-mailboxes, webmin-mon, webmin-mysql, webmin-nis, webmin-openslp, webmin-postfix, webmin-postgresql, webmin-ppp, webmin-pptp-client, webmin-pptp-server, webmin-procmail, webmin-proftpd, webmin-pserver, webmin-quota, webmin-samba, webmin-sarg, webmin-sendmail, webmin-shorewall, webmin-slbackup, webmin-smart-status, webmin-snort, webmin-software, webmin-spamassassin, webmin-squid, webmin-sshd, webmin-status, webmin-stunnel, webmin-updown, webmin-usermin, webmin-vgetty, webmin-webalizer, webmin-wuftpd, webmin-wvdial, webmin-xinetd
 Description: A web-based administration interface for Unix systems.
             Using Webmin you can configure DNS, Samba, NFS, local/remote
             filesystems and more using your web browser.  After installation,
             enter the URL https://localhost:10000/ into your browser and
             login as root with your root password.
charles@atlantis:~$

```

---

### Post by jfaberna on 2010-08-26
Thanks, Jim

---

