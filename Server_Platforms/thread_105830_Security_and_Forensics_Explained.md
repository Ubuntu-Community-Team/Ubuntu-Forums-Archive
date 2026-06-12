---
title: "Security and Forensics Explained"
date: 2005-12-19
forum: Server Platforms
---

### Post by KingBahamut on 2005-12-19
[http://gaming.gwos.org/doku.php/udsf:serverguide](http://gaming.gwos.org/doku.php/udsf:serverguide)

The list is ever changing and expanding daily. 

Leave your own here, and we will add them appropriate.

---

### Post by matthew on 2005-12-19
Great idea! Thanks.

---

### Post by towsonu2003 on 2005-12-19
There is Auditor ( [http://distrowatch.com/table.php?distribution=auditor](http://distrowatch.com/table.php?distribution=auditor) ) but I'm not sure you want a distro in there :)

---

### Post by KingBahamut on 2005-12-19
Actually the intent is to keep this thread Tool specific not Distro out. 

If it was Id like PHLAK, LAS, and other such projects, but Id like just tools to go into it.

---

### Post by h3llfyr3 on 2006-03-18
As a pen tester here is my standard first use tools during a pen test. This does not include 'stuff' I use for exploit development on incident response.

External Testing:
#1 Nmap (Id services being run correlate to known vulns)
#2 Netcat (all sorts of reasons)
#3 Nikto (Dodgy cgi's + scripts)
#4 Nessus (only for lage numbers of hosts, i prefer manual checks)
#5 Hydra (thc.org, brute forces many services) 
#6 IKEScan / PSKCrack (doing cisco vpn concentrators)
#7 Cisco torch + CCSAT (cisco router exploits)
#8 Metasploit (canned exploits with a perl wrapping)
#9 mirrored packetstorm / frsirt / xfocus / milw0rm
#10 default password lists
#11 absinthe (database testing)

Internal testing:
#1 ethereal
#2 Ettercap
#3 Yersinia
#4 john the ripper + 2gb dictionary also used for hydra ;)

wireless testing
#1 Kismet
#2 Airsnort
#3 Aireplay
#4 Wepcrack

General:
#1 VMware some tools work best under windows and I keep windows installed under a VM as well as Backtrack.
#2 fragrouter (IDS evasion)

Personal items
#1 large private exploit collection
#2 large john.pot file (30mb and growing)

---

### Post by majikstreet on 2006-03-18
this is awesome.. thanks!

yeah there are a lot of security distros.. 
if you want to add a couple of sites you could do antionline.com and maybe irongeek.com (<-- has videos of hacking pretty much)

---

### Post by h3llfyr3 on 2006-03-19
hmmn 
antionline is full of wannabes no skill there at all. kinda like zone-h.org and that crew that defaced your website are'nt posting

Irongeek has some good video tutes

sites
securityfocus (bugtraq)
osvdb.com (open source vulns datbase)
milw0rm (exploit code and shellcode)
frsirt (used to be good now crap, as you gots to pay)
insecure.org (mailing lists)
illmob (stuff / tools)
xfocus (stuff tools)
phenolit.de (default password list)
metasploit.com (metasploit framework)

forums
security-forums.com (great knowledge base,intellgent responses, skiddies get eaten)
h4cky0u.org (quite a few blackhats showing off sites they hacked, don't expect anything more than abuse though and php hacks/ brute force nessus scans)

---

### Post by Subnet on 2006-04-04
securitydot.net is a good one, exploits, news, and mailing list

---

### Post by Jebenko on 2006-04-05
To the tools. System monitoring  - htop is a cool one for the 


console[ATTACH]8028[/ATTACH]

---

### Post by auroraborealis on 2006-04-25
CERT Library is good too!

[https://www.vte.cert.org/vtelibrary.html](https://www.vte.cert.org/vtelibrary.html)

---

### Post by Gouki on 2006-08-20
Here's a couple more, very useful, applications:

[p0f](http://lcamtuf.coredump.cx/p0f/p0f.shtml) - passive OS fingerprinting tool

[Yersinia](http://yersinia.sourceforge.net/) - can be used to exploit layer 2 protocols - STP, DTP, CDP, ISL, DHCP, etc

[Kismet](http://www.kismetwireless.net/download.shtml) - I think we all know Kismet ...

[hping](http://www.hping.org/) - TCP/IP packet assembler/analyzer

[Airsnort](http://airsnort.shmoo.com/) - This is fun! Turn your WiFi card (PCMCIA) into an AP (guess what happens next?)

If I remember others, I'll add here.

**Update:**

I forgot to mention [THC-Hydra](http://thc.segfault.net/thc-hydra/). My favorite brute-force cracker. You can find the .Deb package [here](http://www.freshnet.org/debian/dapper/hydra/) or [here](http://files.goukihq.org/Packages). *(Both packages are needed)*

---

### Post by TokenBad on 2006-10-29
I have tried to install the hydra-gtk but get these errors when I try...

checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


gtk is installed...and its is 2.0...not sure what it going on with it...any help?

TokenBad

---

### Post by redwolf963 on 2006-10-29
I like the post from a fellow pentester.
 Now that Backtrack has gone to full 1,0 vers.,it's a good distro for pentesting.
Also,don't overlook Knoppix.
Creating your own rainbow tables...(for password cracking of known,probable,or likely)is very time consuming,but worth the effort,if what you do is test the security of systems(at least from a commonly used ,or easily guessed password perspective.)that require too many passwords,or don't use a type of two-factor authentication.

Also,don't forget secgeeks.com for security info.
Scott

---

### Post by rockdon on 2007-04-24
Medusa is a multi-protocol bruter that I've been using for a while that has been much more useful to me than Hydra.

---

### Post by ghostboy on 2007-05-14
> **redwolf963 said:**
> I like the post from a fellow pentester.
Now that Backtrack has gone to full 1,0 vers.,it's a good distro for pentesting.
Also,don't overlook Knoppix.
Creating your own rainbow tables...(for password cracking of known,probable,or likely)is very time consuming,but worth the effort,if what you do is test the security of systems(at least from a commonly used ,or easily guessed password perspective.)that require too many passwords,or don't use a type of two-factor authentication.
 
Also,don't forget secgeeks.com for security info.
Scott
 
 
Redwolf bring up an excellent point. I love to use BackTrack, but I think that BackTrack is more Distro specific then tool specific. I still think its a great tool though. Here is a link to the newest stable version available, 2.0. [http://www.remote-exploit.org/backtrack_download.html](http://www.remote-exploit.org/backtrack_download.html)

---

### Post by stanjam on 2007-05-16
I would add the following:

Snort - Intrusion Detection Service
BASE - Web based Graphical interface for Snort

SleithKit and Autopsy - Forensics software.

---

### Post by fortAlamo on 2007-05-21
any chance to have a hydra.deb package for feisty ready to be downloaded?

---

### Post by hlmuller on 2007-07-06
Two of the data forensics/recovery programs I use are:

sleuthkit
autopsy

I have had greater success using those than some of the low end commercial windows data recovery programs.

---

### Post by otake-tux on 2007-11-14
I would just like to add

COPS: old but still relevant. will assist in system hardening.
nikto: vuln. scanner
bastille: again, system hardening.

great thread.

---

### Post by optyx-the-producer on 2007-11-17
Don't forget Helix it's a debian dirivitive live CD based on knoppix.  It's got a lot of great tools and utils like Adepto front end for imaging with dcfldd.

---

### Post by FakeOutdoorsman on 2007-12-26
Thelink from the original post has changed to:
[http://doc.gwos.org/doku.php/doc:network:securityanalysis](http://doc.gwos.org/doku.php/doc:network:securityanalysis)

---

### Post by stmurray on 2007-12-27
Unless I missed it (and excuse me if I have) no one has mentioned the  web application penetration and vulnerability tools.  I see a lot of posts in the Ubuntu forums with things like "I have just installed LAMP for a site i am creating.....".  These tools test web applications, which is above and beyond the locking down of the web server and service itself.

There are commercial web application scanners (WebInspect and AppScan) which take you pretty far to get the low hanging fruit , but they test only for what they know (they can't find logic vulnerabilities, for example) and have issues with session time outs, authentication, etc.  

Below are two tools i have used to test the security of the application running on a web site .  Niether tool is "plug and play" kind of tool-- both require some knowledge of web application vulnerabilities and how to exploit them.  (See the reference material with each)

**Burp** has quite a few tools to proxy, spider send crafted http requests, etc (especially try the "intruder" to to send semi-automated http requests that alter each request, based on your input file.)  Download at [http://portswigger.net](http://portswigger.net)  There is a "free" and a fee-based "Professional version.   Portswigger (aka Dafydd Stuttard) also has (IMHO) the newest defacto standard for web app vulnerability testing in "The Web Application Hacker's Handbook".  I have Burp 2.0 beta running quite well on Feisty.  

**WebScarab** from  OWASP (hurray for open source!)  is a similar multi-tool suite.  See [www.owasp.org](www.owasp.org).  I have only used this on Windows (before I made the move to Ubuntu), but as it is JAva based, it should work fine.   if someone is considering building a web application (even a trivial one), then a look at the "OWASP Guide to Building Secure Web Applications"  from this site is recomended.

I've used Achilles in the past, which is a Web Proxy, but either of the tools above match it's functionality and give you more.  (In fact the "Tamper Data" plug-in for Firefox is just as useful as Achilles)

---

### Post by Alyx on 2008-02-10
Perhaps this thread is dead but. I noticed that we haven't touched the WINE/WIN32 world much but there was mention of VM's so, in my VM I have, GFI languard NSS, NESSUS, Retnia, FTK, Encase, SamSpade and a few others I cant remember off the top of my head. Also Backtrack is a fantastic collection as well as Knopix and I also have a collection of Password scripts that round out my collection.

---

### Post by georges023 on 2008-03-30
> **Alyx said:**
> Perhaps this thread is dead but. I noticed that we haven't touched the WINE/WIN32 world much but there was mention of VM's so, in my VM I have, GFI languard NSS, NESSUS, Retnia, FTK, Encase, SamSpade and a few others I cant remember off the top of my head. Also Backtrack is a fantastic collection as well as Knopix and I also have a collection of Password scripts that round out my collection.

Why use a VM for Nessus? You can find .deb for Ubuntu on official site.
BackTrack is good, real good

---

