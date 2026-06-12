---
title: "default sources.list 10.04"
date: 2010-08-20
forum: Server Platforms
---

### Post by amlucent23 on 2010-08-20
could somebody help a brother out.. Anyone happen to have a link to the default sources.list for 10.04.. or could you attach one for me?  Thanks!

the webhost has this one with nothing in it and I am adding them one by one.. its ridiculous.

I think this error is related

I ran the first instruction for this [https://help.ubuntu.com/10.04/serverguide/C/dovecot-server.html]("https://help.ubuntu.com/10.04/serverguide/C/dovecot-server.html")

```
Unpacking dovecot-common (from .../dovecot-common_1%3a1.2.9-1ubuntu6.1_i386.deb) ...
Selecting previously deselected package dovecot-imapd.
Unpacking dovecot-imapd (from .../dovecot-imapd_1%3a1.2.9-1ubuntu6.1_i386.deb) ...
Selecting previously deselected package dovecot-pop3d.
Unpacking dovecot-pop3d (from .../dovecot-pop3d_1%3a1.2.9-1ubuntu6.1_i386.deb) ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up libpq5 (8.4.4-0ubuntu10.04) ...

Setting up dovecot-common (1:1.2.9-1ubuntu6.1) ...

Creating config file /etc/dovecot/dovecot.conf with new version

Creating config file /etc/dovecot/dovecot-ldap.conf with new version

Creating config file /etc/dovecot/dovecot-sql.conf with new version
adduser: Warning: The home directory `/usr/lib/dovecot' does not belong to the user you are currently creating.
Creating generic self-signed certificate:  /etc/ssl/certs/dovecot.pem
(replace with hand-crafted or authorized one if needed).
hostname: Name or service not known
dpkg: error processing dovecot-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dovecot-imapd:
 dovecot-imapd depends on dovecot-common (= 1:1.2.9-1ubuntu6.1); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-imapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-common (= 1:1.2.9-1ubuntu6.1); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                ldconfig deferred processing now taking place
Errors were encountered while processing:
 dovecot-common
 dovecot-imapd
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by amlucent23 on 2010-08-20
im starting to think its this:

```
adduser: Warning: The home directory `/usr/lib/dovecot' does not belong to the user you are currently creating.
Creating generic self-signed certificate: /etc/ssl/certs/dovecot.pem
(replace with hand-crafted or authorized one if needed).
hostname: Name or service not known
```

but i am unsure what they mean.. hostname is incorrect?  Looks correct when i run "hostname" command.

---

### Post by amlucent23 on 2010-08-21
Bump, I added the Dovecot PPA and reattempted the install still same result.  

When I perform this command:

```
apt-get install dovecot-imapd dovecot-pop3d dovecot-common
```

it bombs out with the message above..  I have done a fresh install and same issue occurs.  Can anyone replicated this, maybe its a bug in the package?

---

### Post by wmills on 2010-09-13
I have this problem as well.  It does look like 10.04 is picker about this than 9.10 was.  I don't know if the hostname -f in dovecot is new or hostname has gotten picker.

If I run:
    getent hosts $(hostname)  
it works fine as I have added lines for my IP & my FQDN to /etc/hosts.

If I run 
    hostname -f 
on the command line I get the"Name or service not known" error.

HOWEVER, if I run 
    LOCALDOMAIN=mydomain.org hostname -f
it works fine.

The issue seems to be the domain and search lines in /etc/resolv.conf.  I left them pointing to what is assigned by the DHCP (which I don't control) 

If I edit /etc/resolv.conf manually with my domain it also works.  However EC2 is all DHCP so I need to learn how to get the DHCP client to not overwrite my changes.

BTW: There is some other discussions in this bug:
[https://bugs.launchpad.net/ubuntu/+source/dovecot/+bug/611226](https://bugs.launchpad.net/ubuntu/+source/dovecot/+bug/611226)
(They say its not a bug.)

Background:
I run some servers on Amazon EC2 using the std ubuntu published AMIs.  The config script I run to setup my server runs OK on 9.10 but gets this error on 10.04.

I _do_ change the hostname from what EC2 assigns me.  This may be part of the problem but the EC2 names are not something I want to publish and the `hostname` ends up in some much stuff.

---

### Post by wmills on 2010-09-13
dhcp fix was easy.  Edit /etc/dhcp3/dhclient.conf and uncomment and change the supercede domain-name line.

I  reran with 9.10.  hostname -f worked out of the box with out any change  to /etc/hosts or /etc/resolv.conf.  The only thing I had done was
    sudo hostname MYSERVER.MYDOMAIN.org
    echo MYSERVER.MYDOMAIN.org | sudo tee /etc/hostname

So  10.04 hostname is definitly picker.  Is the new setup more correct.   Yes.  But I am sure we will not be the only people to discover this.

---

### Post by spacechampion on 2010-09-18
Hello, I am having this problem as well, but I do not see the line you said to change.

In my /etc/dhcp3/dhclient.conf file all I have is:
```

request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;

```

---

