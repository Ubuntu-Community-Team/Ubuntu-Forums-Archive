---
title: "Another PPTPD issue"
date: 2010-09-22
forum: Server Platforms
---

### Post by hamilton.jason on 2010-09-22
Hello, I am trying to vpn into my server from a remote host(android cell phone and macbook pro). Both are failing. Logs i am getting are listed below. Looks like it is going through but then fails with a GRE: Bad Checksum. i searched through the forums but nothing exactly fits. Might be an issue with iptables but im not sure what i need to read off. If anybody can assist me with this, that would be awesome. Let me know if you need more data. 

Hardware of server: dell 4400 (old pc) running newest ubuntu server (10.0.4.1 i think). 32 bit. 


Sep 22 12:16:30 homeserver pptpd[7600]: MGR: Launching /usr/sbin/pptpctrl to handle client
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: local address = 192.168.1.105
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: remote address = 192.168.1.110
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: pppd options file = /etc/ppp/pptpd-options
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Client XXXXXXXX control connection started
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Received PPTP Control Message (type: 1)
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Made a START CTRL CONN RPLY packet
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: I wrote 156 bytes to the client.
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Sent packet to client
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Received PPTP Control Message (type: 7)
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Set parameters to 100000000 maxbps, 8192 window size
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Made a OUT CALL RPLY packet
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Starting call (launching pppd, opening GRE)
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: pty_fd = 6
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: tty_fd = 7
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: I wrote 32 bytes to the client.
Sep 22 12:16:30 homeserver pptpd[7602]: CTRL (PPPD Launcher): program binary = /usr/sbin/pppd
Sep 22 12:16:30 homeserver pptpd[7602]: CTRL (PPPD Launcher): local address = 192.168.1.105
Sep 22 12:16:30 homeserver pptpd[7602]: CTRL (PPPD Launcher): remote address = 192.168.1.110
Sep 22 12:16:30 homeserver pptpd[7600]: CTRL: Sent packet to client
Sep 22 12:16:30 homeserver pptpd[7600]: GRE: Bad checksum from pppd.
Sep 22 12:17:00 homeserver pptpd[7600]: GRE: read(fd=6,buffer=805a540,len=8196) from PTY failed: status = -1 error = Input/output error, usual$
Sep 22 12:17:00 homeserver pptpd[7600]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Sep 22 12:17:00 homeserver pptpd[7600]: CTRL: Reaping child PPP[7602]
Sep 22 12:17:00 homeserver pptpd[7600]: CTRL: Client XXXXXXXXXX control connection finished
Sep 22 12:17:00 homeserver pptpd[7600]: CTRL: Exiting now
Sep 22 12:17:00 homeserver pptpd[7597]: MGR: Reaped child 7600

---

### Post by hamilton.jason on 2010-09-22
Current settings for pptpd: anyone see anything wrong? (username/pass altered)

root@homeserver:/# egrep -v '#|^ *$' /etc/ppp/pptpd-options
name homeserver
ms-dns 204.13.248.76
ms-dns 204.13.249.76
proxyarp
nodefaultroute
debug
lock
mtu 1490
mru 1490
noauth
root@homeserver:/#

root@homeserver:/# egrep -v '#|^ *$' /etc/pptpd.conf
ppp /usr/sbin/pppd
option /etc/ppp/pptpd-options
debug
stimeout 10
logwtmp
bcrelay eth1
localip 192.168.1.105
remoteip 192.168.1.110-114

root@homeserver:/# egrep -v '#|^ *$' /etc/ppp/chap-secrets
user0           homeserver      ##########              *
user1           homeserver      ##########              *
root@homeserver:/#

---

### Post by hamilton.jason on 2010-09-22
Something scary. Checking my daemon.log and i see the below read out. Thats not my ip, nor was i attempting to log in at that time. Brasiltelecom is what pen testing shows. All 1000 ports filtered. hmm... barely up for a week and already getting hit.

Sep 22 17:45:17 homeserver in.telnetd[7826]: connect from 189.73.97.4 (189.73.97.4)
Sep 22 17:45:18 homeserver telnetd[7826]: ttloop: peer died: EOF
Sep 22 17:45:20 homeserver in.telnetd[7828]: connect from 189.73.97.4 (189.73.97.4)
Sep 22 17:45:21 homeserver telnetd[7828]: ttloop: peer died: EOF

---

### Post by hamilton.jason on 2010-09-23
Still unable to log in. Did alot of troubleshooting but still getting same push back. 

I believe this is the issue:

Sep 23 09:42:13 homeserver pppd[30871]: LCP: timeout sending   Config-Requests

Sep 23 09:41:43 homeserver pppd[30871]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Sep 23 09:41:43 homeserver pppd[30871]: pptpd-logwtmp: $Version$
Sep 23 09:41:43 homeserver pppd[30871]: pppd options in effect:
Sep 23 09:41:43 homeserver pppd[30871]: debug debug#011#011# (from /etc/ppp/pptpd-options)
Sep 23 09:41:43 homeserver pppd[30871]: dump#011#011# (from /etc/ppp/pptpd-options)
Sep 23 09:41:43 homeserver pppd[30871]: plugin /usr/lib/pptpd/pptpd-logwtmp.so#011#011# (from command line)
Sep 23 09:41:43 homeserver pppd[30871]: name homeserver#011#011# (from /etc/ppp/pptpd-options)
Sep 23 09:41:43 homeserver pppd[30871]: pptpd-original-ip XXXXXXXXXX#011#011# (from command line)
Sep 23 09:41:43 homeserver pppd[30871]: 115200#011#011# (from command line)
Sep 23 09:41:43 homeserver pppd[30871]: lock#011#011# (from /etc/ppp/pptpd-options)
Sep 23 09:41:43 homeserver pppd[30871]: local#011#011# (from command line)
Sep 23 09:41:43 homeserver pppd[30871]: asyncmap 0#011#011# (from /etc/ppp/options)
Sep 23 09:41:43 homeserver pppd[30871]: mru 542#011#011# (from /etc/ppp/options)
Sep 23 09:41:43 homeserver pppd[30871]: hide-password#011#011# (from /etc/ppp/options)
Sep 23 09:41:43 homeserver pppd[30871]: ipcp-accept-local#011#011# (from /etc/ppp/options)
Sep 23 09:41:43 homeserver pppd[30871]: ipcp-accept-remote#011#011# (from /etc/ppp/options)
Sep 23 09:41:43 homeserver pppd[30871]: ipparam 166.188.19.121#011#011# (from command line)
Sep 23 09:41:43 homeserver pppd[30871]: ms-dns xxx # [don't know how to print value]#011#011# (from /etc/ppp$
Sep 23 09:41:43 homeserver pppd[30871]: proxyarp#011#011# (from /etc/ppp/pptpd-options)
Sep 23 09:41:43 homeserver pppd[30871]: 192.168.1.105:192.168.1.110#011#011# (from command line)
Sep 23 09:41:43 homeserver pppd[30871]: noipx#011#011# (from /etc/ppp/options)
Sep 23 09:41:43 homeserver pppd[30871]: pppd 2.4.5 started by root, uid 0
Sep 23 09:41:43 homeserver pppd[30871]: Using interface ppp0
Sep 23 09:41:43 homeserver pppd[30871]: Connect: ppp0 <--> /dev/pts/1
Sep 23 09:42:13 homeserver pppd[30871]: LCP: timeout sending   Config-Requests
Sep 23 09:42:13 homeserver pppd[30871]: Connection terminated.
Sep 23 09:42:14 homeserver pppd[30871]: Modem hangup
Sep 23 09:42:14 homeserver pppd[30871]: Exit.

---

### Post by Groodles on 2010-09-23
What sort of device do you have between the Ubuntu PPTP Server and the internet?

(ADSL/Cable Modem/Router?)

And does that device allow GRE (Protocol 47) pass-through?

Many SOHO ADSL/Cable modem/routers do NOT allow GRE traffic by default (if at all!).

---

### Post by hamilton.jason on 2010-09-23
I am using an airlink101 wireless router. It has the option for vpn, ipsec, and l2tp passthrough. I would assume that means it is not going to block GRE. I have time warner cable, they have this tiny little black box that doesnt have any interface on it. Its a converter box i believe because it takes the cable and converts it over to an ethernet cable. So from the wall it goes to the black box, from the black box to the router, from the router to the server. 

Did a tcp dump but looks like gibberish in that file format. I need to convert it to txt. Guide i was looking at uses ethereal but i dont see an ubuntu version. Anyone have any other program that does it.

root@homeserver:/# tcpdump -i eth0 -w my.tcpdump -s 0 tcp port 1723 or proto 47
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
^C24 packets captured
24 packets received by filter
0 packets dropped by kernel

root@homeserver:/# ethereal my.tcpdump
ethereal: command not found
root@homeserver:/# apt-get ethereal
E: Invalid operation ethereal

---

### Post by hamilton.jason on 2010-09-23
This is my TCP dump from when my phone tries to connected to my vpn server. Everything looks fine to me. 
Also this is a log from my var/log/messages

Notice the LCP: timeout sending Config-Requests which i believe is causing the issue. Might be an iptables issue. Anyone have an example of a good iptables?

Sep 23 15:11:33 homeserver pppd[31282]: pppd 2.4.5 started by root, uid 0
Sep 23 15:11:33 homeserver pppd[31282]: Using interface ppp0
Sep 23 15:11:33 homeserver pppd[31282]: Connect: ppp0 <--> /dev/pts/2
Sep 23 15:12:03 homeserver pppd[31282]: LCP: timeout sending Config-Requests
Sep 23 15:12:03 homeserver pppd[31282]: Connection terminated.
Sep 23 15:12:03 homeserver pppd[31282]: Modem hangup
Sep 23 15:12:03 homeserver pppd[31282]: Exit.




reading from file my.tcpdump, link-type EN10MB (Ethernet)
deleted for security reasons by me
root@homeserver:/#

---

### Post by silbak04 on 2010-09-23
> **hamilton.jason said:**
> I am using an airlink101 wireless router. It has the option for vpn, ipsec, and l2tp passthrough. I would assume that means it is not going to block GRE. I have time warner cable, they have this tiny little black box that doesnt have any interface on it. Its a converter box i believe because it takes the cable and converts it over to an ethernet cable. So from the wall it goes to the black box, from the black box to the router, from the router to the server. 

Did a tcp dump but looks like gibberish in that file format. I need to convert it to txt. Guide i was looking at uses ethereal but i dont see an ubuntu version. Anyone have any other program that does it.

root@homeserver:/# tcpdump -i eth0 -w my.tcpdump -s 0 tcp port 1723 or proto 47
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
^C24 packets captured
24 packets received by filter
0 packets dropped by kernel

root@homeserver:/# ethereal my.tcpdump
ethereal: command not found
root@homeserver:/# apt-get ethereal
E: Invalid operation ethereal

^ should be:

```

root@homeserver:/# apt-get **install** ethereal

```

---

### Post by hamilton.jason on 2010-09-24
Ok well i was able to analyze the tcp dump and everything looks fine. tcpdump -r my.tcpdump shows the below readout. I am not seeing anything strange. My messages when logging in from my mac and phone are the same. LCP: timeout sending Config-Requests

Any suggestions?

```
root@homeserver:/# tcpdump -r my.tcpdump
reading from file my.tcpdump, link-type EN10MB (Ethernet)
filtered for security reasons by me.

```

---

### Post by hamilton.jason on 2010-09-24
still nothing. I desperately need this vpn up... so far ive tried a mac, phone, and windows pcs and all results in the same error message of config request fail. Any ideas?

---

### Post by Groodles on 2010-09-25
Something, is preventing the GRE response from the VPN Client reaching the PPTP server.

If you're sure that your router isn't stopping it then I'd contact your cable company and ask about this "black box" they've installed.

---

### Post by hamilton.jason on 2010-09-26
the router specifically states enable vpn passthrough. I dont think its the router. I also tried vpning from inside the network so that rules out the black box thingy.

---

### Post by kulshoks2121 on 2010-09-26
> Sep 22 12:16:30 homeserver pptpd[7600]: GRE: Bad checksum from pppd.


Try reinstalling the pppd, it might have have been altered, or if you have a DMZ on the router try to disable it first

---

### Post by hamilton.jason on 2010-09-27
apt-get purge pptp
...
apt-get install pptp

after it went through the whole script thing, I basically put the same config in and i get the same error message. I have opened a ticket w/ the router manufacturer to see if maybe it is the router. Current router is AR525W MIMO XR™ 802.11g Wireless Router. Ill let you know what they say.

---

### Post by Groodles on 2010-09-27
> **hamilton.jason said:**
> the router specifically states enable vpn passthrough. I dont think its the router. I also tried vpning from inside the network so that rules out the black box thingy.

Page 24 of this [http://www.airlink101.com/download/download_links/ar525w_manual.pdf](http://www.airlink101.com/download/download_links/ar525w_manual.pdf) says that you need to change a setting to enable the VPN pass-through.  (ie. it's not enabled by default.)

Also you'll need to forward TCP port 1723 to the PPTP host.

---

### Post by SectorNine50 on 2010-09-28
Try getting into the "black box" by typing 192.168.100.1 into a web browser.  Often those units have DHCP and Firewalls in them, even though they don't seem like much.  The box we have from Comcast where I live requires you to forward the GRE ports to the VPN host (I know the Motorola SurfBoard's do not have a firewall).

---

### Post by hamilton.jason on 2010-09-28
> **Groodles said:**
> Page 24 of this [http://www.airlink101.com/download/download_links/ar525w_manual.pdf](http://www.airlink101.com/download/download_links/ar525w_manual.pdf) says that you need to change a setting to enable the VPN pass-through.  (ie. it's not enabled by default.)

Also you'll need to forward TCP port 1723 to the PPTP host.

yea i found that option and enabled it a long time ago. That is what i meant when i said that it specifically stated allow vpn passthrough. I guess it could be that little black box. Literally there is no interface for this thing. Ill see what i can do to get into it when i get home. I have opened a ticket w/ the airlink people to see if its possibly the router. Still waiting on their response.

---

### Post by hamilton.jason on 2010-09-29
> **SectorNine50 said:**
> Try getting into the "black box" by typing 192.168.100.1 into a web browser.  Often those units have DHCP and Firewalls in them, even though they don't seem like much.  The box we have from Comcast where I live requires you to forward the GRE ports to the VPN host (I know the Motorola SurfBoard's do not have a firewall).

Ok went home and did this. Found that i indeed do have the motorola surfboard. I went to the ip address and there is no way to change any configuration on this thing. Ill keep googling to see if there is a known GRE issue w/ these.

---

### Post by hamilton.jason on 2010-10-01
Alright, well airlink got back to me and sent me a firmware update. Tried to update firmware and i keep getting error messages reporting that it is unable to find the config file. Checked the version of the firmware they sent me and its the same that i currently have. I dont even think they read my problem. Either way this indicates that there is something wrong w/ this router so ill be buying a new router this weekend and will see what happens.

---

