---
title: "Firestarter and networks"
date: 2005-04-06
forum: Server Platforms
---

### Post by kozimodo on 2005-04-06
I have Firestarter installed but it interferes with access to various parts of my network.  For example while FS is running I can use the web interface for my NSLU2 network but I can't mount a network drive.  Also, I can't use the web interface for my print server or print to it when FS is running.  I've tried changing various settings to no avail.

Any suggestions?

---

### Post by lordofkhemenu on 2005-04-07
[QUOTE=kozimodo]I have Firestarter installed but it interferes with access to various parts of my network. For example while FS is running I can use the web interface for my NSLU2 network but I can't mount a network drive. Also, I can't use the web interface for my print server or print to it when FS is running. I've tried changing various settings to no avail.

Any suggestions?[/QUOTE]
This is the Tech Support Bob in me speaking in order to cover all the bases, but you didn't mention it: Everything works fine WITHOUT Firestarter running?

---

### Post by kozimodo on 2005-04-07
[QUOTE=lordofkhemenu]This is the Tech Support Bob in me speaking in order to cover all the bases, but you didn't mention it: Everything works fine WITHOUT Firestarter running?[/QUOTE]

Yes indeed.

---

### Post by gheorghe_pop on 2005-04-07
I also have problems with Firestarter and SMB Networks. In FS i have alowed SMB for everyone but I can't see my network until I disable FS. When I disable FS I have no problem viewing network from a windows station, but when i try to view the network from the Ubuntu station it doesen't work. It takes very long time just to open a folder fom the network. Can some one tell me what's wrong?

---

### Post by jdong on 2005-04-08
SMB requires some RPC callbacks in order to work... Check the Denied log listing in Firestarter.

---

### Post by kozimodo on 2005-04-09
[QUOTE=jdong]SMB requires some RPC callbacks in order to work... Check the Denied log listing in Firestarter.[/QUOTE]
Looking at the Events tab, there are IP addresses being denied from outside the network but nothing from within.  That is, I see no IP addresses beginning 192.168.0.xxx.  Am I supposed to be looking somewhere else?

---

### Post by gheorghe_pop on 2005-04-11
In my case I have 2 computers.One is xx.xx.xx.xx1 and the other is xx.xx.xx.xx2. The xx.xx.xx.xx1 ip addres is given by the ISP with and gateway and a DNS addres also. 
xx.xx.xx.xx2 is set by me.
So even if I allow all from xx.xx.xx.xx2 and SMB acces for everyone still no network with FS enabled.
Could it be that the ip's are not set corectly?

---

### Post by Boomgawd on 2005-04-11
I have the same problem, I can allow ports to the outside wolrd but nothing on the local area is accepted.. its just crazy.. I'm allowing 192.168.0.0/24 and still nothing. cant access smb shares. and access windows dives, cant use network places. but azureus ports ok and so does ssh.. I'm stumpted.. no firewall local are is fine.. 

Boomgawd

---

### Post by jdodson on 2005-04-11
you need to basically open the relevant post in firestarter(it closes all ports by default, which is a sane default).  figure out the SMB ports you need open to get things to run correctly, and then set firestarter to allow traffic to those ports.

---

### Post by gheorghe_pop on 2005-04-11
Ok.But when I alow smb in firestarter some ports are opened by default.Isn't this enought or shuldn't be enought? Where can i find details about wich ports should I open to have samba runing?

---

### Post by goofrider on 2005-04-17
[QUOTE=gheorghe_pop]I also have problems with Firestarter and SMB Networks. In FS i have alowed SMB for everyone but I can't see my network until I disable FS. When I disable FS I have no problem viewing network from a windows station, but when i try to view the network from the Ubuntu station it doesen't work. It takes very long time just to open a folder fom the network. Can some one tell me what's wrong?[/QUOTE]


I think FireStarter reject all broadcast packets by default, even for ports that u explicitly allow incoming connections.  Broadcast are needed for NetBIOS browsing/name resolution. Maybe that's why u can't see the network? Try browsing the remote share directly using its IP from Naultius, like:

smb://192.168.0.10/myshare/

As far as I know. you shouldn't need to accept any incoming connections while you browse a remote share. So I think it's a NetBIOS broadcast problem.

FWIW, it's better if u use DNS only (say, u can run a caching DNS server like DNSmasq on your Ubuntu server), or use Samba as a WINS server, so u have a central point of name resolution and bypass NetBIOS peer-based name resolution completely. NetBIOS name resolution is inheritly unreliable and hard to troubleshoot.

---

### Post by goofrider on 2005-04-19
[QUOTE=goofrider]I think FireStarter reject all broadcast packets by default, even for ports that u explicitly allow incoming connections.  Broadcast are needed for NetBIOS browsing/name resolution. Maybe that's why u can't see the network? Try browsing the remote share directly using its IP from Naultius, like:

smb://192.168.0.10/myshare/

As far as I know. you shouldn't need to accept any incoming connections while you browse a remote share. So I think it's a NetBIOS broadcast problem.

FWIW, it's better if u use DNS only (say, u can run a caching DNS server like DNSmasq on your Ubuntu server), or use Samba as a WINS server, so u have a central point of name resolution and bypass NetBIOS peer-based name resolution completely. NetBIOS name resolution is inheritly unreliable and hard to troubleshoot.[/QUOTE]


 I just tried to test it out myself, and it does indeed appear that Firestarter blocks all broadcast traffic from external interface, including NetBIOS and XDMCP. (If you have only one network interface, it'll be defined as both int and ext). And it doesn't record anything to its log when broadcast traffic is blocked .

Go to /etc/firestarter/configuration and look for....

```
BLOCK_EXTERNAL_BROADCAST="on"
```

and change it to....

```
BLOCK_EXTERNAL_BROADCAST="off"
```

That should fix NetBIOS name resolution. You should be able to browse the Windows netowrk for other computers.

---

### Post by jonny on 2005-04-19
[QUOTE=goofrider]I just tried to test it out myself, and it does indeed appear that Firestarter blocks all broadcast traffic from external interface, including NetBIOS and XDMCP. (If you have only one network interface, it'll be defined as both int and ext). And it doesn't record anything to its log when broadcast traffic is blocked .

Go to /etc/firestarter/configuration and look for....

```
BLOCK_EXTERNAL_BROADCAST="on"
```

and change it to....

```
BLOCK_EXTERNAL_BROADCAST="off"
```

That should fix NetBIOS name resolution. You should be able to browse the Windows netowrk for other computers.[/QUOTE]I am so grateful to you for explaining this solution to non-networking type like me.  I would just add two things:

 - A server with external broadcasts blocked will not accept new incoming SMB connections.  This nearly drove me crazy, running up and down the stairs several times each day just to temporarily disable Firestarter!

 - You can change the setting you describe without editing the config file.  It's under Edit -> Preferences -> Advanced Options

---

### Post by kwaanens on 2005-12-13
I'm running a "file server" with dynamic IP, and a laptop with dynamic IP. Both Breezy. Currently I allow samba-access for "anyone" in FS on the server.

Is that safe? And will I have to allow for smb outbound everyone on the client side as well?

- Ketil

---

