---
title: "Port 113 not in stealth mode: should I worry?"
date: 2008-03-25
forum: Security Discussions
---

### Post by Ian-on-the-Trent on 2008-03-25
References:
[https://www.grc.com/port_113.htm](https://www.grc.com/port_113.htm)
[http://ubuntuforums.org/showthread.php?t=450998](http://ubuntuforums.org/showthread.php?t=450998)
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)
Distro: Ubuntu 7.04
Router: EBR-2310
==========================

I've tried to hide my closed Port 113 but have been unsuccessful so far. Should I worry about it? 

I use both static and dynamic IPs on a home LAN. As well, there are XP and Ubuntu boxes on the LAN. Ostensibly, my ISP has given me a dynamic IP address although in reality it never changes...same ip address after 3+ years.

Your thoughts....

---

### Post by pseudo-random on 2008-03-25
Don't worry, that stealth business is a gimmick anyhow.
It's closed.
See here: [http://www.dslreports.com/forum/r18175827-Re-EBR2310-and-stealthing-port-113](http://www.dslreports.com/forum/r18175827-Re-EBR2310-and-stealthing-port-113)

---

### Post by Ian-on-the-Trent on 2008-03-25
> **pseudo-random said:**
> Don't worry, that stealth business is a gimmick anyhow.
It's closed.
See here: [http://www.dslreports.com/forum/r18175827-Re-EBR2310-and-stealthing-port-113](http://www.dslreports.com/forum/r18175827-Re-EBR2310-and-stealthing-port-113)

Thanks for writing back pseudo-random.

I went to the link you provided and used their examples to forward anything sent to Port 113 to a fictional IP address (192.168.0.251). However, it is still  reported open and not stealth. So I wonder if this is the quirk of my EBR-2310.

---

### Post by Oldsoldier2003 on 2008-03-25
> **pseudo-random said:**
> Don't worry, that stealth business is a gimmick anyhow.
It's closed.
See here: [http://www.dslreports.com/forum/r18175827-Re-EBR2310-and-stealthing-port-113](http://www.dslreports.com/forum/r18175827-Re-EBR2310-and-stealthing-port-113)

I never understood why people take GRC as gospel... Gibson is an alarmist and well.... full of crap. Shields up is a just a useless gimic for everyone except to windows users that have a direct connection instead of a shared Nat connection through a router/gateway...

---

### Post by Ian-on-the-Trent on 2008-03-25
> **Oldsoldier2003 said:**
> I never understood why people take GRC as gospel... Gibson is an alarmist and well.... full of crap. Shields up is a just a useless gimic for everyone except to windows users that have a direct connection instead of a shared Nat connection through a router/gateway...

I guess I'm typical of many post-novice Ubuntu users who want to safeguard their home office LAN. What should the security priorities be for systems such as mine? And what measures do we take to safeguard our LANs?
[LIST]
[*]home business files
[*]mixed operating systems including XP
[*]teenagers playing multiplayer, online games
[*]VPN
[*]shared music and documents (ie. homework).
[/LIST]

---

### Post by Oldsoldier2003 on 2008-03-25
> **Ian-on-the-Trent said:**
> I guess I'm typical of many post-novice Ubuntu users who want to safeguard their home office LAN. What should the security priorities be for systems such as mine? And what measures do we take to safeguard our LANs?
[LIST]
[*]home business files
[*]mixed operating systems including XP
[*]teenagers playing multiplayer, online games
[*]VPN
[*]shared music and documents (ie. homework).
[/LIST]

the thing is stealth is just a coined term. a closed port in no less safe than a "stealthed" one. 

I don't claim to be a security expert, but I can give you this advice. Some is from my past  experiences as a network admin and some is just generic advice:

Use strong passwords. Social engineering and brute force attacks fare less well agains a strong random or passphrase/random password.

Make sure you open only the ports necessary to conduct your daily life.

Keep your Os up to date with security patches. AV protection is essential on the windows machines!

Practice safe computing. The firewalls and other precautions are useless if you execute unknown code and email attachments with no regard to the possible consequences.

Limit access into your home office/lan! By stopping access at the firewall/router you prevent most of your problems. Don't run servers without a good reason to do so. From a security standpoint there is never a good reason to run the telnet service or FTP. Use SSH instead.

If you share files through samba, set up the samba server to drop packets coming from public ip addresses ( which is just another layer of safety since you shouldn't have any incoming requests if you have closed the ports on your router.)

Security is a subject that is ever changing and elusive. You can spend tons of time securing your systems and still leave a hole, or you could take a less active role and be "secure enough" for your needs. The bottom line is becoming comfortable with the level of security you have versus the value of your sensitive data.

---

### Post by Ian-on-the-Trent on 2008-03-25
> **Oldsoldier2003 said:**
> ...Make sure you open only the ports necessary to conduct your daily life.

If you share files through samba, set up the samba server to drop packets coming from public ip addresses ( which is just another layer of safety since you shouldn't have any incoming requests if you have closed the ports on your router.)
[LIST=1]
[*]I have not configured my router to block any specific ports. I use Zone Alarm on my Windows boxes and use the default iptables configuration for Ubuntu boxes. Is this sufficient protection?

[*] I use Samba on the Ubuntu PCs so the XP boxes can retrieve files. Personal files are accessible based on username/password but some files (ie. music) are public. Again, is this reasonable protection?
[/LIST]

---

### Post by TuckLive on 2008-04-04
If your router is wireless make sure you are using WPA and you could     also disable SSID broadcast.  Otherwise it sounds like your reasonably protected.

---

### Post by netlogic on 2008-04-04
> **Ian-on-the-Trent said:**
> References:
[https://www.grc.com/port_113.htm](https://www.grc.com/port_113.htm)
[http://ubuntuforums.org/showthread.php?t=450998](http://ubuntuforums.org/showthread.php?t=450998)
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)
Distro: Ubuntu 7.04
Router: EBR-2310
==========================

I've tried to hide my closed Port 113 but have been unsuccessful so far. Should I worry about it? 

I use both static and dynamic IPs on a home LAN. As well, there are XP and Ubuntu boxes on the LAN. Ostensibly, my ISP has given me a dynamic IP address although in reality it never changes...same ip address after 3+ years.

Your thoughts....

No, need to worry. Nobody is stealth on the net.
if you want to look like you are stealth on the net, just forward 113 to an empty ip address on your network.

---

### Post by gear_head on 2008-04-04
It might help to have some knowledge of just what port 113 is and what it does.

[http://www.iana.org/assignments/port-numbers]("http://www.iana.org/assignments/port-numbers")

According  to this port 113 is the authentication service.

I don't know if this is really a threat (probably not) but if you do close it, you may get authentication errors or "certificate revocation information is unavalable...*blah blah blah*" messages on your windows machines. I don't know if Linux cares about authentication or not though.

---

### Post by netlogic on 2008-04-04
some irc servers might not work... who cares...

---

### Post by Ian-on-the-Trent on 2008-04-04
Thanks all.

---

### Post by kutjara on 2008-04-04
> **TuckLive said:**
> If your router is wireless make sure you are using WPA and you could     also disable SSID broadcast.  Otherwise it sounds like your reasonably protected.

Disabling SSID broadcast is really only protection against casual intruders. Any decent wifi stumbler will detect non-broadcasting access points by default.

I've actually had to turn SSID broadcast back on for my network, otherwise my wireless card won't connect to it. This is something that's happened since I installed Hardy beta. Gutsy had no problem with "hidden" SSIDs.

---

### Post by netlogic on 2008-04-04
There are many SSID scanners for Linux and Windows. That wouldn't help. You can find hidden nodes in few seconds. Strong passphrase with WPA2 will stop them.

---

