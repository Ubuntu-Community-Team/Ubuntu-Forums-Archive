---
title: "[SOLVED] Help reconfiguring my network :)"
date: 2008-08-18
forum: Server Platforms
---

### Post by victorbrca on 2008-08-18
Hi guys, 


  I'm trying to reconfigure my home network to lower the amount of PCs I have. Right now I have 3 headless boxes running as servers, and I'm in need of installing another 2x. 

  I'm trying to figure a way of changing my setup, but I'm not too sure how to make the changes while keeping the proper network infrastructure.


**This is what I have:**
Server A - Firewall
Server B - Web and ftp server on DMZ with no access to LAN
Server C - App server and SSH
          \- Virtual Machine - Used for banking
 
**Servers I still need to add:**
Server D - File server
Server E - MythTV


What I'm trying to achieve is security. I don't want to have for example my files in the same server I have my web site, or have my files in a virtual machine that could crash and then I have no access to it anymore.

Any ideas or inputs?


Thanks a lot,

Vic.

---

### Post by victorbrca on 2008-08-19
I hope I didn't come out too arrogant looking like I was expecting someone to really fix my network. 

I was just looking for some pointers and opinions. Any type of comment would be very welcome! :D


Vic.

---

### Post by MJN on 2008-08-19
Here's a comment - do you really need that many separate boxes running? I'm no hippy but it sounds like a real waste of power to me given it is a home network (I'm not belittling the fact, just not seeing the point).

I like humming boxes with flashing lights just as much as the next guy but if I were you I'd cut down massively on the number of separate boxes. There's no reason security has to suffer.

I know this isn't what you asked for but, hey, it's a conversation! ;)

Mathew

---

### Post by doas777 on 2008-08-19
it sounds like all your servers are in your DMZ. so create an internal network (buy a router and mabey a gigibit switch) to connect your internal servers and clients for outbound internet requests/responses. try your best to acheive SPI and never forward a port into your internal net. 

this is of course the exact oppisite of what MJN said. he makes some good points though.

have fun.
franklin

---

### Post by victorbrca on 2008-08-19
Thanks for the replies guys... I don't feel excluded or that I'm talking to myself anymore!!  lol  :D

Actually my network has one server on dmz, and the rest is on my LAN (with one port open). Something like this:

```

[modem]
   |
   |- [Firewall-DHCP] -----  [web-ftp]
       {smoothwall}            {DMZ}
              \
               \
            [switch]
              /    \
             /      \-----[wireless routerA]
    [app-server]                       |
{jinzora, vmachine, ssh, squid}        |
                                   (bunch of client PCs)

```

  I also think it's way too many PCs. I'm just not sure if working with vms on one machine would even be possible with the amount of work load. 

  For example, my app machine sometimes when I'm connecting from work I have one virtual machine, jinzora stream, squid and ssh running at the same time.

  I wonder if having all that, plus file sharing (LAN) and my web-ftp server would work at all.


Vic.

---

### Post by victorbrca on 2008-08-20
Looks like virtualization will be the answer. I've created a new topic [here]("http://ubuntuforums.org/showthread.php?t=895756").

Thanks for the replies guys!! 

Vic.

---

