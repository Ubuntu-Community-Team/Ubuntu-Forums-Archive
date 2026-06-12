---
title: "&quot;Network Settings&quot; and DNS name server config"
date: 2006-10-21
forum: Server Platforms
---

### Post by emersony on 2006-10-21
Trying to configure a dns server on my local network, I found the solution-- but not the answer. 



  After Configuring bind9, dig works and "host -a" works, but nslookup keeps returning the dreaded ""no servers could be reached" message. 



  Port 53 looks like its open and listening, and iptables shows all chains have policy accept. 



  Finally decided to cheat and logged into X (Gnome) and then into networking (network settings) under the administration pull down. Added the IP for the local name server (in the DNS tab) and voila, nslookup will now reutn the correct IP for the local domain, foo.com.  



  The question is, what did the networking dialogue box do? and how can I view/edit those changes from a terminal?


   Its nice when a gui does the job, but its much nicer to know what its doing. 



Emerson

---

### Post by kidders on 2006-10-21
Hi there,

You may be referring to a tweak to your /etc/resolv.conf. That's where you tell your system what DNS server you're using.

---

### Post by emersony on 2006-10-21
Thanks for the reply. 

I did edit resolv.conf to specify the nameserver's IP. In fact without that being set there, I don't think dig or host would have worked. I'll unset it later and try just to test that. 

So network settings must have tweaked something else, but who knows what?

---

### Post by handy on 2006-10-22
[See if Post 3 on this thread shed's any light?]("http://www.ubuntuforums.org/showthread.php?t=279339")

---

### Post by emersony on 2006-10-23
Thanks for the reply and related thread.  Still can't figure out why nslookup was failing but dig was working, but I did notice that dhcp (local net only) keeps clobbering resolv.conf, so if anyone knows how to stop it from doing that, or have it append resolv.conf instead of clobbering it, that would be good to know. 

The real problem however is that the MTA can't find my host's Canonical name, which is strange bc everything seems to be there in the zone file. Having said that, I am unclear exactly which line in the zone file specifies the canonical name of the local host. SO if anyone knows that, that would be a BIG help. 

Emerson.

---

### Post by handy on 2006-10-23
So the following didn't help you with your** resolv.conf** being clobered?

I take it that you are using the current Dapper not the previous Breezy version of Ubuntu?

So if your propblem is that your ISP's DNS addresses keep being lost after a reboot (sometimes it takes more than one reboot, sometimes it happens without a reboot!!)

The following solution, hidden between the dashes, is courtesy of Stream303 I've just made it easier for new users.
----------------
This way is to prepend the resolv.conf file with your known good isp nameservers.

To Edit /etc/dhcp3/dhclient.conf

Enter the following line in the Terminal: (If you are unfamiliar with using the Terminal have a look down this page @ Post 6. for a few simple tips.)

sudo gedit /etc/dhcp3/dhclient.conf

and just before the request line in your dhclient.conf file that you are looking at in gedit, add the following line:

prepend domain-name-servers 123.45.678.90, 123.45.678.91;

(Swapping your isp's DNS addresses for the ones in the above line of course).

For multiple addresses, separate with a comma and don't forget the semicolon at the end.

This will have the effect of prepending your isp nameservers and of having your routers dns address automaticaly come up at the bottom of the list in resolv.conf:

Reboot or just bring your interface down and up again by entering the following in the Terminal:

sudo ifdown eth0

sudo ifup eth0

---

### Post by emersony on 2006-10-26
Thanks Handy, I found your reply very helpful and it looks like my local dns is no cohabitating nicely with my ISP dns. 

Also you have a very cool avatar. 

See you later.

---

