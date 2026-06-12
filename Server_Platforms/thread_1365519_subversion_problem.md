---
title: "subversion problem"
date: 2009-12-27
forum: Server Platforms
---

### Post by jareksuaff on 2009-12-27
Hi I am using 9.04 64 private server from OVH. Every time I  am trying to use subversion it returns error like :

svn: OPTIONS of 'http://code.djangoproject.com/svn/django/trunk': could not connect to server ([http://code.djangoproject.com](http://code.djangoproject.com))

Is there any solution for the above, is it a known problem?

It is not network related I've tried other addresses too with no success.

subversion info here:

s$ svn --version
svn, version 1.5.4 (r33841)
   compiled Aug  7 2009, 02:02:06

Copyright (C) 2000-2008 CollabNet.
Subversion is open source software, see [http://subversion.tigris.org/](http://subversion.tigris.org/)
This product includes software developed by CollabNet ([http://www.Collab.Net/](http://www.Collab.Net/)).

The following repository access (RA) modules are available:

* ra_neon : Module for accessing a repository via WebDAV protocol using Neon.
  - handles 'http' scheme
  - handles 'https' scheme
* ra_svn : Module for accessing a repository using the svn network protocol.
  - with Cyrus SASL authentication
  - handles 'svn' scheme
* ra_local : Module for accessing a repository on local disk.
  - handles 'file' scheme

I've heard that the neon module may not be compatible with ubuntus 9.04 kernel  

Please Help :confused:

---

### Post by raffaele181188 on 2009-12-27
I hope it helps (from Debian)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=531338]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=531338")

---

### Post by jareksuaff on 2009-12-27
Thank you for the link Raffaele I've tried same things they did on Debian
http-library=serf to ~/.subversion/servers.
id did not work.

Tried aptitude for updating the libneon27 and libneon27-gnutls  
same thing it does not work. 
I am a beginner, really I don't know how to install unstables or downgrade to old version

Regards 

J.

---

### Post by noway2 on 2009-12-27
I have seen this message appear when access to the SVN server is blocked, such as when I am at work, in which case I need to proxy through a different, less restrictive connection.  Are you perchance behind a firewall of some sorts?

---

### Post by jareksuaff on 2009-12-28
Hi Noway2 

No I am not behind firewall It is a VPS with freshly installed Ubuntu server 9.04 64 + nginx.  I would normally install the latest but due to VM I am restricted to what my provider offers.

Regards

J.

---

### Post by noway2 on 2009-12-28
There has to be something wrong in your network configuration for Subversion.  Note, I just checked out the entire trunk project, all 12015 files, which also rules out an authentication issue.  I also noticed that it appears that the web-dav is properly configured as you can web-browse the subversion directory tree.  Are you able to access the web directory tree from the system in question?  If you don't have a GUI, try using a text browser such as Lynx.

---

### Post by jareksuaff on 2009-12-29
Thank You Noway 

Thanks to your suggestions I've found out that it must be a network related program.
I can ping and access via lynx many addresses but the djangoproject.com 

 $ ping djangoproject.com
PING djangoproject.com (64.207.133.18) 56(84) bytes of data.
it hangs here until I do ctrl+c 

~$ lynx djangoproject.com
Looking up  'djangoproject.com' first

Looking up djangoproject.com first
Looking up djangoproject.com
Making HTTP connection to djangoproject.com
Alert!: Unable to connect to remote host.

I can access djangoproject.com and  directory tree [http://code.djangoproject.com/svn/django/trunk/](http://code.djangoproject.com/svn/django/trunk/) from my local (windows pc)


I don't know what to edit to make it work


Cheers

J. :confused:

---

### Post by noway2 on 2009-12-29
Ping, and Lynx, is indicating that it can't get through.  I would also recommend that you perform ping with the IP address and do an nslookup to verify that you are resolving the address correctly.  Next, I would recommend doing a traceroute to see where the link is breaking down.  It is possible that the connection isn't getting past your server.

Here is an example traceroute from my system:

traceroute to djangoproject.com (64.207.133.18), 30 hops max, 60 byte packets
 1  192.168.254.254 (192.168.254.254)  0.744 ms  1.180 ms  1.695 ms
 2  1.1.1.1 (1.1.1.1)  7.459 ms  9.604 ms  10.511 ms
 3  h45.18.213.151.static.ip.windstream.net (151.213.18.45)  11.960 ms  13.860 ms  15.529 ms
 4  h92.19.213.151.static.ip.windstream.net (151.213.19.92)  17.697 ms  19.366 ms  20.985 ms
 5  h64.254.213.151.static.ip.windstream.net (151.213.254.64)  23.893 ms  26.037 ms  26.496 ms
 6  xe-10-0-0.bar2.Cleveland1.Level3.net (4.53.194.9)  28.896 ms  9.072 ms  10.170 ms
 7  ae-0-11.bar1.Cleveland1.Level3.net (4.69.136.185)  12.276 ms  13.681 ms  51.313 ms
 8  ae-6-6.ebr1.Washington1.Level3.net (4.69.136.190)  32.807 ms  32.928 ms  33.199 ms
 9  ae-2.ebr3.Atlanta2.Level3.net (4.69.132.85)  43.466 ms  44.629 ms  45.348 ms
10  * ae-7.ebr3.Dallas1.Level3.net (4.69.134.21)  69.406 ms *
11  ae-3.ebr2.LosAngeles1.Level3.net (4.69.132.77)  108.543 ms  108.653 ms  108.721 ms
12  ae-24-70.car4.LosAngeles1.Level3.net (4.69.144.70)  99.927 ms ae-34-80.car4.LosAngeles1.Level3.net (4.69.144.134)  81.981 ms ae-14-60.car4.LosAngeles1.Level3.net (4.69.144.6)  83.052 ms
@

---

### Post by jareksuaff on 2009-12-29
Thanks again 

This is the traceroute result

~$ traceroute djangoproject.com
traceroute to djangoproject.com (64.207.133.18), 30 hops max, 60 byte packets
 1  rbx-24-m1.routers.ovh.net (91.121.201.253)  0.986 ms  1.080 ms  1.232 ms
 2  rbx-1-6k.routers.ovh.net (213.251.191.1)  0.510 ms * *
 3  40g.ams-1-6k.routers.chtix.eu (213.251.130.66)  11.922 ms * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *

nslookup
Name:   djangoproject.com
Address: 64.207.133.18

ping to 64.207.133.18 is  not returning
ping to other addresses name or ip including pings to my local computer does work


good pings to 64.207.133.18   from my local machine


Regards

J.

---

### Post by noway2 on 2009-12-29
It looks like you are not getting past the chtix.eu, which from a whois record is part of OVH.COM, who I am guessing is your provider.  The fact that you can correctly do an NSLOOKUP says that the name server can resolve it and you can identify the IP address.  The fact that your pings and your traceroute fail part way, says that there is a problem, possibly with an ICMP function.  

I would recommend that you contact OVH.com, or your provider, sending them the trace route information, and see what they have to say.  You may also want to try accessing and running a traceroute on a copuple of other sites located in the US.  That will at least show if you are having a connection problem from France to the US.

---

### Post by jareksuaff on 2009-12-30
Many thanks to all of you and especially to noway2
Thanks to your instructions  I've found out that it was actually the provider.
Yesterday after seeing the traceroute I have wrote to them about this  and had a reply that it will be investigated and sorted by this morning. It is still blocked but one of their team answered to my post  on the ovh forum that they had to block it because of spam!! 
I don't believe them, they are very  cheap but their  customer service is really bad


:KS


Regards

J.

---

### Post by noway2 on 2009-12-30
I am Happy to have helped and I am glad that you got it resolved.  I also think that both of us learned some new tricks (re:traceroute) in the process.

Best of luck to you!

---

### Post by jareksuaff on 2009-12-31
Best luck to you to
 Happy 2010 !

---

### Post by Blind-Summit on 2010-03-10
I have a similar problem.

I have just setup Ubuntu Server 9.10 with LAMP and Subversion. I have created a repository on the local system, but can't access it via the network (on a windows domain).

I have shared the /var/www/ directory (visible / accessible over the networ) and can access MySQL / the webhost all fine, but I just can't repo-browse. I see

I get the idea that I may have to setup /svn/ as a vhost in apache, but this is all getting a bit over my head :S

Any ideas would be most appreciated.

---

