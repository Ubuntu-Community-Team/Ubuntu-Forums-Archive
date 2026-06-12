---
title: "How to setup and secure a webserver for Edgy?"
date: 2007-02-20
forum: Server Platforms
---

### Post by tiger.woods on 2007-02-20
I was wondering if there was a "how to" that I've missed on setting up and securing an Edgy webserver. I've got LAMP installed but I'm missing the security pieces for sure.

Also, I was curious if there some type of GUI for managing virtual hosts, etc.

Thanks,

---

### Post by Brazen on 2007-02-20
Ubuntu generally follows the philosophy of "secured by default" so as long as you haven't installed any extaneous programs, you should be fine.  Probably the BEST security measure you could take at this point, is to use Dapper Server instead of Edgy.

As for how to manage virtual hosts, what are you trying to do?  Are you wanting to allow other people to host websites on your server?  If that is the case, I suggest VHCS or zPanel (frankly, I like zPanel better, but they have had some questionable moral behaivor).

If this is a webserver just for yourself, I have found the Apache2 documentation to be invaluable.  I just edit the config files by hand.  If you insist on using some sort of GUI management, I would personally only consider Webmin.

---

### Post by tiger.woods on 2007-02-20
Since I'm new to the Linux world and pretty green I just want to make sure that what I put out on the web is safe from getting hacked. I realize that nothing is totally secure but at least I want to make it hard for it to happen. I've seen a lot of user suggestions in reading posts to change certain things in order to make the server more secure and I guess that's what I was looking for.

When setting up a Windows 2003 server by default it's practically open so I was checking to see what needed to be changed in Ubuntu.

A gui for me for managing sites and what not would be invaluable until I learn the command line better.

> Are you wanting to allow other people to host websites on your server?

Yes, but on a very limited scale. Are VHCS or zPanel similar to IPConfig and Cacti or am I off the mark?

Webmin, is that simply a gui only for Apache?

Thanks.

TW,

---

### Post by Brazen on 2007-02-21
Webmin is basically a "server management" web interface.  I use it change the ip address, configure the firewall, create and change partititions, etc.  It also has modules for managing all sorts of daemons, and the Apache modules, among others, is standard on all Webmin installations.  Installing webmin is as simple as copying the deb from their website to your server and then running "sudo dpkg -i webmin-XXX.deb" and possibly also "sudo apt-get install -f" if it complains about dependencies.

VHCS and zPanel are very similar to IPConfig, but much nicer and polished, IMO.

---

### Post by tiger.woods on 2007-02-22
Brazen,

Thanks for the insight and suggestions. I've downloaded and installed webmin and have downloaded zPanel and waiting for an opportunity to install it.

TW :)

---

### Post by balbir97 on 2007-02-27
Thank a lot..
me too looking for some GUI for server configuration.

problem got solved!!:)

---

### Post by gaten on 2007-03-01
I'd have to agree with the above posts about you "being fine", especially if you are planning on allowing other people to host pages on your site. You should think about jailing apache, and securing PHP and MySQL. My suggestions:
[LIST=1]
[*]Install mod_security ([http://www.modsecurity.org/](http://www.modsecurity.org/))
[*]Install mod_chroot ([http://core.segfault.pl/~hobbit/mod_chroot/](http://core.segfault.pl/~hobbit/mod_chroot/))
[*]*Secure PHP: [http://www.securityfocus.com/infocus/1706](http://www.securityfocus.com/infocus/1706)
[*]Secure MySQL: [http://www.securityfocus.com/infocus/1726](http://www.securityfocus.com/infocus/1726)
[*]Secure Apache: [http://www.securityfocus.com/infocus/1694](http://www.securityfocus.com/infocus/1694)[/LIST]Security Focus is a good resource for security. Hope this helps. 

* Step 3 is VERY important. A HUGE amount a websites are exploited by insecure PHP installations (and the lack of security in the language itself). Hope this helps.

---

### Post by wolfear on 2007-03-21
Was just doing a bit of browsing when I ran across this thread.
I don't wanna rain on anyones parade..but the information from the securityfocus.com (steps 3,4,and 5 from above) is 4 years out of date. (from 2003)

---

### Post by tiger.woods on 2007-03-22
wolfear,

Do you have any other more recent links similar to those posted?

Security is a big concern... 

Thx,

---

### Post by pppetter on 2007-03-22
Hi there!

I would recommend using https for webmin, I beleive it's only available if you already had installed ssh on the server when you installed webmin.

and hey, do NOT install X, gnome, kde, or something else - keep as little as possible on your server, for security reasons among others.
When I started out with my Dapper server I was still kind of a noob when it comes to the commandline, but hey, now I'm in love with vi !!! :)

---

### Post by gaten on 2007-03-23
> Was just doing a bit of browsing when I ran across this thread.
I don't wanna rain on anyones parade..but the information from the securityfocus.com (steps 3,4,and 5 from above) is 4 years out of date. (from 2003)

Very true, but they are still relevant and good. Mostly those articles deal with chrooting the services, which hasn't changed in 4 years. Also, many of the suggestions made still hold true (ie passwording the mysql database) despite the time gap.

The PHP doc is still very relevant, as PHP is a horrible language security wise. In some places you will notice that the PHP team has since set a variable default to a more secure value (like the ones mentioned in the guide), but other than that I didn't find any really outdated information that was necessary to secure the system. 

The Apache guide is dated, yes, but once again the chrooting (the most valuable part of the guide, IMHO) is still valid. 

I understand what you are saying, but the guides still hold their own, and they are part of a very well written series that covers all the bases for a good and secure LAMP install.
If there is something, please point it out to me and I'll try to find an updated guide.

---

### Post by wolfear on 2007-03-23
> **tiger.woods said:**
> wolfear,

Do you have any other more recent links similar to those posted?

Security is a big concern... 

Thx,

Out of curiosity I sat down and did a google search to see what was out there. 
In no particular order or date (and some are indeed a few years old, but are still active topics):

20 ways to Secure your Apache Configuration-[http://www.petefreitag.com/item/505.cfm]("http://www.petefreitag.com/item/505.cfm")

Server Installation and Configuration (Note: I linked to page 6 of this article as I assume most of us will be using the repositories or a server installation)- [http://www.devshed.com/c/a/Apache/Secure-Installation-and-Configuration/5/]("http://www.devshed.com/c/a/Apache/Secure-Installation-and-Configuration/5/")

Security Tips- [http://httpd.apache.org/docs/2.0/misc/security_tips.html]("http://httpd.apache.org/docs/2.0/misc/security_tips.html")

Secure Web Access with Client Certificate (I assume this is(was) an assignment for a college course. It's not for the faint of heart)-[http://cs.uccs.edu/~cs591/secureWebAccess/secureWebAccessNew2.html]("http://cs.uccs.edu/~cs591/secureWebAccess/secureWebAccessNew2.html")

A list of various articles ( did not read all of them)- [http://wiki.linuxquestions.org/wiki/Security]("http://wiki.linuxquestions.org/wiki/Security")

Hardening a Linux Server in 10 minutes (not a great article, but it does have a decent section about iptables)- [http://www.hostlibrary.com/Hardening-a-Linux-server-in-10-minutes-dedicated-server-security]("http://www.hostlibrary.com/Hardening-a-Linux-server-in-10-minutes-dedicated-server-security")

Questions about DMZs and Firewalls (older forum post but it has some good terminology explanations)- [http://www.htmlforums.com/archive/index.php/t-58401.html]("http://www.htmlforums.com/archive/index.php/t-58401.html")

Hardened-PHP Project ( I don't know if this is worth a hill of beans or not, but it looked interesting and was favorably mentioned on several different sites)- [http://www.hardened-php.net/home.8.html]("http://www.hardened-php.net/home.8.html")

A list of general resources from PHP Security Consortium- [http://phpsec.org/library/]("http://phpsec.org/library/")

I am tired, so this 'll be the last one for tonite- [http://us3.php.net/manual/en/security.php]("http://us3.php.net/manual/en/security.php")

Ok..I didn't google the last one..I already had the manual bookmarked.
I'll leave it for others to cover databases, I am tired and headed for bed.

---

### Post by wolfear on 2007-03-23
> **gaten said:**
> Very true, but they are still relevant and good. Mostly those articles deal with chrooting the services, which hasn't changed in 4 years. Also, many of the suggestions made still hold true (ie passwording the mysql database) despite the time gap.

The PHP doc is still very relevant, as PHP is a horrible language security wise. In some places you will notice that the PHP team has since set a variable default to a more secure value (like the ones mentioned in the guide), but other than that I didn't find any really outdated information that was necessary to secure the system. 

The Apache guide is dated, yes, but once again the chrooting (the most valuable part of the guide, IMHO) is still valid. 

I understand what you are saying, but the guides still hold their own, and they are part of a very well written series that covers all the bases for a good and secure LAMP install.
If there is something, please point it out to me and I'll try to find an updated guide.

I quite agree that the overall concerns which are addressed by the series are still very relevant and during my search (which was meant as an addition to, not a replacement of your list. I forgot to specify that earlier), I found several very good articles from securityfocus on some other issues which I found quit informative.
I wasn't trying to imply that they weren't good sources of information. 
I should have instead said the implementation was dated as the information is geared towards apache 1.3/PHP4 configurations.
Someone new might not realize this if they installed via the repositories LAMP setup or a server CD where apache2 and php5 are becoming the standard, or that some features are available as modules which don't require a compile.
No offense was intended.

---

### Post by Brazen on 2007-03-23
> **pppetter said:**
> Hi there!

I would recommend using https for webmin, I beleive it's only available if you already had installed ssh on the server when you installed webmin.

and hey, do NOT install X, gnome, kde, or something else - keep as little as possible on your server, for security reasons among others.
When I started out with my Dapper server I was still kind of a noob when it comes to the commandline, but hey, now I'm in love with vi !!! :)

This is probably the best security advice in this thread.  However, to use https for Webmin, you have to have Openssl installed and the perl-Net-ssleay library installed.  If these are installed before Webmin, then Webmin will use https by default, but if not, then you can install them after and enable https in the Webmin configuration.

---

