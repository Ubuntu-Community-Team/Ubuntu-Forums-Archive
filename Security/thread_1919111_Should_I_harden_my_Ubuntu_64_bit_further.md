---
title: "Should I harden my Ubuntu 64 bit further?"
date: 2012-02-02
forum: Security
---

### Post by Welly Wu on 2012-02-02
Hi. I installed Ubuntu 11.10 64 bit using the alternative installation .ISO file which I burned to a CD-R disc. I setup a custom installation using full disk encryption using LUKS/LVM (AES-CBC mode 256 bits SHA-256 hash algorithm). I also set a unique, strong, complex passwords for my home directory and LUKS/LVM at boot-up.

I opened up the BASH terminal and I typed in chmod 700 $HOME this morning.

I have not setup custom AppArmor profiles or HIDS / NIDS such as Snort yet. I am still reading the stickies to learn more information before I make that decision.

Which gets me to my point: should I harden my Ubuntu 64 bit by carefully following the stickies?

I have an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 PC-8500 SDRAM and an Intel 2nd Generation 2.5" 34nm MLC NAND FLASH X25-M 160 gigabyte Solid State Drive. I replaced my previous operating system which was Microsoft Windows 7 Ultimate 64 bit with Ubuntu 11.10 64 bit as my sole operating system of choice less than three weeks ago.

I have an unencrypted /boot partition of 250 megabytes.
I have an encrypted / root partition of 10 gigabytes.
I have an encrypted /home partition of approximately 130.00 gigabytes and I set a unique, strong, complex password using encryptfs because Ubuntu prompted me to set my password after I installed my operating system and I logged into my user account the first time.

I use my computer and Ubuntu 64 bit to surf the Internet, read and write e-mail messages, chat with my online friends in real time, use social media including Facebook, Twitter, Google+, LinkedIn, YouTube, etc, copy and convert my 1,100+ CDs to .FLAC lossless audio files, rip and copy encrypted DVD-Videos that I purchased, watch movies, TV shows, videos, and listen to music. I also write documents using LibreOffice Writer quite heavily. I read documents such as digital magazines, e-books, Adobe .PDF files, etc.

I don't use my computer or Ubuntu to hack into other people's servers or computers and I do not code my own software projects. I am teaching myself how to code in C++, but I just started a few weeks ago so I am a beginner.

I use TrueCrypt to secure my data on removable storage devices such as my Seagate FreeAgent Desk 1.5 terabyte USB 2 external hard disk drive and my Kingston DataTraveler HyperX 128 gigabyte Super Speed USB 3 thumb drive using AES-XTS mode 256 bits with SHA-512 hash algorithm.

Do I need to go further to harden my Ubuntu 64 bit?

Should I install a HIDS and NIDS such as Snort?

Should I create custom AppArmor profiles for frequently used software applications that can access the Internet such as Google Chrome and Mozilla Thunderbird?

Do I need to install my own hardened kernel which requires me to update and patch it on my own?

I feel a lot safer and more secure using Ubuntu 64 bit with full disk encryption even though I know that once I put in my passwords and mount my drives, I am open to attacks.

I check my hardware firewall logs for suspicious activities and unknown users trying to connect to my home network daily. I use WPA2 AES-TKIP to secure my wireless network with MAC authentication for every wireless device.

I also installed Bitdefender for Unices with a free 1 year license and I scan my computer and storage devices daily.

I use Deja Dup to backup my data and I encrypt it using GPG and a unique, strong, complex password.

How much farther should I go to harden my Ubuntu system? Is it really necessary given my usage scenarios?

I rarely take my ASUS N61JV-X2 notebook PC outside of my home. I have Verizon FiOS fiber optic high speed Internet and TV at home.

What do you recommend? Why?

---

### Post by Welly Wu on 2012-02-02
I also set Ubuntu to lock my screen with my user password every 2 minutes or I manually lock it even when I leave my bedroom every time.

---

### Post by Welly Wu on 2012-02-02
I use KeePass2 with a unique, strong, complex password to store my user IDs, passwords, and other login credentials. I have a LastPass Premium account and I store my online login credentials separately from KeePass2 which I use for offline stuff like local passwords. I use the two-factor Sesame authentication with LastPass Premium and my web browsers.

I use Google Chrome all of the time as my primary web browser.

I setup two-factor authentication for my Google account and Facebook account and HTTPS connections are enabled by default.

I know how to select unique, complex, random, strong passwords. I never reuse old passwords. I never use the same IDs and passwords for multiple accounts or encrypted storage devices either.

---

### Post by Welly Wu on 2012-02-02
I am reading the UFW firewall sticky and I plan to deny in and restrict out to essential ports for services later today.

---

### Post by Ms. Daisy on 2012-02-02
Seems like you might benefit from reading the basic security wiki:
 
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
 
But to answer a couple of your questions, yes. The Apparmor, security & firewall stickys are good to follow.

---

### Post by Welly Wu on 2012-02-02
I saved that wiki so that I can read it offline. I am following some of the recommendations on the wiki, but I have not worked on ufw firewall, Snort, or NIDS. I don't use Mozilla Firefox; I use Google Chrome so some of the add-ons do not exist yet. Accuvant Labs did a research paper looking into the anti-exploitation technologies for all three of the major web browsers using Microsoft Windows as one of their test operating systems and they concluded that Google Chrome scored the highest in terms of anti-exploitation technologies including JIT hardening and sandboxes.

There is a discrepancy between the wiki and the stickies. The stickies seem to cover more advanced topics which are not included in the wiki like Snort.

Thank you for providing a link to that wiki. I have a lot of reading and thinking to do before I decide to harden my Ubuntu 64 bit this weekend.

---

### Post by Welly Wu on 2012-02-02
Ms Daisy,

You are one of the authors of the wiki. Thank you.

---

### Post by Ms. Daisy on 2012-02-02
> **Welly Wu said:**
> There is a discrepancy between the wiki and the stickies. The stickies seem to cover more advanced topics which are not included in the wiki like Snort.
 
The discrepancy is purposeful. The basic security wiki is aimed at first-time linux users. And it wasn't meant to be redundant, so I'd recommend reading the stickies as well.
 
I don't think it really matters which browser you use, but I would recommend that you try to limit scripts in any of them.  I'm pretty sure the equivalent to noscript in Chrome is called Notscript.

---

### Post by haqking on 2012-02-02
Google chromes sandbox was exploited a while ago now though fixed after version 15.xxx or somit or other.

And as Ms Daisy said NotScript is the chrome alternative to NOScript.

Most of your security measures are valid though some are locally based preventative measures for physical access.

For remote security hardening then as you mentioned strong firewall rules both inbound and outbound (refer to the links on the basic security wiki for guides)

UFW is an interface to the Linux firewall Netfilter, interacted with through IPTables directly or UFW as a CLI altrernative or GUFW which is a GUI for UFW, there are also some others but they all use IPTables/Netfilter.

Apparmor to control your applications/ and or SELinux

Most exploits these days on a Linux box are browser based, SSH or running weak services such as VNC (dont run VNC over the internet directly)

Dont do things/log on as root and dont give authorisation for root/sudo actions unless you know you want to authorise them

Read the Wiki and its links and the stickies then come back with more specific questions to suit your services and such like.

Peace

---

### Post by Welly Wu on 2012-02-03
I chose to install Firestarter as it is a bit easier than gufw. I configured it to deny all incoming traffic and I configured it to be restrictive by default to whitelist traffic set by my rules. I opened up some common ports such as 80 for http traffic and a couple of other ones that I know that I will need. I read through the firewall sticky and I have to re-read it again as it is kind of complex for a new Ubuntu user like myself.

---

### Post by haqking on 2012-02-03
> **Welly Wu said:**
> I chose to install Firestarter as it is a bit easier than gufw. I configured it to deny all incoming traffic and I configured it to be restrictive by default to whitelist traffic set by my rules. I opened up some common ports such as 80 for http traffic and a couple of other ones that I know that I will need. I read through the firewall sticky and I have to re-read it again as it is kind of complex for a new Ubuntu user like myself.

Funnily enough when i wrote my post i purposefully missed out firestarter as it is out of date and buggy and not recommended to be honest.

Also it needs to be removed if you want to use UFW/GUFW as they conflict.

When you say you opened up the ports such as port 80 cos you know you will need it, you mean you will be running a web server ?

if not then you dont need to, only allow ports for services you know you will be running.

also read these as they are easy to understand and cover everything you need to know at this point

[do you need a firewall]("http://ubuntuforums.org/showthread.php?t=1871177")

[setting up a firewall in ubuntu using 3 different methods]("http://ubuntuforums.org/showthread.php?t=1876124")

Cheers

---

### Post by Welly Wu on 2012-02-03
I removed Firestarter and I installed gufw. I set it up to deny all in and all out. I also set some specific traffic to be allowed to go out:
Http 80
https 443
IMAP 143
NTP 123
POP3 110
SMTP 25
BitTorrent 6881:6889
Pop3s 995
Https 8080
SSH 22
FTP 20-21
Google 587,993
Irc 667:7000
DNS 53
DHCP 67-68

How does it look now?

---

### Post by haqking on 2012-02-03
> **Welly Wu said:**
> I removed Firestarter and I installed gufw. I set it up to deny all in and all out. I also set some specific traffic to be allowed to go out:
Http 80
https 443
IMAP 143
NTP 123
POP3 110
SMTP 25
BitTorrent 6881:6889
Pop3s 995
Https 8080
SSH 22
FTP 20-21
Google 587,993
Irc 667:7000
DNS 53
DHCP 67-68

How does it look now?

if they are what you need then i guess so, i dont know what you need ;-)

Best to deny all and then allow as you find something not working or you may be letting things which dont necessarily need to be.

Have you allowed UDP for DNS aswell as TCP and same for DHCP?

Do you need IMAP as well as POP ?

I mean i dont know what services you require so cant really say

---

### Post by Welly Wu on 2012-02-03
I just added UDP for DNS right now and I reloaded my firewall rules. Thanks for the tip.

It seems that my list of TCP and one UDP ports is correct because I am able to get access to the Internet through all of my usual software applications. I am not having any problems connecting to the Internet or remote networks that I frequently need access to so far.

Thank you for your help so far.

I will work on HIDS and NIDS and AppArmor this weekend. I am going to be out of my home for most of the day today so I don't have an opportunity to read wikis and stickies to harden my Ubuntu 64 bit.

---

### Post by haqking on 2012-02-03
> **Welly Wu said:**
> I just added UDP for DNS right now and I reloaded my firewall rules. Thanks for the tip.

It seems that my list of TCP and one UDP ports is correct because I am able to get access to the Internet through all of my usual software applications. I am not having any problems connecting to the Internet or remote networks that I frequently need access to so far.

Thank you for your help so far.

I will work on HIDS and NIDS and AppArmor this weekend. I am going to be out of my home for most of the day today so I don't have an opportunity to read wikis and stickies to harden my Ubuntu 64 bit.

cool no worries.

however like i said, just because things work doesnt mean you need them all, only allow what you actually need.

I mean you only need IMAP and POP if you access a POP account as well as a IMAP account, you only need FTP if you use it, you only need SSH if you use it and so on.

Best of luck

Peace

---

### Post by Welly Wu on 2012-10-13
I had to return to this thread to get more help.

I replaced my ASUS N61JV-X2 notebook PC with a new System76 Lemur Ultra Thin (lemu4). I am using Ubuntu 12.10 64 bit Beta 2.

I installed rkhunter, chkrootkit, tiger.

Do I need to install ninja when the root account is disabled by default?

I enabled ufw and I installed GUFW. This time, I am not running any type of host server like Samba Server. I have nothing listed in GUFW and I don't want to restrict outgoing traffic because I use a lot of software applications that depend upon different ports and protocols and it would be too difficult to keep updating my GUFW list on a daily basis. I use BitTorrent, Firefox, Thunderbird, WiTopia Personal VPN PRO using OpenVPN, CISCO IPSec, IRC, Empathy, etc.

I minimized the number of PPAs that I added and use. I have the official System76 PPA for the device driver and that's it. I deleted BitDefender and I deleted the unofficial handbrake PPAs. I also deleted Handbrake. I am using the official and partner repositories by default. It's going to stay this way for years to come in the future.

I am thinking about adding custom Novell AppArmor profiles for Mozilla Firefox and OpenJRE/JDK 7 and its associated programs like mplayer, etc:

[http://rookcifer.blogspot.com/2012/09/custom-firefox-apparmor-profile-for.html](http://rookcifer.blogspot.com/2012/09/custom-firefox-apparmor-profile-for.html)

[http://rookcifer.blogspot.com/2012/10/more-apparmor-profiles-for-ubuntu-1204.html](http://rookcifer.blogspot.com/2012/10/more-apparmor-profiles-for-ubuntu-1204.html)

Otherwise, I wanted to know if this will be sufficient for a full-time Ubuntu user like myself. I am thinking that these additional steps are enough.

I connect to WiTopia Personal VPN PRO most of the time: [http://www.witopia.net](http://www.witopia.net) even while I am at home on my Verizon FiOS Internet service.

I have full-disk encryption using dm-crypt and LUKS.

I think that this should be enough for my needs.

Do I need to install a file integrity checker like aide or tripwire?

Should I install and run Bastille?

What do you recommend?

---

### Post by Welly Wu on 2012-10-13
This time, I wanted to focus on security that makes sense to me. I don't want to go overboard by installing all of the security tools and configuring everything by hand.

In light of this preference, what do you recommend that I consider to harden my Ubuntu 64 bit?

---

### Post by coldraven on 2012-10-13
Not so much for security but more for privacy I run Firefox with AdBlockPlus, NoScript and Ghostery add-ons.
If I go to a web-site and let NoScript "temporarily allow all" then Ghostery will pop up with lots of blocked trackers. Sometimes about 20 of them!
Mozilla  have an experimental add-on called "Collusion", if you run that you will soon do as I do. 
[https://www.mozilla.org/en-US/collusion/](https://www.mozilla.org/en-US/collusion/)
Don't get paranoid but they **are** watching you :)

---

### Post by BrandonIngalls on 2012-10-15
I am currently working on a tutorial for setting up a fully encrypted ubuntu setup. I see your method is close to mine -- the only difference is I have my boot partition on a flash drive around my neck at all times. Along with my YubiKey, I would recommend buying a YubiKey to use with your LastPass account. A YubiKey is a usb OTP generator, it has two configurable slots you could have one that sends a static password and another that sends a OTP.

Here is a paper they have on using the static password with truecrypt, 
[http://static.yubico.com/var/uploads/pdfs/TrueCrypt%202011-03-23.pdf](http://static.yubico.com/var/uploads/pdfs/TrueCrypt%202011-03-23.pdf)

If you bought a YubiKey you could set it up to have a 64 digit random password that is unknown to you if you want and then change your password to use that aswell -- think of it like a salt in a hashing function...
Say your old password was cat...
you change it to catfFEFHjhCjnmPEsTX5aLaJ3T8aWb9UOWF4YKXH5cY9TqSjhpCpiC35G7JDPxgWe8k

As long as you have your /home partition encrypted and have your home folder encrypted with ecryptfs as well you should be set...

Also every few months clean junk files with bleachbit, then migrate all your files to a new user account,
sudo adduser username2 --encrypt-home
then rsync your old files into the new user and shred the old ecryptfs password files...
shred -fun1 /home/.ecryptfs/user1/.ecryptfs/*
or something like that.

---

### Post by Welly Wu on 2012-10-15
I have two Yubico Yubi keys with my LastPass Premium account.

---

### Post by Magnetizer on 2013-01-11
In addition to NoScript and Ghostery you can make use of a restrictive hostsfile.

I wrote a script to automatically set up a hostsfile consisting of several well-known blacklists (like [www.someonewhocares.org](www.someonewhocares.org))

You can add more blacklists to the script if you like, or blacklist, whitelist some hosts yourself. Sometimes it is too restrictive, so you will need to whitelist some hosts (e.g. dropbox.com)

At this moment I block around 300.000 hosts and the script works fine. I get an update nearly every day.

If you want to make use of the script, it is in this thread:

[http://ubuntuforums.org/showthread.php?t=2048812](http://ubuntuforums.org/showthread.php?t=2048812)

---

### Post by Toriku on 2013-01-11
thats cool, I'm trying to bolster security on an Ubuntu server atm, one program I implemented the other day was called "deny hosts" [http://denyhosts.sourceforge.net/]("http://denyhosts.sourceforge.net/").

 It allows you to keep the port for ssh open, but filter out brute force attacks; if you use ssh to access your computer remotely it could be very useful to you, but if you don't then its probably not much use...

 I want to get my Ubuntu server (which among other things) provides DNS to a network of computers, and I want to use host file style protection from undesirable websites much like your script; however I'm trying to get all the computers on this network to use the same hosts file to make it easier to control (the computers on the network include Windows, Mac and Linux machines)

---

### Post by CharlesA on 2013-01-11
> **Toriku said:**
> I want to get my Ubuntu server (which among other things) provides DNS to a network of computers, and I want to use host file style protection from undesirable websites much like your script; however I'm trying to get all the computers on this network to use the same hosts file to make it easier to control (the computers on the network include Windows, Mac and Linux machines)

You wouldn't need to mess with hosts files if you are handling DNS. You could write a script to put DNS entires for anything on the blacklight, or you could just forward external DNS requests to something like OpenDNS, which has filtering capabilities.

---

### Post by Toriku on 2013-01-11
> **CharlesA said:**
> You wouldn't need to mess with hosts files if you are handling DNS. You could write a script to put DNS entires for anything on the blacklight, or you could just forward external DNS requests to something like OpenDNS, which has filtering capabilities.

wouldn't I have to make a domain zone for each entry?

---

### Post by CharlesA on 2013-01-11
> **Toriku said:**
> wouldn't I have to make a domain zone for each entry?
No idea.

It would likely be easier to forward external DNS lookups to [OpenDNS]("http://www.opendns.com/business-solutions/premium-dns/benefits/"), than trying to come up with a homebrew solution.

---

