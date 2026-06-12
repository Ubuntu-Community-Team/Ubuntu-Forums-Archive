---
title: "Samba/NFS?"
date: 2006-01-09
forum: Server Platforms
---

### Post by LightShear on 2006-01-09
I have two ubuntu 5.10's that need to connect to a Ubuntu 5.10 server. The two 'clients' need to log in to the server and get it's own folder. Will Samba work for this, even though nothing is Windows? Do I have to use NFS?

Big thing is the NFS howto I found (Ubuntu's howto link don't work) is very confusing and it jumps around within itself, and most Samba howto's I've seen are more clear. I'd prefer to do it the Samba way, if it's possible. (Which it should be, right?)

---

### Post by LightShear on 2006-01-10
K, changing my question :)

1. When looking in Places > Network Servers, why do my machines come up under "MSHOME" workgroup. They are all changed to something different in their smb.conf files.

2. How do you install the SWAT files on the server?

(Running Samba...obviously)

---

### Post by shadowman on 2006-01-11
The MSHOME that you are seeing is in a workgroup setting in one of the configuration files either on the server or the workstations.  As I recall it is a default. You can easily find it by cd'ing to /etc/samba and issuing grep -i mshome * on your servers and workstations.

hth

---

### Post by grendelkhan on 2006-01-11
If you're talking linux to linux machine connections, NFS is the way to go.  This howto taught me all I needed to get things set up and running:

[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html)

It's amazingly easy.  Now, I have had to add "nolock" to my clients to get this to mount right, but everything works for me and it's rock solid stable.

---

### Post by Thirsteh on 2006-01-11
Samba will work just fine, but it is in fact "for Windows" connectivity, and thus (obviously) you should use NFS if it's possible and you think you are capable. The how-to mentioned above is pretty good.

---

### Post by LightShear on 2006-01-12
Thanks for the advice everyone. I chose the Samba route, and it's a good thing because I didn't even bother to think of the possibility of sharing files and stuff with my roommate (who's running xp). I saw his computer in network places and was like...I didn't think that would happen. Maybe I'll try NFS with the next server I build. While I'm on the topic, do only certain routers allow you to change ports? I have a Linksys WRT54GS v4 (wireless router) and I can't find anything in the setup to change port routing. I don't plan on trying a web or ftp server anytime soon, but if I do, I want to make sure I have the right equipment.

Thanks all

---

### Post by LordHunter317 on 2006-01-12
[QUOTE=grendelkhan]If you're talking linux to linux machine connections, NFS is the way to go. [/quote]No, it's really not.  The NFS driver in Linux is nortiously buggy, always has been, and likely always will be.

It's also an insecure, unreliable protocol anyway.  It's useless over non-secured LANs and links that have tendencies to drop, like wireless.

[quote=Thirsteh]Samba will work just fine, but it is in fact "for Windows" connectivity,[/quote]SMB has a much longer history then being just a Windows protocol, even if current versions of the protocol (i.e., CIFS) are written by MS.

But it's certainly the better protocol in all aspects but out and out speed, unless you consider NFSv4.  Which was a few years too late.

I'm a pretty stanch CIFS support myself, the driver is more stable than NFS on multiple platforms, it has more security, and it gives Windows integration which is a practical must for me.

If it's just Linux clients, it honestly matters little.  In reality though, you're likely going to have/want to deal with a Windows box, making CIFS attractive.

---

### Post by spade_shark on 2006-01-12
> While I'm on the topic, do only certain routers allow you to change ports?  All routers *route* traffic.  Meaning everything is/can forward across the networks.  These devices (wrt54gs) are more like a mini security appliance.  Most of these style units have a DMZ interface or allow one LAN to be exposed to the wan.

> I have a Linksys WRT54GS v4 (wireless router) and I can't find anything in the setup to change port routing. I don't plan on trying a web or ftp server anytime soon, but if I do, I want to make sure I have the right equipment.  Most $40 US units will allow this to work.

---

### Post by LordHunter317 on 2006-01-12
[QUOTE=spade_shark]All routers *route* traffic.[/quote]Right, his statement  isn't even remotely contradictory with that.  His referring to the ability to perform PAT, which yes, his device can do.

>  These devices (wrt54gs) are more like a mini security appliance.Not really.  They do NAT, and NAT, and NAT.  Hardly security at all.

> Most of these style units have a DMZ interface or allow one LAN to be exposed to the wan.Unless you have multiple real IPs, you can only expose via binat one IP address at a time.

---

### Post by Soleil-Raid on 2006-01-12
[QUOTE=LordHunter317]No, it's really not.  The NFS driver in Linux is nortiously buggy, always has been, and likely always will be.
[/QUOTE]

Buggy? I've yet to see an real problems on our network, and it's been running solid for over a year, with bunches of clients hanging off the server.

> 
It's also an insecure, unreliable protocol anyway.  It's useless over non-secured LANs and links that have tendencies to drop, like wireless.

Insecure - hell yes (although, there are various options, but these pretty much suck), but unreliable? This is mostly a problem if you run it in UDP rather than TCP mode.

Plus, From what I've been able to work 

> 
If it's just Linux clients, it honestly matters little.  In reality though, you're likely going to have/want to deal with a Windows box, making CIFS attractive.


Orr.... you can run both. _If_ you can trust the network a little bit till NFSv4 matures, I would use NFS for connecting Linux->Linux, and run a Samba server on the side for Windows connectivity. It's probably worth pointing out that unless you run a full IPSec (which is a royal PITA) stack, CIFS/SMB traffic isn't encypted either (except for the login, which I believe is encrypted at a grand total of... 40 bits DES*).

It does depend on what you want those files for. If you want to keep the workstations seperate, and simply have a bunch of mp3s or movies that you want to share up, I'd go with Samba. If you want your users to have the same home directories on each Linux workstation, NFS is the way to go.

* To be fair, MS has replaced this with the almighty-Kerberos in 2K/2K3 Active Directory enabled servers, but that doesn't help you any in an ad-hoc sharing situation.

---

### Post by imagine on 2006-01-12
Mh, SSHFS anyone? If you already have a working SSH server, it won't become any easier than this.

This might not be a replacement for NFS or Samba in companies, but if I understood it correctly, he only wants to mount some directories on two Ubuntu boxes.

---

### Post by ZylGadis on 2006-01-13
I was just about to suggest that. There is an excellent sshfs howto somewhere in this forum, run a search for it.
Regarding the other argument: You don't need the windows sharing clone (with all related bugs and holes) called samba if you don't use windows. I would go so far as to suggest to never use smb - just run sshd on the linux box and use sftp (free tools available) on the windows one. Anyway, if you have full control over the situation you should not use windows, which makes the entire smb point moot.
I would trust any version of nfs over any version of smb any day. Considering the inherent difficulties in configuring nfs correctly, though, you should really use sshfs.
I wonder if sshfs support will be native in dapper? That tiny trick (it's not even a tool without fuse) is so easy to set up and so omnipotent that I wonder why it's not yet omnipresent :)

---

### Post by Soleil-Raid on 2006-01-13
I hadn't considered sshfs/sftp/scp... but it's a good idea. You can ever get access to it in Nautilus without FUSE, but accessing files via 'sftp://machine_or_ip_/home/foo/whatever'.

Of course, not every application supports sftp, but generally anything that supports smb access from nautilus does.

---

