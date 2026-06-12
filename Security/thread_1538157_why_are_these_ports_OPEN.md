---
title: "why are these ports OPEN????"
date: 2010-07-24
forum: Security
---

### Post by vaibhav292 on 2010-07-24
i am a new user to ubuntu, and someone told me that its inbuilt firewall was good and didn't allow any unnecessary connections to ports, but why...
.
.
->when i PORTSCANed 127.0.0.1, I found
.....port 631(*always open*, service ipp)...and
....a couple of other ports like(44926,53436,50114, etc, etc, ...*open*) 
.
.
->when i PORTSCANed my I.P. add (x.x.x.x)- which is public, i am using mobile GPRS connection...
..... i found ports like(54274,48945,etc,etc,...*open*) seem random to me..
.
.
I DONT KNOW IF THIS IS NORMAL OR NOT, BUT I DO KNOW THAT OPEN PORTS SPELL DISASTER!!!!
.
. 
I HAVEN'T PLAYED WITH MY FIREWALL AT ALL(i do have firestarter, but i barely run it...)

---

### Post by Rubi1200 on 2010-07-24
Open a terminal and post the results of

```
sudo netstat -tulnp
```and/or

```
sudo lsof -i -n -P
```I assume you used nmap to scan your computer?

> I HAVEN'T PLAYED WITH MY FIREWALL AT ALL(i do have firestarter, but i barely run it...)     This is not clear to me. Have you enabled the firewall on Ubuntu and made changes to it or not?

Have you installed any server or remote desktop software or any other web facing programs?

---

### Post by vaibhav292 on 2010-07-24
no server or remote desktop software has been installed by me....i just use internet(client)
.
.
i think that ubuntu firewall is enabled by DEFAULT, isn't it???..., and it rejects any incoming connection from the internet, right???..., so why are these ports still open???
.
and i am starting to assume that this is why my firestarter shows me in *EVENT LOG* that some IP's are trying to estaplish *TCP* connection through these open ports...!!!
.
.
_***------------U R G E N T    H E L P   N E E D E D-----------***_

---

### Post by Rubi1200 on 2010-07-24
First read this:

[https://wiki.ubuntu.com/Security/Features#ports](https://wiki.ubuntu.com/Security/Features#ports)

and please post the results of the commands I gave you because that will help us determine what is going on.

---

### Post by HPD2 on 2010-07-24
Being new to Ubuntu some thing to keep in mind is Ubuntu is **_not_** Windows. A lot of windows security necessity's are not needed in Ubuntu. Firewalls and Virus scanners are among two arguably unneeded tool in a general linux desktop environment.

I don't thing the firewall is enabled by default, you may want to run```
sudo ufw enable
sudo ufw default deny
```After you post the out put of Rubi1200 commands.

---

### Post by Rubi1200 on 2010-07-24
It might be a good idea if you read the security sticky by bodhi.zazen as well. especially the section on firewalls:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

In an attempt to help ease any concerns you have, I can tell you that on a default Ubuntu installation the only service you are likely to find listed as listening is cups (the printing service).

---

### Post by vaibhav292 on 2010-07-24
> **HPD2 said:**
> Being new to Ubuntu some thing to keep in mind is Ubuntu is **_not_** Windows. A lot of windows security necessity's are not needed in Ubuntu. Firewalls and Virus scanners are among two arguably unneeded tool in a general linux desktop environment.

I don't thing the firewall is enabled by default, you may want to run```
sudo ufw enable
sudo ufw default deny
```After you post the out put of Rubi1200 commands.
.
.
my *FIRESTARTER* applet is showing that my firewall is running(with no exceptions as policy tabs are empty) , then do i still need to put those commands(sudo ufw enable , sudo ufw default deny) in??
.
.
```
***OUTPUTS******
vaibhav@vaibhav-desktop:~$ sudo netstat -tulnp
[sudo] password for vaibhav: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN      23364/transmission
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3133/cupsd      
tcp6       0      0 :::6881                 :::*                    LISTEN      23364/transmission
tcp6       0      0 ::1:631                 :::*                    LISTEN      3133/cupsd      
udp        0      0 0.0.0.0:58031           0.0.0.0:*                           3118/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3118/avahi-daemon: 
******************
vaibhav@vaibhav-desktop:~$ sudo lsof -i -n -P
COMMAND     PID    USER   FD   TYPE  DEVICE SIZE NODE NAME
avahi-dae  3118   avahi   14u  IPv4    7447       UDP *:5353 
avahi-dae  3118   avahi   15u  IPv4    7448       UDP *:58031 
cupsd      3133    root    2u  IPv6    7493       TCP [::1]:631 (LISTEN)
cupsd      3133    root    3u  IPv4    7494       TCP 127.0.0.1:631 (LISTEN)
firefox   11450 vaibhav   51u  IPv4 2892310       TCP 117.xx.xx.xx:38593->64.233.181.100:80 (ESTABLISHED)
firefox   11450 vaibhav   57u  IPv4 2892345       TCP 117.xx.xx.xx:38521->74.125.98.93:80 (ESTABLISHED)
transmiss 23364 vaibhav   17u  IPv4 2881931       TCP 117.xx.xx.xx:37562->88.191.20.206:80 (ESTABLISHED)
transmiss 23364 vaibhav   18r  IPv4 2881924       UDP 117.xx.xx.xx:51126->192.200.1.21:5351 
transmiss 23364 vaibhav   19u  IPv6 2881932       TCP *:6881 (LISTEN)
transmiss 23364 vaibhav   20u  IPv4 2881933       TCP *:6881 (LISTEN)
transmiss 23364 vaibhav   21u  IPv4 2883012       TCP 117.xx.xx.xx:38403->78.87.163.167:26516 (ESTABLISHED)
transmiss 23364 vaibhav   23u  IPv4 2892457       TCP 117.xx.xx.xx:43613->195.5.125.50:40880 (SYN_SENT)
```

**************I HAVE PUT (xx) TO HIDE MY IP ADD :-)****************

---

### Post by vaibhav292 on 2010-07-24
> **vaibhav292 said:**
> 
.
.
->when i portscaned 127.0.0.1, i found
.....port 631(*always open*, service ipp)...and
....a couple of other ports like(44926,53436,50114, etc, etc, ...*open*) 
.
.
->when i portscaned my i.p. Add (x.x.x.x)- which is public, i am using mobile gprs connection...
..... I found ports like(54274,48945,etc,etc,...*open*) seem random to me..
.
.

i am still expecting an answer for this...!!!!!!??????

---

### Post by lykwydchykyn on 2010-07-24
Ok, basically you have open ports because:
 - Your print service (CUPSD) is listening for print clients.  If you don't have a printer or don't have other computers printing to it, you can block this port.

 - Transmission (bittorrent client) is running, and presumably you're seeding something or other, so it needs ports open.

 - avahi-daemon is listening on a couple of ports.  Avahi is a service that listens for network services on other network devices to find and auto-configure services.  You don't need it, as long as you don't mind setting up remote services the hard way.

Questions?

---

### Post by CharlesA on 2010-07-24
Please don't use firestarter, it is no longer under development and UFW/GUFW is a better replacement for it.

---

### Post by vaibhav292 on 2010-07-24
hey [lykwydchykyn,]("http://ubuntuforums.org/member.php?u=603141")
.
i also mentioned that i found these *RANDOM PORT NO.(50114,50274)* in PORTSCAN,and found them open, how to i specify which ports i want open, i.e. i want to run CUPSD,bittorrent client,avahi-daemon BUT i dont want other ports through which damage cud be done!!!
.
could you help me with some other stuff...???
.
(1)how do i stop seeding my files that i am downloading, in bittorent(no uploads)
.
(2)some software of ubuntu similar to windows DAP??

---

### Post by vaibhav292 on 2010-07-24
....

---

### Post by CharlesA on 2010-07-24
If you are downloading a torrent, you always upload, I do not believe there is a way to download only.

If the file is always downloaded, all you need to do is tell the client to stop seeding the torrent.

---

### Post by lykwydchykyn on 2010-07-24
> **vaibhav292 said:**
> hey [lykwydchykyn,]("http://ubuntuforums.org/member.php?u=603141")
.
i also mentioned that i found these *RANDOM PORT NO.(50114,50274)* in PORTSCAN,and found them open, how to i specify which ports i want open, i.e. i want to run CUPSD,bittorrent client,avahi-daemon BUT i dont want other ports through which damage cud be done!!!
.
could you help me with some other stuff...???
.
(1)how do i stop seeding my files that i am downloading, in bittorent(no uploads)
.
(2)some software of ubuntu similar to windows DAP??

Those random ports are probably bittorrent.  High ports like that are typically opened by applications run by the user, since it takes root privileges to open a port under 1024.

Shut down transmission and do another port scan, and see if those random ports aren't closed.

---

### Post by rookcifer on 2010-07-24
OP,

Port scanning your machine from itself is pointless.  The ports such a scan shows open are not open to the Internet at large.  A better way is to scan from another machine or use ShieldsUp at grc.com to get a more accurate view.

Port 631 (CUPS) is binded to localhost (this means it cannot listen to the Internet).  The other ports you listed are probably torrents or something.  Again, please post the output of 

```
sudo netstat -tulpv
```

---

### Post by cariboo on 2010-07-24
IF you are using System->Administration->Network Tools to do a post scan of localhost, you will get false positives, as there is a bug in the the tool that hasn't been fixed yet. As the others have said do your port scan from a different system on your network using nmap.

---

### Post by vaibhav292 on 2010-07-25
> **rookcifer said:**
> OP,

Port scanning your machine from itself is pointless.  The ports such a scan shows open are not open to the Internet at large.  A better way is to scan from another machine or use ShieldsUp at grc.com to get a more accurate view.

Port 631 (CUPS) is binded to localhost (this means it cannot listen to the Internet).  The other ports you listed are probably torrents or something.  Again, please post the output of 

```
sudo netstat -tulpv
```
****************************************************8
***************output*********************************
vaibhav@vaibhav-desktop:~$ sudo netstat -tulpv
[sudo] password for vaibhav: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      3133/cupsd      
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      3133/cupsd      
udp        0      0 *:58031                 *:*                                 3118/avahi-daemon: 
udp        0      0 *:mdns                  *:*                                 3118/avahi-daemon: 
************************************************************
*************grc.com sheilds-up**********************************
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000060]Your system has achieved a **perfect** "TruStealth" rating. **Not a single packet** — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.[/COLOR][/SIZE][/FONT]
********************************************************************

---

### Post by vaibhav292 on 2010-07-25
hey every1..

i m using mobile GPRS internet and i am always given a public IP add(though it changes everytime i connect).....,
.
.
so could i set up my computer to run as a server..?..i want to use apache tomcat to serve some fun HTML apps i created, to my friends w/o the need for me to use some other internet server??
.
.
if yes..could you tell me how...
.
.
----->>>>>i also asked one of my friends on facebook to *PING* me, BUT they couldn't, they reported (REQUEST TIMED OUT),<<<<<<<---------

---

### Post by vaibhav292 on 2010-07-25
hey every1 just to inform you I have just passed my  *AMCE*  CERTIFICATION!!
.
AMCE- ANTI MICROSOFT CERTIFIED ENGINEER
.
.
questions on the exam->
(1)which  OS  do you use - UBUNTU(9.04)
(2)which  PROG.  LANG.   - C++ , JAVA
(3)which server platforms- APACHE
(4)which database        - Oracle,Derby
.
.
****************************************************************
THE PREVIOUS COMMENTS WERE THE OPININS OF A SINGLE INDIVISUAL THEY WERE MEANT TO HEART ANY1's  MICRO FEELINGS....
***************************************************************
.
.
the joke is over now you can laugh...:smile::razz::razz::razz::grin::grin::grin:

---

### Post by CharlesA on 2010-07-25
This is starting to seem like spam. >.>

If you need to serve content from a machine that has an IP address that changes frequently, you would have to use a dynamic DNS service. I use dyndns.org myself.

---

### Post by bodhi.zazen on 2010-07-25
> **vaibhav292 said:**
> hey every1 just to inform you I have just passed my  *AMCE*  CERTIFICATION!!
.
AMCE- ANTI MICROSOFT CERTIFIED ENGINEER
.
.
questions on the exam->
(1)which  OS  do you use - UBUNTU(9.04)
(2)which  PROG.  LANG.   - C++ , JAVA
(3)which server platforms- APACHE
(4)which database        - Oracle,Derby
.
.
****************************************************************
THE PREVIOUS COMMENTS WERE THE OPININS OF A SINGLE INDIVISUAL THEY WERE MEANT TO HEART ANY1's  MICRO FEELINGS....
***************************************************************
.
.
the joke is over now you can laugh...:smile::razz::razz::razz::grin::grin::grin:

Honestly I can not tell if you have a question, if you profoundly do not understand networking / security, or it you are trolling. This post makes me think you are trolling. If that is the case, go ahead and stay with Microsoft.

Assuming you want an answer, you need to understand the loopback interface. You will see a different list of open ports if you scan from the local machine then you will from a second computer on your LAN.

If you scan from the internet, such as "ShieldsUp!", you are scanning your router.

In terms of the open ports, you are seeing cups, which is printing, and avahi

[http://avahi.org/](http://avahi.org/)

cups, but default, should not accept external connections, so the port is closed, and personally I disable avahi as I do not use it.

Beyond that, is there and additional question ?

---

