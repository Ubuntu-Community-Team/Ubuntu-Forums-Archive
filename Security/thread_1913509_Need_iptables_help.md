---
title: "Need iptables help"
date: 2012-01-22
forum: Security
---

### Post by jpdeaton on 2012-01-22
I am very new to this. I am trying to setup iptables for my laptop on a home network. I've basically done as much as i can without help. Once i execute all the rules I lose all internet. I'm not asking for anyone to write it for me, I just need to be pointed in the right direction. I've read a few of the tutorial IP tables threads as well as the stick.

[B]iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP[/B]
	
	```
Chain INPUT (policy DROP)
	target     prot opt source               destination         

	Chain FORWARD (policy DROP)
	target     prot opt source               destination         

	Chain OUTPUT (policy DROP)
	target     prot opt source               destination 
```

[B]iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
[/B]
	```
Chain INPUT (policy DROP)
	target     prot opt source               destination         
	ACCEPT     all  --  anywhere             anywhere ctstate RELATED,ESTABLISHED 

	Chain FORWARD (policy DROP)
	target     prot opt source               destination         

	Chain OUTPUT (policy DROP)
	target     prot opt source               destination         
	ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
```

[B]iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
iptables -A OUTPUT -p tcp -m state --state NEW --dport 443 -j ACCEPT
iptables -A OUTPUT -p tcp -m state --state NEW --dport 53 -j ACCEPT
iptables -A OUTPUT -p udp -m state --state  NEW --dport 53 -j ACCEPT
iptables -A OUTPUT -p udp -m state --state  NEW --dport 67 -j ACCEPT
iptables -A INPUT -p udp -m state --state NEW --dport 67 -j ACCEPT
iptables -A OUTPUT -p udp -m state --state  NEW --dport 68 -j ACCEPT
iptables -A INPUT -p udp -m state --state NEW --dport 68 -j ACCEPT
iptables -A INPUT -p tcp --dport ssh -j ACCEPT[/B]

	```
Chain INPUT (policy DROP)
	target     prot opt source               destination         
	ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
	ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www state NEW 
	ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:bootps 
	ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:bootpc 
	ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 

	Chain FORWARD (policy DROP)
	target     prot opt source               destination         

	Chain OUTPUT (policy DROP)
	target     prot opt source               destination         
	ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
	ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:https 
	ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:domain 
	ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:domain 
	ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:bootps 
	ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:bootpc 
```

**I run -netstat -atpvn**(I cannot load a page in the browser)
```
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      980/cupsd       
tcp        0      1 192.168.1.3:46xx6       xx.xxx.216.119:80       SYN_SENT    3066/firefox    
tcp        0      1 192.168.1.3:33xxx       xx.xxx.94.12:80         SYN_SENT    3083/chrome     
tcp        0      0 192.168.1.3:xxxxx       xxx.xxx.167.5:443        TIME_WAIT   -               
tcp        0      1 192.168.1.3:4xx63       xxx.x.55.72:80          SYN_SENT    3083/chrome     
tcp        0      0 192.168.1.3:35xx8       xx.xxx.159.139:443      ESTABLISHED 3083/chrome     
tcp        0      0 192.168.1.3:3xx02       xx.xxx.159.139:443      TIME_WAIT   -               
tcp        0      1 192.168.1.3:4xx76       xxx.xx.52.190:80         SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:3xx13       xx.xxx.65.125:5222      SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:3xx75       xx.xx9.x4.12:80         SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:3xx73       xx.xxx.x4.12:80         SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:5xx73       xxx.xxx.52.196:80       SYN_SENT    3083/chrome     
tcp        0      0 192.168.1.3:36xx6       xx.xxx.47.103:4xx      TIME_WAIT   -               
tcp        0      1 192.168.1.3:38xx1       xx.xxx.xx9.239:80       SYN_SENT    3083/chrome     
tcp        0      0 192.168.1.3:60xx1       xx.xx.181.105:44x       TIME_WAIT   -               
tcp        0      1 192.168.1.3:38xx9       xx.xxx.23x.239:80       SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:575xx       1xx.x.xx.1xx:80         SYN_SENT    3083/chrome    
tcp        0      1 192.168.1.3:57xxx       xxx.xxx.x2.1xx:80       SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:389xx       xx.xxx.x5.xx5:522xx      SYN_SENT    3083/chrome     
tcp        0      0 192.168.1.3:548xx       xxx.1xx.x4.81:44xx       ESTABLISHED 3083/chrome     
tcp        0      1 192.168.1.3:407xx       xxx.x.x8.xx0:80         SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:508xx       xx.xx5.x5.1xx:8x        SYN_SENT    3083/chrome     
tcp        1      0 192.168.1.3:398xx       7x.1xx.4x.xx5:xx3       CLOSE_WAIT  2261/gvfsd-http 
tcp        0      1 192.168.1.3:575xx       1xx.7.x9.xx0:80         SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:415xx       1xx.7.5x.7x:80          SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:331xx       x1.xx9.x4.x2:80         SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:465xx       xx.1xx.2xx.xx9:80       SYN_SENT    3066/firefox    
tcp        0      1 192.168.1.3:415xx       xxx.xx.x5.7x:80          SYN_SENT    3083/chrome     
tcp        0      0 192.168.1.3:602xx       xx.1x.xx7.5:x3        TIME_WAIT   -               
tcp        0      0 192.168.1.3:548xx       xxx.1x4.9x.8x:44x       TIME_WAIT   -               
tcp        0      1 192.168.1.3:xxxxx       xx.xx.xx.7x:8x          SYN_SENT    3083/chrome     
tcp        0      1 192.168.1.3:xxxxx       x1x.x.7x.xx0:80         SYN_SENT    3083/chrome     
tcp6       0      0 ::1:631                 :::*                    LISTEN      980/cupsd 
```

When i clear all the rules I don't have internet... i get this error:

	This webpage is not available
The server at ubuntuforums.org can't be found, because the DNS lookup failed. DNS is the network service that translates a website's name to its Internet address. This error is most often caused by having no connection to the Internet or a misconfigured network. It can also be caused by an unresponsive DNS server or a firewall preventing Google Chrome from accessing the network. Once I restart i get internet back.

---

### Post by CharlesA on 2012-01-22
Are you using that machine as a proxy or something?

---

### Post by Dangertux on 2012-01-22
Try this script and tell me if it works.

```

#!/bin/bash

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 67 -j ACCEPT
iptables -A OUTPUT -p udp --dport 67 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT

# Add any other ports you need to reach external services in the format above

```Hope this helps

---

### Post by jpdeaton on 2012-01-22
awesome that works! what's the best way to save the script and have it load at startup? Are there any other ways to add security through iptables that is fairly simple?

Thanks

---

### Post by Dangertux on 2012-01-22
> **jpdeaton said:**
> It's not a proxy, it's mainly used for browsing, I just want a strong firewall.
 I'll give that script a try. I know there has to be an easier way to do it than copy/pasting each line into the terminal.. do you know of anything?

copy and past that whole block of text into a file call it iptables.sh

do the following in a terminal

```

sudo chmod 755 iptables.sh
sudo ./iptables.sh

```

---

### Post by jpdeaton on 2012-01-22
I saved it in my user forum... should I change it from ./home to ./home/bluntmaster? Or do I need to move the file? ok well only ./iptables.sh works. 

Any idea what this connection is that netstat shows?

tcp6       0      0 ::1:631                 :::*                    LISTEN

---

### Post by Dangertux on 2012-01-22
> **jpdeaton said:**
> I saved it in my user forum... should I change it from ./home to ./home/bluntmaster? Or do I need to move the file? ok well only ./iptables.sh works. 

Any idea what this connection is that netstat shows?

tcp6       0      0 ::1:631                 :::*                    LISTEN

That is the Common Unix Printing Service otherwise known as CUPS


As far as making you rules persistent 

> 
Making your rules persistent :

If you want these rules to be restored on every reboot you can do the following. 
code : sudo iptables-save > /etc/iptables.rules
     Code:
     sudo nano /etc/network/interfaces 
Assuming wlan0 is the interface you use to connect to the network  add the following at the end of the block. Alternatively you can add it  to any interface you want and the rules will be loaded when that  interface is brought up. Keep in mind this does not change the nature of  the rules, or how they are applied.

     Code:
     pre-up iptables-restore < /etc/iptables.rules 
Then save the file.

This bit of information as well as other ways for making your iptables rules persistent can be found here : [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

We're done.
[B]

From my thread here [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)
[/B]

---

### Post by jpdeaton on 2012-01-22
> **CharlesA said:**
> Are you using that machine as a proxy or something?

No, it's mainly for web browsing.

I got the whole saving/startup thing figured out but I'm not sure the best way to log... it seems a lot of the methods involve changing the existing scripts.

---

### Post by CharlesA on 2012-01-22
I just use iptables-apply with a rules file (created with iptables-save) instead of a script, and have it applied when the interface comes up.

[http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html](http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html)

---

### Post by jpdeaton on 2012-01-22
Thanks everyone. 

Now that I have a firewall up and running what would be the next step towards making my laptop more secure? There's so much info I don't know where to start. 

maybe apparmor?

---

### Post by Dangertux on 2012-01-22
Apparmor or browser security (though they can go hand in hand) are good spots to pick up. Apparmor may be a little difficult if you had trouble with iptables but you can give it a shot. 

Also check out [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Might help. Have fun

---

### Post by jpdeaton on 2012-01-23
I finished a clean install less than an hour ago. I did all the updates and had iptables setup before connecting to the internet.

**rkhunter -c shows**:

/usr/bin/unhide.rb                                       [ Warning ]
Checking for passwd file changes                         [ Warning ]
   Checking for group file changes                          [ Warning ]
 Checking for hidden files and directories                [ Warning ]

**chkrootkit shows:**
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED

 The following suspicious files and directories were found:  /usr/lib/pymodules/python2.7/.path /usr/lib/jvm/.java-1.6.0-openjdk.jinfo

wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[892], /sbin/dhclient (deleted)[2596])

user bluntman deleted or never logged from lastlog!

 The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         1146 tty7   /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none





Any idea what gvfsd is and how to get rid of it?

sudo netstat -antp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      17997/cupsd     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      9374/master     
tcp        0      0 192.168.1.3:51495       74.125.45.105:80        ESTABLISHED 30531/firefox   
tcp        1      0 192.168.1.3:34902       91.189.89.31:80         CLOSE_WAIT  2738/gvfsd-http 
tcp        0      0 192.168.1.3:51497       74.125.45.105:80        ESTABLISHED 30531/firefox   
tcp       38      0 192.168.1.3:45520       91.189.89.106:443       CLOSE_WAIT  2738/gvfsd-http 
tcp        1      0 192.168.1.3:43680       91.189.89.106:80        CLOSE_WAIT  2738/gvfsd-http 
tcp       38      0 192.168.1.3:45529       91.189.89.106:443       CLOSE_WAIT  2738/gvfsd-http 
tcp        1      0 192.168.1.3:43684       91.189.89.106:80        CLOSE_WAIT  2738/gvfsd-http 
tcp       38      0 192.168.1.3:40269       91.189.89.105:443       CLOSE_WAIT  2738/gvfsd-http 
tcp        1      0 192.168.1.3:34896       91.189.89.31:80         CLOSE_WAIT  2738/gvfsd-http 
tcp        0      0 192.168.1.3:51496       74.125.45.105:80        ESTABLISHED 30531/firefox   
tcp        1      0 192.168.1.3:46644       91.189.89.105:80        CLOSE_WAIT  2738/gvfsd-http 
tcp6       0      0 ::1:631

 sudo lsof -i -n -P
COMMAND     PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae   757    avahi   13u  IPv4    668      0t0  UDP *:5353 
avahi-dae   757    avahi   14u  IPv6    669      0t0  UDP *:5353 
avahi-dae   757    avahi   15u  IPv4    670      0t0  UDP *:41723 
avahi-dae   757    avahi   16u  IPv6    671      0t0  UDP *:58306 
dhclient   2596     root    6u  IPv4  19190      0t0  UDP *:68 
gvfsd-htt  2738 bluntman    9u  IPv4  70179      0t0  TCP 192.168.1.3:45520->91.189.89.106:443 (CLOSE_WAIT)
gvfsd-htt  2738 bluntman   12u  IPv4  70180      0t0  TCP 192.168.1.3:34896->91.189.89.31:80 (CLOSE_WAIT)
gvfsd-htt  2738 bluntman   14u  IPv4  72916      0t0  TCP 192.168.1.3:40269->91.189.89.105:443 (CLOSE_WAIT)
gvfsd-htt  2738 bluntman   15u  IPv4  72944      0t0  TCP 192.168.1.3:34902->91.189.89.31:80 (CLOSE_WAIT)
gvfsd-htt  2738 bluntman   16u  IPv4  71607      0t0  TCP 192.168.1.3:46644->91.189.89.105:80 (CLOSE_WAIT)
gvfsd-htt  2738 bluntman   17u  IPv4  70212      0t0  TCP 192.168.1.3:43680->91.189.89.106:80 (CLOSE_WAIT)
gvfsd-htt  2738 bluntman   18u  IPv4  73878      0t0  TCP 192.168.1.3:45529->91.189.89.106:443 (CLOSE_WAIT)
gvfsd-htt  2738 bluntman   20u  IPv4  73879      0t0  TCP 192.168.1.3:43684->91.189.89.106:80 (CLOSE_WAIT)
master     9374     root   12u  IPv4  76749      0t0  TCP *:25 (LISTEN)
http       9638     root    3u  IPv4 568608      0t0  TCP 192.168.1.3:46074->204.45.82.194:80 (CLOSE_WAIT)
http       9639     root    3u  IPv4 571616      0t0  TCP 192.168.1.3:45523->91.189.92.169:80 (ESTABLISHED)
cupsd     17997     root    9u  IPv6  48150      0t0  TCP [::1]:631 (LISTEN)
cupsd     17997     root   10u  IPv4  48151      0t0  TCP 127.0.0.1:631 (LISTEN)
firefox   30531 bluntman   63u  IPv4 566986      0t0  TCP 192.168.1.3:46659->74.125.47.139:80 (ESTABLISHED)
firefox   30531 bluntman   64u  IPv4 566987      0t0  TCP 192.168.1.3:43649->74.125.65.139:80 (ESTABLISHED)

---

### Post by Dangertux on 2012-01-23
It's a backend for the gvfs hal. Basically it allows you to mount USB and other devices in a dav like fashion.

---

### Post by jpdeaton on 2012-01-29
how would i allow IMAP port 993 and SMTP port 465 for email/thunderbird?

---

### Post by Dangertux on 2012-01-29
If you look back at the original script I gave you

```

#!/bin/bash

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 67 -j ACCEPT
iptables -A OUTPUT -p udp --dport 67 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT

# Add any other ports you need to reach external services in the format above

```

it contains a comment that explains how to allow other external services.

so your format is basically

```

iptables -A OUTPUT -p tcp --dport $portnumber -j ACCEPT

```

Does that make sense?

---

### Post by jpdeaton on 2012-01-29
yea, thanks

---

