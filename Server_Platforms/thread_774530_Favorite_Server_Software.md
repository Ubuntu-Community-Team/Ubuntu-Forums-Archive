---
title: "Favorite Server Software???"
date: 2008-04-29
forum: Server Platforms
---

### Post by carbm1 on 2008-04-29
What other software are people running on their home servers?

I currently only use mine for Cacti (Network Monitoring), Apache2 (Fun and Games), SSH, Samba (File Sharing and Customer backups), DHCP (TFTPD for PXE).

I PXE boot most of my utilities when I'm working on other peoples computers. I have BartPE, Damn Small Linux, Hard Drive Utilities, etc. on my PXE boot. 

I run VMWare Server and house test machines. 

Its a Compaq Proliant ML310, P4 2.53Ghz, 3GB RAM, 80GB IDE, 500GB SATA.  Was Cheap on Ebay well over a year ago!

I would really like to expand on my Ubuntu and Open Source Experience(s).   Any other recommended or interesting packages I might want to consider?

---

### Post by SpaceTeddy on 2008-04-30
- exim
 - courier IMAPs/POP3s for local mail
- Nagios
- Teamspeak
- Shoutcast
- SVN via webdav/trac
--- used to run CVS, svn is better :)
- rsnapshot/rsync
- openvpn 
--- one roaming network
--- five static networks to connect scattered networks together
- squid
--- transparent so people don't know it is being used
- tc (traffic control) 
--- this is not really a programm, but fun to play around with as bandwith shaping is usually greatly underestimated
- used to run mldonkey (not anymore)
- used to run pptpd (windows VPN server)

that's the stuff i have/had configured on my Server (I did not mention things you already said). Mainly for Test purposed, some stuff is used productivly for uni/work

Projects for the future for me are (stuff i want to do sometime):
- Asterisk
- Bacula
- Amanda
- full understanding of tc
- Snort

I hope this list helps you select a few interesting ideas on what to do next. Enjoy :)

PS: OpenVPN is a good choice. Lots of people need it, almost nobody can do it. It's small, slim and highly configurable. I just love it

---

