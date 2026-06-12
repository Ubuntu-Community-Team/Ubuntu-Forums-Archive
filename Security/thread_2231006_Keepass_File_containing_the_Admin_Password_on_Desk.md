---
title: "Keepass File containing the Admin Password on Desktop good or bad?"
date: 2014-06-22
forum: Security
---

### Post by zerglinG734 on 2014-06-22
Hi,

Is it a good plan to keep a keepass file containing my Admin password on my desktop or is it better to type in the password by hand?

The reason why i am asking is because i started to notice  "strange things" happening on my netbook (Ubuntu 14.04).
My Netbook is connected to my modem/rooter and was the only machine connected to it all the time.

First thing i noticed was that my UFW controll interface seemed to turn off every hour or so without me closing the window.
Then the language changed from german to english.

Then i noticed some new entries in the reported listening section of my graphical ufw overlay.

I backup my system like every day and the only new programs i installed were google chrome, wine, sandboxie (tried to install it using wine but it did not work), firefox plus i installed a webcam and streamed using the platform justin.tv.
Also i changed from typing in the Admin password manually to using a keepassx file that i saved to my desktop.

Appart from that i didnot download anything messed up and used chrome because of the autosandbox for browsing.

Well the only other thing i did was exchanging files between my netbook and my android but i dont believe that my network is infected.

I will overwrite the partition with an older backup and try if i get the same firewall entries when doing the same stuff.

I will add all screenshots to the attachment section, sorry but putting it in the right place and uploading didnot work out for me right now and i am in a rush.
Also i will add a terminal codeline (i just realise it is in german but maybe it helps xD) i am happy for all the input to that thread.

Regards
zerglinG734

```

erzwo@erzwo:~$ apt-cache policy samba
samba:
  Installiert:           2:4.1.6+dfsg-1ubuntu2.14.04.1
  Installationskandidat: 2:4.1.6+dfsg-1ubuntu2.14.04.1
  Versionstabelle:
 *** 2:4.1.6+dfsg-1ubuntu2.14.04.1 0
        500 [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2:4.1.6+dfsg-1ubuntu2 0
        500 [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
erzwo@erzwo:~$ sudo netstat -tupan
[sudo] password for erzwo: 
Aktive Internetverbindungen (Server und stehende Verbindungen)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      2955/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      836/cupsd       
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      678/smbd        
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      678/smbd        
tcp        0      0 192.168.0.11:51544      64.15.113.114:443       VERBUNDEN   3149/chrome     
tcp        0      0 192.168.0.11:53999      64.15.113.98:443        VERBUNDEN   3149/chrome     
tcp6       0      0 ::1:631                 :::*                    LISTEN      836/cupsd       
tcp6       0      0 :::445                  :::*                    LISTEN      678/smbd        
tcp6       0      0 :::139                  :::*                    LISTEN      678/smbd        
udp        0      0 0.0.0.0:10723           0.0.0.0:*                           2949/dhclient   
udp        0      0 127.0.1.1:53            0.0.0.0:*                           2955/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           2949/dhclient   
udp        0      0 0.0.0.0:631             0.0.0.0:*                           935/cups-browsed
udp        0      0 0.0.0.0:59528           0.0.0.0:*                           823/avahi-daemon: r
udp        0      0 192.168.0.255:137       0.0.0.0:*                           3087/nmbd       
udp        0      0 192.168.0.11:137        0.0.0.0:*                           3087/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           3087/nmbd       
udp        0      0 192.168.0.255:138       0.0.0.0:*                           3087/nmbd       
udp        0      0 192.168.0.11:138        0.0.0.0:*                           3087/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           3087/nmbd       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3149/chrome     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           823/avahi-daemon: r
udp6       0      0 :::33610                :::*                                2949/dhclient   
udp6       0      0 :::38533                :::*                                823/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                823/avahi-daemon: r
erzwo@erzwo:~$ ps -fC smbd,nmbd
UID        PID  PPID  C STIME TTY          TIME CMD
root       678     1  0 21:54 ?        00:00:00 smbd -F
root       728   678  0 21:54 ?        00:00:00 smbd -F
root      3087     1  0 22:02 ?        00:00:00 nmbd -D
erzwo@erzwo:~$ sudo iptables-save
# Generated by iptables-save v1.4.21 on Sun Jun 22 22:13:30 2014
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [2:80]
:ufw-after-forward - [0:0]
:ufw-after-input - [0:0]
:ufw-after-logging-forward - [0:0]
:ufw-after-logging-input - [0:0]
:ufw-after-logging-output - [0:0]
:ufw-after-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-before-input - [0:0]
:ufw-before-logging-forward - [0:0]
:ufw-before-logging-input - [0:0]
:ufw-before-logging-output - [0:0]
:ufw-before-output - [0:0]
:ufw-logging-allow - [0:0]
:ufw-logging-deny - [0:0]
:ufw-not-local - [0:0]
:ufw-reject-forward - [0:0]
:ufw-reject-input - [0:0]
:ufw-reject-output - [0:0]
:ufw-skip-to-policy-forward - [0:0]
:ufw-skip-to-policy-input - [0:0]
:ufw-skip-to-policy-output - [0:0]
:ufw-track-forward - [0:0]
:ufw-track-input - [0:0]
:ufw-track-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-user-input - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
:ufw-user-logging-forward - [0:0]
:ufw-user-logging-input - [0:0]
:ufw-user-logging-output - [0:0]
:ufw-user-output - [0:0]
-A INPUT -j ufw-before-logging-input
-A INPUT -j ufw-before-input
-A INPUT -j ufw-after-input
-A INPUT -j ufw-after-logging-input
-A INPUT -j ufw-reject-input
-A INPUT -j ufw-track-input
-A FORWARD -j ufw-before-logging-forward
-A FORWARD -j ufw-before-forward
-A FORWARD -j ufw-after-forward
-A FORWARD -j ufw-after-logging-forward
-A FORWARD -j ufw-reject-forward
-A FORWARD -j ufw-track-forward
-A OUTPUT -j ufw-before-logging-output
-A OUTPUT -j ufw-before-output
-A OUTPUT -j ufw-after-output
-A OUTPUT -j ufw-after-logging-output
-A OUTPUT -j ufw-reject-output
-A OUTPUT -j ufw-track-output
-A ufw-after-input -p udp -m udp --dport 137 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 138 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp -m tcp --dport 139 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp -m tcp --dport 445 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 67 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 68 -j ufw-skip-to-policy-input
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input
-A ufw-after-logging-forward -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-after-logging-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 4 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-forward -j ufw-user-forward
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 4 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT
-A ufw-before-input -j ufw-not-local
-A ufw-before-input -d 224.0.0.251/32 -p udp -m udp --dport 5353 -j ACCEPT
-A ufw-before-input -d 239.255.255.250/32 -p udp -m udp --dport 1900 -j ACCEPT
-A ufw-before-input -j ufw-user-input
-A ufw-before-output -o lo -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -j ufw-user-output
-A ufw-logging-allow -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW ALLOW] "
-A ufw-logging-deny -m conntrack --ctstate INVALID -m limit --limit 3/min --limit-burst 10 -j RETURN
-A ufw-logging-deny -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP
-A ufw-reject-input -j REJECT --reject-with icmp-port-unreachable
-A ufw-skip-to-policy-forward -j DROP
-A ufw-skip-to-policy-input -j REJECT --reject-with icmp-port-unreachable
-A ufw-skip-to-policy-output -j ACCEPT
-A ufw-track-output -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-output -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable
-A ufw-user-limit-accept -j ACCEPT
COMMIT
# Completed on Sun Jun 22 22:13:30 2014

```

---

### Post by bashiergui on 2014-06-22
> Is it a good plan to keep a keepass file containing my Admin password on my desktop or is it better to type in the password by hand?It's a good plan to use keepass which encrypts the password database. It is also a good plan to memorize it and manually type it in. A bad plan would be to keep the password in a plain text file on your computer.

---

### Post by HermanAB on 2014-06-23
Keepassx and long randomized passwords are best.  Put the Keepassx database in dropbox or copy.com and then you can access it from everywhere.

---

### Post by sammiev on 2014-06-23
> **HermanAB said:**
> Keepassx and long randomized passwords are best.  Put the Keepassx database in dropbox or copy.com and then you can access it from everywhere.

I rather keep mine on a USB stick than on a cloud for backup.

---

### Post by slickymaster on 2014-06-23
> **sammiev said:**
> I rather keep mine on a USB stick than on a cloud for backup.

+1
That's also what I do.

---

### Post by HermanAB on 2014-06-25
The db is encrypted, so whether you use a schtick or the cloud, doesn't matter really, and it can be very inconvenient to plug a USB thingy into a cell phone for example.

---

