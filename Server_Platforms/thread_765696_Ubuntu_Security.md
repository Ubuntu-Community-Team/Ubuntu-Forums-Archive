---
title: "Ubuntu Security"
date: 2008-04-24
forum: Server Platforms
---

### Post by LaRoza on 2008-04-24
*Written by: bodhi.zazen*

[center][img]http://www.sompy.com/gr/oriental/yinyang01/yinyang01400.jpg[/img]


[size=8]**Ubuntu Security[/size]**[/center]


I am writing this guide as a concerned member of the Ubuntu Community. Security is a concern for us all and in welcoming new (and experienced) users to Ubuntu I would like to demystify the complexities of security that come with your new OS.

[color=darkred]_Disclaimer_ : I am not an expert in security. This document is intended as a security overview for new users. This thread is not intended as an all inclusive how-to or discuss the merits of any particular security measure. I offer no guarantee that by running Ubuntu with any or all of these suggestions your security will be foolproof or that you will never be cracked.[/color]

I would like to direct any general security discussions to the [Servers & Security](http://ubuntuforums.org/forumdisplay.php?f=7) and any comments on this introductory sticky [here](http://ubuntuforums.org/showthread.php?t=510792).

I would like to thank the Ubuntu Staff, especially [color=darkred]jdong[/color] and [color=red]compiledkernel[/color] for their review and suggestions.


**_Introduction_ **: Security is an ongoing process and, like an onion, it has layers and stinks. The best defense you have is to read and learn how to secure your OS.

Alas, there is not single action you can take to achieve absolute security (the only safe computer is one that is turned off, disconnected from the Internet, and in a locked vault) and security concerns and "ease of use" are sometimes competing concerns.

_Clarification of terms_:

The "_Windows Mindset_" is intended as exactly that. I assume most new users are coming from Windows and the issues under this section are both most familiar to them and areas of FAQ on the forums (how often do we see questions from the "Ubuntu Mindset" on ABT?).

The "_Ubuntu Mindset_" is thus likely new information for most new users.

*Those divisions/titles are intended to divide security information into familiar/unfamiliar territory (assuming the reader comes from a windows background) or to lighten up an otherwise dry topic. Specifically it is my intention that the "windows mindset" will help users new to Linux (Ubuntu) feel more at home by starting with familiar themes. These titles or divisions are certainly not intended to convey more or less importance to any particular issue, those decisions I leave for "self determination".*


**_Summary**_: There is no such thing as "security in a box (tm)". Information security is an active job -- it is not installing some product on the system and sitting back and relaxing.

[center]The good news ~ Ubuntu (Linux) is fairly secure "out of the box".[/center]

_**How to proceed_**: Prepare to read, read, read ... do not expect to get through this document in one session.

**Contents**:

> 1. Intro
[indent]Basics[/indent]

2. Windows mindset
[indent]Antivirus
Firewall
Wireless Security
Adware[/indent]

3. Ubuntu mindset
[indent]Permissions and Encryption
Root kits
Intrusion detection
compiledkernel's suggested applications
Secure servers
Hardened kernels
Logs
How to perform a hardened installation
Screening your system for potential security holes[/indent]

4. Forensics

5. References



[center][size=6]**Basics [/size]**[/center]


This advice is fairly generic and applies to almost any OS. These simple steps offer a solid foundation that you should be able to implement almost immediately.

[list][*]Enforce strong passwords [http://en.wikipedia.org/wiki/Password_strength](http://en.wikipedia.org/wiki/Password_strength)
[*]In general, do not write your passwords down, and if you must, keep them in a secure place (Do not put them on a sticky note attached to your monitor for example).
[*]Limit root access (Do not log in or run programs as root). Ubuntu accomplishes this by locking the root account and the use of sudo.[list]Consider creating an account without sudo access for "daily use".[/list]
[*]Physical access (physical access = big security hole). Physical access allows root access to your system (via a live CD if necessary).
[*]Do not install software or add repositories from untrusted sources (See also "Social engineering" below).
[list][*]This includes running scripts that modify your /etc/apt/sources.list Take care not to let the "need" to run the newest/latest/greatest compromise security.[/list]
[*]Likewise, do not run code or enter commands into the terminal from untrusted sources. If you are unsure of what a command might do best do a google search first.
[*]Keep your system up to date. Updates, particularly security updates, bring you the newest and latest fixes.
[*]If you run a server, it is your responsibility to learn how to secure it.[/list]

[Psychocats ~ Security on Ubuntu](http://www.psychocats.net/ubuntu/security)

[color=blue]Thanks to Johan! for the advice on 3rd party repos[/color]

_Note_: Social Engineering. Click [here](http://www.securityfocus.com/infocus/1527) for more information.

> **Social engineering** is a collection of techniques used to manipulate people into performing actions or divulging confidential information.[1] While similar to a confidence trick or simple fraud, the term typically applies to trickery for information gathering or computer system access and in most cases the attacker never comes face-to-face with the victim.

[indent]~ *Quote from Wikipedia*[/indent]



[color=blue][center][size=6]**The Windows Mindset **[/size][/center][/color]


If you are coming from a windows background you are used to terms like antivirus, spyware, and firewalls. Linux is different and these are not as important. They are discussed first because these are FAQ on the forums. Unfortunately, it is sometimes difficult for new users to wade through some of the FUD (some of which is produced by anti-virus companies) ...


**[size=4]_Viruses_[/size]**

The fact of the matter is: viruses/worms take advantage of flaws or holes in the code. At this time of this writing, there are no significant Linux viruses "in the wild". Linux boxes are no less targets than any other OS, many of the large (ie valuable) Internet sites run on *nix so there is no lack of motivation to crack into *nix. 

Do not believe the suggestion that the Linux community is complacent or "behind the times" in terms of viruses, or any other security issue. Linux developers have not "ignored" viruses, rather the OS is built to be highly resistant to them and since the code is "Open" there are literally thousands of eyes watching ... 

This is an example of what it would take to install malware on an Ubuntu box : 

[Install evilmalware](http://www.gnu.org/fun/jokes/evilmalware.html)

(Don't worry, that link will NOT install anything :twisted: )

For the most part, Linux anti-virus programs scan for Windows viruses which do not run on Linux, even on wine ([http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)). Anti-virus programs are "reactive" in that they can only protect you from known viruses. They can only protect you against the next Linux virus *after* it is developed, not before. Furthermore the "fix" will be to close any hole(s) in the code, *these fixes will be available through security updates* (which are more frequent in Linux then your previous OS if you are coming from Windows). 

My advice is to skip the anti-virus if you run Ubuntu. Why ? [list=number][*]They scan primarily for Windows viruses.[*]There is a high rate of false positives.[*]Isolation/inoculation is poor.[*]And currently there are no known active Linux viruses (so there is essentially nothing to detect).[/list]

Running antivirus can make some sense if you are intending to "protect" windows users, however, IMO, for a variety of reasons, it is best if Windows users learn to protect themselves. In fact the most common usecase for a Linux antivirus program is to run a Windows fileserver or serve mail to Windows clients.

_Note_: There have been many documented cases in Windows and Linux that a buffer overflow in an antivirus product has been an attack vector!

If you would like to run an antivirus program on Ubuntu you have several choices :

[list][*][http://doc.gwos.org/index.php/How_to_ClamAV](http://doc.gwos.org/index.php/How_to_ClamAV)
[*][http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)
[*][http://www.pandasoftware.com/download/linux.htm](http://www.pandasoftware.com/download/linux.htm)
[*][http://www.centralcommand.com/linux_server.html](http://www.centralcommand.com/linux_server.html)
[*][http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)[/list]


**[size=4]_Firewall_[/size]**

Discussions about firewalls often are passionate (just search the Ubuntu forums). By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens **zero** ports to the outside world, so a firewall is redundant. However, installing "server software" will cause ports to open, so some people like to use a firewall as a catch-all layer to find mistakes in their configuration.

Another use for firewalls is for the administrator to forcibly impose network policies on the user. For example, users may not talk to example.com, open up a listening port for remote connections, and so on.

Also, a periodic audit of the system for open ports is a good practice. For example, running the "nmap" command from another machine, or using one of many online port scanners:

[http://nmap-online.com/](http://nmap-online.com/)
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Remember, what you care about are open ports. Closed ports and stealth ports are equally secure, in that they are inaccessible to the public.

_**Iptables references_** :
[list][*][https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[*][http://www.linuxguruz.com/iptables/howto/](http://www.linuxguruz.com/iptables/howto/)
[*][http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)
[*][http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/security-guide/s1-fireall-ipt-act.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/security-guide/s1-fireall-ipt-act.html)
[*][https://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/ref-guide/ch-iptables.html](https://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/ref-guide/ch-iptables.html)
[/list]

The "problem" is iptables is not so new user friendly. Fortunately, there are several more (new) user friendly interfaces available to allow you to manipulate your firewall (Firestarter and Guarddog are both GUI front ends for iptables) :

[list][*][Firestarter](http://www.fs-security.com/) is one of the most popular GUI front ends.
[indent][How to Firestarter](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)
**Default Firestarter Policies**:
> [list][*]New inbound connections from the Internet to the firewall or client hosts are blocked.
[*]The firewall host is freely allowed to establish new connections.
[*]All client hosts are allowed to establish new connections to the Internet, but not to the firewall host.
[*]Traffic from the Internet in response to connection requests from the firewall or client hosts is allowed back in through the firewall.[/list]

This policy allows normal Internet usage such as web browsing and e-mail on the secured hosts, but blocks any attempts to access network services from the outside and shields the local network.[/indent]
[*][Guard dog](http://www.simonzone.com/software/guarddog/) uses the KDE libraries.
[indent][Guarddog Online Guide](http://www.simonzone.com/software/guarddog/manual2/index.html)[/indent][/list]

A source of confusion sometimes occurs when users feel the need to be running firestarter/Guarddog for their firewall to be active. **This is untrue !** Keep in mind that these applications are not firewalls, but rather configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest :twisted:. 


**[size=4]_Wireless Security ~ WPA1, WPA2, LEAP, etc._[/size]**

Wireless connections are becoming ever more popular. Half the battle is to get your hardware working :lolflag:

Next be sure to secure your wireless router as much as possible (IMO wireless will always be less secure ... )

[[color=red]wieman01[/color]](http://ubuntuforums.org/member.php?u=113534) maintains a very complete page on wireless security [Here](http://ubuntuforums.org/showthread.php?t=318539)


**[size=4]_Browser / Spyware : Java/Flash/Ad-ware/Trackers/Cookies_[/size]**

This is where most users will have the most risk. We all want Java/Flash, but our Internet browser opens us to attacks.

I advise :
[list=number][*]Deny all cookies and add trusted sites, allowing only for session.
[*]Install [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722). Again block all and add trusted sites to a white list.
[*]Install [Safe History](https://addons.mozilla.org/en-US/firefox/addon/1502)
[*]Adblocking : I block with a hosts file rather then [Adblock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865) or [Adblock Filterset.G](https://addons.mozilla.org/en-US/firefox/addon/1136) because a hosts file protects more then just firefox.
[list][*][http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)[*]Linux script : [http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)[/list][/list]

_Edit_: Thank you [color=blue]Seisen[/color] for pointing out that No Script also blocks flash.


See this link for additional information : [[color=blue]How to Secure Firefox[/color]](http://ubuntuforums.org/showthread.php?t=671604)


[center][size=6]**[COLOR="Sienna"]The Ubuntu Mindset[/COLOR]**[/size][/center]


**[size=4]_Permissions and Encryption_[/size]**

The first layer of defense is permissions. Permissions are used to set access and thus protect both system and user files.

[Basic permissions](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

See also **umask** at the bottom of that link. The umask value can be set in ~/.bashrc.

To set a "private home", as a user, ```
chmod 700 $HOME
```

[Sharing files in UNIX](http://hep.pa.msu.edu/user/groups.html)

Encryption is used as an additional layer of protection. One limit of encryption is that protection is only offered when mounting an encrypted partition (once the partition is mounted it is assessable/crackable just like any other file).

[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

[http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)


**[size=4]_Root kits_[/size] **

From [http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit) :

> The term rootkit (also written as root kit) originally referred to a set of recompiled Unix tools such as ps, netstat, w and passwd that would carefully hide any trace of the intruder that those commands would normally display, thus allowing the intruders to maintain root access (highest privilege) on the system without the system administrator even seeing them.

The term is no longer restricted to Unix-based operating systems ...

_Root kit detection_:
[rkhunter](http://rkhunter.sourceforge.net/)
[indent][http://wiki.linuxquestions.org/wiki/Rootkit_Hunter](http://wiki.linuxquestions.org/wiki/Rootkit_Hunter)[/indent]
[ckrootkit](http://www.chkrootkit.org/) 
[indent][http://www.howtoforge.com/howto_chkrootkit_portsentry](http://www.howtoforge.com/howto_chkrootkit_portsentry)[/indent]


**[size=4]_Intrusion Detection_[/size]**

_Note_: Adding an intrusion detection system like snort that analyzes network traffic for attack patterns, it can potentially introduce **additional vulnerabilities**. There have been documented examples of vulnerabilities in snort's preprocessor that granted hackers snort user, or even root user, access to the system!

My initial suggestions are [OSSEC HIDS](http://www.ossec.net/) and [Snort](http://www.snort.org/).

How to's:
[list][*][http://doc.gwos.org/index.php/OSSEC-HIDS](http://doc.gwos.org/index.php/OSSEC-HIDS)
[*][http://www.howtoforge.com/intrusion_detection_with_ossec_hids](http://www.howtoforge.com/intrusion_detection_with_ossec_hids)
[*][How to snort](http://searchsecurity.techtarget.com/general/0,295582,sid14_gci1083823,00.html)[/list]


**[size=4]_Compiledkernel's Suggested Applications_[/size]**

[color=red]compiledkernel's[/color] suggested applications (Nagios, ntop, and darkstat are in the Ubuntu Repositories, check the home page to see if newer versions are available):

[list][*][Nagios](http://www.nagios.org/about/) ~ A host and service monitor designed to inform you of network problems.


[*][ZenOSS](http://www.zenoss.com/product/core) ~ An open source IT monitoring product that delivers the functionality to effectively manage the configuration, health, performance of networks, servers and applications through a single, integrated software package.


[*][ntop](http://www.ntop.org/overview.html) ~ A network traffic probe that shows the network usage, similar to what the popular top Unix command does.


[*][darkstat](http://dmr.ath.cx/net/darkstat/) ~ A packet sniffer that runs as a background process on a cable/DSL router, gathers all sorts of statistics about network usage, and serves them over HTTP.[/list]


**[size=4]_Running Server(s)_[/size]**

Part of setting up a server is reading/learning how to secure it. Common servers include NFS, Samba, FTP, SSH, VNC, RDP, and HTTP. If the "how-to" you are following does not review security, you need to keep looking ...***"Desktops" become "Servers"*** if server software is installed.

_Questions to ask yourself include_:

[list=number][*]What port(s) or services does this software provide?
[*]Who will be able to connect to this? (i.e. is it restricted to a range of IP addresses Password protected?)
[*]What level of access will the visitor have to the system? (i.e. does the server run under a restricted user, or the root acount? What can this restricted user do in a worst case scenario?)
[*]Does this service expose any additional information that's useful to a hacker? (i.e. does it allow users to transmit their passwords in cleartext? Does it have a 'statistics' view that reveals logged-in users, ip addresses, network configuration, or other potentially helpful information?)
[*]What is the **security history** of this software? Does it have a long long history of vulnerability and patch after patch? Or has it had a relatively unmarred history?[/list]

Examples :

[SSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[UDSF Secure SSH](http://doc.gwos.org/index.php/SecureSSH)
[VNC](https://help.ubuntu.com/community/VNCOverSSH)
[Apache](http://www.howtoforge.com/apache_mod_security)


**[size=4]_Hardened Kernels_[/size]**

Hardened kernels are modifications to the Linux kernel that add additional security measures. This could include:

[list=number][*]The randomization of ports, memory addresses, process ID's, and other information that is typically predictable. This can thwart off many types of common attacks.
[*]Identify and prevent buffer overflow attacks from resulting in compromise by killing compromised processes (PaX bundled with grsecurity, or Redhat's Exec-Shield combined with prelink randomization). Edgy and higher contain GCC stack protection enforced in most applications, but is unable to respond to several kinds of attacks that a kernel-layer enforcer could. Likewise, PaX and friends have weakness that GCC stack protection helps cover, so the two work great as a duo.
[*]Hiding information that Linux usually allows everyone to see, including all running processes on the system, load averages, CPU info, IP addresses, etc. Obscuring this information can help keep attackers "in the dark" so to speak.
[*]More aggressive enforcement of buffer overflow protection than what Ubuntu's standard gcc stack protector can do.
[*]Adding additional restrictions on the capabilities of regular users that prevent channels of attack.
[*]Additional permissions systems that allow finer-grained tuning of various aspects of Linux.[/list]

These techniques combined have been shown to be very effective in the real world in guarding against unknown attacks. For example, many administrators of hardened kernel servers either report or even prove that their hardened systems were invulnerable to newly discovered security holes, or that the severity of a breach was significantly reduced.

The most common hardened kernel patch is called "grsecurity2" ([http://grsecurity.org/](http://grsecurity.org/)), which does everything on this list. This requires, however, that you manually patch and recompile the kernel. SELinux and [AppArmor](http://www.novell.com/linux/security/apparmor/overview.html) do the "additional permissions systems" part. The basic theory is that by providing finer definitions of permissions than UNIX users and the "chmod" bits, even a successful attack against one service is virtually useless to attacking the rest of the system.

_Note_: *AppArmor is available in Feisty (7.04) and will be installed by default in Gutsy, Ubuntu 7.10.*

_AppArmor Links_

[AppArmor ~ Ubuntu Community Wiki](https://help.ubuntu.com/community/AppArmor)
[[color=green]AppArmor Geeks (OpenSUSE)[/color]](http://en.opensuse.org/AppArmor_Geeks)

All of these hardened systems, however, take effort on the administrators behalf to implement. They also take a lot of trial-and-error to find the correct balance of user functionality and security restrictions. Tightening the rules too much could cause various applications to stop working, and not tightening them enough could lead to a weaker security setup.

If you run a large multiuser system where you must grant people shell access, or run services that have that unfortunate long history of attacks, then it is highly recommended that you look into setting up a hardened kernel.


**[size=4]_Reading the Logs_[/size]**

Learn how to read your system logs and become familiar with "normal" activity. It should go without saying,  your first introduction to system logs should *not* be when you suspect your system has been compromised.

You should also be aware that if someone has root access they can alter system logs. This is when it is most helpful to be aware of "normal" activity.

[Ubuntu wiki ~ Linux Log Files](https://help.ubuntu.com/community/LinuxLogFiles)

There is a package called "logwatch" that e-mails to you the new portions of your log every night. This can help make log reading more enjoyable.


**[size=4]_How to perform a hardened installation_[/size]**

This how to will walk you through a hardened install with an encrypted root partition and other goodies.

This is a link to a how to for Debian : 

[Towards a moderately paranoid Debian laptop setup](http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system)

You will need to use the "Alternate" install disk.

[How to Alternate Install](http://users.bigpond.net.au/hermanzone/)

*[color=blue]Thank you to Uwe Hermann for posting a How-to for the moderately paranoid and hermanzone for the How-to with the alternate CD*[/color]


**[size=4]_Screening your system_[/size]**

There is a package, tiger, which will screen your system for potential security holes. While not complete it may be an excellent place to start (tiger does not check your firewall for example).

For an overview of tiger see [man tiger](http://www.penguin-soft.com/penguin/man/8/tiger.html) , scroll to the bottom and you will see a listing and brief description of the tests performed (modules).

Install by any means, *tiger john chkrootkit*
```
sudo apt-get install tiger john chkrootkit
```

Run tiger from the command line with :
```
sudo tiger -H
```

The -H flag will produce a very nice HTML document.

The command tigexp can be used to explain the results.

> $ /usr/sbin/tigexp pass014w

The listed login ID is disabled in some manner ('*' in passwd field, etc),
but the login shell for the login ID is a valid shell (from /etc/shells
or the system equivalent).  A valid shell can potentially enable the
login ID to continue to be used.  The login shell should be changed to
something that doesn't exist, or to something like /bin/false.

Tiger should give you some ideas on things to research. As always there can be false positives so take care not to either panic or blindly make system changes without understanding what you are doing and how to undo your changes (ie make backups of system files before you edit them).


**[center][size=6]_Forensics_[/size][/center]**

What to do when you think you have been cracked :

[list=number][*]Power off.
[*]Disconnect/disable your Internet connectivity.
[*]Boot a live CD and image your hard drive (for analysis later).
[*]Re-install. Unfortunately there is no way to trust a compromised system.
[*]When you install, be sure to install off line, use a stronger password, and research intrusion detection.[/list]

_Intrusion References_
[CERT® Coordination Center ~ Steps for Recovering from a UNIX or NT System Compromise](http://www.cert.org/tech_tips/root_compromise.html)
[CERT® Coordination Center ~ Intruder Detection Checklist](http://www.cert.org/tech_tips/intruder_detection_checklist.html)


*Whew ...*


_[size=4]**Further Reading:[/size]**_

[Ubuntu wiki ~ Security page](https://help.ubuntu.com/community/Security)

[Ubuntu wiki ~ Installing Security Tools](https://help.ubuntu.com/community/InstallingSecurityTools)

[UDSF Security Analysis Tools](http://doc.gwos.org/index.php/SecurityAnalysis)

[The Big Ol' Ubuntu Security Resource](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

[Locking Down Ubuntu](http://www.linuxforums.org/security/locking_down_ubuntu.html)

[Ubuntu geek ~ Security category](http://www.ubuntugeek.com/category/security/)

[Security references](http://www.linuxquestions.org/questions/showthread.php?t=45261) Topics include Basics, firewall, Intrusion detection, Chroot, Forensics/Recovery, and Securing networked services.

~ Thank you to [color=blue]unSpawn[/color] at [LinuxQuestions.org](http://www.linuxquestions.org/)


Peace be with you,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

