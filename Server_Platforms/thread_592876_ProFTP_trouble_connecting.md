---
title: "ProFTP trouble connecting"
date: 2007-10-26
forum: Server Platforms
---

### Post by poisonmushroom on 2007-10-26
Hello,

I have installed ProFTPD on my linux server (Command Line only), i used the tutorial posted on this forum ([http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server](http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server))

After setting up everything, and forwarding the FTP ports 20-21 on my modem i tried opening the browser and typing [ftp://mylanip](ftp://mylanip) and it asked for login information, i used them and they worked OK.

But here's where the problem comes, when i try to use my WAN ip, so the outside world can also access my server, it asks for login information  but when i enter them correctly it does nothing, it looks like its working but nothing happens. I pinged the IP and let others ping it and it was ok, the ports are correctly forwarded in my modem configuration page and my firewall is also probably set up correctly since other users can connect to SSH on my server.

I have tried to think about a logical reason for this but i couldn't find any, first i thought it was this IPvB6 thing but i solved it using google but nothing happened.

This is really annoying, i don't find anything wrong anywhere but it simply doesn't work.

Does anyone know a way around this?

Big Thanks! :)

---

### Post by HermanAB on 2007-10-26
You need to enable FTP tracking in your firewall.  FTP uses port 21 for the initial negotiation, then it turns things around and switches to a random high port for the data transfer.  Otherwise, you need to run FTP in Passive Mode, which doesn't do that (but which has a higher server load).

---

### Post by poisonmushroom on 2007-10-27
I read in the ProFTPD config file about the Passive Mode, i used the command in the config and used these port ranges 49152-65534, and then i Forwarded the same ports on my firewall.

I tried connecting using firefox browser but i get the same problem, it asks for login but does nothing.

Any other suggestions?  


P.S: I saw this in the config file, do i need this too?

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

---

### Post by freebeer on 2007-10-27
That certainly looks like a likely candidate to get it to work -- I personally haven't tried it.  My solution, as suggested by the previous post, was to have the client login in active mode.  I've also read where some routers have trouble with forwarding a large range of port addresses, or just high port address numbers.  Rather than trying to work that little issue out, I opted for active mode only.  That works just fine in my experience.

---

### Post by xion.os2k on 2007-11-07
Sorry to bump the thread, but I'm having this same issue. I've opened up all the ports on my router, I even tried DMZ'ing the ip for the pc the server's running on, and it just won't connect. I'm dual-booting with Gutsy and XP x64, and I don't have this problem when I'm in Windows. I love linux, and especially ubuntu, but I just can't seem to get this thing to work right. 

I tried setting up a website, ftp, even hosting a ut2004 server on both windows and gutsy, and while I can access any of them from an outside computer using windows, I can't connect to anything with the same exact setting when I'm on Ubuntu. I've opened up all the proper ports for the servers, I just can't see anything from outside my LAN when I switch to Ubuntu.

Normally I'd just blame my router, but like I said, I opened up all the ports and I've even tried DMZ'ing and flat out disabling the firewall altogether, I just can't access it :( Any help would be greatly appreciated

---

### Post by Daveski on 2007-11-08
> **poisonmushroom said:**
> 
P.S: I saw this in the config file, do i need this too?

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

Well I found that with Masquerade on I could not passive connect from outside even though the FTP client reported that the server gave it the correct public IP and a valid port in the passive port range. When I finally tried without a MasqueradeAddress line it started to work. Perhaps my NAT router is cleverer than I thought and does this anyway...

---

