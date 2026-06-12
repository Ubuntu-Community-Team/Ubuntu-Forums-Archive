---
title: "Port Security Help"
date: 2007-12-01
forum: Server Platforms
---

### Post by phimurh on 2007-12-01
Can Someone Show Me How To Lock This Down

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-01 21:31 EST
Interesting ports on localhost (127.0.0.1):
Not shown: 1674 closed ports
PORT      STATE SERVICE
1/tcp     open  tcpmux
11/tcp    open  systat
15/tcp    open  netstat
79/tcp    open  finger
111/tcp   open  rpcbind
119/tcp   open  nntp
143/tcp   open  imap
540/tcp   open  uucp
631/tcp   open  ipp
635/tcp   open  unknown
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
6667/tcp  open  irc
12345/tcp open  NetBus
12346/tcp open  NetBus
27665/tcp open  Trinoo_Master
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11
54320/tcp open  bo2k

Nmap finished: 1 IP address (1 host up) scanned in 0.177 seconds

---

### Post by Cybergod on 2007-12-01
Install Firestarter, run 'sudo aptitiude install firestarter' from a terminal.  You can then access Firestarter by going to "System" -> "Administration" -> "Firestarter".

---

### Post by phimurh on 2007-12-01
> **Cybergod said:**
> Install Firestarter, run 'sudo aptitiude install firestarter' from a terminal.  You can then access Firestarter by going to "System" -> "Administration" -> "Firestarter".

I already have firestarter installed
what caused there ports to open?
Is there anyway to close them, permanently?
Just a pay ago i only had one ipp port open

---

### Post by Cybergod on 2007-12-02
> **phimurh said:**
> I already have firestarter installed
what caused there ports to open?
Is there anyway to close them, permanently?
Just a pay ago i only had one ipp port open

If you are on a LAN try scanning this computer with another one on your network.  Maybe you should check out this [link]("https://help.ubuntu.com/community/IptablesHowTo").

---

### Post by p_quarles on 2007-12-02
> **Cybergod said:**
> If you are on a LAN try scanning this computer with another one on your network.  Maybe you should check out this [link]("https://help.ubuntu.com/community/IptablesHowTo").
You don't even really need to use a different computer. You can just use nmap to scan your public IP address. You can get that [here]("http://www.ip-adress.com/"). Then:
```
sudo nmap -P0 *ip-address*
```
Note that that's a zero, not a capital "o".

If all those ports show up on a scan of the public IP address, then you've got something to worry about (and the "worry" here is that you've been rootkitted). If not, you're fine.

---

### Post by phimurh on 2007-12-02
> **p_quarles said:**
> You don't even really need to use a different computer. You can just use nmap to scan your public IP address. You can get that [here]("http://www.ip-adress.com/"). Then:
```
sudo nmap -P0 *ip-address*
```
Note that that's a zero, not a capital "o".

If all those ports show up on a scan of the public IP address, then you've got something to worry about (and the "worry" here is that you've been rootkitted). If not, you're fine.

I still received this

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-02 10:19 EST
sendto in send_ip_packet: sendto(5, packet, 44, 0, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51840 > **.***.***.**:6667 S ttl=37 id=53084 iplen=44  seq=4058308063 win=2048 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51841 > **.***.***.**:6667 S ttl=51 id=23268 iplen=44  seq=4058373598 win=4096 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51842 > **.***.***.**:6667 S ttl=45 id=11489 iplen=44  seq=4058439133 win=2048 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51843 > **.***.***.**:6667 S ttl=39 id=44453 iplen=44  seq=4058504668 win=4096 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51840 > **.***.***.**:79 S ttl=42 id=58170 iplen=44  seq=4058308063 win=3072 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51841 > **.***.***.**:79 S ttl=39 id=19458 iplen=44  seq=4058373598 win=4096 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51842 > **.***.***.**:79 S ttl=50 id=11647 iplen=44  seq=4058439133 win=3072 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, 0, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51843 > **.***.***.**:79 S ttl=44 id=48025 iplen=44  seq=4058504668 win=1024 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44,**.***.***.**.71, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51840 > **.***.***.**:1 S ttl=47 id=12308 iplen=44  seq=4058308063 win=4096 <mss 1460>
sendto in send_ip_packet: sendto(5, packet, 44, **.***.***.**, 16) => Operation not permitted
Offending packet: TCP 192.168.0.100:51841 > **.***.***.**:1 S ttl=57 id=28110 iplen=44  seq=4058373598 win=2048 <mss 1460>
Omitting future Sendto error messages now that 10 have been shown.  Use -d2 if you really want to see them.
Interesting ports on ***-**-***-***-***.***.***.**.*** (**.***.***.***):
Not shown: 1692 closed ports
PORT     STATE    SERVICE
1/tcp    filtered tcpmux
11/tcp   filtered systat
79/tcp   filtered finger
80/tcp   open     http
6667/tcp filtered irc

Nmap finished: 1 IP address (1 host up) scanned in 6.933 seconds

Any Ideas

---

### Post by p_quarles on 2007-12-02
It looks like only port 80 is actually open to the outside, and that would make sense if you're running a web server from somewhere on the LAN. If not, it would be a simple matter to close it off. 

Apart from that, though, all your ports are either closed or filtered. This is a typical situation for a LAN behind a NAT router. Not much to worry about in terms of ports.

---

### Post by phimurh on 2007-12-02
I often use large LAN's

within these i have gotten many NMAP and other vulnerability scans
i need to work under the assumption a router will not protect me

---

### Post by p_quarles on 2007-12-02
So I take it this is a laptop, then? 

The options are basically to use a firewall creating wizard like Firestarter, or manually configure your firewall rules with the iptables commands. While I took the latter route myself, I believe that Firestarter is capable of closing or stealthing ports on a 1-by-1, customized basis. 

I would also take a look at your startup services, and simply turn off anything that you won't be using. If you aren't sure what it does, don't turn it off, but if things like game servers and bluetooth are initializing at startup, you should have a good idea whether you need them or not. 

Finally, use some intrusion detection software, like Snort, if you aren't already. You say you've gotten vulnerability scans, so I'm assuming you are using something like this.

---

### Post by HermanAB on 2007-12-02
Well, there is nothing magical about ports on Linux.  The common 'port hangup' comes from the Windows world where no-one knows what the system is doing.  In Linux, it is pretty easy to see what is running with 'ps -e' and to stop daemons that are not needed with 'chkconfig'.

If you are worrying about 'open ports' then you are merely worrying about the symptom.  You should be worrying about the daemons that you are running instead.

Cheers,

Herman

---

### Post by phimurh on 2007-12-02
> **HermanAB said:**
> Well, there is nothing magical about ports on Linux.  The common 'port hangup' comes from the Windows world where no-one knows what the system is doing.  In Linux, it is pretty easy to see what is running with 'ps -e' and to stop daemons that are not needed with 'chkconfig'.

If you are worrying about 'open ports' then you are merely worrying about the symptom.  You should be worrying about the daemons that you are running instead.

Cheers,

Herman

when i used the ps-e the ports did not match up but how do i figure out which applications are running these processes. I don't care how it is done i just need to lock this down.

---

### Post by p_quarles on 2007-12-02
> **phimurh said:**
> when i used the ps-e the ports did not match up but how do i figure out which applications are running these processes. I don't care how it is done i just need to lock this down.
You don't need to match the ports to the processes. Herman's point is that the fact that a port is "open" on a *nix system is irrelevant. If a daemon isn't listening for requests on that port, every attempted connection will be silently ignored. 

So, the idea is that you need to find out if your system is inadvertently running an daemons (i.e., server software) that you don't need. If it is, you get rid of those processes.

---

### Post by phimurh on 2007-12-02
What daemons caused these and how do i close them down

my firewall log shows 
Ports 11,1,79 and 6667
being connected to by an IP 192.168.0.101
accessing services
Finger
TcpMux
Ircd
sysstat

---

### Post by phimurh on 2007-12-02
Who is search on connecting IP if that helps at all

 whois 192.168.0.101

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    IANA-CBLK1
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    [http://www.arin.net/reference/rfc/rfc1918.txt](http://www.arin.net/reference/rfc/rfc1918.txt)
RegDate:    1994-03-15
Updated:    2007-11-27

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  [email]abuse@iana.org[/email]

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  [email]abuse@iana.org[/email]

# ARIN WHOIS database, last updated 2007-12-01 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

---

### Post by p_quarles on 2007-12-02
Yeah, whois won't help because that's a LAN IP address. It either belongs to the router you're using (most likely) or someone else on the network. 

Don't know what's responsible for those connections, but if you can post the output of
```
 ps -e
```
I could at least try to give you some educated guesses.

---

### Post by phimurh on 2007-12-02
Hes the result
 ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:00 kacpid
   34 ?        00:00:00 kacpi_notify
  197 ?        00:00:00 kseriod
  224 ?        00:00:00 pdflush
  225 ?        00:00:00 pdflush
  226 ?        00:00:00 kswapd0
  277 ?        00:00:00 aio/0
  278 ?        00:00:00 aio/1
 2209 ?        00:00:02 ata/0
 2210 ?        00:00:00 ata/1
 2211 ?        00:00:00 ata_aux
 2216 ?        00:00:02 scsi_eh_0
 2217 ?        00:00:00 scsi_eh_1
 2243 ?        00:00:00 ksuspend_usbd
 2244 ?        00:00:00 khubd
 2278 ?        00:00:00 khpsbpkt
 2323 ?        00:00:00 scsi_eh_2
 2324 ?        00:00:00 scsi_eh_3
 2551 ?        00:00:00 kjournald
 2609 ?        00:00:00 knodemgrd_0
 2849 ?        00:00:00 udevd
 3920 ?        00:00:00 tifm
 4002 ?        00:00:00 kpsmoused
 4020 ?        00:00:00 pccardd
 4022 ?        00:00:00 ipw3945/0
 4023 ?        00:00:01 ipw3945/1
 4024 ?        00:00:00 ipw3945/0
 4025 ?        00:00:00 ipw3945/1
 4148 ?        00:00:02 ipw3945d-2.6.22
 4719 tty4     00:00:00 getty
 4720 tty5     00:00:00 getty
 4722 tty2     00:00:00 getty
 4723 tty3     00:00:00 getty
 4724 tty1     00:00:00 getty
 4728 tty6     00:00:00 getty
 4935 ?        00:00:00 acpid
 4978 ?        00:00:00 kondemand/0
 4979 ?        00:00:00 kondemand/1
 5054 ?        00:00:00 syslogd
 5108 ?        00:00:00 dd
 5110 ?        00:00:00 klogd
 5131 ?        00:00:00 dbus-daemon
 5147 ?        00:00:00 NetworkManager
 5161 ?        00:00:00 NetworkManagerD
 5174 ?        00:00:00 system-tools-ba
 5175 ?        00:00:00 dbus-daemon
 5194 ?        00:00:00 hald
 5195 ?        00:00:00 hald-runner
 5256 ?        00:00:00 hald-addon-keyb
 5257 ?        00:00:00 cupsd
 5259 ?        00:00:00 hald-addon-cpuf
 5260 ?        00:00:00 hald-addon-acpi
 5261 ?        00:00:00 hald-addon-keyb
 5262 ?        00:00:00 hald-addon-keyb
 5334 ?        00:00:00 sony-laptop
 5410 ?        00:00:00 console-kit-dae
 5493 ?        00:00:04 hald-addon-stor
 5500 ?        00:00:00 avahi-daemon
 5501 ?        00:00:00 hald-addon-keyb
 5502 ?        00:00:00 avahi-daemon
 5503 ?        00:00:00 hald-addon-keyb
 5504 ?        00:00:00 hald-addon-keyb
 5505 ?        00:00:00 hald-addon-keyb
 5519 ?        00:00:00 dhcdbd
 5539 ?        00:00:00 hcid
 5551 ?        00:00:00 bluetoothd-serv
 5552 ?        00:00:00 bluetoothd-serv
 5558 ?        00:00:00 krfcommd
 5591 ?        00:00:00 gdm
 5594 ?        00:00:00 gdm
 5599 tty7     00:01:49 Xorg
 5637 ?        00:00:00 atd
 5651 ?        00:00:00 cron
 5765 ?        00:00:00 gnome-keyring-d
 5768 ?        00:00:01 x-session-manag
 5803 ?        00:00:00 ssh-agent
 5805 ?        00:00:00 gconfd-2
 5809 ?        00:00:00 dbus-daemon
 5811 ?        00:00:00 gnome-settings-
 5817 ?        00:00:00 compiz
 5819 ?        00:00:04 gnome-panel
 5821 ?        00:00:02 nautilus
 5826 ?        00:00:00 gnome-volume-ma
 5830 ?        00:00:00 bonobo-activati
 5876 ?        00:00:00 gnome-vfs-daemo
 5918 ?        00:00:03 gtk-window-deco
 5919 ?        00:01:10 compiz.real
 5920 ?        00:00:03 gnome-screensav
 5927 ?        00:00:00 vino-session
 5928 ?        00:00:00 bluetooth-apple
 5930 ?        00:00:00 update-notifier
 5937 ?        00:00:00 evolution-alarm
 5939 ?        00:00:00 trackerd
 5942 ?        00:00:00 nm-applet
 5943 ?        00:00:00 python
 5946 ?        00:00:00 gnome-power-man
 5959 ?        00:00:00 trashapplet
 5976 ?        00:00:00 mapping-daemon
 5998 ?        00:00:00 evolution-excha
 6008 ?        00:00:00 evolution-data-
 6033 ?        00:00:00 fast-user-switc
 6035 ?        00:00:00 deskbar-applet
 6037 ?        00:00:00 mixer_applet2
 6104 ?        00:00:00 notification-da
 6852 ?        00:00:00 wpa_supplicant
 6853 ?        00:00:00 dhclient
 7616 ?        00:00:16 firestarter
 7618 ?        00:00:00 gconfd-2
 7886 ?        00:00:01 gnome-terminal
 7889 ?        00:00:00 gnome-pty-helpe
 7890 pts/1    00:00:00 bash
 7913 ?        00:00:00 firefox
 7925 ?        00:00:00 run-mozilla.sh
 7929 ?        00:01:37 firefox-bin
 8063 pts/2    00:00:00 bash
 8124 ?        00:00:11 pidgin
 8527 ?        00:00:03 gedit
 8863 pts/1    00:00:00 ps

---

### Post by p_quarles on 2007-12-02
That looks like a very standard process list. All of the daemons you are running are internal services, so are connected via localhost (i.e, not available to other computers). The only thing that I can see on there that would be accepting incoming connections is Pidgin, and that only from the servers associated with your IM accounts. I'm fairly certain (not 100%) that the services you asked about in post #13 are related to IM protocols. 

My others will want to weigh on this question, but I think your setup is perfectly secure as it is.

---

### Post by phimurh on 2007-12-02
I think you may be right. Nothing seems blatantly malicious. I will log connections and restricted new services.

If there are any security measures that are recomended please submit

---

### Post by p_quarles on 2007-12-02
Well, like I said earlier, Snort is a good intrusion detection utility. Consider running that if you're not already. Apart from that, the best thing to do is keep an eye on things. To instantly list current network connections, you can type:
```
netstat -tunva
```
And then, a sniffer like Wireshark is a good way of logging connections 
for later review. Finally, you might consider using Bastille to lock down permissions on your system a bit. Be careful with this, though, because if you make it too secure *you* won't be able to get in. :)

---

