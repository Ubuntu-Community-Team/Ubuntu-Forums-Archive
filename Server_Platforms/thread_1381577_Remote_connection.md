---
title: "Remote connection"
date: 2010-01-14
forum: Server Platforms
---

### Post by cmadooly on 2010-01-14
Hey guys,

I tried googling this but couldn't really come across a page that fit exactly what I'm trying to do. Any advice/links are much appreciated as always. I can take over once you point me to the right direction.

Right now, I have Ubuntu Server 9.10 for samba and ftp. Everything is working fine. This is actually for a friends small business.

My friend also wants the flexibility to work from home. All of his computers at work, and home, run some variation of windows.

Is there an application that I can install on my ubuntu server that would allow my friend to VPN into his work network, and then use Remote Desktop Connection to remotely connect to his PC?

At my old job, where everything ran on windows, I was able to launch a vpn connection, and after it was connected, I would launch MS RDC, type in the local 192.168.x.x IP address and remote to my desktop at work. Kind of looking for a similar setup here.

Thanks in advance.

---

### Post by HermanAB on 2010-01-15
Howdy, 

Windows RDP is secure, you don't need to run it over a VPN.  Therefore, all you need to do is forward port 3389/TCP in your firewall so that he can reach the PC from his home. If he has to reach multiple PCs, then adjust the port used by RDP in the Windows registry and forward multiple ports.  In RDP (and rdesktop) simply specify the address as:

ipaddressoffirewall:3389

Cheers,

Herman

---

### Post by Lars Noodén on 2010-01-15
> **cmadooly said:**
> 
Is there an application that I can install on my ubuntu server that would allow my friend to VPN into his work network, and then use Remote Desktop Connection to remotely connect to his PC?


See some of these:

[http://www.tightvnc.com/](http://www.tightvnc.com/)

[http://docs.kde.org/stable/en/kdenetwork/krfb/](http://docs.kde.org/stable/en/kdenetwork/krfb/)

[https://help.ubuntu.com/community/Vinagre](https://help.ubuntu.com/community/Vinagre)

[http://ubuntuforums.org/showthread.php?t=392184](http://ubuntuforums.org/showthread.php?t=392184)

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

You can use RDP or VNC to connect between Linux and legacy systems with the right clients.  I've shown Ubuntu and Debian desktops to Windows users with VNC utilities.   Both will have to be tunneled over SSL/TLS or SSH.

---

### Post by Lars Noodén on 2010-01-15
@ HermanAB : Like VNC, RDP needs to be tunneled over SSH or at least over SSL/TLS.  

RDP is basically an 'extended', read damaged, variant of [ITU-T T.128](http://www.rdesktop.org/#docs)  RDP itself is quite insecure, somewhat adjustably so depending on the settings.  The origin should give the big hint there.

See thousands of articles, including an old one from 2005
[http://www.oxid.it/downloads/rdp-gbu.pdf](http://www.oxid.it/downloads/rdp-gbu.pdf)

Wrapping in TLS/SSL or tunnelling with SSH can ameliorate both of these still extant problems of sub-standard encryption and lack of authentication: "Terminal Services sessions use native Remote Desktop Protocol (RDP) encryption.  However, RDP does not provide authentication to verify the identity of a Terminal Server. "
[http://blogs.technet.com/askperf/archive/2008/02/16/ws2008-network-level-authentication-and-encryption.aspx](http://blogs.technet.com/askperf/archive/2008/02/16/ws2008-network-level-authentication-and-encryption.aspx)

---

### Post by cmadooly on 2010-01-15
Thanks for the suggestions.

Lars Noodén, I think I didn't clarify one important point.

My friend wants to remotely connect from his windows home pc to his windows work pc. He doesn't want to connect to the ubuntu server (which, doesn't have a GUI and he doesnt know anything about linux).

I would prefer not to use a 3rd party app's like logmein or even vnc.

So I guess to diagram this, it would be

Home PC ====> VPN ====> (Something to authenticate)===>MSTSC ====> Work PC

The office doesn't have a domain controller or anything. The office just has stand alone windows machines with shared drives and printers.


Herman, I understand what you're saying but like Lars Nooden said, I don't know if that's a secure way of accessing the work pc.

Isn't there some way that he can connect to his work network, where the request goes to the ubuntu server, the ubuntu server authorizes the user, and then the user can MSTSC into his work pc?

---

### Post by Lars Noodén on 2010-01-15
> **cmadooly said:**
> Thanks for the suggestions.

Lars Noodén, I think I didn't clarify one important point.

My friend wants to remotely connect from his windows home pc to his windows work pc. He doesn't want to connect to the ubuntu server (which, doesn't have a GUI and he doesnt know anything about linux).

I would prefer not to use a 3rd party app's like logmein or even vnc.

So I guess to diagram this, it would be

Home PC ====> VPN ====> (Something to authenticate)===>MSTSC ====> Work PC

The office doesn't have a domain controller or anything. The office just has stand alone windows machines with shared drives and printers.


Herman, I understand what you're saying but like Lars Nooden said, I don't know if that's a secure way of accessing the work pc.

Isn't there some way that he can connect to his work network, where the request goes to the ubuntu server, the ubuntu server authorizes the user, and then the user can MSTSC into his work pc?

I've only dealt with Windows users going the opposite direction, showing the linux *desktop* to them.  Even then it was about 3 or 4 years at the last.  There are apparently a number of free-of-charge VNC clients or RDP clients available.  

About his work machines, shared drives and printer sharing can be done very well by Samba.  At least in the early days of Windows getting forced into the server room, Samba was doing the job even if the CFO could show a receipt for purchasing some kind of Windows server.  So later, after the desktop sharing, you might look into Samba to save him some time, work, security and money.

---

### Post by cmadooly on 2010-01-15
> **Lars Noodén said:**
> I've only dealt with Windows users going the opposite direction, showing the linux *desktop* to them. Even then it was about 3 or 4 years at the last. There are apparently a number of free-of-charge VNC clients or RDP clients available. 
 
About his work machines, shared drives and printer sharing can be done very well by Samba. At least in the early days of Windows getting forced into the server room, Samba was doing the job even if the CFO could show a receipt for purchasing some kind of Windows server. So later, after the desktop sharing, you might look into Samba to save him some time, work, security and money.
 
 
I have the SAMBA server running already, with FTP. That part is done (see original post).
 
Just need to find a way for him to remotely connect to his PC without a 3rd party app. Worse comes to worst, I'll just try the method Herman explained.

---

