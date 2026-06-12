---
title: "Shields Up! is showing port 443 open..."
date: 2005-11-13
forum: Server Platforms
---

### Post by mhancoc7 on 2005-11-13
Hi,
I have never really worried about security since I started using Ubuntu, and I have never had a problem. I recently decided to try out the firestarter firewall. That is when I came across the Shields Up! site. I expected to be fully stealthed. I found that most of my ports are closed. I have a few that are stealthed and I have 3 open ports. Port 22, 443, and 447. Is this a real problem?

Here are my system specs:

Compaq Armada 1750
Hoary 5.04
ASDL
wireless router
firestarter
dansguardian

Here are the results of 'netstat -l -np -p':

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN     6109/dansguardian
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5452/cupsd
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN     6093/tinyproxy
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     5777/master
udp        0      0 0.0.0.0:68              0.0.0.0:*                          6879/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     8007     5237/gdm            /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     8384     5419/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     9674     6110/dansguardian   /tmp/.dguardianipc
unix  2      [ ACC ]     STREAM     LISTENING     9675     6111/dansguardian   /tmp/.dguardianurlipc
unix  2      [ ACC ]     STREAM     LISTENING     10596    6604/ssh-agent      /tmp/ssh-ZJfQtf6559/agent.6559
unix  2      [ ACC ]     STREAM     LISTENING     10618    6610/gconfd-2       /tmp/orbit-mhancoc7/linc-19d2-0-40d926b24be9b
unix  2      [ ACC ]     STREAM     LISTENING     10628    6559/x-session-mana /tmp/orbit-mhancoc7/linc-199f-0-a7c050964992
unix  2      [ ACC ]     STREAM     LISTENING     10993    6559/x-session-mana /tmp/.ICE-unix/6559
unix  2      [ ACC ]     STREAM     LISTENING     11002    6652/gnome-keyring- /tmp/keyring-HC3RYF/socket
unix  2      [ ACC ]     STREAM     LISTENING     11011    6654/bonobo-activat /tmp/orbit-mhancoc7/linc-19fe-0-6e66c1249c9de
unix  2      [ ACC ]     STREAM     LISTENING     11030    6656/gnome-settings /tmp/orbit-mhancoc7/linc-1a00-0-2244b48c44369
unix  2      [ ACC ]     STREAM     LISTENING     11171    6694/metacity       /tmp/orbit-mhancoc7/linc-1a26-0-2bed5e977958
unix  2      [ ACC ]     STREAM     LISTENING     11216    6707/gnome-volume-m /tmp/orbit-mhancoc7/linc-1a33-0-3eccf4d06a0e5
unix  2      [ ACC ]     STREAM     LISTENING     11230    6705/nautilus       /tmp/orbit-mhancoc7/linc-1a31-0-3eccf4d09395d
unix  2      [ ACC ]     STREAM     LISTENING     11239    6703/gnome-panel    /tmp/orbit-mhancoc7/linc-1a2f-0-3eccf4d0e4fff
unix  2      [ ACC ]     STREAM     LISTENING     11261    6713/update-notifie /tmp/orbit-mhancoc7/linc-1a39-0-28e8a850dd9d7
unix  2      [ ACC ]     STREAM     LISTENING     11288    6715/gnome-cups-ico /tmp/orbit-mhancoc7/linc-1a3b-0-195e6d661f575
unix  2      [ ACC ]     STREAM     LISTENING     11328    6723/gnome-vfs-daem /tmp/orbit-mhancoc7/linc-1a43-0-79f74e3042bb4
unix  2      [ ACC ]     STREAM     LISTENING     11351    6729/mapping-daemon /tmp/mapping-mhancoc7
unix  2      [ ACC ]     STREAM     LISTENING     11369    6736/wnck-applet    /tmp/orbit-mhancoc7/linc-1a50-0-b9931bee2c84
unix  2      [ ACC ]     STREAM     LISTENING     11408    6739/notification-a /tmp/orbit-mhancoc7/linc-1a53-0-3d511e061860
unix  2      [ ACC ]     STREAM     LISTENING     11438    6742/gweather-apple /tmp/orbit-mhancoc7/linc-1a56-0-6d4f5744287a8
unix  2      [ ACC ]     STREAM     LISTENING     11648    6752/clock-applet   /tmp/orbit-mhancoc7/linc-1a60-0-ad2f034d1b1a
unix  2      [ ACC ]     STREAM     LISTENING     8577     5572/dbus-daemon-1  /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     11658    6746/battstat-apple /tmp/orbit-mhancoc7/linc-1a5a-0-ad2f034e4ad3
unix  2      [ ACC ]     STREAM     LISTENING     11669    6744/gnome-netstatu /tmp/orbit-mhancoc7/linc-1a58-0-ad2f0cb4455
unix  2      [ ACC ]     STREAM     LISTENING     11683    6748/multiload-appl /tmp/orbit-mhancoc7/linc-1a5c-0-3419897f26764
unix  2      [ ACC ]     STREAM     LISTENING     11695    6750/trashapplet    /tmp/orbit-mhancoc7/linc-1a5e-0-3419897f45ec5
unix  2      [ ACC ]     STREAM     LISTENING     11783    6759/stickynotes_ap /tmp/orbit-mhancoc7/linc-1a67-0-2e6f884220a
unix  2      [ ACC ]     STREAM     LISTENING     9157     5777/master         public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     11799    6761/mixer_applet2  /tmp/orbit-mhancoc7/linc-1a69-0-6cf2180127f4f
unix  2      [ ACC ]     STREAM     LISTENING     18343    7669/gconfd-2       /tmp/orbit-root/linc-1df5-0-1676d3b9c8691
unix  2      [ ACC ]     STREAM     LISTENING     18351    7667/firestarter    /tmp/orbit-root/linc-1df3-0-2f0be63bcd2f8
unix  2      [ ACC ]     STREAM     LISTENING     19023    8187/galeon         /tmp/orbit-mhancoc7/linc-1ffb-0-2584b4ea6d22
unix  2      [ ACC ]     STREAM     LISTENING     20948    8334/gnome-terminal /tmp/orbit-mhancoc7/linc-208e-0-57b81273662
unix  2      [ ACC ]     STREAM     LISTENING     9164     5777/master         private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     9172     5777/master         private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     10601    6608/dbus-daemon-1  @/tmp/dbus-jullwLrtsa
unix  2      [ ACC ]     STREAM     LISTENING     9176     5777/master         private/defer
unix  2      [ ACC ]     STREAM     LISTENING     9180     5777/master         private/trace
unix  2      [ ACC ]     STREAM     LISTENING     9184     5777/master         private/verify
unix  2      [ ACC ]     STREAM     LISTENING     9188     5777/master         public/flush
unix  2      [ ACC ]     STREAM     LISTENING     9192     5777/master         private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     9196     5777/master         private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     9200     5777/master         private/relay
unix  2      [ ACC ]     STREAM     LISTENING     9204     5777/master         public/showq
unix  2      [ ACC ]     STREAM     LISTENING     9208     5777/master         private/error
unix  2      [ ACC ]     STREAM     LISTENING     9212     5777/master         private/local
unix  2      [ ACC ]     STREAM     LISTENING     9216     5777/master         private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     9220     5777/master         private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     9224     5777/master         private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     9228     5777/master         private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     9232     5777/master         private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     9236     5777/master         private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     9240     5777/master         private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     9244     5777/master         private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     11055    6659/gam_server     @/tmp/fam-mhancoc7-
```

I look forward to hearing back.

Thanks in advance, God Bless, Jereme

---

### Post by zman58 on 2005-11-13
It is interesting that you mention a wireless router. Think about what you are testing with "Shields UP"--which is a web based test. If your UBUNTU system is going through the router, then you may be testing the firewall -on the ISP side of the router-. That is to say you may be testing the router's firewall. If you want to use Shields Up to test the UBUNTU system with firestarter, then you would have to connect the UBUNTU system directly to the internet.

I use UBUNTU on my main server that is connected directly to my cable modem. The eth0 interface is connected directly to the ISP through the cable modem. The eth1 interface on my main server feeds an internal subnet through a network switch with several other systems attached to the switch.

---

### Post by mhancoc7 on 2005-11-13
Thank you so much. That puts my mind at ease. I tried to connect my laptop directly to my cable modem using a usb adapter which is what I was using before I got my wireless. For some reason I could not get it to work. Since I am going to continue using my wireless router I decided that it was not worth trying figure out why the usb adapter is not working now.

I also ran ClamAv just to give it a try. It only came up with one Oversized Zip file. It is a Damn Small Linux download so I believe that it is probably a bogie like mentioned on the ClamAv FAQ.

I also have firestarter installed just to try it as well. I know that it is all probably overkill, but I figure that it never hurts to have extra security.

Is there anything that I should be concerned about concerning my wireless connection?

I really appreciate your help with this.

God Bless, Jereme

---

### Post by Zerocool10482 on 2005-11-14
I connected directly to my dsl and I fail. Is there away to be stealth.

---

### Post by jdong on 2005-11-14
Sure, install Firestarter or be really brave and configure Shorewall....

There's typically no good reason to be "stealth" because it doesn't afford you any new sense of security. Closed ports are NOT exploitable in any way, and as soon as you reach out and talk to another computer (like visiting a website), it doesn't take Einstein as a server admin to figure out that you exist!

---

### Post by Zerocool10482 on 2005-11-15
Thank's I've been using Firestarter at the start. I wish ubuntu had it install on boot.

---

