---
title: "Ubuntu server in Windows Active Directory - how realistic ?"
date: 2009-01-19
forum: Server Platforms
---

### Post by if_else on 2009-01-19
As per thread title:

I have a multi-site Windows network in place, all securely linked across L2TP/IPSEC VPN on leased lines.

We have one Exchange 2003 mail server and 9 file servers spread around here and there, with a couple of the file servers doubling as print servers.

All desktop/remote clients are Windows XP Pro, and all servers are currently Windows Server 2003 R2 Standard (32 bit and 64 bit), installed on HP ML350 boxes with various hardware specs.

I have a new file server to bring online over the next few weeks and if we can ignore the admirable enthusiasm of Ubuntu fans, how realistic is a Ubutnu file server in a Windows Active Directory domain to a relative Linux novice ?

That last part is key here.

I can roll out another Windows file server without blinking an eye, but I have been looking at the potential benefits of a Linux file server, with particular reference to handling a heavier user load on the same hardware or requiring less hardware for the same load as a Windows file server.

This is not necessarily a request for spoon-fed tutorials.

Merely bouncing around how realistic it would be for a relative Linux beginner to roll out a live file server in a corporate environment.

Common sense tells me to steer clear unless I can bring the right skills to the table:

What happens if something goes wrong ?

How do I address problems ?

What problems am I likely to encounter ?

Etc, etc..,

These and others are questions I am trying to pin down before risking a live Linux file server.

Installation will be on an HP ML350 with 4GB RAM and four 500GB SATA drives in two RAID1 arrays.

In summary:

Windows is the common sense roll out in this situation.

Are the likely problems a Ubuntu file server may have going to be purely down to the user at the helm ?

If so, the question of platform is answered beyond doubt.

Thoughts appreciated.

---

### Post by Masuran on 2009-01-19
If we are talking about a production environment and you are a novice, then yes please don't attempt it. 

I know some people here will dislike me for saying this but if you already have a windows enviroment and don't have the required skills then you will (at some point) screw up and get a bad view of Linux and Open Source software in general. 

I'm integrating Open Source software for a living and while it can save you many thousands of dollars, it all depends. It depends on the knowledge you have, what you're willing to invest and what timeframe you have in mind.

From what I can figure out one way you could go is find a capable Linux consultant and have them implement it. But you already seem to have the Windows skills inhouse so in the short term you will be off more cheaper implementing another Windows server. 

If you are looking to cut down your IT budget (or do more with the same budget), you will save lots of money by integrating Open Source Software in your infrastructure. But do it professionally, don't tinker around yourself like its a hobby. Get professional support and do it the right way.

**_Edit:_** If it was unclear from my original post, it is perfectly possible to run a Linux server as part of an AD domain.

---

### Post by thirteendog on 2009-01-19
I'm also looking to launch a Linux file sharing/printer/DNS/DHCP server in the next 6 months, but need to learn more about the linux enviroment.  Personally, I'm running Ubuntu and Vista on the same machine, the rest of my machines run XP SP3.  I also plan on introducing a new workstation of Ubuntu, that is built to look like XP ( I don't want to confuse my end users).  Everything is server based for the most part, and we're already getting away from microsoft office products and using open office.  Any suggestions for reading material, and experience stories I can learn from are greatly appreciated.  A good friend of mine is a Linux Pro, so i do have support when I happen to need it.

---

### Post by brown.hornet on 2009-01-19
if_else -

Masuran is correct if you are looking for a quick and easy deployment then I would stick with Windows 2003.  Also I might suggest that you do a search here for ML350 as there are several post concerning the installation of Ubuntu Server on a ML350.

Respectfully –

---

### Post by capscrew on 2009-01-19
I agree for the most part with **Masuran** and **brown.hornet**.  You should stick with what you know for the production side.  

That being said, if you are a decent Windows sysadmin and have the ability to have a test lab, then the best knowledge comes from doing.  

I started with MS DOS and moved to Solaris way back when.  It can be done.  

If you need, go back and take some Linux or UNIX classes for the background.  What ever you do, check everyone's advice against an authoritative source.

---

### Post by HermanAB on 2009-01-19
Using Linux in a MS ADS domain is trivial with Redhat, Fedora, Mandriva and Suse, since they all have a wizard for it - clickety-click done.

Doing it with Ubuntu can be difficult.  See this old Mandriva guide (from the days before the wizard was working properly): [http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by cteneyck on 2009-01-19
try it in a virtual enviroment and if you can get it working then go for it

---

### Post by linux_tech on 2009-01-19
another good reference: 
[http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication](http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication)

---

### Post by if_else on 2009-01-20
Thanks to everyone for your replies, and in particular thanks to Masuran for such a considered and honest confirmation of my own thoughts, without bringing a Linux bias into the mix.

I have several spare machines I can play with (I always keep spares for additional redundancy) and I have some experience of Linux as a desktop client, so over time I think I will tinker and gather a skillset to perhaps make this a practical exercise. There is no real sense of urgency here, so I can take my time and play in a zero-risk environment.

This latest live server will go out into the big wide world with Windows on it (apologies to all ;) ) but given the time to play I think I will pursue this, hopefully up to the point of being comfortable in my ability to fully support a Linux system.

I think this afternoon will see a start - I will set up an internally facing developement web server and start tinkering with backups and so on. Once I am happy with that, I will open it up to the outside world, and then go on to file servers some time during summer this year.

Thanks again to everyone and wish me luck...

---

