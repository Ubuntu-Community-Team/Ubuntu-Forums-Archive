---
title: "Question about Security Issues"
date: 2009-08-21
forum: Security
---

### Post by chandru155 on 2009-08-21
I thought there is no virus,spywares,malwares etc in Linux. Thats why i switched from Windows to Linux. In this Sticky threads, I saw INTRUSION DETECTION. Is it possible that anyone can hack my system(Ubuntu 9.04). I am going to use torrent. And also going to pay some bills online. Will i be safe? will my transactions safe? Help me please......

---

### Post by jrusso2 on 2009-08-21
Its quite possible to get hacked especially if your running a server or server services like ssh and have a weak password, or you don't keep your system updated and secured.

Usually this happens to the people coming from Windows who don't have the knowledge to prevent it.

---

### Post by chandru155 on 2009-08-21
Thanks for the reply. I am going to watch some movies, hear some songs and download some movies and softwares via direct download and via torrent. I am not going to use any server. So does anyone can hack my system. One more thing, i am going to do some online transaction. I am afraid so much. help me to protect my system. Surely, i ll update my system via update manager daily.

---

### Post by jrusso2 on 2009-08-21
If you just running the default install you should not have any problems.  Be careful what you download and run on your pc.  Make sure the software is from the repository or other trusted sources and keep it updated.

You can also run a gui firewall manager if you want to make the firewall more secure, but if you not running any server services it should be fine as the default offers no services to connect to.

---

### Post by bodhi.zazen on 2009-08-22
In general Ubuntu is more secure out of the box then Windows after it has been "hardened".

That is not the same thing as saying it is invulnerable and I have seen several Linux systems "cracked".

Most common by far is a VNC server (sharing your desktop) or a ssh server with a weak password.

The next most common is a "simple" browse attack, usually involving java, fava script, or flash.

See :  [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

Torrents are risky only because you are downloading files from unreliable sources and thus potentially open to "social engineering".

If you wish to harden your system further learn to use apparmor.

I have posted on line aa profile repositories, the most up to date are [here](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/)

---

### Post by lisati on 2009-08-22
> **chandru155 said:**
> I thought there is no virus,spywares,malwares etc in Linux. Thats why i switched from Windows to Linux. In this Sticky threads, I saw INTRUSION DETECTION. Is it possible that anyone can hack my system(Ubuntu 9.04). I am going to use torrent. And also going to pay some bills online. Will i be safe? will my transactions safe? Help me please......

It's a rich topic - receiving something nasty while you read your email or surf the web isn't necessarily the same as someone remotely breaking into your computer but can be just as inconvenient. It can sometimes take a little while to digest all the information available. A little bit of good sense about what you look at on your computer and taking the time to learn a few basic settings will go a long way, regardless of which OS you are using.

Good luck!

---

### Post by TuckLive on 2009-08-23
bodhi.zazen sent you the FireFox security thread, which talks about NoScript.  I strongly advise you to install the NoScript addon.

---

### Post by dk06 on 2009-08-23
> **chandru155 said:**
> I thought there is no virus,spywares,malwares etc in Linux. Thats why i switched from Windows to Linux. In this Sticky threads, I saw INTRUSION DETECTION. Is it possible that anyone can hack my system(Ubuntu 9.04). I am going to use torrent. And also going to pay some bills online. Will i be safe? will my transactions safe? Help me please......

Nothing on the Internet is 100% secure. 

Viruses, Rootkits & Malware DO exist on Linux too, the community just keeps up with threats better than some other OSes like Windows.

Your security will depend on your surfing habits, password strengths and general good security practices that apply to every OS.

If you're concerned about security, Run only necessary services and keep software down to a minimum (the more software you have installed, the more ways your computer can be exploited) AND Keep your installation up-to-date.

I'm not a security expert but I did stay at a Holliday Inn Express last night..... 

BTW: How do I install this .exe file, it seems like none of my Windows programs work in this Ubuntu ;) j/k

NoScript works great troo

---

### Post by MelDJ on 2009-08-23
this may make interesting reading: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)   :popcorn:

---

### Post by rookcifer on 2009-08-23
> **dk06 said:**
> Viruses, Rootkits & Malware DO exist on Linux too, the community just keeps up with threats better than some other OSes like Windows.

There are many hundreds of viruses and other nasties written for Unix/Linux, but I challenge anyone to show me even one of these viruses making rounds in the wild.  There are none.  This is not because the Linux community is more "on top" of security updates, it's because the multi-user nature of Linux makes it more difficult to spread malware.

> Your security will depend on your surfing habits

This is advice for Windows users, not Linux.  I routinely surf to any site I want and I have never had a Linux box "infected" or compromised because of it.  In fact, I even surfed over to a few well known attack sites and watched as *nothing* happened.  Of course, I have Firefox locked down with AppArmor, but I am not so sure even that is necessary.  As long as you keep FF itself up to date, you should be fine (though NoScript is a great tool as well.  I personally don't run it since I use AppArmor).

Now, of course, I am assuming a modicum of common sense on the part of the user -- that is, the ability to avoid phishing attacks and other such scams (no OS can protect from this).  But this notion that one must avoid surfing to certain sites because of the threat of malware is unfounded (this is even true with a correctly configured Windows box -- that is a Windows box running LUA, SRP, and Integrity controls).

> If you're concerned about security, Run only necessary services and keep software down to a minimum (the more software you have installed, the more ways your computer can be exploited) AND Keep your installation up-to-date.

Use rcconf and turn off all services you do not need (there are quite a few in the default Ubuntu install).  Use netstat and see what services are listening by default (there should be only a couple bound locally and none listening to the Internet at large).  Only install software if it is from the Ubuntu repos.  Look into NoScript or AppArmor for Firefox.

If the above advice is followed, 99.99% of *desktop* users would never have any security worries.

---

### Post by chandru155 on 2009-08-23
Thanks for all who replied to this post. I ll start study about AppArmor.

---

### Post by dk06 on 2009-08-23
> **rookcifer said:**
> There are many hundreds of viruses and other nasties written for Unix/Linux, but I challenge anyone to show me even one of these viruses making rounds in the wild. There are none. This is not because the Linux community is more "on top" of security updates, it's because the multi-user nature of Linux makes it more difficult to spread malware.



This is advice for Windows users, not Linux. I routinely surf to any site I want and I have never had a Linux box "infected" or compromised because of it. In fact, I even surfed over to a few well known attack sites and watched as *nothing* happened. Of course, I have Firefox locked down with AppArmor, but I am not so sure even that is necessary. As long as you keep FF itself up to date, you should be fine (though NoScript is a great tool as well. I personally don't run it since I use AppArmor).

Now, of course, I am assuming a modicum of common sense on the part of the user -- that is, the ability to avoid phishing attacks and other such scams (no OS can protect from this). But this notion that one must avoid surfing to certain sites because of the threat of malware is unfounded (this is even true with a correctly configured Windows box -- that is a Windows box running LUA, SRP, and Integrity controls).
[B]
Dude....

Malware does exist for linux & just because they aren't as common does not mean they are 'unfounded', rootkits and exploits are the biggest threat for Linux users

I'm currently studying at a university for  a dual  B.S. in Network Security & Computer Network Technology and I can assure you that Linux is not invincible to malware
[/B]
> 
**[Trojan DHCP Malware Server Exploit In The Wild]("http://infosecurity.us/?p=7190")**

                      By             [Marc Handelman]("http://infosecurity.us/?author=21") on               March 18th, 2009                     
                       
You are to be congratulated on your keen and inquisitive intellect, eminent wisdom, and, of course, your superior search skills! If you are new here, you should [**subscribe to the Infosecurity.US RSS feed**]("http://infosecurity.us/?feed=rss2") for updates on this topic.

 
[News]("http://www.theregister.co.uk/2009/03/16/dns_hijacking_trojan/"), yesterday, of trojan DHCP servers connecting to nefarious DNS servers thereby compromising a wide range of networked devices; utilizing surreptitious  DHCP servers on local networks, the trojan is reportedly similar to our “little friend” ***Trojan.Flush.M***.  [SANS]("http://www.sans.org/") has [reported]("http://isc.sans.org/diary.html?storyid=6025") this particular rogue exploit in the wild, and apparently the Trojan is actively in an aggressive attack mode.
 The salient point of import here is: The exploit can compromise ***any*** type of device on a network, this includes, printers, copiers, networked door locks, access gateways, hand and facial scanners, vending devices, radios,  medical telemetric devices, i.e, any device that utilizes dynamic host control protocols to garner an IP address. More information, including linkage, and the address of the malicious DNS systems feeding the DHCP side of the equation, appears after the jump. 
 From the SANS Post: “[New rogue-DHCP server malware]("http://isc.sans.org/diary.html?storyid=6025")“
 Thanks to Irwin for alerting us about a new version of rogue DHCP server malware he found in his network. The malware appears to be similar to Trojan.Flush.M which was found last December. Like back then, after infecting its target, the malware installs a rogue DHCP server. The main goal of the DHCP server is to spread a bad DNS server IP address.
 Irwin did a good job comparing the two versions. Here is his summary of the differences:
 
[LIST]
[*]The new version sets the DHCP lease time to 1 hour.
[*]it sets the MAC destination to thebroadcast address, rather then the MAC address of the DHCP client
[*]it does not specify a DNS Domain Name.
[*]the options field does not contain an END option followed by PAD options.
[*]Unlike Trojan.Flush.M, the BootP Broadcast Bit is set.
[/LIST]
 The malicious DNS server is 64.86.133.51 and 63.243.173.162.
 Recommendation: monitor connections to DNS servers other then the approved one pushed out by your DHCP server. This should help you spot this kind of malware. Yes, you can block the two IP addresses listed above, but it will likely do little good.
 
  
From [The Register’s]("http://www.theregister.co.uk/") [Dan Goodin]("http://forms.theregister.co.uk/mail_author/?story_url=/2009/03/16/dns_hijacking_trojan/"): “[New DNS trojan taints entire LAN from single box]("http://www.theregister.co.uk/2009/03/16/dns_hijacking_trojan/")“
 Internet security experts are warning of a new rash of malware attacks that can hijack the security settings of a wide variety of devices on a local area network, even when they are hardened or don’t run on Windows operating systems.
 Once activated, the trojan sets up a rogue DHCP, or dynamic host configuration protocol, server on the host machine. From there, other devices using the same LAN are tricked into using a malicious domain name system server, instead of the one set up by the network administrator. The rogue DNS server sends the devices to fraudulent websites that in many cases can be hard to identify as impostors. A new variant of Trojan.Flush.M is making the rounds, Johannes Ullrich, CTO of the SANS Internet Storm Center [warns here]("http://isc.sans.org/diary.html?storyid=6025"). It offers several improvements over its predecessor, which was discovered in [early December]("http://www.theregister.co.uk/2008/12/05/new_dnschanger_hijacks/"). Among other changes, the new strain no longer specifies a DNS domain name, making the rogue DHCP server harder to detect.
   
  

 
 “This kind of malware is definitely dangerous because it affects systems that themselves are not vulnerable” to the trojan, Ullrich told *The Register*. “So all you need is one system infected in the network and it will affect a lot of other nonvulnerable systems.” Of course, one way to thwart the attack is to hardwire DNS server settings into your iPhone, computer or other net-connecting device. This will direct it to bypass the rogue DNS server even if the device is unfortunate enough to get its internet connection from the impostor DHCP server.> 
[B][SIZE=3]Analysis of the T0rn Rootkit[/SIZE]
[EMAIL="infowar@erols.com"]Toby Miller[/EMAIL]      2000-11-29[/B]     
[COLOR=Red]http://www.securityfocus.com/infocus/1230[/COLOR]
[SIZE=1]
[/SIZE]                        
          [SIZE=1]               Purpose   The purpose of this paper is to inform the IDS community of signatures related to the t0rn rootkit. This paper will not serve as a how-to guide to the t0rn rootkit; rather, it is designed to identify binaries and ports that t0rn uses. This paper will also provide md5sums of binaries and analysis on how to detect t0rn.
  T0rn Rootkit  The t0rn rootkit is designed for speed. By that I mean that it was designed to install quickly on Linux machines. T0rn can do this because it takes very little skill to install and run. All of the binaries that the attacker would need come pre-compiled and the installation process is as simple as ./t0rn. T0rn comes standard with a log cleaner called t0rnsb, a sniffer named t0rns and a log parser called t0rnp. 
   Red Hat 6.1 Details  T0rn has many details that need to be discussed and analyzed in order to detect it in the wild.  The computer that was used in this analysis is a RH 6.1 box with no applied patches, the inetd.conf file had been secured, the password had 6 characters and was connected to an internal network.  In order to analyze t0rn, I had to complete some pre-installation t0rn data collection that included documenting the sizes and creation dates of both the RH binaries and the pre-compiled t0rn binaries.
     First, we want to take a look at the Red Hat 6.1 binaries (before t0rn is installed) their date, size and timestamps. Figure 1 is a list of RH 6.1 binaries and their characteristics.


[/SIZE][quote][COLOR=Red]
[http://www.vupen.com/english/threats/](http://www.vupen.com/english/threats/)
[/COLOR]
[CENTER]                                           [FONT=Verdana]                                           VUPEN Security - [/FONT]                                                                                      [FONT=Verdana][COLOR=#3a3936]                                           Security Threats Watch 24x7[/COLOR][/FONT][/CENTER]
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         [FONT=Verdana] 
[/FONT][FONT=Verdana][COLOR=#3a3936][B]                                               [U]Sun Released Critical Security Updates for Java
                                              
                                              [/U]                                               [/B][IMG]http://www.vupen.com/blog/images/java.png[/IMG] Sun has released security updates for Java JDK, JRE and SDK to address multiple critical [_vulnerabilities_]("http://www.vupen.com/english/advisories/2009/2153").

Fixed flaws include implementation issues, buffer and integer overflows, and input validation errors which could be exploited by attackers to bypass security restrictions, disclose sensitive information, cause a denial of service, or compromise an affected system.

We recommend upgrading to Sun JDK and JRE 6 Update 15 or 5.0 Update 20, and to SDK and JRE 1.4.2_22 or 1.3.1_26.

                                              [/COLOR][/FONT]                                               [I]                                               [FONT=Verdana][SIZE=1][COLOR=#a9a9ac]                                               Published : 2009-08-05 15:56:03 UTC

[/COLOR][/SIZE][/FONT][/I][FONT=Verdana] 
[/FONT][FONT=Verdana][COLOR=#3a3936][B]                                               [U]Adobe Flash, Acrobat and Reader Zero-Day Exploit
                                              
                                              [/U]                                               [/B][IMG]http://www.vupen.com/blog/images/adobe.gif[/IMG] Adobe released a [_security advisory_]("http://www.vupen.com/english/advisories/2009/1986") related to a critical and unpatched zero-day vulnerability being exploited in the wild.

The issue affects Adobe Acrobat, Reader and Flash Player on Windows, Macintosh and Linux, and allows code execution.

_Update_ : Security fixes are now [_available_]("http://www.adobe.com/support/security/bulletins/apsb09-10.html").

                                              [/COLOR][/FONT]                                               [I]                                               [FONT=Verdana][SIZE=1][COLOR=#a9a9ac]                                               Published : 2009-07-22 23:33:37 UTC - Updated : 2009-07-31 20:18:25 UTC
[/COLOR][/SIZE][/FONT][/I]
> 
[COLOR=Red]http://www.vupen.com/english/linux-advisories/[/COLOR]
**[FONT=Verdana]>> [/FONT][FONT=Verdana]VUPEN Security - Linux Advisories[/FONT]**
[CENTER]          [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Fedora Security Update Fixes Qt WebKit Memory Corruption Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2345")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Fedora Security Update Fixes OCS Inventory SQL Injection Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2344")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Fedora Security Update Fixes SquirrelMail Security Bypass Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2343")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Fedora Security Update Fixes neon Spoofing and DoS Vulnerabilities[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2342")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Fedora Security Update Fixes Afuse Command Injection Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2340")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Fedora Security Update Fixes Pidgin Memory Corruption Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2339")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Fedora Security Update Fixes Kobo Admin Authentication Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2338")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Fedora Security Update Fixes Nagios CGIs AE Commands Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2337")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Mandriva Security Update Fixes GnuTLS Security Bypass Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2336")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Mandriva Security Update Fixes OpenJDK Code Execution Vulnerabilities[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2335")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Mandriva Security Update Fixes Libgadu Denial of Service Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2334")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Ubuntu Security Update Fixes Pidgin Memory Corruption Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2333")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : Turbolinux Security Update Fixes Flash Code Execution Vulnerabilities[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2332")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]21.08.2009 : SuSE Security Update Fixes Kernel Memory Corruption and DoS Issues[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2331")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]20.08.2009 : Ubuntu Security Update Fixes GnuTLS Security Bypass Vulnerabilities[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2327")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]20.08.2009 : Slackware Security Update Fixes Pidgin Memory Corruption Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2326")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]20.08.2009 : Debian Security Update Fixes Pidgin Memory Corruption Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2325")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]20.08.2009 : Debian Security Update Fixes cURL Certificate Spoofing Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2324")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]20.08.2009 : Debian Security Update Fixes kdegraphics Code Execution and DoS[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2323")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]20.08.2009 : Debian Security Update Fixes Kde4libs Code Execution Vulnerabilities[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2322")[/FONT][/LEFT]
[RIGHT][FONT=Verdana]
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]20.08.2009 : Debian Security Update Fixes Kdelibs Code Execution Vulnerabilities[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2321")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]20.08.2009 : Mandriva Security Update Fixes Compress::Raw::Bzip2 Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2320")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]19.08.2009 : Gentoo Security Update Fixes Dillo PNG Integer Overflow Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2312")[/FONT][/LEFT]
                  [RIGHT]     [FONT=Verdana]     
[/FONT][/RIGHT]
          [LEFT][FONT=Verdana]  [[FONT=Verdana][COLOR=#3a3936]19.08.2009 : Gentoo Security Update Fixes DokuWiki Local File Inclusion Vulnerability[/COLOR][/FONT]]("http://www.vupen.com/english/advisories/2009/2311")[/FONT][/LEFT]
[/CENTER]

> 
[SIZE=1][COLOR=Red]**[http://www.chkrootkit.org/](http://www.chkrootkit.org/)**[/COLOR]
[/SIZE][SIZE=1]01. lrk3, lrk4, lrk5, lrk6 (and variants);[/SIZE]   [SIZE=1]02. Solaris rootkit;[/SIZE]   [SIZE=1]03. FreeBSD rootkit;[/SIZE]      [SIZE=1]04. t0rn (and variants);[/SIZE]   [SIZE=1]05. Ambient's Rootkit (ARK);[/SIZE]   [SIZE=1]06. Ramen Worm;[/SIZE]     [SIZE=1]07. rh[67]-shaper;[/SIZE]   [SIZE=1]08. RSHA;[/SIZE]    [SIZE=1]09. Romanian rootkit;[/SIZE]     [SIZE=1]10. RK17;[/SIZE]   [SIZE=1]11. Lion Worm;[/SIZE]   [SIZE=1]12. Adore Worm;[/SIZE]     [SIZE=1]13. LPD Worm;[/SIZE]    [SIZE=1]14. kenny-rk;[/SIZE]   [SIZE=1]15. Adore LKM;[/SIZE]     [SIZE=1]16. ShitC Worm;[/SIZE]   [SIZE=1]17. Omega Worm;[/SIZE]   [SIZE=1]18. Wormkit Worm;[/SIZE]      [SIZE=1]19. Maniac-RK;[/SIZE]   [SIZE=1]20. dsc-rootkit;[/SIZE]   [SIZE=1]21. Ducoci rootkit;[/SIZE]     [SIZE=1]22. x.c Worm;[/SIZE]   [SIZE=1]23. RST.b trojan;[/SIZE]    [SIZE=1]24. duarawkz;[/SIZE]     [SIZE=1]25. knark LKM;[/SIZE]   [SIZE=1]26. Monkit;[/SIZE]   [SIZE=1]27. Hidrootkit;[/SIZE]     [SIZE=1]28. Bobkit;[/SIZE]    [SIZE=1]29. Pizdakit;[/SIZE]   [SIZE=1]30. t0rn v8.0;[/SIZE]     [SIZE=1]31. Showtee;[/SIZE]   [SIZE=1]32. Optickit;[/SIZE]   [SIZE=1]33. T.R.K;[/SIZE]      [SIZE=1]34. MithRa's Rootkit;[/SIZE]   [SIZE=1]35. George;[/SIZE]   [SIZE=1]36. SucKIT;[/SIZE]     [SIZE=1]37. Scalper;[/SIZE]   [SIZE=1]38. Slapper A, B, C and D;[/SIZE]    [SIZE=1]39. OpenBSD rk v1;[/SIZE]     [SIZE=1]40. Illogic rootkit;[/SIZE]   [SIZE=1]41. SK rootkit.[/SIZE]   [SIZE=1]42. sebek LKM;[/SIZE]     [SIZE=1]43. Romanian rootkit;[/SIZE]    [SIZE=1]44. LOC rootkit;[/SIZE]   [SIZE=1]45. shv4 rootkit;[/SIZE]     [SIZE=1]46. Aquatica rootkit;[/SIZE]   [SIZE=1]47. ZK rootkit;[/SIZE]   [SIZE=1]48. 55808.A Worm;[/SIZE]      [SIZE=1]49. TC2 Worm;[/SIZE]   [SIZE=1]50. Volc rootkit;[/SIZE]   [SIZE=1]51. Gold2 rootkit;[/SIZE]     [SIZE=1]52. Anonoying rootkit;[/SIZE]   [SIZE=1]53. Shkit rootkit;[/SIZE]   [SIZE=1]54. AjaKit rootkit;[/SIZE]     [SIZE=1]55. zaRwT rootkit;[/SIZE]   [SIZE=1]56. Madalin rootkit;[/SIZE]   [SIZE=1]57. Fu rootkit;[/SIZE]     [SIZE=1]58. Kenga3 rootkit;[/SIZE]   [SIZE=1]59. ESRK rootkit;[/SIZE]   [SIZE=1]60. rootedoor rootkit;[/SIZE]     [SIZE=1]61. Enye LKM;[/SIZE]   [SIZE=1]62. Lupper.Worm;[/SIZE]   [SIZE=1]63. shv5;[/SIZE]     [SIZE=1]64. OSX.RSPlug.A;[/SIZE][COLOR=Red][B]
[COLOR=Black]also see these:[/COLOR]

[http://insecure.org/](http://insecure.org/)
[http://www.sans.org/](http://www.sans.org/)
[http://www.vupen.com/](http://www.vupen.com/)
[http://www.nist.org/news.php](http://www.nist.org/news.php)
[http://www.linux-sec.net/RootKits/](http://www.linux-sec.net/RootKits/)[/B][/COLOR]

---

### Post by Kinstonian on 2009-08-23
Good post, dk06.

---

### Post by rookcifer on 2009-08-23
> **dk06 said:**
> [B]
Dude....

Malware does exist for linux & just because they aren't as common does not mean they are 'unfounded', rootkits and exploits are the biggest threat for Linux users

If you can't take the time to read my post, then please don't bother responding.  However, out of courtesy, I will summarize what I said -- this time only:

1) Yes, there have been MANY viruses written for *nix.

2) The half lives of these viruses in the wild have invariably been quite short.

3) I would like for you to provide me one example of a major *nix virus **in the wild**.  Just one.  The examples you posted do not qualify (for one, DNS server exploits are not OS specific and **a rootkit is not a virus.**  A rootkit is a hacker tool, much like a port scanner or metasploit.  A rootkit on its own is *worthless* without having an *already* compromised machine.  The AV companies are dishonest and in order to make more Linux sales, they erroneously report rootkits as malware.  The truth is, a rootkit cannot do anything without a human on the other end.

4) Adobe always posts advisories for all operating systems even though Windows is the platform by far the most at risk, both because of market share *and* because of the lack of privilege separation inherent in most installs.  Besides, the Adobe advisory **is not malware**.  Neither are the other advisories you listed.  **They are not viruses.**  They are advisories for flaws in software.  Yes, it is possible in theory to create malware that exploits these flaws, but we are back to my original challenge: show me an example!

> I'm currently studying at a university for  a dual  B.S. in Network Security & Computer Network Technology and I can assure you that Linux is not invincible to malware

You have a lot to learn.

---

### Post by dk06 on 2009-08-24
> **rookcifer said:**
> If you can't take the time to read my post, then please don't bother responding.  However, out of courtesy, I will summarize what I said -- this time only:

1) Yes, there have been MANY viruses written for *nix.

2) The half lives of these viruses in the wild have invariably been quite short.

3) I would like for you to provide me one example of a major *nix virus **in the wild**.  Just one.  The examples you posted do not qualify (for one, DNS server exploits are not OS specific and **a rootkit is not a virus.**  A rootkit is a hacker tool, much like a port scanner or metasploit.  A rootkit on its own is *worthless* without having an *already* compromised machine.  The AV companies are dishonest and in order to make more Linux sales, they erroneously report rootkits as malware.  The truth is, a rootkit cannot do anything without a human on the other end.

4) Adobe always posts advisories for all operating systems even though Windows is the platform by far the most at risk, both because of market share *and* because of the lack of privilege separation inherent in most installs.  Besides, the Adobe advisory **is not malware**.  Neither are the other advisories you listed.  **They are not viruses.**  They are advisories for flaws in software.  Yes, it is possible in theory to create malware that exploits these flaws, but we are back to my original challenge: show me an example!



You have a lot to learn.

[B]Wowie...

I don't claim to know it all but tell me, what information in my post was inaccurate???

You seem to be set on this *'virus in the wild'* thing when in all actuality, people don't need a virus to infect your machine. 

Exploits are designed to 'Exploit' vulnerabilities in your machine....perhaps elevating privileges and ultimately taking control of your machine with say...a rootkit
[/B][B]
Here are some examples:

[http://www.youtube.com/watch?v=UdkpJ13e6Z0](http://www.youtube.com/watch?v=UdkpJ13e6Z0)[/B]

[B][http://www.youtube.com/watch?v=WggODNeBdeY](http://www.youtube.com/watch?v=WggODNeBdeY)

And more on exploits:
[http://insecure.org/sploits_linux.html](http://insecure.org/sploits_linux.html)


Viruses:
[/B]> 
[B] [COLOR=Red]https://help.ubuntu.com/community/Linuxvirus[/COLOR]
[/B]**The Alaeda Virus** is relatively recent (May) and infects other binary (program) files in the same directory. If you run as a normal user doing non-programming work, you should not have any other binaries in your home folder. Alaeda won't have anything to infect. This is a good reason why you shouldn't download and install random files off the Internet. If you don't know why you're typing in your password, don't do it. Realistically, though, ELF files (the Linux equivalent of a Windows .exe) are pretty picky about what system they run on, so sthe chance of getting infected is slight.
[B]
This one is from 2007,
[http://it.toolbox.com/blogs/locutus/new-macos-and-linux-virus-found-in-the-wild-15440](http://it.toolbox.com/blogs/locutus/new-macos-and-linux-virus-found-in-the-wild-15440)

===========================================================================================

[I][U]Here are a couple sites that can help with securing Ubuntu:
[COLOR=Red]
[/COLOR][/U][/I] [COLOR=Red][http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)[/COLOR] 
[/B]

---

