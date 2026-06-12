---
title: "Firewall and Anti-Virus for Ubuntu"
date: 2008-04-03
forum: Security Discussions
---

### Post by rectec794613 on 2008-04-03
This how-to will teach you about all of the firewall and anti-virus programs available for Ubuntu.
I found these programs [**here.**]("http://www.LinuxAppFinder.com")
**[Available Anti-Virus ]("http://linuxappfinder.com/security/anti-virus")**
**[Available Firewalls]("http://linuxappfinder.com/security/firewalls")**

I have a firewall (FireStarter) And an Anti-Virus (ClamTK)
DESCRIPTIONS:
**ClamTK**:  ClamTk is a GUI front-end for ClamAV using gtk2-perl.It is designed to be an easy-to-use frontend for Linux systems.
**FireStarter**: Firestarter is an Open Source visual firewall program. The software aims to combine ease of use with powerful features, therefore serving both Linux desktop users and system administrators.
__________________________________**_Pictures_**__________________________________
**ClamTK**[IMG]http://linux.softpedia.com/screenshots/ClamTk_1.png[/IMG]_____________
Screenshot  of ClamTk 3.08

**FireStarter**[IMG]http://www.fs-security.com/pics/active-connections.png[/IMG]
________________________________________________________________________________________
**ClamTK**
**[COLOR="Blue"][Homepage]("http://clamtk.sourceforge.net")[/COLOR]**
**[COLOR="Blue"][Download .Deb for Ubuntu/Debian (v3.07-1)]("http://superb-west.dl.sourceforge.net/sourceforge/clamtk/clamtk_3.07-1_all.deb")[/COLOR]**
________________________________________________________________________________________
**FireStarter**
[COLOR="Blue"][Homepage]("http://www.fs-security.com/")[/COLOR]
Install via Synaptic (Applications>System>Synaptic Package Manager.)

**ALTERNATIVE INSTALLATION:**
1.Open Terminal
2. Type:```
sudo apt-get install firestarter
```
3. Press "Enter" and wait for the installation to finish.
Then your done!:)

---

### Post by Koori23 on 2008-04-05
I would add the following to the Firestarter configuration

Open Firestarter

Open the EDIT menu

Click PREFERENCES

on the left side, find ICMP FILTERING

click the checkbox "ENABLE ICMP FILTERING"

---

### Post by hyper_ch on 2008-04-05
firestarter is not a firewall

---

### Post by euler_fan on 2008-04-05
> **hyper_ch said:**
> firestarter is not a firewall

Please pardon what may come off as a rant, but . . . 

I think just about every time I read a thread which mentions firewalling an Ubuntu host this gets mentioned. Isn't this fact in one or more of the stickies? If so can we just leave it alone unless the course of a thread demands it be pointed out again? In fact, we have some perfectly good stickies to send people to who need basic education on security in the Ubuntu world.

For all intents and purposes, unless we are talking hardcore firewall configuration and management, Firestarter may as well be the firewall since most people who use Ubuntu will never delve beyond it.

---

### Post by netlogic on 2008-04-05
I think what he meant was firestarter is just an interface to the iptables.  It is only a front end. Technically, he is right.  No need to get upset over something small.

---

### Post by rectec794613 on 2008-04-05
> **Koori23 said:**
> I would add the following to the Firestarter configuration

Open Firestarter

Open the EDIT menu

Click PREFERENCES

on the left side, find ICMP FILTERING

click the checkbox "ENABLE ICMP FILTERING"
Thats not a pic of my firestarter if thats what u thought.
I would've added  mine if they let u upload them to the thread.

---

### Post by rectec794613 on 2008-04-05
> **hyper_ch said:**
> firestarter is not a firewall
Well I think it is. When you have FrostWire running without firestarter installed it says that it does NOT detect a firewall.
When you DO have it installed it says it does.

STOP HIJACKING MY THREAD If you dont have anything good to say

---

### Post by Chayak on 2008-04-05
> **rectec794613 said:**
> Well I think it is. When you have FrostWire running without firestarter installed it says that it does NOT detect a firewall.
When you DO have it installed it says it does.

STOP HIJACKING MY THREAD If you dont have anything good to say

That's because iptables is not configured.  Firestarter is just an interface and when you run it you get a default configuration.  There is already a sticky on AV and firewalls on ubuntu so this is redundant information anyway.

ClamAV is not a very good engine.  It may pick up old stuff but I've never seen it hit on any of the new malware.

---

### Post by hyper_ch on 2008-04-05
> **rectec794613 said:**
> Well I think it is.

You think - I know

As said before, firestarter is a gui tool for basic configuration of iptables. In case firestarter was the firewall, then it wouldn't run as long as you wouldn't start it...

And because you do not make the difference between firestarter and iptables and call firestarter a firewall, there has been a large amount of confusion of noobs being confused about it and panic...

and to add as last bit, in a lan, behind a router, you don't really need firestarter and can leave iptables unconfigured as you have a hardware firewall in your router that should be configured properly.

P.S.: No need to shout and keep it friendly in here...

---

### Post by zetetic on 2008-04-05
Firestarter is not a Firewall.

If someone has told you Firestarter is a firewall, just ask your money back.

---

### Post by aysiu on 2008-04-05
I think it bears mentioning, in case paranoid new users stumble upon this thread, that anti-virus is completely unnecessary unless you are running Ubuntu as a mail server or as a file server for Windows computers.

The best security is education and strong passwords.

---

### Post by rectec794613 on 2008-04-06
I think we all know that Ubuntu is already so secure that it doesn't need a firewall or antivirus. I'm just putting out this thread for people who are paranoid because they got Identity theft or something and/or want to be able to control their Ubuntu security.

---

### Post by netlogic on 2008-04-06
I understand you are contributing to the community, but most identity theft is based  around stolen drives, not properly wiping the drives before selling, installing random software, and giving out too much information on the net. Social networks are the heaven's ground for internet crooks. People give out too much information about themselves.

---

### Post by hyper_ch on 2008-04-06
it seems not to be too uncomming in England that government official walk around with government notebooks and forget them or get them stolen with tons and tons of private citizen data on it... there have been two or three cases in the press lately (well, I think it happens also in other countries but twice in England within a short period of time with vast numbers of individuals concenred)

---

### Post by netlogic on 2008-04-06
> **hyper_ch said:**
> it seems not to be too uncomming in England that government official walk around with government notebooks and forget them or get them stolen with tons and tons of private citizen data on it... there have been two or three cases in the press lately (well, I think it happens also in other countries but twice in England within a short period of time with vast numbers of individuals concenred)

It is very sad. I have been saying this all along. Government workers shouldn't use PC, USB drives, laptops, smart phones, social networks, yahoo, google, msn, and PDAs. They should just stick to thin client machines with restricted sites. Three major targeted areas for crooks are government, free email sites, and social networks. That is why I prefer using google mail and only use the pop mail feature. It isn't hard to brute force a non-ssl account and try that on the ssl based account to see if the passwords match. Most analysts say, people can only remember six difficult passwords. Most people have more than six sites they logon to.  I know I have said this before, the security is the policy. it isn't the applications. Reason certain UNIX based system such as Solaris, Linux, xBSD are more secure are they have more control over the environmental configurations. You can push more policy guidelines to the machines. Relying on the application layer of software to change the security is always doomed for a failure. Why shoot at the bullet proof vest if it is easier  shoot his legs and shoot his head?

---

### Post by aysiu on 2008-04-06
> **netlogic said:**
> I understand you are contributing to the community, but most identity theft is based  around stolen drives, not properly wiping the drives before selling, installing random software, and giving out too much information on the net. Social networks are the heaven's ground for internet crooks. People give out too much information about themselves. My concern is that people will get a false sense of security from installing a firewall graphical configuration frontend and anti-virus for Windows while neglecting real security measures (education about how to avoid social engineering, not starting up services that are unnecessary, using strong passwords).

---

### Post by netlogic on 2008-04-06
> **aysiu said:**
> My concern is that people will get a false sense of security from installing a firewall graphical configuration frontend and anti-virus for Windows while neglecting real security measures (education about how to avoid social engineering, not starting up services that are unnecessary, using strong passwords).

I agree!

---

### Post by zetetic on 2008-04-06
I also agree!

---

### Post by shahin on 2008-04-08
Greetings-
     I am looking for a way to view what traffic is traversing ( or not ) my iptables.  I found ACID, and I found a way to report the firewall events to syslog.  Syslog comes with a warning re: the space in my "var" directory.  So here is my questions:
1-  How do I keep an eye on this please?
2-  Where is some good reference material on iptables rules, ( I guess it is called sticky ), how to use firestarter, different ways of reporting events from firewall, and even the host itself to a tool?  
3-  How can I view these events on a gui like BASE?
Please note I am reading other stuff also meanwhile.  I just like to leverage my time by asking for good reference.
Regards

---

### Post by Filter.JL on 2008-04-11
> **hyper_ch said:**
> You think - I know

As said before, firestarter is a gui tool for basic configuration of iptables. In case firestarter was the firewall, then it wouldn't run as long as you wouldn't start it...

And because you do not make the difference between firestarter and iptables and call firestarter a firewall, there has been a large amount of confusion of noobs being confused about it and panic...

and to add as last bit, in a lan, behind a router, you don't really need firestarter and can leave iptables unconfigured as you have a hardware firewall in your router that should be configured properly.



Hello all,

I think that the above might not be 100% accurate. I am behind a router with DD-WRT. All options for remote management/SSH/Telnet are off. Not to mention only HTTPS access.

This setting might look the best bet for securing my internal LAN but there seems to be a pinhole on the router that allows hackers in, by  using brute force. 

I have only recently decided to start using Ubuntu after long periods of lurking quietly around this forum and generally am totally convinced of the better safety standards inherent in the Ubuntu OS, compared to WinXP. I am hoping to break the Windows chains on me as I am practically pissed at having to format/reinstall Windows every 2 months coz of malware/bots/viruses/ hacking. The source of these pests are...well that's another story.

As a noob here, I am exhausted already climbing the steep learning curve of the Linux OS.

I don't know how to view my running processes, if any firewall is running or not, though I have installed Firestarter. I don't see any tray icons, and if I start it manually, the icon will vanish in a few minutes.

How do I add an option to view/obtain the logs from the router to my Ubuntu machine? This can be done on WinXP by installing Wallwatcher and adding IDS with myNetwatchman.

Your help would greatly appreciated.

Thanks.

JL

---

### Post by shahin on 2008-04-12
JL,
     See if your router supports reporting using syslog.  If so, just put the ip address of your Ubuntu machine in the router.  Syslog messages are in /var/logs/ directory.  If you do not see any, there is a syslog.conf file which tells you on which port and protocol your machine is expecting syslog traffic on.  Make sure what your router is using matches what your machine expects.  By default traffic is udp 514 but you can change this.  Also let me warn you there is two syslog.conf files.  If you verify this, and things don't work look for the other file.  Best way is to use "search for files" utility under places.  
I am sure there is software that will collect syslog, and snmp, and allow you manage your messages, and leverage your time.  I am still trying to find a good one.  Good luck.

---

