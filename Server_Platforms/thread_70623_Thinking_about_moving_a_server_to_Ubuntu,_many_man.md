---
title: "Thinking about moving a server to Ubuntu, many many questions"
date: 2005-09-30
forum: Server Platforms
---

### Post by Fuzzplug Jones on 2005-09-30
Hello there, I'm an armchair server admin, I have a couple of sites for myself and a couple more sites I host for friends.  I appreciate Linux for its stability and set-it-and-forget-it nature.  I am not one of the people who considers "eh, just mess with it for 92 days, 24 hours a day" as a proper alternative to a well-maintained distro.  Best-case scenario is the box is like a toaster: It does what it does, and does it just about the same every time, and you shouldn't have to make toast by hand with this much toaster technology sitting around using up all your electricity :-).

So it may surprise you that I am currently trying to get out from under a Gentoo install.  When I installed it, I didn't associate it with "ricer" behavior, I was coming from Slackware (which is a real manual sort of distro) and I appreciated that it could type "./configure; make; sudo make install" by itself (the portage system).  I'm a big fan of computers doing stuff for *me*, not the other way around.

Anyway, I have a friend who runs Debian at a major hosting company and he's happy with it.  But I have a friend who swears by Ubuntu.  While reading the Gentoo forums today (to desperately get around a major cluster-**** regarding Apache) I saw a few people who mentioned this debacle was the last straw and they were moving to Ubuntu.

So here I am, and I'd appreciate your objective opinons of how Ubuntu fares as a mission-critical server distro, and especially why I would run it over stock Debian.

I will be running the following things on this box, and not much more, ever: Apache2, PHP (4 is fine), MySQL, sshd, samba, Postfix, Amavisd, ClamAV, Spamassassin, Courier-IMAPd/POP3d (or a better IMAP/POP daemon if you can recommend one), ProFTPd (also open to suggestions), and perhaps a control panel like VHCS.  The box will likely never run X, and I also don't need a million little programs I'd never use installed by default (though things like lspci, netstat, iptraf, etc. are nice).  I might also like Pine for those weird days when it's easier to get my mail over a term window.  I need security updates fast, but other than that I want the most solid, stable, steady versions of packages so there are as few 3am surprises as possible (or at least fewer than with Gentoo).

I don't have a lot of extra hardware laying around so I don't know if I'll be able to build out a testbox and play with it for weeks before putting it on the server.  But since I despise Red Hat (yes I still have flashbacks to dependency-hell in 1999), and Slackware and Gentoo are out, pretty much the only serious distro left is Debian, or distros based on Debian.  I've heard nothing but good things about Ubuntu so now I'd like some specifics.  What's it good for, what's it not-so-good for?

I appreciate greatly any and all time taken to reply.

-Mark

---

### Post by mlomker on 2005-09-30
This may be unpopular, but I don't see the point in using Ubuntu on a production server.  The primary aims of Ubuntu--making the machine user friendly and frequent updates actually go against the philosophy of a server.  Servers need to be very infrequently updated in order to be rock solid and going with an operating system vendor that is focused on security and not adding features makes more sense.

Here's the other problem, as I see it.  If you're going to run any commercial application on the box (database, ecommerce, audio) then the vendor will only want to support RHE and maybe SUSE server editions.  If you're on Ubuntu they may just blow you off on support.

I love Ubuntu on my desktop, but all of my servers requiring vendor support are RHE and the others are Debian Stable.

---

### Post by cactus on 2005-09-30
I agree. I use ubuntu on the desktop (truly great for that), but for the server, I either use debian stable, or archlinux, or Centos (rhel clone).

---

### Post by drogoh on 2005-09-30
I'm going to go against the grain and recommend something that isn't Linux:  FreeBSD

It is quite suited for the server environment (Yahoo anyone?  Hotmail before it started sucking?  Hell, these forums (according to Netcraft)).  Coming from Slackware, a BSD wouldn't be too much different and would loosely remind you of Gentoo with ports.

My main personal server currently runs Apache 2.0 with PHP 4 and MySQL for my website, Postfix with ClamAV+dspam+Dovecot for the mail, lukemftpd (the default from inetd) if I need to download something over the LAN fast, sshd (for when I need to log in remotely, of course), SMB for the Windows machines and OpenBSD's PF combined with bruteforceblocker.pl to keep the drones off my ass.

---

### Post by az on 2005-09-30
[QUOTE=Fuzzplug Jones]Hello there, I'm an armchair server admin, I have a couple of sites for myself and a couple more sites I host for friends.  I appreciate Linux for its stability and set-it-and-forget-it nature.  I am not one of the people who considers "eh, just mess with it for 92 days, 24 hours a day" as a proper alternative to a well-maintained distro.  Best-case scenario is the box is like a toaster: It does what it does, and does it just about the same every time, and you shouldn't have to make toast by hand with this much toaster technology sitting around using up all your electricity :-).
So it may surprise you that I am currently trying to get out from under a Gentoo install.  When I installed it, I didn't associate it with "ricer" behavior, I was coming from Slackware (which is a real manual sort of distro) and I appreciated that it could type "./configure; make; sudo make install" by itself (the portage system).  I'm a big fan of computers doing stuff for *me*, not the other way around.
Anyway, I have a friend who runs Debian at a major hosting company and he's happy with it.  But I have a friend who swears by Ubuntu.  While reading the Gentoo forums today (to desperately get around a major cluster-**** regarding Apache) I saw a few people who mentioned this debacle was the last straw and they were moving to Ubuntu.
So here I am, and I'd appreciate your objective opinons of how Ubuntu fares as a mission-critical server distro, and especially why I would run it over stock Debian.
I will be running the following things on this box, and not much more, ever: Apache2, PHP (4 is fine), MySQL, sshd, samba, Postfix, Amavisd, ClamAV, Spamassassin, Courier-IMAPd/POP3d (or a better IMAP/POP daemon if you can recommend one), ProFTPd (also open to suggestions), and perhaps a control panel like VHCS.  The box will likely never run X, and I also don't need a million little programs I'd never use installed by default (though things like lspci, netstat, iptraf, etc. are nice).  I might also like Pine for those weird days when it's easier to get my mail over a term window.  I need security updates fast, but other than that I want the most solid, stable, steady versions of packages so there are as few 3am surprises as possible (or at least fewer than with Gentoo).
I don't have a lot of extra hardware laying around so I don't know if I'll be able to build out a testbox and play with it for weeks before putting it on the server.  But since I despise Red Hat (yes I still have flashbacks to dependency-hell in 1999), and Slackware and Gentoo are out, pretty much the only serious distro left is Debian, or distros based on Debian.  I've heard nothing but good things about Ubuntu so now I'd like some specifics.  What's it good for, what's it not-so-good for?
I appreciate greatly any and all time taken to reply.
-Mark[/QUOTE]

I would think that debian has slightly better security support than Ubuntu for the applications you need.  Now, the next release of Ubuntu (after Breezy) will have a supported server version, but right now, that is not the case.

---

### Post by Fuzzplug Jones on 2005-09-30
[QUOTE=drogoh]I'm going to go against the grain and recommend something that isn't Linux:  FreeBSD
It is quite suited for the server environment (Yahoo anyone?  Hotmail before it started sucking?  Hell, these forums (according to Netcraft)).  Coming from Slackware, a BSD wouldn't be too much different and would loosely remind you of Gentoo with ports.
My main personal server currently runs Apache 2.0 with PHP 4 and MySQL for my website, Postfix with ClamAV+dspam+Dovecot for the mail, lukemftpd (the default from inetd) if I need to download something over the LAN fast, sshd (for when I need to log in remotely, of course), SMB for the Windows machines and OpenBSD's PF combined with bruteforceblocker.pl to keep the drones off my ass.[/QUOTE]

I appreciate this.  I looked into it a bit, and right now I just can't take the time to get used to all the differences, especially when I still have Linux servers elsewhere that I use.  I'm already frustrated enough.

To answer someone else's question here, I won't be running any "commercial" type applications where the support people would be preferential to RedHat and SuSE, just a normal free-software LAMP server wtih e-mail and FTP.

Looks like Debian is winning.  I would appreciate any additional comments.  Maybe I can set this all up in a VirtualPC window on my Windows box so I have something pre-installed and working when I'm ready to change over.

---

### Post by Finchwizard on 2005-10-02
I've been testing out Ubuntu server for quite a while now, and I've never had a problem with it yet, it's just a personal site, with some friends hosted as well.
So nothing production.

And it's always updated, never any problems with packages or problems.
The updates to Ubuntu are quicker than say Debian.

What I would like to know is, is there any difference between speeds? Because Debian using a i386 kernel and Ubuntu uses the i686 one on my machine.

Is this faster than the Debian one at all? And things like running a Counterstrike Source server, which has the i686 executables etc.

But to the OP, I've never had any problems with it, if it's just a personal type server to run a few sites for yourself and friends, I have emails, but very rarely get any, so I'm not sure if there are any problems with handling more emails.

---

### Post by nverhaar on 2005-10-02
I run an Ubuntu server install at work for our main firewall/web/mail/dns/openvpn server, and I must say it does a FANTASTIC job!! I work for a newspaper company that produces approximately 28 community newspaper publications, so this box definitely takes a bit of a pounding when it comes to web and email, and its never even flinched.

Any feature or package we have ever needed has been available via the repositories, the box is EXTREMELY stable, and everything has a tendency to just work!!

Ive got nothing but compliments for Ubuntu, its the best linux distro ive ever used for both server and desktop environments. Cant wait to give the new Breezy a crack when the final version is released.

---

### Post by nocturn on 2005-10-03
[QUOTE=mlomker]This may be unpopular, but I don't see the point in using Ubuntu on a production server.  The primary aims of Ubuntu--making the machine user friendly and frequent updates actually go against the philosophy of a server.  Servers need to be very infrequently updated in order to be rock solid and going with an operating system vendor that is focused on security and not adding features makes more sense.
[/quote]

Not really, Ubuntu's goal is to be a drop in product for data centers too (using the server install).  You can run the current version of the distro for at least 18 months after release (with updates).  6.04 will introduce a server lifecycle of 5 years.

While Debian is great for production servers, their slipping release cycle turned me off it.  

> 
Here's the other problem, as I see it.  If you're going to run any commercial application on the box (database, ecommerce, audio) then the vendor will only want to support RHE and maybe SUSE server editions.  If you're on Ubuntu they may just blow you off on support.


This is a problem for many setups, but none of the functions the OP listed require this, so a Debian-based distro would do nicely here.  Don't get me wrong SuSE is nice but IMO, they cannot beat apt...

---

### Post by nocturn on 2005-10-03
[QUOTE=drogoh]I'm going to go against the grain and recommend something that isn't Linux:  FreeBSD
It is quite suited for the server environment (Yahoo anyone?  Hotmail before it started sucking?  Hell, these forums (according to Netcraft)).  Coming from Slackware, a BSD wouldn't be too much different and would loosely remind you of Gentoo with ports.
[/quote]

I used to run FreeBSD, but it has some drawbacks.  One is the lack of binary updates (like Gentoo), which is a problem on non-clustered systems.  

The other issue is hardware support, FreeBSD does not support nearly as much hardware as Linux (5.0 came with very limited USB2 support, making my external HD useless).

---

### Post by kananga on 2005-10-03
I too am interested in setting up an Ubuntu server. Is there someplace I can find some documentation on this?

---

### Post by Glut on 2005-10-04
We run two ubuntu servers for mission critical applications, but neither of those require external support and neither of them are accessable from the internet.
We are able to use Ubuntu because we don't have to make paid support calls for these applications and ubuntu had been used as a test base on some smaller servers for some time beforehand.

Part of using these two servers is just to test ubuntu as a possible server base, which may conclude shortly. 
What I like about ubuntu is the very predicable nature of the releases. If I can say, 'yes, we will need to do one dist upgrade, and this will occur in x month in y year' then it makes everything much nicer for everyone.
Having access to more up to date packages than the stable debian distro is nice, but this only affects me because my users (and boss...) generally demand 'bleeding edge' style features.

Thus far, ubuntu has been quite stable as a server, we havn't seen a lot of difference in the uptime compared to our debian servers (which are our internet facing servers.) I think that it's still a bit untested to trust on connected servers.

The biggest problem I see in using ubuntu as a server is its 'newness'. Tried and tested is a better for a server than new and funky. We havn't had to use canoniacle for support, and don't intend to, but the usefulness of that support could also affect its adoption.

---

