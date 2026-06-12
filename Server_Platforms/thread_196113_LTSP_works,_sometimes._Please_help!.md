---
title: "LTSP works, sometimes. Please help!"
date: 2006-06-13
forum: Server Platforms
---

### Post by AlexMorin on 2006-06-13
I have this lab full of thin clients. A brand new HP Proliant server @ 3.2 GHZ w/ 2 gigs of RAM running Dapper, full server install.

The clients are Compaq Deskpro EN PIII 866mhz machines w/ 256 MB.

The thin clients work, most of the time. But sometimes, they only go up to tty6 (text login), and switching manually to full GUI (Ctrl-alt-F7) does nothing. I reboot them and usually get them to work the second time.

I have not been able to isolate the cause (cabling, individual stations). This seems random right now... Can someone offer me an idea of where to look? Thanks for reading!

Help. :confused:

---

### Post by kihai on 2006-07-17
This is probably a router problem. Some routers (or most of them, I don't know) drop udp packets when there are too many. As the initial communication between clients and server runs via udp, several clients booting up at the same time seem to produce too many packets and the router just drops some, resulting in the error you described. I guess you can't do anything about that but buying another router (No clue, which one would work for that, though...)

---

### Post by AlexMorin on 2006-08-08
> **kihai said:**
> This is probably a router problem. Some routers (or most of them, I don't know) drop udp packets when there are too many. As the initial communication between clients and server runs via udp, several clients booting up at the same time seem to produce too many packets and the router just drops some, resulting in the error you described. I guess you can't do anything about that but buying another router (No clue, which one would work for that, though...)
Just got back from vacation.
Thanks, I'll check with networking.
We use Cisco 3524 and 2950 switches for the fiber backbone. The clients are connected to 10/100 cheapo 24 port D-Link/Asanté switches.

Would anyone know about "better" switches which would not freak out from the traffic from such a lab? But that are still simple switches...
We need very good reliability from our setup, since it will be on another continent once it's delivered...

---

### Post by waltrothfuss on 2006-08-26
I don't believe it is the router.  I have the same problem using edubuntu's ltsp implementation, and have tried it with three different routers all with the same result.  However, with an identical setup using k12ltsp, all of the terminals boot as they should regardless of whatever router is used.  Indeed, they are booting over my office lan that has several routers in it between the thin client server and the various terminals; the lan is also running several standalone machines and a windows terminal server, it is not just on a dedicated router for the ltsp terminals.  I have tried edubuntu both ways, with and without a dedicated router for the terminals.  It is some quirk with the edubuntu implementation.  I have no clue as to what.  Sometimes all terminals will boot, sometimes only the first terminal will boot, then all the others, even when delaying their startups for several minutes, will only go to the text login.  Trying to login from the text screen is always unsuccessful.  This is frustrating.  I am not fond of Fedora 4, and was hoping that this dapper version of edubuntu would be better.

---

### Post by UbuWu on 2006-08-27
You should probably file a bug about it.

---

### Post by Psylon on 2006-09-06
> **AlexMorin said:**
> 
The thin clients work, most of the time. But sometimes, they only go up to tty6 (text login), and switching manually to full GUI (Ctrl-alt-F7) does nothing. I reboot them and usually get them to work the second time.


Can you try just an Alt-F7 AlexMorin?

We are seeing the same behavior but with a dapper server based install and the ltsp-server package. The server is an over built multicore opteron box and we are using LTSP Term 150 ([http://www.disklessworkstations.com/cgi-bin/web/info/ltsp_t150.html?id=sVIsgkVz](http://www.disklessworkstations.com/cgi-bin/web/info/ltsp_t150.html?id=sVIsgkVz)) over a 100Mbit network.

I have seen some other threads concerning this issue, but have not seen a resolution yet:

[http://www.nabble.com/Cannot-get-X-to-start-on-some-clients-t2178429.html](http://www.nabble.com/Cannot-get-X-to-start-on-some-clients-t2178429.html)
[http://www.ubuntuforums.org/showthread.php?t=245841](http://www.ubuntuforums.org/showthread.php?t=245841)
[http://www.ubuntuforums.org/showthread.php?t=196113](http://www.ubuntuforums.org/showthread.php?t=196113)

X starts to load, I see a grey background and the mouse pointer, but then just a console login screen. I can manually switch back to X with an ALT-F7 though.

I did post to the bug tracking system at:

[https://launchpad.net/distros/ubuntu/+source/ltsp/+bug/39294](https://launchpad.net/distros/ubuntu/+source/ltsp/+bug/39294)

It might be good if you guys posted which hardware you are using to this bug report as well.

---

### Post by AlexMorin on 2006-09-06
Is it just me or has the fix for that bug ben released? Thats what it says on that page... [https://launchpad.net/distros/ubuntu/+source/ltsp/+bug/39294/+viewstatus](https://launchpad.net/distros/ubuntu/+source/ltsp/+bug/39294/+viewstatus)

So it's fixed? In which distros? Just Ubuntu? At what date has the patch been integrated in dapper updates?

---

### Post by AlexMorin on 2006-09-13
Hi all!

Well, we've tested a Cisco 2950 switch, and it does not seem to make a difference. So this issue is probably not hardware related.

On the software side, I've done all updates to Edubuntu Dapper (6.06.1LTS) and installed a 686-smp kernel (Pentium 4 HT cpu). Stil no luck.

The terminals now boot up until:
[FONT="Courier New"]Uncompressing Linux... Ok, booting the kernel.
IP-Config: eth0 hardware address 00:02:a5:XX:XX:XX mtu 1500 DHCP RARP
_[/FONT]

Hang there for anything between 5-10 minutes and only the continue to the GUI.
They seem to boot in bunches. I have maybe 4 complete boot-ups after a few minutes, then all of the others at once 10 minutes later.
So the behavior has changed a bit (no text login prompt), but it's still not 100% identical. 

I should also mention that the server's syslog shows the time gaps mentionned when logging the client's DHCPREQUEST and the immediate 'mountd authenticated mout request':
[FONT="Courier New"]Sep 13 19:20:17 edubuntu dhcpd: DHCPACK on 192.168.0.228 to 00:02:a5:56:f2:cd via eth0
Sep 13 19:20:17 edubuntu mountd[4890]: authenticated mount request from 192.168.0.228:1008 for /opt/ltsp/i386 (/opt/ltsp)
Sep 13 19:21:54 edubuntu ntpd[5065]: synchronized to 132.246.168.148, stratum 2
Sep 13 19:26:12 edubuntu ntpd[5065]: kernel time sync enabled 0001
Sep 13 19:29:05 edubuntu dhcpd: DHCPREQUEST for 192.168.0.221 (192.168.0.1) from 00:02:a5:56:b1:4e via eth0
Sep 13 19:29:05 edubuntu dhcpd: DHCPACK on 192.168.0.221 to 00:02:a5:56:b1:4e via eth0
Sep 13 19:29:06 edubuntu dhcpd: DHCPREQUEST for 192.168.0.182 (192.168.0.1) from 00:02:a5:54:45:76 via eth0
Sep 13 19:29:06 edubuntu dhcpd: DHCPACK on 192.168.0.182 to 00:02:a5:54:45:76 via eth0
Sep 13 19:29:06 edubuntu mountd[4890]: authenticated mount request from 192.168.0.221:1008 for /opt/ltsp/i386 (/opt/ltsp)[/FONT]

So does it still look like a bug?

---

### Post by AlexMorin on 2006-09-18
Where should I go with this?

Should I post it in one of the more general categories?

---

### Post by AlexMorin on 2006-09-18
EUREKA! Sorry!

Well, while fixing a video issue for which I had posted earlier, I solved this one too!

Specifying a 16 bit color depth in a brand new lts.conf file fixed the issue.
At 24 bits, I was having* very* mixed fortunes booting the terminals.
At 32 bits, none would come up.
16 works like a charm, and probably takes a load off the network.

[Default]
SERVER = 192.168.0.1
X_COLOR_DEPTH = 16

Of course, there are many more settings to be done in there. See : [http://wiki.ltsp.org/twiki/bin/view/...#X_COLOR_DEPTH](http://wiki.ltsp.org/twiki/bin/view/...#X_COLOR_DEPTH)

Wee!

---

### Post by AlexMorin on 2006-10-23
Well, it still works, sometimes... So it is not solved.

I have found that 16 bits seems to be the sweetspot. As nuts as it may sound, 8 bits is about as worse as 32 bits! 

Bit depth - Terminal boot success rate (rough average)
8 bits = 25%
16 bits = 95%
32 bits = 0%

This is driving me insane as you might imagine. It's completely random, and does not even seem related to network load (as shown by the bad 8 bit success rate).

---

### Post by Pamir on 2006-10-24
Hellow everyone, 

Sorry being ....

I thought it is better to ask here.

I wanted to install ubutn server and LTSP  on HP proliant server with SATA Adaptect Raid controler. Unfortunatley could not do it!! I had to install Opesn SuSe instead and now I can not get the client working!  I am using a DLink switch. The back bone link is cat 5 and the interface is 100 mb for trial will change it to gb once it is running.

Can some one help me  please? 

I am planning to install Ubuntu again how shal solve the problem of SATA Adaptec RAID?

---

### Post by AlexMorin on 2006-10-25
Off-topic...

Please post a new-thread or search trough the forums.

---

### Post by Kalif on 2006-12-07
my gues is that this is not a router problem, since there is probably no router. Though, switches are known to drop packets as well, and more expensive switches with VLAN support (and from well known vendors) usually have much more buffer capacity than cheap no name stuff that you buy in your local DIY car spare parts chain.
/k

---

### Post by AlexMorin on 2006-12-14
We are running with a Cisco 2950 switch now, and are still experiencing the same issues. I can't upgrade to Edgy until I stop reading about bad experiences with RAID boot volumes.

---

