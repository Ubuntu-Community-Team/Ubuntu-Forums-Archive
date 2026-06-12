---
title: "Followup Poll: How many Users Have Installed Server Programs such as HTTP, SSH, FTP?"
date: 2008-06-04
forum: The Cafe
---

### Post by kevdog on 2008-06-04
I appreciate your guys responses so far.  This is a followup poll to original poll dealing with Firewalls: [http://ubuntuforums.org/showthread.php?t=818300](http://ubuntuforums.org/showthread.php?t=818300)

I'm just wondering how many users since the Ubuntu base install, have installed additional server processes such as SSH, FTP, HTTP (Apache), MySQL, NTP, DNS, Samba, NFS, or any such process that binds itself to a TCP/UDP port.  I'm trying to get an idea about how many users actually install "server" software.

If curious to find if you have listening processes, you can do at command line:

netstat -a | grep LISTEN | grep -v unix

---

### Post by Phenax on 2008-06-04
I run SSH server for tunneling (secure browsing, etc), transferring documents, and programming in my own environment from school and work.

---

### Post by michaelzap on 2008-06-04
I voted "I'm not sure but I have listening processes on the machine as shown by netstat" but actually I'm pretty sure that I have *not* installed any server software and I still have a ton of listening processes. None of them actually seem to be server processes, however, so perhaps that netstat command is not the best test for this purpose. What should we actually be looking for in that output?

---

### Post by kevdog on 2008-06-04
Can you list some of your output?

---

### Post by michaelzap on 2008-06-04
> **kevdog said:**
> Can you list some of your output?

```

tcp        0      0 localhost:ipp           *:*                     LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     15495    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     14461    @/var/run/hald/dbus-f2AKU4g7XG
unix  2      [ ACC ]     STREAM     LISTENING     15780    /tmp/orbit-zap/linc-1982-0-4c4e01b41affe
unix  2      [ ACC ]     STREAM     LISTENING     15790    /tmp/orbit-zap/linc-1980-0-f5535f42e4b9
unix  2      [ ACC ]     STREAM     LISTENING     15958    /tmp/keyring-7uOen4/socket
unix  2      [ ACC ]     STREAM     LISTENING     15960    /tmp/keyring-7uOen4/ssh
unix  2      [ ACC ]     STREAM     LISTENING     15962    /tmp/keyring-7uOen4/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     16118    /tmp/orbit-zap/linc-1985-0-40202787d8120
unix  2      [ ACC ]     STREAM     LISTENING     16149    /tmp/seahorse-v2pkJj/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     16192    /tmp/orbit-zap/linc-1985-0-758942c1da17
unix  2      [ ACC ]     STREAM     LISTENING     16210    @/tmp/dbus-HhdFSnrCU1
unix  2      [ ACC ]     STREAM     LISTENING     16196    /tmp/.ICE-unix/6533
unix  2      [ ACC ]     STREAM     LISTENING     16257    /tmp/orbit-zap/linc-19c4-0-7e21cb1338355
unix  2      [ ACC ]     STREAM     LISTENING     20523    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     14363    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     20527    /tmp/pulse-zap/native
unix  2      [ ACC ]     STREAM     LISTENING     20568    /tmp/orbit-zap/linc-19cb-0-3ab62738f3583
unix  2      [ ACC ]     STREAM     LISTENING     20768    /tmp/orbit-zap/linc-19dc-0-4bb7ec38350fb
unix  2      [ ACC ]     STREAM     LISTENING     20955    /tmp/orbit-zap/linc-19e3-0-5992aefe9e4a4
unix  2      [ ACC ]     STREAM     LISTENING     21020    /tmp/orbit-zap/linc-19e5-0-5992aefec2676
unix  2      [ ACC ]     STREAM     LISTENING     21498    /tmp/orbit-zap/linc-1a26-0-65e5813cc592
unix  2      [ ACC ]     STREAM     LISTENING     21627    /tmp/orbit-zap/linc-1a32-0-65e5813c5fb3c
unix  2      [ ACC ]     STREAM     LISTENING     21681    /tmp/orbit-zap/linc-1a29-0-4855458966537
unix  2      [ ACC ]     STREAM     LISTENING     21687    /tmp/orbit-zap/linc-1a30-0-65e5813c66b50
unix  2      [ ACC ]     STREAM     LISTENING     23002    /tmp/orbit-zap/linc-1ad5-0-4f1af4ec27e8f
unix  2      [ ACC ]     STREAM     LISTENING     21903    /tmp/orbit-zap/linc-19e9-0-1f56dfada098c
unix  2      [ ACC ]     STREAM     LISTENING     14478    @/var/run/hald/dbus-6igr16Gd4Y
unix  2      [ ACC ]     STREAM     LISTENING     21954    /tmp/orbit-zap/linc-1a35-0-316c783b3210e
unix  2      [ ACC ]     STREAM     LISTENING     22025    /tmp/orbit-zap/linc-1a55-0-1b692d45cfd9f
unix  2      [ ACC ]     STREAM     LISTENING     22120    /tmp/orbit-zap/linc-1a5f-0-95c4a8cb37f8
unix  2      [ ACC ]     STREAM     LISTENING     23066    /tmp/orbit-zap/linc-1ad7-0-77042dc594ae8
unix  2      [ ACC ]     STREAM     LISTENING     23531    /tmp/orbit-zap/linc-1af5-0-a9d1cd0bb3a2
unix  2      [ ACC ]     STREAM     LISTENING     23592    /tmp/orbit-zap/linc-1b01-0-314755c229dc
unix  2      [ ACC ]     STREAM     LISTENING     23652    /tmp/orbit-zap/linc-1b05-0-314755c3af02
unix  2      [ ACC ]     STREAM     LISTENING     25473    /tmp/orbit-zap/linc-1b5d-0-1af66aeaf26ef
unix  2      [ ACC ]     STREAM     LISTENING     34229    /tmp/orbit-zap/linc-1c81-0-342c327e9be8
unix  2      [ ACC ]     STREAM     LISTENING     15293    @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     15457    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     24773    /home/zap/.geany/geany_socket
unix  2      [ ACC ]     STREAM     LISTENING     13932    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     15238    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     14217    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     15240    @/var/run/dbus-lK8V2RoUmV
unix  2      [ ACC ]     STREAM     LISTENING     14307    /var/run/avahi-daemon/socket

```

---

### Post by -grubby on 2008-06-05
Well, I would, if my ISP didn't block ports, even if I unblock them in my modem config (and no, I don't have a router, I have a hub)...

---

### Post by kevdog on 2008-06-05
Ive modified the netstat, grep statement, -- sorry about the confusion.

---

### Post by FuturePilot on 2008-06-05
Yes, I've installed a number of Server stuff on my server. SSH, Apache, PHP, proftpd, and MySQL.
```
tcp        0      0 *:mysql                 *:*                     LISTEN     
tcp        0      0 localhost:submission    *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:smtp          *:*                     LISTEN     
tcp        0      0 localhost:6010          *:*                     LISTEN     
tcp6       0      0 [::]:www                [::]:*                  LISTEN     
tcp6       0      0 [::]:ftp                [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 ip6-localhost:6010      [::]:*                  LISTEN     

```

---

### Post by Dr. C on 2008-06-05
I run on my Ubuntu box for starters:

1)  Samba to talk to the "dark side"
2)  Apache2, PHP, MySQL to test and develop websites
3)  DHCP for my home LAN 
4)  Bind9 I use my own DNS instead of my ISP's DNS. Not only is this faster, and more private, but I am ready in case my ISP decides to do evil things in the future such as monetize miss typed domains or mess around with Phorm / NebuAd. 

Running server services is one of the big advantages of GNU / Linux over the "dark side" especially for SOHO users.

---

### Post by akiratheoni on 2008-06-05
I do have apache installed but only to test backups and mods to my forum. It's not used for the public or anything.

---

### Post by ghindo on 2008-06-05
I'm messing with ssh and a spare box, so I've got that going on.  At the moment, I'm running rTorrent (and surprisingly, with only legal torrents! ;))

---

### Post by michaelzap on 2008-06-05
Just for comparison, here's the output from my Eee PC running the stock Xandros:

```
/home/user> netstat -a | grep LISTEN | grep -v unix
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:sunrpc                *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN

```

---

### Post by scorp123 on 2008-06-05
> **kevdog said:**
>  netstat -a | grep LISTEN | grep -v unix This one produces nicer output IMHO: ```
sudo lsof -n -i -P | grep LISTEN
```

---

### Post by HunterThomson on 2008-06-05
Well I was wrong in the poll.

I have cupsd, exim4, priveoxy and tor listening.

What are cupsd and exim4? More importantly should they be protected at all?

---

### Post by ghindo on 2008-06-05
> **HunterThomson said:**
> Well I was wrong in the poll.

I have cupsd, exim4, priveoxy and tor listening.

What are cupsd and exim4? More importantly should they be protected at all?Cupsd is the common unix printing system daemon.  It manages print jobs.

No idea about exim4.

---

### Post by HunterThomson on 2008-06-07
exim4 is used by evolution to fetch mail. So, it seems wile Ubuntu installs with no listening services it dose install services that will be listening once you click on them. 

evolution
bittorrent
instant messengers
remote desktop
remote desktop sharing
irc
rss feed reader
cups
...

---

### Post by Bachstelze on 2008-06-07
I always have at least SSH, since SCP/SFTP is a very convenient, low-hassle way to transfer files around a LAN. It's usually the only one I have for my non-server machines, and it's of course not open to the world.

---

### Post by insane_alien on 2008-06-07
i have SSH running. i like to be able to access my machine from anywhere(i have puTTY on a USB drive incase i can't get to a linux machine). never know when you might need an important file that you forgot or a game of frozenbubble.

---

### Post by billgoldberg on 2008-06-07
Well I have a upnp server (mediatomb) running on my desktop to stream music and videos to the ps3 and my laptop.

It's only accessible on my network, not to the outside.

And it goes without saying I've got transmission on most of the time.

---

### Post by spupy on 2008-06-07
```
X          4891  root    1u  IPv4   8813       TCP *:6000 (LISTEN)
mpd       26321 uibxn    3u  IPv4  65331       TCP 127.0.0.1:6600 (LISTEN)
```

I'm thinking of setting up ssh. Then I can leave my laptop in suspend mode sleeping in my dorm room. I can wake it up from anywhere, get/do whatever I need, and put it back to sleep.

EDIT: Forgot to say, this is not on Ubuntu, but on Gentoo. Too lazy to reboot in Ubuntu right now.

---

