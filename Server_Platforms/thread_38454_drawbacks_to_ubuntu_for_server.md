---
title: "drawbacks to ubuntu for server"
date: 2005-05-31
forum: Server Platforms
---

### Post by ryness on 2005-05-31
i've been enjoying running ubuntu on laptops and workstations, and use it as my home media server, but am now considering it as a production server for my office to host web, mail, db. 

SO, what are the drawbacks or benefits of ubuntu as a production server? eg: why would or wouldn't i just stick with sarge?

---

### Post by thrift on 2005-05-31
Mainly because Ubuntu is designed with desktop usage in mind.  Ubuntu could very well make a decent server, but it's not ideal.  

For one you would be running X and Gnome on the server, which is usually somethign that you don't want to do, since they are going to eat a bunch of CPU, RAM, and disk space.

Also, Ubuntu isn't neccessarily bleeding edge, but it's also not extremely mature.  For a production server this can be a big deal.

If your other options rather than debian, are RedHat or SuSe, they have a lot of tools which can help you get a production server doing what it is you want them to do quite easily.

Once thing Ubuntu does handle quite well is autodetection of RAID devices and EVMS, if you are looking at creating a file server with software RAID or something like that, Ubuntu may be able to do a fine job.  You could after all disable X once everything was complete, but you would still be running a lot daemon's that were desktop specific, so you would end up trimming a lot of the distro away.

Ubuntu's CUPS is also not remotely administratable by default and after playing with it for quite a while I couldn't figure out quite how to do that, so Ubuntu for a print server would probably not be ideal.

These are just right off the top of my head.  

If I were to make a server that did not need enterprise support, I would think Debian or Slackware would be a much better choice.  If I were to make a server that did need enterprise support I would choose SuSe or RedHat.  If I had a bunch of Ubuntu Clients to support, I would use Ubuntu or Debian for the server.  If I had administrators that were used to windows who were going to have to use the box and we couldn't afford a distrobution like RedHat or SuSe, I would also go with Ubuntu.

Hope that helps a bit.

---

### Post by LordHunter317 on 2005-05-31
Ubuntu doesn't offer an official support cycle that's long enough yet.  

AFAIK, Canoncial nor any other corporation is currently offering contract support for the software.  I could be wrong or it could be in the works, but most enteprise organizations need/want that support.

Their kernel doesn't have all the features one needs for big iron support.

The distribution isn't offically supported for Oracle or anything like that, which may be a big deal.

It really depends on your needs and desires.  For the enterprise, I'm not sure it's acceptable, but I don't recommend anything but RHEL for the above reasoning generally.  For a home box, it's more than fine.

---

### Post by David Cartwright on 2005-06-01
[QUOTE=thrift]Mainly because Ubuntu is designed with desktop usage in mind.  Ubuntu could very well make a decent server, but it's not ideal.  

For one you would be running X and Gnome on the server, which is usually somethign that you don't want to do, since they are going to eat a bunch of CPU, RAM, and disk space.[/QUOTE]

If you choose the **server** option during the installation, then Xorg and GNOME are not installed.

[QUOTE=thrift] Also, Ubuntu isn't neccessarily bleeding edge, but it's also not extremely mature.  For a production server this can be a big deal.

If your other options rather than debian, are RedHat or SuSe, they have a lot of tools which can help you get a production server doing what it is you want them to do quite easily.

Once thing Ubuntu does handle quite well is autodetection of RAID devices and EVMS, if you are looking at creating a file server with software RAID or something like that, Ubuntu may be able to do a fine job.  You could after all disable X once everything was complete, but you would still be running a lot daemon's that were desktop specific, so you would end up trimming a lot of the distro away.

Ubuntu's CUPS is also not remotely administratable by default and after playing with it for quite a while I couldn't figure out quite how to do that, so Ubuntu for a print server would probably not be ideal.[/QUOTE]

See the Unofficial Ubuntu Guide for info on enabling the root account. Once that is done you can setup CUPS.

One of the big advantages of Ubuntu as a server OS versus Debian is the awesome support of new hardware. If you are using new hardware from a vendor such as IBM, HP or Dell, you'll find that 5.04 is a much easier installation than the standard Debian distro. Just one example, how many distros support Gigabit LAN adapters straight "out of the box."? I've found 5.04 to be impressive in all such areas.

---

### Post by nocturn on 2005-06-01
Now that we are on this topic, I am in a similar situation.

I'm considering to build two servers with Ubuntu or Debian.
Ubuntu seems to be ahead for my goals, but I have some questions and reservations.

1. The servers will be serving a Kerberos realm, but MIT kerberos is not in main (altough it does seem to get security fixes in time)

2. As much daemon software as possible should support krb5 authentication.  This includes primarily Cyrus IMAP and Postfix (through SASL).  
It is unclear if the Ubuntu packages where build with it.

3. The 18 month support cycle is fine for my purpose, but it seems that cou cannot skip upgrades.  So doing something like Warty -> Breezy is not supported ot tested.  You will need to do Warty -> Hoary -> Breezy.  (major drawback, specially for the second server).

---

### Post by mendicant on 2005-06-01
[QUOTE=LordHunter317]
AFAIK, Canoncial nor any other corporation is currently offering contract support for the software.  I could be wrong or it could be in the works, but most enteprise organizations need/want that support.
[/QUOTE]

Canonical does have some support, but it's only for the packages in main and restricted:

[http://www.ubuntulinux.org/support/supportoptions/paidsupport](http://www.ubuntulinux.org/support/supportoptions/paidsupport)

---

### Post by ryness on 2005-06-02
the server hardware i'm working with is recognized by debian and ubuntu just the same (incl intel gigabit pci nic), so i've only noticed ubuntu's better hardware support across laptops and workstations. for servers i stick to supermicro which is very well supported by woody and sarge. scaled down, ubuntu is just like debian, altho maybe a little more bleeding edge and hence a little less stable (or so goes common wisdom). also it could be my eyes but i think sarge is a tad quicker than hoary. i'll go with debian on this one particular mission-critical web/db box, because ubuntu minus all the frills is pretty much... debian... but i'll be keeping my home server ubuntu and see how it does.

---

### Post by Gtaylor on 2005-06-05
I agree with what was said about file serving earlier and think that Ubuntu is fine for smaller projects, but I really wouldn't run it on a mission-critical box. Ubuntu is a/**the** desktop distro, and it's wonderful at it. However, I don't think the server side of things should be worried about too much until the Desktop is absolutely rock solid like that of SuSe (although a lot more up-to-date). 

We've slated our local LUG's server to run Ubuntu + Apache + PHP + MySQL to test this out. Ubuntu is definitely like a more up to date Debian which is great since we need new PHP/Apache/MySQL for what we do, but if you're running an E-Commerce site and just happen to download a miffed update to SQL and just happen to lose a lot of customer data, you're up the creek even if you only lose a few records without backup :)

---

### Post by mmealman on 2005-06-06
[QUOTE=ryness]i've been enjoying running ubuntu on laptops and workstations, and use it as my home media server, but am now considering it as a production server for my office to host web, mail, db. 

SO, what are the drawbacks or benefits of ubuntu as a production server? eg: why would or wouldn't i just stick with sarge?[/QUOTE]

If it's just for your office, I don't see the big deal with running Ubuntu. The issues you can run into are:

Ubuntu is more up-to-date, meaning it changes more often than Debian. With highly critical server environments, you don't want to change them often.

Ubuntu as a server is still new, while stock Debian has been doing it for about a decade.

The benefits of Ubuntu are better bleeding edge hardware support and the software on the box won't trail behind the current version as much as it would on Debian. For most servers, neither is really a priority. But if you're used to running Ubuntu and using it on your workstations, it can be nice to keep the Linux distributions the same across your environment.

You really have to weigh the pros and cons for each individual situation.

---

### Post by syndicate on 2005-06-28
[QUOTE=nocturn]
1. The servers will be serving a Kerberos realm, but MIT kerberos is not in main (altough it does seem to get security fixes in time)

2. As much daemon software as possible should support krb5 authentication.  This includes primarily Cyrus IMAP and Postfix (through SASL).  
It is unclear if the Ubuntu packages where build with it.
[/QUOTE]

This is huge for me.  Kerberos should be compiled into all possible packages.  Virtually none of them have kerberos support (except libnss-krb5 and libpam-krb5 :D)

---

### Post by Ubuntu Warrior on 2005-07-14
Just to add my toosense ... We were also going nowhere trying to decide between Ubuntu, Debian, Fedora, Red Hat, Suse, etc. Finally decided to investigate Ubuntu a bit further as a server os (as we already had it on some of our desktops) so put some systems into production. This was about 6 months back and today we have about 10 Ubuntu Linux servers in production supporting ISC DHCP, ISC DNS, LAMP, Web, Intranet, LDAP Directory Services, Samba, Squid, etc. The servers were a doddle to install and deploy (and maintain/manage with webmin) and we have absolutely no problems with stability. The Ubuntu systems are hosted on many different hardware platforms, from HP ProLiant DL385 servers to 5-year-old white boxes.

I have read many articles and posts on this issue and must say I would probably have gone for the safer Debian option if it were not for our positive Ubuntu experience. Sometimes our thinking can get clouded in hype and theory so I just wanted to balance this with a solid, extremely successful Ubuntu server experience. Today I would have absolutely no problem recommending Ubuntu as a server platform and to date have helped many other organisations deploy Ubuntu servers.

---

### Post by relix42 on 2005-07-15
My job keeps me running Ubuntu, Debian and Red Hat servers and workstations.  I've found problems of one sort or another (nothing big or unsurmountable) running any of them as a server solution.  The big argument for Debian is the stability and security of the more "enterprise" release cycle the Debian crew favors.   The downside is getting newer software into the stable release. However, across 100 boxes or so, I really have as many issues with RH/Fedora as I do with by Debian/Ubuntu machines.  Granted, the problems are different, but no less costly timewise and no less frustrating.

Over the 10 years I've been running/admining/developing on Linux, this has stayed true over all the different distros I've used - RedHat, Debian, SlackWare, WGS, SuSE, Turbo, Mandrake/Mandriva, LFS, Corel, Progeny, SOL - just to name a few.

Although people have enormous success with their favored flavor, there isn't one that makes "a perfect server" or "perfect desktop" distribution - no more then the Windows or OS X products do.  They all have issues, they all have their up and down points and they all change.

What I've found to be more important is to use the distro with which they have the highest level of comfort and trust.  For some, that's Debian or something Debian based.  They are comfortable with the development cycles and the licensing - many people are turned off by what is considered the "Debian attitude".  With others, Red Hat is their choice - even though in-place distribution upgrades have never worked well and many releases are put out before they are seaoned enough for real use.  Some people like the purity of a SlackWare system whereas others are bothered by the lack of real package management.  Others are put off by what they see as "corporate" distributions and other will run nothing but that.

So, even though the question has been asked, I believe, to a degree, that you have to answer it for yourself.

---

### Post by crmanski on 2005-07-15
I have also implemented squid, bind, apache/mysql/php in a similar situation and have had the same positive experience. Ubuntu perfoms well and is stable for me.

[QUOTE=Ubuntu Warrior] This was about 6 months back and today we have about 10 Ubuntu Linux servers in production supporting ISC DHCP, ISC DNS, LAMP, Web, Intranet, LDAP Directory Services, Samba, Squid, etc. The servers were a doddle to install and deploy (and maintain/manage with webmin) and we have absolutely no problems with stability. The Ubuntu systems are hosted on many different hardware platforms, from HP ProLiant DL385 servers to 5-year-old white boxes..[/QUOTE]

---

### Post by Finchwizard on 2005-07-17
I've been running a Ubuntu server for a few months so far, running my website, Email, FTP etc etc.

All seems fine, runs well, stable, good support for the newer hardware, and haven't run into any show stopping problems at all.

So if it's for home server, or one to just play around on, even if it has to be pretty stable it's fine. But I wouldn't be putting it in a critical role as a server in a biggish company, I'd be using something else more stable with slower release cycles and upmost stability, such as FreeBSD or Debian.

But apart from that, it's been running fine, so far 27day uptime with no problems.

---

