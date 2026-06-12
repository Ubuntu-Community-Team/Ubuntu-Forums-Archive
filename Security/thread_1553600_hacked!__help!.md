---
title: "hacked?!  help!"
date: 2010-08-15
forum: Security
---

### Post by mrmohan on 2010-08-15
im a newbie to ubuntu but i think my  computer got hacked the sound wasn't working, here is the system logs. i had offed my computer and turned on only to see that ufw was allowing and auditting.
   



Jul 10 20:00:01 violet5 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
  
  Jul 10 20:00:01 violet5 dhclient: 
  
  Jul 10 20:00:01 violet5 NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
  
  Jul 10 20:00:01 violet5 dhclient: Listening on xxxxxxxxxxxx
  
  Jul 10 20:00:01 violet5 dhclient: Sending on   xxxxxxxxxxxxx
  
  Jul 10 20:00:01 violet5 dhclient: Sending on   Socket/fallback
  
  Jul 10 20:00:02 violet5 dhclient: DHCPREQUEST of xxxxxxxxxxx on eth1 to xxxxxxxxxxxxx port 67
  
  Jul 10 20:00:02 violet5 dhclient: DHCPACK of xxxxxxxxxxxxxxxxxxxx from xxxxxxxxxx

  
  Jul 10 20:00:02 violet5 dhclient: bound to xxxxxxxxxxxxx-- renewal in 39534 seconds.
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>  DHCP: device eth1 state changed preinit -> reboot
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>    address xxxxxxxxxxxxx
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>    prefix 24 xxxxxxxxxxxxx
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>    gateway xxxxxxxxxxxxx
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>    nameserver xxxxxxxxxxxxx
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>    nameserver 'xxxxxxxxxxxxx
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
  
  Jul 10 20:00:02 violet5 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
  
  Jul 10 20:00:02 violet5 avahi-daemon[677]: Joining mDNS multicast group on interface eth1.IPv4 with address xxxxxxxxxxxxx.
  
  Jul 10 20:00:02 violet5 avahi-daemon[677]: New relevant interface eth1.IPv4 for mDNS.
  
  Jul 10 20:00:02 violet5 avahi-daemon[677]: Registering new address record for xxxxxxxxxxxxxon eth1.IPv4.
  
  Jul 10 20:00:03 violet5 NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
  
  Jul 10 20:00:03 violet5 NetworkManager: <info>  Policy set 'Auto linksys_SES_xxxx' (eth1) as default for routing and DNS.
  
  Jul 10 20:00:03 violet5 NetworkManager: <info>  Activation (eth1) successful, device activated.
  
  Jul 10 20:00:03 violet5 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
  
  Jul 10 20:00:04 violet5 ntpdate[1608]: adjust time server xxxxxxxxxxxxx offset 0.160592 sec
  
  Jul 10 20:00:49 violet5 kernel: [   xxxxxxxxxxxxx] [**UFW BLOCK**] IN=eth1 OUT= MAC=xxxxxxxxxxxxxSRC=xxxxxxxxxxxxxDST=xxxxxxxxxxxxxLEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=24604 DF PROTO=TCP SPT=80 DPT=35878 WINDOW=121 RES=0x00 ACK URGP=0 
  
  Jul 10 20:00:58 violet5 AptDaemon: INFO: Initializing daemon
  
  Jul 10 20:01:39 violet5 sudo: pam_sm_authenticate: Called
  
  Jul 10 20:01:39 violet5 sudo: pam_sm_authenticate: username = [violet5]
  
  Jul 10 20:01:39 violet5 sudo: pam_sm_authenticate: /home/violet5 is already mounted
  
  Jul 10 20:02:09 violet5 kernel: [  1xxxxxxxxxxxxx] [UFW BLOCK] IN=eth1 OUT= MAC=xxxxxxxxxxxxx SRC=xxxxxxxxxxxxx.xxxxxxxxxxxxx DST=xxxxxxxxxxxxxLEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=3968 PROTO=TCP SPT=80 DPT=37161 WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [xxxxxxxxxxxxx] [UFW BLOCK] IN=eth1 OUT= MAC=xxxxxxxxxxxxxSRC=xxxxxxxxxxxxx.118 DST=xxxxxxxxxxxxxLEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxx PROTO=TCP SPT=80 DPT=37163 WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [  xxxxxxxxxxxxx] [UFW **BLOCK**] IN=eth1 OUT= MAC=xxxxxxxxxxxxx SRC=xxxxxxxxxxxxx DST=xxxxxxxxxxxxxLEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxx PROTO=TCP SPT=80 DPT=37165 WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [  xxxxxxxxxxxxx] [UFW **BLOCK**] IN=eth1 OUT= MAC=xxxxxxxxxxxxx DST=xxxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxx PROTO=TCP SPT=80 DPT=37162 WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [  xxxxxxxxxxxxx] [UFW **BLOCK**] IN=eth1 OUT= MAC=xxxxxxxxxxxxxDST=xxxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxx PROTO=TCP SPT=80 DPT=37166 WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [  xxxxxxxxxxxxx] [UFW **BLOCK**] IN=eth1 OUT= MAC=xxxxxxxxxxxxxDST=xxxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxxPROTO=TCP SPT=80 DPT=36015 WINDOW=150 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [  xxxxxxxxxxxxx] [UFW BLOCK] IN=eth1 OUT= MAC=xxxxxxxxxxxxxDST=xxxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxxxx PROTO=TCP SPT=80 DPT=37161 WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [  xxxxxxxxxxxxx] [UFW BLOCK] IN=eth1 OUT= MAC=xxxxxxxxxxxxxDST=xxxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxxxPROTO=TCP SPT=80 DPT=37163 WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [  xxxxxxxxxxxxx] [UFW BLOCK] IN=eth1 OUT= MAC=xxxxxxxxxxxxx SRC=xxxxxxxx.118 DST=xxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxxx PROTO=TCP SPT=80 DPT=37165 WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:09 violet5 kernel: [  xxxxxxxxxxxxx] [UFW BLOCK] IN=eth1 OUT= MAC=xxxxxxxxxxxxxDST=xxxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxx PROTO=TCP SPT=80 DPT=xxxx WINDOW=106 RES=0x00 ACK FIN URGP=0 
  
  Jul 10 20:02:49 violet5 kernel: [  xxxxxxxxxxxxx] [UFW BLOCK] IN=eth1 OUT= MAC=xxxxxxxxxxxxx SRC=xxxxxxxxxxxxxDST=xxxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=24605 DF PROTO=TCP SPT=80 DPT=xxxxWINDOW=121 RES=0x00 ACK URGP=0 
  
  Jul 10 20:04:04 violet5 wpa_supplicant[683]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
  
  Jul 10 20:04:04 violet5 NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected
  
  Jul 10 20:04:04 violet5 NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
  
  Jul 10 20:04:09 violet5 wpa_supplicant[683]: Trying to associate with xxxxxxxxxxxxx (SSID='linksys_SES_' freq=2437 MHz)
  
  Jul 10 20:04:09 violet5 wpa_supplicant[683]: Association request to the driver failed


**more i had been done in between this point but to shorten this, here is what i found nearing the end.....**


ul 10 20:17:05 violet5 NetworkManager: <info>  Policy set 'Auto linksys_SES_xxxxxxxxxxxx' (eth1) as default for routing and DNS. 
Jul 10 20:17:05 violet5 NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jul 10 20:17:05 violet5 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jul 10 20:17:06 violet5 ntpdate[1874]: adjust time server xxxxxxxxxxxx offset -0.085905 sec 
Jul 10 20:23:43 violet5 sudo: pam_sm_authenticate: Called 
Jul 10 20:23:43 violet5 sudo: pam_sm_authenticate: username = [violet5] 
Jul 10 20:23:43 violet5 sudo: pam_sm_authenticate: /home/violet5 is already mounted 
Jul 10 20:24:49 violet5 kernel: [ xxxxxxxx] [UFW **AUDIT**] IN= OUT=eth1 SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=xxxxxxxxxxxx DF PROTO=TCP SPT=xxxx DPT=80 WINDOW=142 RES=0x00 ACK FIN URGP=0  
Jul 10 20:24:49 violet5 kernel: [ xxxxxxxx] [UFW **AUDIT**] IN=eth1 OUT= MAC=xxxxxxxxxxxxSRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxx PROTO=TCP SPT=80 DPT=44153 WINDOW=190 RES=0x00 ACK FIN URGP=0  
Jul 10 20:24:49 violet5 kernel: [ xxxxxxxx] [UFW **AUDIT**] IN= OUT=eth1 SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=xxxxxxxxxxxx DF PROTO=TCP SPT=xxxx DPT=80 WINDOW=142 RES=0x00 ACK URGP=0  
Jul 10 20:25:04 violet5 kernel: [ xxxxxxxx] [UFW **AUDIT**] IN= OUT=eth1 SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=xxxxxxxxxxxx DF PROTO=TCP SPT=xxxx DPT=80 WINDOW=399 RES=0x00 ACK FIN URGP=0  
Jul 10 20:25:04 violet5 kernel: [ xxxxxxxx] [UFW **AUDIT**] IN=eth1 OUT= MAC=xxxxxxxxxxxx SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=xxxxPROTO=TCP SPT=80 DPT=57789 WINDOW=272 RES=0x00 ACK FIN URGP=0  
Jul 10 20:25:04 violet5 kernel: [ xxxxxxxx] [UFW **AUDIT**] IN= OUT=eth1 SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=xxxxxxxxxxxx DF PROTO=TCP SPT=xxxx DPT=80 WINDOW=399 RES=0x00 ACK URGP=0  
Jul 10 20:25:19 violet5 kernel: [ xxxxxxxx] [UFW AUDIT] IN= OUT=eth1 SRC=xxxxxxxxxxxxDST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=xxxxxxxxxxxx DF PROTO=TCP SPT=xxxx DPT=80 WINDOW=259 RES=0x00 ACK FIN URGP=0  
Jul 10 20:25:19 violet5 kernel: [ xxxxxxxx] [UFW AUDIT] IN=eth1 OUT= MAC=xxxxxxxxxxxx SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=xxxx PROTO=TCP SPT=80 DPT=47499 WINDOW=269 RES=0x00 ACK FIN URGP=0  
Jul 10 20:25:19 violet5 kernel: [ xxxxxxxx] [UFW AUDIT] IN= OUT=eth1 SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=xxxxxxxxxxxx DF PROTO=TCP SPT=xxxx DPT=80 WINDOW=259 RES=0x00 ACK URGP=0  
Jul 10 20:26:34 violet5 kernel: [ xxxxxxxx] [UFW AUDIT] IN= OUT=eth1 SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=xxxxxxxxxxxx DF PROTO=TCP SPT=xxxx DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0  
Jul 10 20:26:34 violet5 kernel: [ xxxxxxxx] [UFW ALLOW] IN= OUT=eth1 SRC=xxxxxxxxxxxx DST=xxxxxxxxxxxx LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=xxxxxxxxxx DF PROTO=TCP SPT=xxxx DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0  


**i was not connected to the  next day internet yet it continued. i wish to know if other computers connected to my router were affected as well.sorry for the long post. thanks.**

---

### Post by MooPi on 2010-08-15
Why do you believe you're hacked ? I'm no expert but your log file doesn't indicate much in the way of hacKery :-). Unless your not voilet5 ?

---

### Post by CharlesA on 2010-08-15
All it shows is blocked ports.

What makes you think you were "hacked" ?

---

### Post by DrMelon on 2010-08-15
The allowing and auditing is on port 80 - which is the port used by HTTP (your web browsers, etc).

You're being very, very paranoid.
Also note that you have nothing a hacker would be interested in. Hackers target businesses and corporations, as they have useful information. As a home user, you mean nothing to a hacker.

---

### Post by CharlesA on 2010-08-15
> **DrMelon said:**
> The allowing and auditing is on port 80 - which is the port used by HTTP (your web browsers, etc).

You're being very, very paranoid.
Also note that you have nothing a hacker would be interested in. Hackers target businesses and corporations, as they have useful information. As a home user, you mean nothing to a hacker.
Not entirely true. There are (or used to be, haven't seen one in a bit) threads about people being "hacked" cuz they turned on the "Remote Desktop" application in Ubuntu Desktop and didn't bother to secure it. Same deal goes with SSH, since there are bots that try to bruteforce commonly used services if they are allowed to be accessible from the internet.

If you have no ports forwarded on yer router and don't have anything outside of a normal Ubuntu Desktop install, you aren't really at any risk of getting "hacked."

---

### Post by supershin on 2010-08-15
> **DrMelon said:**
> The allowing and auditing is on port 80 - which is the port used by HTTP (your web browsers, etc).

You're being very, very paranoid.
Also note that you have nothing a hacker would be interested in. Hackers target businesses and corporations, as they have useful information. As a home user, you mean nothing to a hacker.

Hacker = script kiddy = bad guy doing bad stuff. That's what it means to a lot of people.
"you mean nothing to a hacker." is wrong.

---

### Post by mrmohan on 2010-08-15
I am very thankful to the ubuntu community and all those who replied to my inquiry-Thanks for the response!:D

---

### Post by rookcifer on 2010-08-15
His sound stopped working, so it *must* be a hacker.  Occam's razor at work here, you see. :P

---

