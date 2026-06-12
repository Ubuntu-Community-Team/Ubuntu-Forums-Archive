---
title: "Ubuntu Server Release"
date: 2005-01-14
forum: Server Platforms
---

### Post by lee_connell on 2005-01-14
I seen on here that there is talk about ubuntu server edition.  anyone have any articles etc... about the progress & ideas behind this?

Lee

---

### Post by az on 2005-01-14
From what I have heard, the custom option will be renamed to server in the next release.

Ubuntu already has a lot to offer as a server OS.

---

### Post by daniels on 2005-01-15
We are not forking separate desktop and server trees, as we see no reason to.

---

### Post by tvlad on 2005-01-15
I think perhaps including a second cd would be a good idea if possible, if you are to use it for servers, it needs several packages that i didn't find on the cd, and while sure i can apt-get my way for the packages, there is the time problem, because on a 256kbit bandwidth , 256 being the maximum transfer if you're lucky, dlding all the necessary programs requires quite an amount of time.

---

### Post by LB06 on 2005-01-15
[QUOTE=daniels]We are not forking separate desktop and server trees, as we see no reason to.[/QUOTE]
I am glad to hear this. Now all the effort can go to a single entity, which will be more efficient in the long run.

But to use Ubuntu act as a LAMP server for example, one will inevitably need some packages from universe (most notably php4-mysql), which is imho a bad thing, escpecially for servers.

---

### Post by tvlad on 2005-01-15
My point exactly, several packages needed for servers should be included on the cd.

---

### Post by daniels on 2005-01-15
Ubuntu's standard CD as a single install CD is non-negotiable; that said, I don't think the idea of a server install CD is a bad one.  But packages from universe is a separate issue, and I'll take a look at that, too.

---

### Post by LB06 on 2005-01-15
[QUOTE=daniels]Ubuntu's standard CD as a single install CD is non-negotiable; that said, I don't think the idea of a server install CD is a bad one.  But packages from universe is a separate issue, and I'll take a look at that, too.[/QUOTE]
Great! Personally I don even need a server CD, but as long as I will be able to run a combined desktop-server system I'll be fine. (In other words, imho it would be bad if one had to choose between server and desktop).

---

### Post by tvlad on 2005-01-15
So you would consider releasing a server installation cd separate from the cd curently available ? because in your first post you said you wouldn't make separate distributions for server and desktop.

---

### Post by daniels on 2005-01-15
We already have separate CDs -- one for netinst, the other for a normal desktop install.  Providing a separate server CD, which took out stuff like GNOME/OOo and added Apache, PHP, PostgreSQL, etc, would be a good idea, I think, and it doesn't mean we have to fork separate desktop/server distributions; just a different package set on the initial CD.  People who install one could still install packages from the other.

---

### Post by Alessio on 2005-01-16
[QUOTE=daniels]We already have separate CDs -- one for netinst, the other for a normal desktop install.  Providing a separate server CD, which took out stuff like GNOME/OOo and added Apache, PHP, PostgreSQL, etc, would be a good idea, I think, and it doesn't mean we have to fork separate desktop/server distributions; just a different package set on the initial CD.  People who install one could still install packages from the other.[/QUOTE]

Good Idea, what do developers think about it?

---

### Post by daniels on 2005-01-16
I am one. :) And I'll ask the others.

---

### Post by tvlad on 2005-01-16
I completely agree, it's a great idea, just a thought, maybe you could include xfce by default, since gnome would most likely not be on the cd as you said, i think it's light and small enough to belong to a server cd.

---

### Post by lee_connell on 2005-01-16
I agree on XFCE for server & a server cd which just contains server related packages would be ultimate!

---

### Post by az on 2005-01-17
What does XFCE have to do with a server?  Why do you even need X?

---

### Post by jdong on 2005-01-17
I was reading a bunch of *nix security books. There are plenty of X deceptions/exploits, such that inexperienced users shouldn't be running X on a server.

---

### Post by Carzzzer on 2005-01-17
[QUOTE=azz]What does XFCE have to do with a server?  Why do you even need X?[/QUOTE]
If you have a J2EE server (WebSphere/Tomcat) running and one of your apps e.g. generates images to represent financial graphs using AWT - then you need X!  :D

---

### Post by randy on 2005-01-17
You don't need x to run j2ee awt applications.  You just have to specify to the jvm that you're running headless at the beginning.  One a different note would it be possible to see Ubuntu ported to server only architectures such as the IBM s390/s390x?

---

### Post by meneer on 2005-01-18
That being said, see [this thread](http://www.ubuntuforums.org/showthread.php?t=11567) about a server version too. For Ubuntu to be an internet lamp server, some basic firewalling could be usefull.

---

### Post by sevenm on 2005-01-26
for firewall i suggest to use 'firehol'
(i was looking for a right one so long before i found it)

anyway, i remember reading about 'enterprise' version of ubuntu with different release schedule etc, will it be desktop/server also?

---

### Post by Tichondrius on 2005-01-26
[QUOTE=daniels]I am one. :) And I'll ask the others.[/QUOTE]

Are all the developers located in Australia ? And are you actually employed by Ubuntu and have a real office branch there ?

Thanks for all the great work.

---

### Post by daniels on 2005-01-26
I'm the only distribution team member in Australia; we all work from home.  Canonical as a company is based in the Isle of Man.

---

### Post by jdodson on 2005-01-27
[QUOTE=daniels]I'm the only distribution team member in Australia; we all work from home.  Canonical as a company is based in the Isle of Man.[/QUOTE]

someday i hope to head over there actually.  then i can get a picture with the rocketman himself.... er, hopefully he will be there at least.

then again, he might be too busy to get his picture taken with a dork like me :D

oh well, at least my wife and i talked it over, i think i might come to the next ubuntu confrence.  hopefully it will be in mexico or someplace, i love mexico :-P

---

### Post by daniels on 2005-01-27
The next Ubuntu conference will be in the week after linux.conf.au (Canberra, April 17-23 or thereabouts), in Sydney.

---

### Post by jdodson on 2005-01-27
[QUOTE=daniels]The next Ubuntu conference will be in the week after linux.conf.au (Canberra, April 17-23 or thereabouts), in Sydney.[/QUOTE]

oof.  i thought it would be a bit more out than that(like a year)..... hmmmm, guess i will have to start saving some quarters then:)

**UPDATE** WOW! 2.1K(2,143USD) for a round trip ticket(priceline.com)...... i could do a thousand, but two thousand is a bit much..... you guys do any form of price matching:)  anyways, i might catch it in the nextConfrence++ iteration.

---

### Post by daniels on 2005-01-27
We have them every four months or so.  Look harder for your tickets, though -- when I flew from Sydney->Boston last year, it was only $au1.45k or so (around $us1k, a little less), and that was Sydney->LA->Boston, so also flying across the entire US once I got there.

---

### Post by jdodson on 2005-01-27
[QUOTE=daniels]We have them every four months or so.  Look harder for your tickets, though -- when I flew from Sydney->Boston last year, it was only $au1.45k or so (around $us1k, a little less), and that was Sydney->LA->Boston, so also flying across the entire US once I got there.[/QUOTE]

ok i will, thanks.

---

### Post by saltydog on 2005-01-27
I agree on this last: having separate CDs for CD installation, and having a choise (desktop/server) during netinst. I am eager to test ubuntu-server. It could be useful to have a simple procedure to update from a debian-sarge server.
Where ubuntu will differ from a debian server?

---

### Post by machiner on 2005-01-27
LAMP (choice of apache)
plethora of perl schtuff
postgre
Firewall
NO-X
IDS
MRTG (see related post "to guage happiness of box" ) ??
regular stuff: FTP, DNS, DHCP, MAIL (pick ond and stick it out)
spamassasin
maybe Squid, webalizer (although there are better)
SSH

WHat? More -- just a simple array of server apps to satisfy us wannabes and the paranoid amoung us as well.

I'd take it.  Of course, I'd also like to see a choice at install..I don't need an email server, or proxy server.

Yeah - man - this would be cool -- I could get LAMP off my regular box -- there is one little problem, however -- what about development?
For folks (like me - 85% of the sites that I build) that use the php.mysql packages to produce sites, or wikis: this development is done through a browser...

I don't mind writing in nano or vim or whatever...but
I wouldn't want to FTP my sites to the box 10 feet from me....so, maybe X  might not be bad...but something really light, fast and small...icewm?

---

### Post by Tichondrius on 2005-01-27
[QUOTE=daniels]We have them every four months or so.  Look harder for your tickets, though -- when I flew from Sydney->Boston last year, it was only $au1.45k or so (around $us1k, a little less), and that was Sydney->LA->Boston, so also flying across the entire US once I got there.[/QUOTE]

I always wanted to go to Australia, this could be a nice oppurtuninty if I can find a reasonable ticket. Isle of Man......hmmm, isn't that a bit remote, I wonder why start a company there ?

---

### Post by jdodson on 2005-01-27
[QUOTE=Tichondrius]I always wanted to go to Australia, this could be a nice oppurtuninty if I can find a reasonable ticket. Isle of Man......hmmm, isn't that a bit remote, I wonder why start a company there ?[/QUOTE]

ok my bad, mark lives in london.  i had bad info :-({|=

---

### Post by mdr on 2005-02-07
[QUOTE=Tichondrius]Isle of Man......hmmm, isn't that a bit remote, I wonder why start a company there ?[/QUOTE]

*cough* Tax Reasons *cough* would be my bet  :lol:

---

### Post by DriverJC on 2005-02-07
I am running UBuntu 4.10 as a server and it hasn't hickup'd yet. 

Here are the programs I would like to see on a Server install Disk

1. Apache2
2. PHP-4
3. MySql
4. NFS
5. Samba
6. Sendmail
7. PureFTP-Mysql
8. Web-Based Control Panel (Webmin/Usermin or more preferable Ensim or Plesk)
9. Some type of X (I love gnome, and do use it on my server, it makes mass coping so much easier (for me at least))
10. Some DVD-Burning software (K3B would be awesome as i use k3b for backing up files on the server to DVD disk)
11. firewall

Thank you
Joel 
[www.drivercomputing.net](www.drivercomputing.net) (Ubuntu Server)

---

### Post by smok on 2005-02-08
[QUOTE=DriverJC]I am running UBuntu 4.10 as a server and it hasn't hickup'd yet. 

Here are the programs I would like to see on a Server install Disk

6. Sendmail

Thank you
Joel 
[www.drivercomputing.net](www.drivercomputing.net) (Ubuntu Server)[/QUOTE]

The choice of MTA will be argued over.  I'd sugegst Postfix as a defauult as that is what Ubuntu desktop uses.  However Exim/Sendmaiul/Qmail all are requested frequently.

I'd add the following apps to be considered -

CUPS
DNS Server
DHCP Server
Imap Server
Webmail Server

Richard

---

### Post by rufius on 2005-02-08
Should the server cd not come around by means of the main Ubuntu developer team, is anyone interested in doing it as a 3rd Party Project? I'd be interested in helping out with that seeing as I'm not a member of the actual Ubuntu developer team, therefore not having a means of swaying the popular opinion of the members.

---

### Post by lee_connell on 2005-02-08
postfix, cyrus-sasl, cyrus-imap.
bind9, dhcpd.
squid-proxy, dansguardian, squidguard.
samba, nfs
cups
mysql
apache w/ssl & appropriate mods, mod_python, mod_php, mod_perl, mod_ssl etc...
egroupware, phpgroupware, opengroupware (egroupware works great in uni now)


what else???

---

### Post by rbrugman on 2005-02-09
This is the problem with a server release...everyone has different needs for a server.  Granted, having some files on a cd would be convenient, I prefer to use apt-get to install them myself as I need them.  I was very satisfied with my 7-minute "custom" ubuntu install.

Robert

---

### Post by Rottweiler on 2005-02-16
Regarding the original topic (server CD for Ubuntu) ...
  
 I'd just like to vote that I'm pretty happy with the way things are. Entering "custom" or "server" or somesuch at the boot prompt is easy enough.
  
 It gives you a very minimalist install that is ready to run and you can build it up from there. It's a good approach and maximizes developer resources. So I don't see much of an advantage for a server-specific CD.
  
  I wish more of the server-ish packages were in main instead of universe, but that's not a showstopper.

---

### Post by lee_connell on 2005-02-16
i agree as is, is good enough, but it would be nice to see more server related software available in main and fully supported.

---

### Post by sebwills on 2005-02-18
Just to add weight to lee's post: Surely the big issue for using Ubuntu as a server is the fact that almost all key server packages (apache, dhcpd, etc etc) are in universe rather than main? If I'm going to run a server, I need to know that security updates are going to be made available for all services I run, in a timely fashion.

This seems to be a far bigger issue than questions about special CDs or installer options. Or am I missing something?

I'm a co-sysadmin for a linux server with 1000's of users, currently running Debian stable. We discussed moving to Ubuntu, but dropped the idea when we realised we'd need to use stuff from universe which doesn't have security updates.

cheers
Seb

---

### Post by Rottweiler on 2005-02-18
[QUOTE=sebwills]Just to add weight to lee's post: Surely the big issue for using Ubuntu as a server is the fact that almost all key server packages (apache, dhcpd, etc etc) are in universe rather than main? If I'm going to run a server, I need to know that security updates are going to be made available for all services I run, in a timely fashion.
 
 This seems to be a far bigger issue than questions about special CDs or installer options. Or am I missing something?[/QUOTE]Well said.

---

### Post by daniels on 2005-02-18
apache2, php4, mysql, postgresql and many others are in main already.

---

### Post by lee_connell on 2005-02-18
Any comments from ubuntu dev's on this topic as I feel it is a really critical part of running ubuntu as a server???

Lee

---

### Post by sebwills on 2005-02-19
[QUOTE=daniels]apache2, php4, mysql, postgresql and many others are in main already.[/QUOTE]
Ah, thanks for pointing out apache2. I'd only checked apache. Looks like I didn't notice bind9, dhcp3-server for similar reasons. (I just checked bind and dhcp).

php4 is *just about* in main. All the extra modules for it (php4-mysql, php4-imagick, etc), many of which are needed by "typical" php4 applications, seem to be in universe. I'd love to see these in main, along with phpmyadmin. Also vncserver.

There's probably a more efficient way of doing this, but in case it's any use to anyone reading this, here's one way to list which packages from universe you have installed:
```
for n in `dpkg-query -W --showformat='${Package} '`; do if ( apt-cache show $n | grep -q "^Filename:.*/universe/") ; then echo $n; fi; done
```

---

### Post by hoeken on 2005-02-24
theres definitely a way to keep ubuntu a 1-cd *installation*.  it's simple:

at the end of the standard install (format, base packages, etc.)  prompt the user for any additional software cd's they'd like to install from.

then you simply offer additional software addon disks.  completely optional!

if you like to do small, custom installs and then install from net you will be totally free to.  but sometimes its either faster or impractical to download it ahead of time and install then.  what if you were installing ubuntu in a location that does not have internet?  or on multiple computers at once?  there are many places less fortunate than the usa or australia that would definitely benefit from  a free os that can run on very modest hardware.

---

