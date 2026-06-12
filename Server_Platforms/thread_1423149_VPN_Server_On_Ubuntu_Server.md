---
title: "VPN Server On Ubuntu Server"
date: 2010-03-06
forum: Server Platforms
---

### Post by Doktor-X on 2010-03-06
Hi to all, i have one big problem i buy vps from santrex.net and wanna convert this vps to vpn server so that i can from my home pc have ip adress of vps and access to sites like hulu, problem is that i cant connect from my home pc to server i get error 806 i set my server like this:

first i rebuild server from centos to ubuntu 9.04 then i login to server like root with ssh and enter this commands
```
apt-get update
``````
apt-get install pptpd
```then i use command 
```
vi /etc/pptpd.conf
``` to edit file
```
localip "server ip"
remoteip 192.168.1.0-5
```then i edit file chap-secrets with command 
```
vi /etc/ppp/chap-secrets
```and add line like this
```
test pptpd 12345 *

```which meend that user name is test protocol is pptpd password is 12345 add * meens that all ip in defined range is allow
after that i open file sysctl.conf with command 
```
vi [FONT=courier new]/etc/sysctl.conf[/FONT]
```and uncommand net.ipv4.ip_forward=1
reboot system and try to connect on vpn from windows client but i get error 806

---

### Post by Doktor-X on 2010-03-11
anyone?
[LEFT][/LEFT]

---

### Post by HermanAB on 2010-03-11
Install sshd on the server and then configure a ssh sox proxy on your home machine.  Then simply tell Firefox to connect to the socks proxy on localhost.

---

### Post by Doktor-X on 2010-03-11
thanks for reply but this is not working for me, i meen i was able to make all to work but speed is low and hulu dont work
[LEFT][/LEFT]

---

### Post by Samatva on 2010-03-11
You can also use Apache as a proxy
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)

So are you trying to circumvent a firewall to watch TV at work? ;-)

---

### Post by Doktor-X on 2010-03-11
no i'm simply outside us and wanna wach hulu
[LEFT][/LEFT]

---

### Post by AlexanderTumanovsky on 2010-03-12
Maybe somebody will help.
I've setted up the pptpd same as you've described, but it accepts connections from vista/xp/se7en.

But faced another problem:

I use Dir-655 as router, it's ip is 192.168.1.1
Ubuntu Server ip is 192.168.1.4
VPN port and GRE forwarder to this ip from WAN.

PPTPD accepts incoming connection, user is authenticated, all is fine, except... internet.
Connected user can't go to any page, but ping and tracert works fine all over the world.

Any ideas?

ip_forward is enabled.

---

### Post by Doktor-X on 2010-03-14
ok guys after several days i manage to install squid proxy but still hulu dont work abc.com and others work but hulu not
[LEFT][/LEFT]

---

