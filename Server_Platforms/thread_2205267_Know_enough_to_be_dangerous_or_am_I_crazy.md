---
title: "Know enough to be dangerous or am I crazy"
date: 2014-02-12
forum: Server Platforms
---

### Post by eborghi1 on 2014-02-12
Hi people! I'm new here. I have been selling, servicing and supporting  PC systems since 1985. I've played with Ubuntu since version 5.04 I  believe it was but was never really serious about it.  At this point in  my business I have scaled down to wanting to support only businesses  with 10 or fewer seats and a server if they have one. With all the  upheaval in the economy many of my competitors have gone under so  business for me is not bad. The only problem is I'm stuck with Windows  servers in a few places and I must say I wholly dislike them!  How many  different screen and dialogs can they possibly come up with for  something as simple as setting permissions or taking ownership of a  file???!!! Not to mention a plethora of other issues.  I really liked  Netware until version 4.01 and had no problem supporting it.  Soooooooo........ I took the plunge and installed 13.04 server on an old  Dell system I had hanging around the shop. I've been beating it up  pretty good for a week or so and it seems to perform beautifully. I  installed Webmin because it's easy but I configured the server on the  command line where I must say I feel at home to this day. Webmin is just  kind of nice for quick additions especially if I'm too lazy to get up  off my backside and walk over to the server. I think I'm on to something  here since many of my clients don't need anything but a file server to  keep data centralized, easy to backup, secure and so forth. At some  point if they need a mail or web server it can be added so Ubuntu Server  seems to be the way to fly. Most have balked at a server because of the  cost of a Windows server and all the ongoing licensing issues and such.   So, my questions are: Should I be somewhere else in the community  since I really need to talk about servers but am still a beginner to  Ubuntu pretty much?  I have a server running on my shop network and at  home and all seems well. Can it be this easy to set up? Do I dare drop  12.04 LTS into a business environment as a pure file server with little  Ubuntu (Linux) experience?

---

### Post by tfrue on 2014-02-13
If you are going to use Ubuntu Server on a production level, then I would use the most recent LTS(Long Term Support) version which is 12.03.04, since it's "more stable" than the non-LTS version. April 17th is when 14.04 LTS will be released with the new kernel and other newer stuff, so I would either wait until then or set yourself in such a position that you will be able to upgrade with ease.

I would do more research on how to set up security and what your actual needs are from this server before you push it to production because if it fails, you are the only one to fix it.

---

### Post by TheFu on 2014-02-13
To give you an idea of what it takes to [harden a Linux Server]("http://ubuntuforums.org/showthread.php?t=1002167").  Most people don't do this sort of stuff and haven't seen any issues, but it all depends on the threat level for the server, network, etc ...  Nobody forces anyone else to harden their servers.

[CENTER]Just because something works, doesn't mean it is secure.[/CENTER]

OTOH, if you avoid running any internet facing services besides a VPN and ssh, then life is pretty easy. Securing **ssh** and setting up **OpenVPN** for customer access should cover pretty much everything you'd want on a self-hosted file server in a client location. If everything from outside has to go through OpenVPN, it is hard to fall under a successful remote attack. Just sayin'.

---

### Post by tgalati4 on 2014-02-13
Go for it and tell us your experiences.  If you are really good, you will put yourself out of a job.

---

### Post by SeijiSensei on 2014-02-13
Are these servers going to be running primarily in office environments and not exposed to the Internet?  Security in this case is still important, but not as difficult as with servers that are publicly visible.  I wouldn't deploy a server on the Internet without a solid understanding of firewalls and packet filtering with iptables.  

As a simple file server running Samba or NFS in an office setting, Linux is pretty much set it and forget it.  If the server will be located behind an office firewall, you can use [OpenVPN with shared keys]("http://openvpn.net/shared.html") to have your server make a VPN connection back to you when it boots up.  However if the server needs to be part of an Active Directory domain, things can get a bit more complex.  Offices that use Exchange pose another complication if you're looking to replace a mail server.  I have Linux machines in locations with Exchange that do things like virus and spam scanning of inbound email, but the messages are then forwarded to the Exchange server.

One other common application in office settings is management of web browsing via the [Squid]("http://www.squid-cache.org/") proxy.  While proxies can also improve performance by caching frequently-used objects, today they seem more commonly used to control where users' may go on the Internet.  With some bells-and-whistles like [SquidClamAV]("http://squidclamav.darold.net/"), you can scan every downloaded object for malware.  As exploits migrate from email attachments to "drive-by" web downloads, scanning your web traffic makes more and more sense.

---

### Post by volkswagner on 2014-02-13
> **eborghi1 said:**
> Hi people! I'm new here.... [snip]   I  installed Webmin because it's easy but I configured the server on the  command line where I must say I feel at home to this day. Webmin is just  kind of nice for quick additions especially if I'm too lazy to get up  off my backside and walk over to the server.   

Do yourself a favor.  Don't use Webmin. Ubuntu does not officially support Webmin.  You can get unexpected results while using Webmin.

You should "never" need to physically connect keyboard/monitor to a server.  You can use ssh on your lan, and you can even harden the connection to
use it over WAN.  Most folks will have two cables connected to there server.... LAN and Power!  

> **eborghi1 said:**
> 
So, my questions are: Should I be somewhere else in the community  since I really need to talk about servers but am still a beginner to  Ubuntu pretty much?  I have a server running on my shop network and at  home and all seems well. Can it be this easy to set up? Do I dare drop  12.04 LTS into a business environment as a pure file server with little  Ubuntu (Linux) experience?

Welcome to the Forums.  I think you are in the right place.

I suggest getting familiar with [SAMBA4]("https://wiki.samba.org/index.php/Samba").  It can be a Primary Domain Controller replacement.  It is under heavy development and is currently fairly stable.  For an office environment the following may be of interest.

[OpenSSH]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")
[SAMBA]("https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html") This is version 3 More stable but won't replace Active Directory DC
[CUPS]("https://help.ubuntu.com/10.04/serverguide/cups.html")
[Apache2]("https://help.ubuntu.com/10.04/serverguide/httpd.html")
[OpenVPN]("https://help.ubuntu.com/10.04/serverguide/openvpn.html")
[MySQL]("https://help.ubuntu.com/10.04/serverguide/mysql.html")

All the above can be administered via the command line.
All links above are from the [sticky at the top of this forum]("http://ubuntuforums.org/showthread.php?t=1046738").

Enjoy!

---

### Post by eborghi1 on 2014-02-13
> **volkswagner said:**
> Do yourself a favor.  Don't use Webmin. Ubuntu does not officially support Webmin.  You can get unexpected results while using Webmin.

You should "never" need to physically connect keyboard/monitor to a server.  You can use ssh on your lan, and you can even harden the connection to
use it over WAN.  Most folks will have two cables connected to there server.... LAN and Power!  



Welcome to the Forums.  I think you are in the right place.

I suggest getting familiar with [SAMBA4]("https://wiki.samba.org/index.php/Samba").  It can be a Primary Domain Controller replacement.  It is under heavy development and is currently fairly stable.  For an office environment the following may be of interest.

[OpenSSH]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")
[SAMBA]("https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html") This is version 3 More stable but won't replace Active Directory DC
[CUPS]("https://help.ubuntu.com/10.04/serverguide/cups.html")
[Apache2]("https://help.ubuntu.com/10.04/serverguide/httpd.html")
[OpenVPN]("https://help.ubuntu.com/10.04/serverguide/openvpn.html")
[MySQL]("https://help.ubuntu.com/10.04/serverguide/mysql.html")

All the above can be administered via the command line.
All links above are from the [sticky at the top of this forum]("http://ubuntuforums.org/showthread.php?t=1046738").

Enjoy!

I am "new" to Ubuntu/Linux, not concepts and certainly not servers in general. I supported some large Netware installations and a pile of peer to peer junk in the early days. I'm well aware as I have been told that Unix/Linux is a different animal. It sort of like Netware was different than Lantasic but, despite it all, I/we learned, we grew and we succeeded.  As for cables, you have it right on. My little test server has 2 cables connected. My file servers would be in offices, not visible to the public but I do plan on learning about security PDQ so that when someone decides they want a web server or mail or whatever I won't be scrambling. Also, I have NO PROBLEM at all hiring experts where needed. That is one of the reason I was successful years ago. I knew what I didn't know or what I was weak on and hired experts to help. They taught me what I needed to know and I paid them well for their service and teaching. As for command line, I love it. vi, not so much but I'm smart enough to know that if you're stuck in a mess it might be the only editor you have so I'll learn it well.  As with edlin in the old DOS/Win3 days when the chips were down and the local people couldn't edit config files the guys who knew edlin (me) came to the rescue. Linux is a new world for me but logic, learning and computers is not. I thank you all for your suggestions and I will heed your warnings. I look forward to more discussion and learning as much as I can.

---

### Post by volkswagner on 2014-02-13
Although vi is a very powerful editor, you may enjoy using nano. It may allow you to spend more time editing vs. Learning the editor ;)

---

### Post by 1clue on 2014-02-13
Don't put a "foreign" system in your most demanding customer's network.  Learn on the happy and easy-going ones first.

The basic principles are going to be the same.  Protocols are protocols, and issues with RDP on Windows or Linux are going to be pretty much the same.  CIFS is CIFS, the configuration tools are different but it's the same thing at the network level.

Webmin:  I personally don't buy the webmin hate.  I don't use it for myself, but when you're dealing with non-Linux people who need to manage a server it's great.  Don't expose it to the Internet.  That said, lots of distros just randomly drop it without warning.  That gets infuriating when you had everything configured that way, you do an update and suddenly webmin isn't there anymore.

Security:  Start by not exposing anything to the outside.  Then go here:  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

FWIW most of the NAS devices out there are mostly Open Source software on a Linux or FreeBSD kernel with something very similar (sometimes indistinguishable from) webmin for configuration.

Learning:  You might want to set up virtual machines to learn this stuff.  You can save the VM at each step, and if you mess up you can revert in less than 5 minutes.  You can also save VMs at handy starting points so you can quickly clone it and customize for a customer.

---

### Post by 1clue on 2014-02-13
Another thing you might be worried about:

Linux exists in server rooms all over the world.  Small businesses, homes, and all the way up to fortune 500s.  From embedded stuff to almost every one of the 500 fastest supercomputers.  [http://top500.org](http://top500.org) lets you search on operating system, look for the ones that are some sort of Linux and you get almost all of them.

The days of Linux being naughty for business is gone.  It seems that almost every small office/home office appliance has some sort of Linux or BSD on it, and LOTS of open source software.

---

### Post by eborghi1 on 2014-02-14
> **1clue said:**
> Don't put a "foreign" system in your most demanding customer's network.  Learn on the happy and easy-going ones first.

The basic principles are going to be the same.  Protocols are protocols, and issues with RDP on Windows or Linux are going to be pretty much the same.  CIFS is CIFS, the configuration tools are different but it's the same thing at the network level.

Webmin:  I personally don't buy the webmin hate.  I don't use it for myself, but when you're dealing with non-Linux people who need to manage a server it's great.  Don't expose it to the Internet.  That said, lots of distros just randomly drop it without warning.  That gets infuriating when you had everything configured that way, you do an update and suddenly webmin isn't there anymore.

Security:  Start by not exposing anything to the outside.  Then go here:  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

FWIW most of the NAS devices out there are mostly Open Source software on a Linux or FreeBSD kernel with something very similar (sometimes indistinguishable from) webmin for configuration.

Learning:  You might want to set up virtual machines to learn this stuff.  You can save the VM at each step, and if you mess up you can revert in less than 5 minutes.  You can also save VMs at handy starting points so you can quickly clone it and customize for a customer.

Which brings me to my next question. What does anyone think of Virtual Box?  I find it a little buggy on Windows and in some cases (machines) it throws a BSOD on vmm00r.sys. Not good!  I like VMware much better.

---

### Post by TheFu on 2014-02-14
> **eborghi1 said:**
> Which brings me to my next question. What does anyone think of Virtual Box?  I find it a little buggy on Windows and in some cases (machines) it throws a BSOD on vmm00r.sys. Not good!  I like VMware much better.

Which VMware? They make 6+ products. I've used most of those. ESXi is pretty awesome, if you have $8K-$50K for the licenses and a Windows box somewhere to run vSphere  Never used Fusion - don't have a Mac and I've never used their VDI stuff. After Vmware management screwed their vRAM pricing costs around a few years ago, my company dropped all VMware product use within 6 months and have been leading our clients away too. That CEO is gone, but the possibility still remains.

Oracle/Virtualbox is fine for casual desktop-on-desktop stuff, but I'd never deploy a server with it. Stability under Win7 got pretty good the last time I used it, but the last time I tried it on a Linux host, it locked up the entire physical machine, not just the client VM. I do know 1 small business happily running multiple server VMs using it with Windows as the hostOS. They'd been using it with RAID10 SSDs to get performance - and had very happy workers.  Given the choice between VirtualBox and VMware Player - I'd pick the F/LOSS solution EVERY TIME, though picking the lesser of those evil companies would be difficult. If I were in a commercial setting with a need for 20 desktop VMs for my testing group, then VMware Workstation is hard to beat.  If I were running mostly Windows servers, I'd suck it up and get ESXi, but for Linux servers ... KVM or Xen all the way, until LXC gets a little better. This assumes you don't need fancy networking, then KVM or Xen are it with openvswitch.

For the last 2 yrs, I've been running KVM servers after migrating off Xen, ESXi and VirtualBox. Extremely stable, bonehead to use, does what we need.  My primary desktop is running now inside a KVM VM on a server a few rooms away, if that is any indication of performance and stability.

Sorry for the anti-corporate parts - you asked for an opinion. ;)   Usually a different question deserves a different thread to get different eyes.

---

### Post by 1clue on 2014-02-14
I don't like the "VMware tax."  Basic functionality for small servers is pretty fine, except when you go above their limits you're suddenly paying for everything, and every VM or feature seems to be just a little bit more.

Likewise, ESXi (the free hypervisor) is pretty easy for most things but then there are some things you have to jump through a LOT of hoops for.  Can't think of an example right now, but you'll figure it out before you're done.  Once you start spending money with VMware it never stops.

I use Parallels (on a Mac laptop) and QEMU on Linux.

There are lots of virtualization engines out there.  I like QEMU because it starts when the system starts, and doesn't require anyone to log in.

As such I haven't used VirtualBox much.  I've never tried VirtualBox with a Windows host, so I don't know about stability there.

---

### Post by SeijiSensei on 2014-02-16
> **eborghi1 said:**
> What does anyone think of Virtual Box?  I find it a little buggy on Windows and in some cases (machines) it throws a BSOD on vmm00r.sys. Not good!  I like VMware much better.
Why would you choose to run VirtualBox on a Windows host?  It's very stable on Linux, hosting both Linux and Windows guests.  

I would never assume that an application's performance on Windows tells you much about well it will perform on Linux.  The operating system fundamentals are quite different.

---

### Post by eborghi1 on 2014-02-19
> **SeijiSensei said:**
> Why would you choose to run VirtualBox on a Windows host?  It's very stable on Linux, hosting both Linux and Windows guests.  

I would never assume that an application's performance on Windows tells you much about well it will perform on Linux.  The operating system fundamentals are quite different.

My experience on 2 Win 7 hosts has been: VirtualBox runs fine with the limited testing I've been able to do. The problem has something to do with video or network drivers and vmm00r.sys, and not usually when VB is running but afterward. The Win 7 machine BSOD's and the offending driver is vmm00r.sys. Of course one could say it's the other drivers and vmm00r is not at fault but unless VB is run and closed the BSOD never happens. So VB isn't cleaning up it's house very well and it seems they have no intention of doing so. The question of why one would run VB on Windows and not Linux.............  I have no idea except right now I have a kick ass windows box I use and am fully invested in windows at home. Yes I can and will dual boot it soon and try VB on Ubuntu in fact I'm probably going to do that this evening.

---

### Post by eborghi1 on 2014-02-19
Next question (and I've spent a couple days on this) I have 13.10 server running great. All shares work, all requiring validation work correctly, all permissions work correctly. I have tried to get 12.04 LTS to do the same with no luck. The win clients can see the shares but they can't be accessed. Am I missing something elementary that is done for me in 13.10 but not 12.04?  I've checked and rechecked the smb.conf files. I even dropped the 13.10 file into the 12.04 system. Any ideas? I've exhausted the web articles on the subject, well as much as I want to at this time, and nothing seems to work. I know one thing, the same question comes up a ton in google searches specifically about 12.04.

---

### Post by Iowan on 2014-02-19
What sort of messages when they attempt access? 
They have Linux and Samba accounts on 12.04?

---

### Post by eborghi1 on 2014-02-19
Users have accounts on both Linux and Samba.  Message says the share can't be accessed because the user may not have permissions.  This is after it asks for a login and it authenticates successfully.

---

### Post by coldraven on 2014-02-20
> **volkswagner said:**
> Although vi is a very powerful editor, you may enjoy using nano. It may allow you to spend more time editing vs. Learning the editor ;)

+1 for nano

I have been experimenting with Ubuntu server and for me the easiest way is by running them in VirtualBox. As mentioned above I can take snapshots and rollback to a version that I have not messed up. 
I learned to SSH into the server and to install/configure Apache and PHP.
I also learned to keep a text file with every change or edit noted down for future reference.
I was very pleased with myself when I managed to get my virtual server into the DMZ of my router and had a friend remotely login to an account that I had created for him. I did not keep it exposed to the internet for long, it was just a test of my ability. Have fun hacking away with Linux :)
You can download ready made VBox images here: [http://virtualboxes.org/images/](http://virtualboxes.org/images/)

---

### Post by 1clue on 2014-02-20
-1 for nano, +1 for vim.

If you plan to really delve into Linux and especially scripting on systems with no gui, then there's really just 2 choices:  vim or emacs.  Both are excellent.  Both compare favorably with many modern advanced gui editors.  Both have a learning curve.

Certainly use nano until you can't stand it anymore, but in the meantime you should try vim and emacs and see which one suits you best.

---

### Post by brokenhachi on 2014-02-20
> **eborghi1 said:**
> Next question (and I've spent a couple days on this) I have 13.10 server running great. All shares work, all requiring validation work correctly, all permissions work correctly. I have tried to get 12.04 LTS to do the same with no luck. The win clients can see the shares but they can't be accessed. Am I missing something elementary that is done for me in 13.10 but not 12.04?  I've checked and rechecked the smb.conf files. I even dropped the 13.10 file into the 12.04 system. Any ideas? I've exhausted the web articles on the subject, well as much as I want to at this time, and nothing seems to work. I know one thing, the same question comes up a ton in google searches specifically about 12.04.

Could this be a difference between samba3 and samba4? Have you tried authenticating as *username@workgroup*? Can you post an example of your share config?

---

### Post by eborghi1 on 2014-03-06
> **brokenhachi said:**
> Could this be a difference between samba3 and samba4? Have you tried authenticating as *username@workgroup*? Can you post an example of your share config?

Don't know about Samba 3 vs 4. I didn't try logging in as you suggest and I have since killed the 12.04 VM. It certainly would be easy enough to install and give a try. I'll let you know and thanks for your suggestion.

---

