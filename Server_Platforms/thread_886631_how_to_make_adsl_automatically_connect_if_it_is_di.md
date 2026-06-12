---
title: "how to make adsl automatically connect if it is disconnected"
date: 2008-08-11
forum: Server Platforms
---

### Post by q.dinar on 2008-08-11
how to make adsl always automatically connect if it is disconnected?
(how to keep connection?)

(i've selected ubuntu prefix because i use ubuntu)

---

### Post by q.dinar on 2009-01-28
there is /etc/ppp/options file. i have read in a mail-archive site suggestions to uncomment "persist" and others.. i have increased "lcp-echo-failure" and [then] uncommented "persist". that site i have found with searching "lcp terminated by peer" that was in log. also i think and may be i had read that that provider maybe terminates idle connections so may be connecting to an irc server can help. i am connected to some irc servers always. and in that site was said that that may be provider's problem and user should say to his provider.

---

### Post by RomanIvanov on 2009-01-28
I have modem and It reconnected automatically - because I pup user login and password to modem PPPoP settings. Check the same ability in your modem.

---

### Post by q.dinar on 2009-01-28
i [said](http://ubuntuforums.org/showthread.php?t=1022671) about that:
"even before i installed firestarter i could no connect to my modem. i have remembered that, have known out its ip and tried but cannot, but once i connected to it when used windows. ... my modem is "zte zxdsl 831 series". i try to open it this way:
[http://smartinfo.com.my/IT/PC_Hardwa..._831_Modem.htm](http://smartinfo.com.my/IT/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm)
but [http://192.168.1.1](http://192.168.1.1) is not opening."
and i still cannot open my modem page, and have not tried much.

---

### Post by q.dinar on 2009-03-03
hello. today at night it has not connected automatically.

Mar  3 01:09:48 linux2009 pppd[5174]: No response to 4 echo-requests
Mar  3 01:09:48 linux2009 pppd[5174]: Serial link appears to be disconnected.
Mar  3 01:09:48 linux2009 pppd[5174]: Connect time 42.0 minutes.
Mar  3 01:09:48 linux2009 pppd[5174]: Sent 285478 bytes, received 339526 bytes.
Mar  3 01:09:54 linux2009 pppd[5174]: Connection terminated.
Mar  3 01:09:54 linux2009 pppd[5174]: Modem hangup
Mar  3 01:10:59 linux2009 pppd[5174]: Timeout waiting for PADO packets
Mar  3 01:12:04 linux2009 pppd[5174]: Timeout waiting for PADO packets
Mar  3 01:12:34 linux2009 pppd[5174]: PPP session is 3754
Mar  3 01:12:34 linux2009 pppd[5174]: Using interface ppp0
Mar  3 01:12:34 linux2009 pppd[5174]: Connect: ppp0 <--> eth0
Mar  3 01:12:35 linux2009 pppd[5174]: Remote message: Authentication failed
Mar  3 01:12:36 linux2009 pppd[5174]: Connection terminated.
Mar  3 01:13:06 linux2009 pppd[5174]: PPP session is 7182
Mar  3 01:13:06 linux2009 pppd[5174]: Using interface ppp0
Mar  3 01:13:06 linux2009 pppd[5174]: Connect: ppp0 <--> eth0
Mar  3 01:13:10 linux2009 pppd[5174]: Remote message: Authentication failed
Mar  3 01:13:10 linux2009 pppd[5174]: Connection terminated.
Mar  3 01:13:40 linux2009 pppd[5174]: PPP session is 10856
Mar  3 01:13:40 linux2009 pppd[5174]: Using interface ppp0
Mar  3 01:13:40 linux2009 pppd[5174]: Connect: ppp0 <--> eth0
Mar  3 01:13:44 linux2009 pppd[5174]: Remote message: Authentication failed
Mar  3 01:13:44 linux2009 pppd[5174]: Connection terminated.
Mar  3 01:14:14 linux2009 pppd[5174]: PPP session is 14406
Mar  3 01:14:14 linux2009 pppd[5174]: Using interface ppp0
Mar  3 01:14:14 linux2009 pppd[5174]: Connect: ppp0 <--> eth0
Mar  3 01:14:18 linux2009 pppd[5174]: Remote message: Authentication failed

after i have switched adsl modem off and on just as i usually do it succeeded to connect:

Mar  3 08:15:55 linux2009 kernel: [249850.327627] eth0: link down.
Mar  3 08:15:55 linux2009 NetworkManager: <info>  (eth0): carrier now OFF (device state 1) 
Mar  3 08:16:57 linux2009 kernel: [249911.925228] eth0: link up.
Mar  3 08:16:57 linux2009 NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Mar  3 08:17:01 linux2009 /USR/SBIN/CRON[20589]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  3 08:17:02 linux2009 kernel: [249916.897037] eth0: link down.
Mar  3 08:17:02 linux2009 NetworkManager: <info>  (eth0): carrier now OFF (device state 1) 
Mar  3 08:17:04 linux2009 kernel: [249918.635891] eth0: link up.
Mar  3 08:17:04 linux2009 NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Mar  3 08:18:07 linux2009 pppd[20775]: Plugin rp-pppoe.so loaded.
Mar  3 08:18:07 linux2009 pppd[20777]: pppd 2.4.4 started by root, uid 0
Mar  3 08:18:07 linux2009 pppd[20777]: PPP session is 20402
Mar  3 08:18:07 linux2009 pppd[20777]: Using interface ppp0
Mar  3 08:18:07 linux2009 pppd[20777]: Connect: ppp0 <--> eth0
Mar  3 08:18:07 linux2009 pppd[20777]: PAP authentication succeeded
Mar  3 08:18:07 linux2009 pppd[20777]: peer from calling number 00:19:2F:78:D7:3C authorized
Mar  3 08:18:07 linux2009 pppd[20777]: Cannot determine ethernet address for proxy ARP
Mar  3 08:18:07 linux2009 pppd[20777]: local  IP address 89.232.85.48
Mar  3 08:18:07 linux2009 pppd[20777]: remote IP address 192.168.228.9
Mar  3 08:18:07 linux2009 pppd[20777]: primary   DNS address 89.232.109.74
Mar  3 08:18:07 linux2009 pppd[20777]: secondary DNS address 217.23.176.1
Mar  3 08:18:08 linux2009 postfix/master[5499]: reload configuration /etc/postfix
Mar  3 08:22:36 linux2009 ntpd[5277]: Listening on interface #7 ppp0, 89.232.85.48#123 Enabled
Mar  3 08:25:29 linux2009 ntpd[5277]: no servers reachable

may be it could connect itself if it stopped eth0 and then started eth0 itself? (like this:

Mar  3 08:17:02 linux2009 kernel: [249916.897037] eth0: link down.
Mar  3 08:17:04 linux2009 kernel: [249918.635891] eth0: link up.)

---

### Post by q.dinar on 2009-03-04
it has disconnected again today and i see that it tried to connect few times. then i have remembered that this installation i have not modified /etc/ppp/options and have just now modified it.

---

### Post by q.dinar on 2009-05-16
now i have set also:

maxfail 0

in /etc/ppp/options file.

---

### Post by q.dinar on 2010-02-17
my current /etc/ppp/options
say if something is wrong, please.

---

