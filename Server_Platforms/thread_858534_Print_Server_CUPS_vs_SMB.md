---
title: "Print Server: CUPS vs SMB"
date: 2008-07-13
forum: Server Platforms
---

### Post by oxsyn on 2008-07-13
I have a Ubuntu 8.04 CLI server running at home.  Just hooked up a USB printer, hoping to set up a print server on it.  I already have SMB installed and running, serving my apache files locally as a windows share (for editing purposes!).

I believe SMB supports print serving as well, yes?  But when I checked the [Ubuntu Wiki for Print Server]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html"), they recommend using CUPS. 

Any suggestions as to which path I should pursue?  Thanks!

---

### Post by oxsyn on 2008-07-13
Looks like I was a little mixed up.  SMB is only for serving files, but provides a link that allows clients to "find" the CUPS server.  CUPS it is.

---

### Post by NuxIT on 2011-06-21
> 
Re: Print Server: CUPS vs SMB
Looks like I was a little mixed up. SMB is only for serving files, but provides a link that allows clients to "find" the CUPS server. CUPS it is. 
Does anyone of if this is true? I'm curious because I'm currently printing from my windows box after installing samba on my Ubuntu Natty Load and sharing the printer over smb. It's also running cups but from what I can tell all the printing is happening through smb and not cups.:!::?: 

I just did a network capture while printing a test page and it seemed to be using smb and msrpc protocols. I'd like to know without having to uninstall cups to test printing. Thanks.

---

### Post by y2kboy23 on 2011-06-21
I believe that SMB just makes sharing a printer easier since it's trying to emulate Windows Networking on a UNIX system.  I have cups-server installed and running on my system and networking printing works flawlessly.  I don't think you could print without cups installed.

---

### Post by NuxIT on 2011-06-21
> **y2kboy23 said:**
> I believe that SMB just makes sharing a printer easier since it's trying to emulate Windows Networking on a UNIX system.  I have cups-server installed and running on my system and networking printing works flawlessly.  I don't think you could print without cups installed.

Yeah, I'm not sure. I'm just going to leave it installed for now or try and look into some cups logs to see if it's been handling print jobs.

---

### Post by crispy_420 on 2011-06-22
Samba is how Windows shares both printers and files, its all the same. This is the Windows native approach.

[http://www.codefx.com/CIFS_Explained.htm](http://www.codefx.com/CIFS_Explained.htm)

CUPS is a Linux/UNIX only protocol.

[http://www.cups.org/](http://www.cups.org/)

Sure you could get Windows to work with CUPS with a little work and some additional downloads. That means instead of setting up one server, you have to setup numerous clients. I'd pick the easy route.

Also if you remove samba be prepared to redo the shared printers.

---

### Post by Morbius1 on 2011-06-22
Samba is a pass through to CUPS. So you can either use cups directly or use Samba to get to cups. Either way you are using cups.

You need to set up the printer properly in CUPS on the server - meaning you flagged it as being "shared" and "published".

There is a [printers] section in smb.conf that looks something like this:
> [printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700You will notice that there are no references to a specific printer in there. It's one of Samba's special shares ( like [homes] ) and the way it works is during boot the CUPS service is started first and makes available the printer list so that when samba starts it knows what printer services are available.

---

### Post by Wim Sturkenboom on 2011-06-22
On holiday and no linux systems at my disposal, but at home I have a desktop (10.04) with a HP1005 connected via USB. No Samba installed. I can print from any machine (Linux as well as Windows) directly to that printer.

In the GUI on 10.04, I could set the printer to be shared. On the other Linux machines there is a way (if I'm not mistaken) to find the shared printer. And in Windows it's a matter of specifying the IP address and something more (not quite sure what I did).

Searching on the web for 'linux printer sharing' and something like 'access linux printer from windows' should give the required info.

---

### Post by lykwydchykyn on 2011-06-22
> **crispy_420 said:**
> 
CUPS is a Linux/UNIX only protocol.

[http://www.cups.org/](http://www.cups.org/)




No, CUPS is an implementation of [Internet Printing Protocol (IPP)](http://en.wikipedia.org/wiki/Internet_Printing_Protocol), which is natively understood by all versions of Windows since windows 2000.  

It lacks some of the automagical setup features of smb/cifs printing, but it also lacks some of the security complications.

---

### Post by crispy_420 on 2011-06-22
Sorry just going off what the developer states at there website, I assumed they knew their product.

---

### Post by lykwydchykyn on 2011-06-22
> **crispy_420 said:**
> Sorry just going off what the developer states at there website, I assumed they knew their product.

I don't see where it states that CUPS uses a Unix-only protocol.

CUPS is designed to *run* on Unixlike systems (linux, bsd, osx, etc), but the *protocol* used is IPP, an open standard that is understood by most modern operating systems.

I'm not trying to labor the point here, but it's important that nobody get confused -- Windows (and many other operating systems) can talk to a CUPS server just fine without SAMBA or any third-party clients.

---

### Post by crispy_420 on 2011-06-22
I re-read my previous post and you are right, my wording could have been better. I used the word "only" when I should have stated something like "UNIX/Linux native" or similar wording. IPP can be used by Windows clients. I misinterpreted the wording. It was late and I was burnt out.

But either way removing would require redoing printers. Also I am partial to samba because it is just easier in my opinion and if you are already in a mixed OS environment I feel it would be the natural choice.

---

### Post by Cool Javelin on 2011-09-02
OK, with all this, I am still confused.

Is it possible to share a printer attached to a Linux machine with others (Linux/Windows) without CUPS using only Samba?

Mark.

---

### Post by lykwydchykyn on 2011-09-02
> **Cool Javelin said:**
> OK, with all this, I am still confused.

Is it possible to share a printer attached to a Linux machine with others (Linux/Windows) without CUPS using only Samba?

Mark.

CUPS is more than just a print service provider, it's the whole printing subsystem -- it manages the print drivers, print jobs, etc.  

SAMBA only provides the sharing layer for those print services over Microsoft's SMB/CIFS printing protocol.  So no, you can't do a print server with *just* samba.  I suppose it might be possible to configure SAMBA to work with the antiquated LPR daemon, but that would be pointless in most situations.

---

### Post by Cool Javelin on 2011-09-03
Thanks, lykwydchykyn.

---

