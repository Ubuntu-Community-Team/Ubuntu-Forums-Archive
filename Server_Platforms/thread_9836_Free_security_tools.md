---
title: "Free security tools?"
date: 2005-01-01
forum: Server Platforms
---

### Post by tleroy on 2005-01-01
Can anyone point me to some security tools for Linux?  I'm interested in authorized port scanning, penetration testing, and intrusion detection.  This is all for legitimate purposes, but if anyone's uncomfortable posting such answers here, please Private Message me.

Sincerely,

---

### Post by word_virus on 2005-01-02
[QUOTE=tleroy]Can anyone point me to some security tools for Linux?  I'm interested in authorized port scanning, penetration testing, and intrusion detection.  This is all for legitimate purposes, but if anyone's uncomfortable posting such answers here, please Private Message me.

Sincerely,[/QUOTE]

If you have the bandwidth, try downloading a copy of Knoppix-STD (Security Tools Distribution).  It's a Knoppix-based LiveCD that includes a plethora of open-source security and intrusion-detection utilities; password crackers, packet sniffers, port scanners, WEP crackers, encryption utilities, firewall and anti-virus software, etc. etc. 
You can get it at [www.knoppix-std.org](www.knoppix-std.org)

Since it's Knoppix, it's usefulness extends into other realms as well, making it an ideal tool for data-recovery and virus scanning on Windows boxes.  Check out O'Reilly's excellent "Knoppix Hacks" for more information on the subject.
[http://www.oreilly.com/catalog/knoppixhks/index.html](http://www.oreilly.com/catalog/knoppixhks/index.html)

If you're looking for some tools to run on your ubuntu system here are a few of my favorites, most of which are a quick "apt-get" away if you've enabled the universe repository; keep in mind this list reflects a high personal bias and should by no means be considered definitive:

packet-sniffing: Ethereal
port scanning:  Nmap
network visualization:  Etherape
password cracking: l0phtcrack
wep cracking: airsnort
wardriving: kismet
firewall: Firestarter
antivirus: clamAV
encryption: GnuPG

Hope this helps!

---

### Post by maxim_86ualb2 on 2005-01-02
thanks for the good list of progs :)

---

### Post by tleroy on 2005-01-02
Thanks WordVirus!  I'll check them out.  :)

Sincerely,

---

### Post by jbh on 2005-01-04
[QUOTE=tleroy]Can anyone point me to some security tools for Linux?  I'm interested in authorized port scanning, penetration testing, and intrusion detection.  This is all for legitimate purposes, but if anyone's uncomfortable posting such answers here, please Private Message me.

Sincerely,[/QUOTE]


get nessus and nmap. nessus is great, I found out by running it against a work server the sql password was blank, and there were dozens of open ports that should've been filtered

There's also [http://www.phrack.org/](http://www.phrack.org/) and 2600 magazine.

---

### Post by twisted_steel on 2005-01-04
Some of these tools you may want to get from source rather than a repository since there are updated versions that have not yet made it into universe. For example, a new version of [nmap]("http://www.insecure.org") is available with faster and improved scanning.
 
 Another nice piece of software is [ettercap]("http://ettercap.sourceforge.net/").

---

### Post by jdodson on 2005-01-05
this is good, i am going to stick this.  feel free to keep adding to the list.

---

### Post by scp on 2005-01-08
Check out:  [http://www.wiretapped.net/](http://www.wiretapped.net/)

Have fun! :)

---

### Post by tleroy on 2005-01-12
Awsome tools and links.  Thanks everyone!  :)

---

### Post by ghost on 2005-02-01
This list is the best. I installed all of these on my ubuntu box.

90% of these are in the repositry. Others just compile them from source.

[http://www.phlak.org/modules/sections/index.php?op=viewarticle&artid=1](http://www.phlak.org/modules/sections/index.php?op=viewarticle&artid=1)

---

### Post by ming0 on 2005-02-02
[http://unix.freshmeat.net/projects/las/](http://unix.freshmeat.net/projects/las/) 

Local Area Security is my favorite Linux live security distro
(the official website takes a long time to load--and it's being moved)

you can still get the ISO's (from the freshmeat link)

it's got pretty much all the security widgets you can think of...

BEST OF ALL, it has an easy to use version of nessus (I think that's what it's called) which is a full scanner that will sniff out known vulns!

---

### Post by Mute on 2005-02-10
I know most of these have been mentioned, but thought I would throw in my 2cents.  I have used all of these and found them to be extremely useful.  Of course these are besides Nmap and Nessus.

-Nemesis (Packet Injection Utility) [http://www.packetfactory.net/projects/nemesis/](http://www.packetfactory.net/projects/nemesis/)
-Snort (IDS) [http://www.snort.org/](http://www.snort.org/)
-Netcat [http://netcat.sourceforge.net/](http://netcat.sourceforge.net/)
-Argus (Network Monitor) [http://www.qosient.com/argus/](http://www.qosient.com/argus/)
-Ethereal (obvious I know, but an amazing tool non the less)  [http://www.ethereal.com/](http://www.ethereal.com/)
-MTR (My Traceroute - Gui frontend for Traceroute) [http://www.bitwizard.nl/mtr/](http://www.bitwizard.nl/mtr/)
-Tcpdump (another obvious one...) [http://www.tcpdump.org/](http://www.tcpdump.org/)

The list could actually go on forever, it really all depends on what you are looking to do.  Just MHO - take of it what you will.

-Mute

---

### Post by nate on 2005-03-14
Most of these have been mentioned, but they're some of my favorites:

Snort is an excellent IDS. It rivals most or all closed source IDS. It can be customized to do other things besides intrusion detection such as recording all traffic on a network.

Ethereal is an excellent packet analyzer.

Tcpdump is useful in a lot of situations and goes hand-in-hand with a number of other tools.

[Helix](http://www.e-fense.com/helix/index2.html) is a customized Knoppix distribution designed specifically for Incident Reponse and Forensics. The iso contains a ton of tools. It has both Windows and Linux tools.

---

### Post by ghost on 2005-03-15
[http://www.metasploit.com](http://www.metasploit.com)

---

### Post by ghost on 2005-03-15
Bluetooth hacking tools

[http://trifinite.org/trifinite_stuff.html](http://trifinite.org/trifinite_stuff.html)

---

### Post by s0c0 on 2005-05-03
The only thing that I can think of that has not been listed is paratrace (parasitic traceroute).  This basically piggybacks traceroute onto another protocol so you can get an inside look at the network behind the firewall/router.  Sometimes it works, sometimes it doesn't.  This package is available through apt.

---

### Post by jodef on 2005-05-05
[Security Tools Linux and Windows](http://basicsec.org/tools.html)

---

### Post by jodef on 2005-05-05
Here's another :
> Rootkit Hunter


Description

    Rootkit scanner is scanning tool to ensure you for about 99.9%* you're clean of nasty tools. This tool scans for rootkits, backdoors and local exploits by running tests like:

    - MD5 hash compare
    - Look for default files used by rootkits
    - Wrong file permissions for binaries
    - Look for suspected strings in LKM and KLD modules
    - Look for hidden files
    - Optional scan within plaintext and binary files

    Rootkit Hunter is released as GPL licensed project and free for everyone to use.

    * No, not really 99.9%.. It's just another security layer 
[Rkhunter](http://www.rootkit.nl/projects/rootkit_hunter.html) and Ubuntu is supported as well.

---

### Post by mohaham on 2005-05-05
nice links and tools..Thanks everybody..

---

### Post by DJ_Max on 2005-05-09
[www.chkrootkit.org/](www.chkrootkit.org/)
[www.shorewall.net](www.shorewall.net)
[Kiss My Firewall](http://www.geocities.com/steve93138/) 

Here's some good scripts
[http://rfxnetworks.com/proj.php](http://rfxnetworks.com/proj.php)

---

### Post by ghost on 2005-05-11
[Exploit Tree](http://www.securityforest.com/wiki/index.php/Category:ExploitTree)

---

### Post by Kurai on 2005-05-12
Go to [http://insecure.org](http://insecure.org) they have the top 50 or 75 tools there w/ platform compatability listed plus it's where nmap is

---

### Post by [pl]ice on 2005-05-15
hm,  :
sara
tara
toast :)
xprobe2 (interesting....)
queso 
dnshijacker
they are not new ones...

honeyd  :>
did someone mentioned .... 

[http://ettercap.sourceforge.net/](http://ettercap.sourceforge.net/)   :>  probably on insecure page...

re: tcpdump, just an example, i read now IDS and used tcpdump on my box, and what can i see? strange arp from router to xp box on lan :)  guy had weird virus in temp, blocked up the whole network!! (not that its big!! )
  so yeh, it's wicked tool   ;-)

---

### Post by DaturaX on 2005-06-16
I've used Hping and found it to be useful.It is a command-line oriented TCP/IP packet assembler/analyzer.

[Guide to Hping](http://security.linux.com/security/05/06/08/135232.shtml?tid=35) 

[Hping official site](www.hping.org)

---

### Post by Burgundavia on 2005-06-16
Funny, when I scanned the forums, I read this as "Free security holes" and I thought, well, there are lots of those, and some are even non-free.

Corey

---

### Post by apollyonis on 2005-06-20
WHoppix. Bootable .iso and you can install from the CD itself, so you just need a single CD. All of the tools you would want plus the exploits from several sources....thousands that you can compile and try. Several neat demos of how a local network is cracked, WEP, etc. as well. Well worth a look!

[WHoppix Home Page](http://www.whoppix.net/)

---

### Post by halilicelik on 2005-07-10
I want to mention a great tool or linux distro: IPCop. It is ideal for home and small office use as an internet connection sharing tool.

[www.ipcop.org](www.ipcop.org)

A secure Linux distribution managed through a web-interface. It turns an old PC
into a firewall and VPN gateway. Features an Intrusion Detection System.

---

### Post by craigevil on 2005-07-24
[QUOTE=][/QUOTE]
 LinuxQuestions.org - Security references 
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=45261](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=45261)

---

### Post by zaal on 2005-07-28
nessus is great !

---

### Post by kirsche on 2005-07-31
check scanrand out.
[http://www.sans.org/resources/idfaq/scanrand.p](http://www.sans.org/resources/idfaq/scanrand.p)

one of the fastest scanners.

---

### Post by atilasendil on 2005-08-04
[QUOTE=Burgundavia]Funny, when I scanned the forums, I read this as "Free security holes" and I thought, well, there are lots of those, and some are even non-free.

Corey[/QUOTE]

lol :-)

I have been reading the topic and thinking if it were the non-free OS I could have contributed. And thank you all for giving me a starting point as *I have been living in a non-free security-hole for years trying to use such tools from within-the-hole* :-)

Respect

---

### Post by lotusleaf on 2005-08-22
I have tons of links to useful sites regarding security (including but not limited to computer security):

[http://lotusleafslinks.tuxfamily.org/](http://lotusleafslinks.tuxfamily.org/)

Browse my site via web or download the entire list of links as a bookmarks.html file and import it into your web browser of choice.

---

### Post by Jeezis on 2005-08-28
i'm looking for an antivirus scanner with a gui. just a standard deal like what you can find for winblows. any ideas? thanks a lot \\:D/

---

### Post by matthew on 2005-08-28
[QUOTE=Jeezis]i'm looking for an antivirus scanner with a gui. just a standard deal like what you can find for winblows. any ideas? thanks a lot \\:D/[/QUOTE]
Look here: [http://www.ubuntuforums.org/showthread.php?t=25421](http://www.ubuntuforums.org/showthread.php?t=25421)

---

### Post by Jeezis on 2005-08-29
[QUOTE=matthew]Look here: [http://www.ubuntuforums.org/showthread.php?t=25421](http://www.ubuntuforums.org/showthread.php?t=25421)[/QUOTE]
 thanks, i'm using clam av with the kde frontend Klamav. it works wonderfully :)

---

### Post by seiflotfy on 2005-09-16
try aegis-virus-scanner or f-prot!! also good

---

### Post by matthew on 2005-09-16
[QUOTE=Jeezis]thanks, i'm using clam av with the kde frontend Klamav. it works wonderfully :)[/QUOTE]
You are welcome. Glad it worked for you!

---

### Post by Technoviking on 2005-09-22
This is one I use, [Auditor security collection](http://new.remote-exploit.org/index.php/Auditor_main) . It is scary the tools that are in it.

Mike

---

### Post by matthew on 2005-09-22
[QUOTE=Mike Basinger]This is one I use, [Auditor security collection](http://new.remote-exploit.org/index.php/Auditor_main) . It is scary the tools that are in it.

Mike[/QUOTE]
Wow. That's impressive looking. I'm going to have to download it and take a closer look. Thanks for the referral!

---

### Post by moondog on 2005-10-27
Here's another good list:

[http://www.insecure.org/tools.html]("http://www.insecure.org/tools.html")

Cheers.

---

### Post by kikingm on 2005-11-10
need help!!!

how to block/filter Internet Messenger (yahoo). or is there any special software that i can install?

thanks.

---

### Post by PokerFacePenguin on 2005-11-11
Haven't tried it myself, but I would think any firewall would do.  Personally, I use guarddog.  The most effective way to make it happen would probably be to deny all traffic from the servers at yahoo.

Some good info found on the help sites at yahoo
> I'm behind a firewall. Can I still use my webcam on Yahoo!?

In order to use Yahoo! Chat's Webcam feature, your firewall must permit outgoing TCP connections to webcam.yahoo.com on port 5100.

If you use a proxy server to connect to the Internet, you will not be able to use the Webcam feature. 



Setting up Firewall & Proxy Ports
If you are connecting to the Internet from behind a firewall and/or proxy server, you may have trouble using our chat software. To get around this, you can contact your system administrators to request that they give you access to our servers. If you do not have a system administrator, please contact the company that made your firewall for further assistance in accessing our servers.

The default settings for our Chat servers are 8000-8030. You will need TCP inbound and outbound access for these ports.





That ought to get you started in the right direction........check your logs after some chat traffic goes thru, get the subdomain name(s)  etc and block em.

---

### Post by yuri6312 on 2005-11-16
thanks for everyone's list and links.
i will see

---

### Post by RikBlankestijn on 2005-12-20
I saw someone posting this one already: [rootkit hunter]("http://www.rootkit.nl/projects/rootkit_hunter.html"), but has anyone else tried it already? It looks very good to me, but can one confirm it is really good in finding security holes too?

---

### Post by jodef on 2005-12-21
[QUOTE=RikBlankestijn]I saw someone posting this one already: [rootkit hunter]("http://www.rootkit.nl/projects/rootkit_hunter.html"), but has anyone else tried it already? It looks very good to me, but can one confirm it is really good in finding security holes too?[/QUOTE]

I have used it on a variety of distros and it's excellent!! Not only detects rootkits but looks at file permissions and other security flaws as well. The reports are ver comprehensive.

---

### Post by Peter76 on 2006-01-05
I just found out about tcptrack; it shows your network connections in a top like state. In the universe repository's

---

### Post by sadjack on 2006-02-13
whax, auditor, helix - all good live security cd's, auditor is awsome\\:D/

---

### Post by suRoot on 2006-02-24
Auditor is awesome.  backtrack, which someone posted a link to looks pretty good too... downloading it now.  I deal with this stuff every day & having these awesome live cds over the past year or two have been such a big help.

Just a word of warning to any of you who don't know what some of this stuff does - it's cool to play & learn, but don't be stupid.  ettercap alone is enough to fsck an entire network.

---

### Post by ifishfortorque on 2006-07-31
hping3
ngrep
nmap (obvious, but more powerful than you think)
ettercap

The four of these and a willingness to learn will get you a long way.  

Matt

---

### Post by sl_4ck on 2006-08-05
NMAP - Network mapping utility used for port scanning and fingerprinting.
Ethereal - Excellent packet sniffer and analyzer.
Ettercap - Packet sniffer, with arp poisoning.
Kismet - Wireless network detector
Aircrack - Used for testing wireless network security.
Firestarter - Firewall (personal)
IPCop - Firewall distribution (larger scale).
John the Ripper - Used for testing password strength.

---

### Post by Soap_Dude on 2006-08-06
What about intrusion prevention, like IP ban and stuff?

---

### Post by Cyraxzz on 2006-08-08
what about programs for eavesdropping? i would like to try that on my system.

---

### Post by Gouki on 2006-08-21
> **Soap_Dude said:**
> What about intrusion prevention, like IP ban and stuff?

DenyHosts is very good.
Snort - It's an IDS, but if I recall right, it can be active.

> **Cyraxzz said:**
> what about programs for eavesdropping? i would like to try that on my system.

WireShark (previously Ethereal)

---

### Post by talrasha on 2006-08-21
> **word_virus said:**
> If you have the bandwidth, try downloading a copy of Knoppix-STD (Security Tools Distribution).  It's a Knoppix-based LiveCD that includes a plethora of open-source security and intrusion-detection utilities; password crackers, packet sniffers, port scanners, WEP crackers, encryption utilities, firewall and anti-virus software, etc. etc. 
You can get it at [www.knoppix-std.org](www.knoppix-std.org)

Since it's Knoppix, it's usefulness extends into other realms as well, making it an ideal tool for data-recovery and virus scanning on Windows boxes.  Check out O'Reilly's excellent "Knoppix Hacks" for more information on the subject.
[http://www.oreilly.com/catalog/knoppixhks/index.html](http://www.oreilly.com/catalog/knoppixhks/index.html)

If you're looking for some tools to run on your ubuntu system here are a few of my favorites, most of which are a quick "apt-get" away if you've enabled the universe repository; keep in mind this list reflects a high personal bias and should by no means be considered definitive:

packet-sniffing: Ethereal
port scanning:  Nmap
network visualization:  Etherape
password cracking: l0phtcrack
wep cracking: airsnort
wardriving: kismet
firewall: Firestarter
antivirus: clamAV
encryption: GnuPG

Hope this helps!


Yeah! And I believe that Knoppix was built for hacking :-D  lol

---

### Post by fk4n on 2006-09-06
there are losts tools on [www.icewalkers.com](www.icewalkers.com)

---

### Post by dolphinsonar on 2006-09-21
I installed airsnort, but its not on any menu in the GUI.  Is it command line only?  How do I run it to get online at the local cafe?

---

### Post by alex_fiberd on 2006-09-25
[FONT="Verdana"]PLease OAKS... Go to this link instead of Knoppix-STD (STD--hahahh)

[www.remote-exploit.org](www.remote-exploit.org)

Download Backtrack...

For security analysis.....

When is Ubuntu going to launch a Penetration version of ubuntu linux.. Cause my ubuntu6 is running smoothly with no probs.. Anyone keenz to develop an MONO distro with mono applications... Cause JSCript.net/C#.net/ RULE on linux with no problems.. Except API functions buggy...

Chaos[/FONT]

aKa_aLeX:-D :-k [-( :confused: ](*,)

---

### Post by Da Choice on 2006-10-14
If I wanted to prove once and for all to my LANing buddies that Linux > Windows in security in a practical way, what tools should I use? How should I use them? What should I do? 

I don't *need* to do anything malicious to their systems, just enough to prove that they need to use firewalls =)

P.S. If you are unconfortable posting it here, PM me.

Edit: Metasploit looks perfect for this sort of thing, but I can't seem to ge t it working. I've downloaded the latest version, but how do I run it? Whenever I try and run it in the terminal it closes immediately. Help for teh n00b please?

---

### Post by Chayak on 2006-10-15
TrueCrypt is a great encryption program for creating encrypted volumes, open source and trusted.
[http://www.truecrypt.org/]("http://www.truecrypt.org/")

---

### Post by nixios on 2006-10-16
check [www.nubuntu.org](www.nubuntu.org) its also a live CD like knoffix-STD.

---

### Post by 454redhawk on 2006-11-10
> **Da Choice said:**
> If I wanted to prove once and for all to my LANing buddies that Linux > Windows in security in a practical way, what tools should I use? How should I use them? What should I do? 

I don't *need* to do anything malicious to their systems, just enough to prove that they need to use firewalls =)

P.S. If you are unconfortable posting it here, PM me.

Edit: Metasploit looks perfect for this sort of thing, but I can't seem to ge t it working. I've downloaded the latest version, but how do I run it? Whenever I try and run it in the terminal it closes immediately. Help for teh n00b please?

I like to show people how I can change their admin windows password loginto THERE own account, setup  MY OWN account and password then logout and restore there password then login with my newly created admin account. All without them knowing it ever happened if I wanted to.

Tools

bootable USB flash drive or CD
Slax popcorn
NTFS-3g
chntpw

Boot the computer with the above mentions disk.
mount the drive with NTFS-3g
copy the SAM SECURITY & SYSTEM files to a temp dir.
run chntpw and blank the admin password
reboot into windows admin with no password
create your new admin account
reboot the flash drive
restore the old password by copying the SAM SECURITY & SYSTEM files back to original location
reboot windows with YOUR new admin account.

I wrote a script that does it all for you and only takes a min or two.

---

### Post by meyrd on 2006-11-18
This is pretty good too.

[http://www.linux-forensics.com/](http://www.linux-forensics.com/)

---

### Post by RjBanker18 on 2006-11-20
Heres a good one I found.  "Top 100 list of security tools" + paragraph sized descriptions of them.  I've found alot of these in the repositories.  Have fun!
[http://sectools.org/]("http://sectools.org/")

---

### Post by Patrick-Ruff on 2006-12-23
can someone /please/ edit the first post to make it easier on everyone? I don't think anyone wants to read 7 pages just to find some good tools.

---

### Post by fakie_flip on 2007-03-04
> **jbh said:**
> get nessus and nmap. nessus is great, I found out by running it against a work server the sql password was blank, and there were dozens of open ports that should've been filtered

There's also [http://www.phrack.org/](http://www.phrack.org/) and 2600 magazine.

I tried nessus, but it was taking an extemely long time to finish scanning a host. Did it work good for you?

---

### Post by SjRaptor on 2007-03-16
Just adding a couple that haven't been mentioned yet..

[tcptrace](http://www.tcptrace.org/) - Analyze information from input files of several different packet capture tools and output statistics and graphs
[NetDude](http://netdude.sourceforge.net/) - Edit trace files and packets headers
[Tcpreplay](http://tcpreplay.synfin.net/trac/) - Allows you to 'replay' saved packet capture files

---

### Post by alamba on 2007-03-21
I'm surprised PHLAK hasn't been mentioned yet: [http://www.phlak.org/modules/news/](http://www.phlak.org/modules/news/)

A

---

### Post by Selmer79 on 2007-05-13
IPTraf!
([http://iptraf.seul.org/](http://iptraf.seul.org/))
Excellent, easy to use network traffic monitor.

Also, Audit no longer exists.. It's merged with Whax to make BackTrack ([http://remote-exploit.org/backtrack.html](http://remote-exploit.org/backtrack.html))

---

### Post by ICUR2Ys on 2007-05-23
unfortunately PHLAK development has stopped.

dace

---

### Post by netlogic on 2007-06-11
1. BackTrack
2. Operator
3. PHLAK
4. Auditor
5. L.A.S Linux
6. Knoppix-STD
7. Helix
8. F.I.R.E
9. nUbuntu
10. INSERT Rescue Security Toolkit
11. knoppix-nsm
12. NST
13. Pentoo
14. Phlak
15. WarlInux
16. wHOOPIX
17. plac
18.sentinix
19.frenzy

Backtrack is my favorite

---

### Post by telmo on 2008-01-22
[Protech]("http://techm4sters.org") based on Ubuntu...

---

### Post by hackertarget on 2008-03-17
Free online scanning options (nessus, nmap, nikto and sqlix).

All open source all quality. Ok so some of our scanning servers are running Centos - but I am looking at moving all to Ubuntu one of these days.  :)

Link is in the sig.

---

### Post by gg234 on 2008-04-23
here is big security tool list with installation instructions [http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html)

---

### Post by rodneyaltam on 2008-04-30
Bro;

If you want a CD based security tool then Backtrack Security Suite is the best fit. It is a Live CD Distro. This is for checking the security of the server.

Please see the link below.....

[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1212195,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1212195,00.html)

---

