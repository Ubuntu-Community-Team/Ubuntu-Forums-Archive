---
title: "repository address not working????"
date: 2007-02-23
forum: Repositories &amp; Backports
---

### Post by NeoGreen on 2007-02-23
I tried to update my laptop from Ubuntu 5.10 to 6.10.  The problem is that I get an error message stating that my repository/update address does not work.  The address is [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt).  I really don't understand what repositories do.  Please correct me if I am wrong, but to my understanding I have to have a valid web address to get updates from that address for my laptop.  Is this correct?

---

### Post by MepisReign on 2007-02-24
Not only Automatix, seems to be that some other repos are down as as well.

Greetz,

MepisReign

---

### Post by Oceola on 2007-02-24
I've been updating and setting up an "off-line" system for the past month or so and the last few visits to the repositories have been inflicted with a DOS signal from what is identified as "Prat.Canonical.com" or "forster.canonical.com"
IPs are 91.189.89.182 - 91.189.89.6- 91.189.89.8. This signal impeded at first but now impedes access to all repositories except Security. Breezy was supposed to be supported until April but I'm wondering if this is some kind of changeover.

I'd update to Feisty if I had a billing/mailing address, repositories (this as I've figured out how to piece meal a system wide update) or they'd put the newer versions on CD instead of DVD. Be nice if it would support my hardware as well. I'm not going to buy new hardware to satiate some addiction to promiscuous updating of hardware and software to drive the market or Keep up with the Jones' with no real improvement except some inane concept - the more crap in the system the more we can sell - mentality.

Breezy was and is working fine and while I didn't update to Dapper because of the initial bugs in the hardware support, amongst other things I find it highly suspect this blocking of the repositories for anything except security since the announced date of "non-support" is April.
This is still February isn't it???

:confused:

---

### Post by docomo on 2007-02-24
> **Oceola said:**
> I've been updating and setting up an "off-line" system for the past month or so and the last few visits to the repositories have been inflicted with a DOS signal from what is identified as "Prat.Canonical.com" or "forster.canonical.com"
IPs are 91.189.89.182 - 91.189.89.6- 91.189.89.8. This signal impeded at first but now impedes access to all repositories except Security. Breezy was supposed to be supported until April but I'm wondering if this is some kind of changeover.

I'd update to Feisty if I had a billing/mailing address, repositories (this as I've figured out how to piece meal a system wide update) or they'd put the newer versions on CD instead of DVD. Be nice if it would support my hardware as well. I'm not going to buy new hardware to satiate some addiction to promiscuous updating of hardware and software to drive the market or Keep up with the Jones' with no real improvement except some inane concept - the more crap in the system the more we can sell - mentality.

Breezy was and is working fine and while I didn't update to Dapper because of the initial bugs in the hardware support, amongst other things I find it highly suspect this blocking of the repositories for anything except security since the announced date of "non-support" is April.
This is still February isn't it???

:confused:

I'm on Edgy and I can only access Security as well, so I don't think the problem is about Breezy.

---

### Post by MepisReign on 2007-02-24
Are we getting a solution/expectation before this thread go over 1000 posts?

Greetz

MepisReign

---

### Post by NeoGreen on 2007-02-24
Looks Like we are probably not.  I will keep investigating and I will post what I find.

---

### Post by canopus4320 on 2007-02-24
same here, can't access edgy repos except for security, i hope this get fixed soon

---

### Post by clooch on 2007-02-25
I am not sure if this is relevant, I have firestarter running, it shows a hit from forester.canonical.com as well as prat.canonical.com. no matter what I allow, firestarter still shows a hit and I get a time out from the server. 
 I am at a loss as to why the repositories servers would trigger such action now. it was working fine 3 or 4 days ago

sorry if this is not the right to put this. I haven't found any other threads that come as close as this one for an explanation.

tia for ideas and suggestions

---

### Post by tgui on 2007-02-25
I've been getting port scanned by forster.canonical.com since I did an update on my edgy machine. Firestarters really getting pissed, and so am I. Any clue as to who the hell this is? Here is a smiley face to cheer up my first post here :)

:P

---

### Post by Oceola on 2007-02-26
It's still the same this morning US E.S.T.
Couple of things I noticed. I have both the US and Channel repositories for Breezy and there's a signal going out when you try and access both location's  the repositories other than the Security and Security Community. I'm wondering if Synaptic isn't borked or this is some kind of tracking setup that's gone "run-a-muck." Synaptic is giving funny reads on the sizes of files as well and I tried to re-install it but couldn't get to the update because of the blocking.

I tried blocking the original ports the signals came in on and it's coming from the repositories themselves either the repos changed ip address for the url or something else is redirecting the signal. I've seen this signal "spoofing" on my ISP at their mail site before and it is directly relational to something the ISP is doing. It may have something to do with Flash or RealMedia.

Be nice to know one way or the other. Spending a year or two in support and use seems kind of wasted without some kind of "Go away we don't like you", "We changed things you can't get in any more" or "You'll have to pay to access the Repos" or maybe just a Big Happy face and a "We fixed it and didn't say anything as a big surprise." I don't want to get anymore sinister in assumptions because there's some downtrodden techie just pulling his hair out about now trying to figure out how the chimps got hold of the rudder.
:roll:

---

### Post by clooch on 2007-02-26
Well I found a work around, I stopped the firewall, and low and behold everything went, well with a couple of server and gpg problems, fine. Ihated to try that way but it seemed to work.:) 

When I find more I will update. 
cheers

---

### Post by kristalsoldier on 2007-02-26
I don't have any firewalls on my Ubuntu side of my machine, and the repository downloads don't work - not via Synaptic nor via the terminal. In the latter, it sticks at 99% and then says 'connection timed out'. On Synaptic, I get the following:

[http://givre.cabspace.com/ubuntu/dists/edgy/Release.gpg:](http://givre.cabspace.com/ubuntu/dists/edgy/Release.gpg:) Could not connect to givre.cabspace.com:80 (65.175.85.100), connection timed out
[http://givre.cabspace.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2:](http://givre.cabspace.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2:) Could not connect to givre.cabspace.com:80 (65.175.85.100), connection timed out
[http://givre.cabspace.com/ubuntu/dists/edgy/main-all/i18n/Translation-en_US.bz2:](http://givre.cabspace.com/ubuntu/dists/edgy/main-all/i18n/Translation-en_US.bz2:) Could not connect to givre.cabspace.com:80 (65.175.85.100), connection timed out

---

### Post by goosey on 2007-02-26
i'm having the same problem as well

i'm on optimum online in metro ny.  Most people seem to be able to access [http://archive.ubuntu.com](http://archive.ubuntu.com)   quite easily. So I wonder if they're blocking and scanning only certain ip ranges.  It would be nice to get other people's info on their provider and general location as well.

---

### Post by hikaricore on 2007-02-26
kristal: givre.cabspace.com is a non standard repo, you'll need to comment it out in your *sources.list* file (*/etc/apt/sources.list*) if you're not able to connect to that server, then run **sudo apt-get update** from a terminal.

---

### Post by SuSUntu on 2007-02-26
I didn't want to reply here without giving adequate time for things to be sorted out, but I've been trying to access us.archives and main archives since Friday with no luck. As everyone else has noted, security repos do work for me.

I finally switched to the Great Britain repos yesterday by doing a find and replace (replace 'us.' with 'gb.') in my sources list. Everything works fine (and fast) with those repos.

I've switched back periodically to test the US archives and the main archives, but they still are failing.

---

### Post by goosey on 2007-02-26
ahh the gb repos work well

open 

sudo vim /etc/apt/sources.list

type in 

:%s/archive/gb.archive/

full replace =)   of archive to gb.archive

---

### Post by vgrisham on 2007-02-26
Here's what I get when I try to update Dapper: 
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
[http://asher256-repository.tuxfamily.org/dists/ubuntu/Release.gpg:](http://asher256-repository.tuxfamily.org/dists/ubuntu/Release.gpg:) Error reading from server - read (104 Connection reset by peer)
[http://debian.tagancha.org/debian/dists/dapper/main/binary-i386/Packages.gz:](http://debian.tagancha.org/debian/dists/dapper/main/binary-i386/Packages.gz:) Error reading from server - read (104 Connection reset by peer)
[http://debian.tagancha.org/debian/dists/dapper/restricted/binary-i386/Packages.gz:](http://debian.tagancha.org/debian/dists/dapper/restricted/binary-i386/Packages.gz:) 400 Bad Request
[http://debian.tagancha.org/debian/dists/dapper/main/source/Sources.gz:](http://debian.tagancha.org/debian/dists/dapper/main/source/Sources.gz:) Error reading from server - read (104 Connection reset by peer)
[http://debian.tagancha.org/debian/dists/dapper/restricted/source/Sources.gz:](http://debian.tagancha.org/debian/dists/dapper/restricted/source/Sources.gz:) 400 Bad Request

What gives?

---

### Post by SledgeHammer_999 on 2007-02-27
Same problem here. I can access only the security repos. 
OS: Ubuntu 6.10
Locations: Greece

---

### Post by kristalsoldier on 2007-02-27
> **hikaricore said:**
> kristal: givre.cabspace.com is a non standard repo, you'll need to comment it out in your *sources.list* file (*/etc/apt/sources.list*) if you're not able to connect to that server, then run **sudo apt-get update** from a terminal.

Thanks. Will do.

---

### Post by kristalsoldier on 2007-02-27
> **kristalsoldier said:**
> Thanks. Will do.
 Originally Posted by hikaricore  View Post
kristal: givre.cabspace.com is a non standard repo, you'll need to comment it out in your sources.list file (/etc/apt/sources.list) if you're not able to connect to that server, then run sudo apt-get update from a terminal.

BTW, when you say "comment it out in your sources.list file...", how does one 'comment it out'. Thanks.

---

### Post by SledgeHammer_999 on 2007-02-27
> **kristalsoldier said:**
> Originally Posted by hikaricore  View Post
kristal: givre.cabspace.com is a non standard repo, you'll need to comment it out in your sources.list file (/etc/apt/sources.list) if you're not able to connect to that server, then run sudo apt-get update from a terminal.

BTW, when you say "comment it out in your sources.list file...", how does one 'comment it out'. Thanks.

Put a "#" character in front of that line.

---

### Post by kristalsoldier on 2007-02-27
> **SledgeHammer_999 said:**
> Put a "#" character in front of that line.

Cool! Thanks!

I think the repository problem worked out. I looked up some posts and then following directions went to [www.psychocats.net/ubuntu/sources](www.psychocats.net/ubuntu/sources). They have a very simple 'howto' with the code. After one panic attack, I did a cut and paste job into the list.source file, saved. Then went back to Synaptic and ran the update. Stuff loaded up and things seem OK!

Thanks to all for the help!

---

### Post by SledgeHammer_999 on 2007-02-27
I think I solved the problem. I opened Synaptic and went Settings->Repositories. There I changed the "Download from:" to "Main server" and "Reload". Previously I had the "Server for Greece". It seems that this server for now is broken.

---

### Post by balloons on 2007-02-27
> **clooch said:**
> I am not sure if this is relevant, I have firestarter running, it shows a hit from forester.canonical.com as well as prat.canonical.com. no matter what I allow, firestarter still shows a hit and I get a time out from the server. 
 I am at a loss as to why the repositories servers would trigger such action now. it was working fine 3 or 4 days ago

sorry if this is not the right to put this. I haven't found any other threads that come as close as this one for an explanation.

tia for ideas and suggestions

Exact same here. I have to turn off the firewall for it to work. But why am I being port scanned by canonical.com? lots of high ports show up in the logs. Something isn't right here

---

### Post by Oceola on 2007-02-28
> **hikaricore said:**
> kristal: givre.cabspace.com is a non standard repo, you'll need to comment it out in your *sources.list* file (*/etc/apt/sources.list*) if you're not able to connect to that server, then run **sudo apt-get update** from a terminal.
Thanks for this, it's been a week or more and I wasn't finished with the off-line box yet.

SuSuntu - Thank you as well. 

=D>

---

### Post by debananda.sahoo on 2007-10-27
hello....
 i m using ubuntu7.04...
when i m going install any programme everything is failing to install showing the message...
           "The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

and the error repositories showing are 

        [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz:](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz:) 307 Authorization Redirect
[http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:) 307 Authorization Redirect
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) 307 Authorization Redirect [IP: 91.189.88.46 80]


pls tell me what to do...i m unable to install flashplayer also because  of this error....

how to remove and from where to remove...
            debananda,india

---

