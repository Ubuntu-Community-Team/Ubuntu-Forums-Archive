---
title: "Suspicious entries in syslog"
date: 2010-05-25
forum: Security
---

### Post by sisyphus1978 on 2010-05-25
I have seen a few threads which appear related, although nothing helpful. Looking over my logs I noticed quite a lot of these:

```
May 25 14:38:29 Computer kernel: [ 9489.127606] Inbound IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=92.48.118.34 DST=192.168.0.0 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=15257 PROTO=TCP SPT=80 DPT=55117 WINDOW=0 RES=0x00 ACK URGP=0 
May 25 14:38:29 Computer kernel: [ 9489.127650] Inbound IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=92.48.118.34 DST=192.168.0.0 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=15256 DF PROTO=TCP SPT=80 DPT=55117 WINDOW=65535 RES=0x00 ACK URGP=0 
May 25 14:43:13 Computer kernel: [ 9774.105465] Inbound IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=92.48.118.34 DST=192.168.0.0 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=19302 PROTO=TCP SPT=80 DPT=55117 WINDOW=0 RES=0x00 ACK URGP=0 
May 25 14:43:13 Computer kernel: [ 9774.105904] Inbound IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=92.48.118.34 DST=192.168.0.0 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=19301 DF PROTO=TCP SPT=80 DPT=55117 WINDOW=65535 RES=0x00 ACK URGP=0 
```The MAC and DST have been changed. WHOIS provides this:

```
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See http://www.ripe.net/db/support/db-terms-conditions.pdf

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '92.48.118.0 - 92.48.118.63'

inetnum:        92.48.118.0 - 92.48.118.63
netname:        AS29550-infra
descr:          Canonical range for 17P
remarks: ##############################################################
remarks:        Please report abuse incidents to abuse@as29550.net.
remarks:        Messages sent to other contact addresses may not be acted upon.
remarks: ##############################################################
remarks:        INFRA-AW
country:        GB
admin-c:        AO904-RIPE
tech-c:         AO904-RIPE
status:         ASSIGNED PA
mnt-by:         as29550-mnt
source:         RIPE # Filtered

role:           AS29550 Operators
address:        BlueSquare House
address:        Priors Way
address:        Maidenhead
address:        Berkshire
address:        SL62HP
remarks:        For abuse please contact abuse@as29550.net
phone:          +44 (0)1628 673131
admin-c:        PETE3-RIPE
admin-c:        BJR
admin-c:        JOSH
admin-c:        CDP
tech-c:         PETE3-RIPE
tech-c:         BJR
tech-c:         CDP
tech-c:         JOSH
mnt-by:         as29550-MNT
nic-hdl:        AO904-RIPE
source:         RIPE # Filtered
abuse-mailbox:  abuse@as29550.net

% Information related to '92.48.64.0/18AS29550'

route:          92.48.64.0/18
descr:          Blueconnex Networks Ltd
origin:         AS29550
remarks:        ***********************************
remarks:        *                                 *
remarks:        * Abuse: abuse@blueconnex.net     *
remarks:        *                                 *
remarks:        * Peering: peering@blueconnex.net *
remarks:        *                                 *
remarks:        ***********************************
mnt-by:         blueconnex-mnt
source:         RIPE # Filtered

```Anything to be worried about? Thanks

---

### Post by cdenley on 2010-05-25
Not if you were trying to browse this site:
[http://ovalpowered.com/](http://ovalpowered.com/)

---

### Post by sisyphus1978 on 2010-05-25
No. I wasn't browsing that site. Plus. it seems to be occurring every 5 minutes or so.

---

### Post by cdenley on 2010-05-25
> **sisyphus1978 said:**
> No. I wasn't browsing that site. Plus. it seems to be occurring every 5 minutes or so.

Something is attempting to connect to that site. You can try doing a packet capture to identify what request is being sent. You can try using netstat to identify what program is sending the web request. Is there anything running or scheduled to run by cron that might be related to that site?

---

### Post by cdenley on 2010-05-25
Actually, it looks like that server has other virtualhosts. The default one appears to provide weather information.
```

[COLOR="Silver"]cdenley@ubuntu:~$ [/COLOR]echo -e "GET /data/noaa.rrd\n"|nc -q 1 92.48.118.34 80|strings
0003
Temp
GAUGE
Pressure
GAUGE
Humidity
GAUGE
GAUGE
WindSpeed
GAUGE
WindDir
GAUGE
AVERAGE
AVERAGE

```

---

### Post by sisyphus1978 on 2010-05-25
That's some good detective work Lou! I did see that rrd file, but it stumped me.

 > Is there anything running or scheduled to run by cron that might be  related to that site?     Not that I know of.

I'm still not sure if it's okay though...

Have I been compromised or am I under attack?

---

### Post by OpSecShellshock on 2010-05-25
Do you have a weather applet running, like say in awn, screenlets, or in the panel?

---

### Post by sisyphus1978 on 2010-05-25
I shut the weather applet down. Still showing in the logs.

However after checking the logs I noticed it started just after installing texlive 2009:

```
May 24 23:35:10 Computer sudo:    bob : TTY=pts/6 ; PWD=/media/Stuff/Downloads/install-tl-20100512 ; USER=root ; COMMAND=/usr/bin/apt-get remove texlive-*
May 24 23:39:39 Computer sudo:    bob : TTY=pts/6 ; PWD=/media/Stuff/Downloads/install-tl-20100512 ; USER=root ; COMMAND=./install-tl
```Coincidence?

---

### Post by sisyphus1978 on 2010-05-26
Still going strong. Any ideas how I determine what's going on?

---

### Post by OpSecShellshock on 2010-05-26
Block the external IP and see what breaks?

---

### Post by sisyphus1978 on 2010-05-26
I already tried that. I don't really run anything which I would expect to be doing this. I'm not happy just to leave it, but reinstalling isn't much of an option (I'd like to find out what it is that's happening). Is it innocuous or is it something to be worried about?

---

### Post by AcidMoon on 2010-05-26
The TTL=58 signature looks weird. 
Say you'd look at TTL values to try and determine a remote OS or maybe your own. 
Can you ping your own IP then take a look at the syslog to see if it matches TTL=58?

---

### Post by sisyphus1978 on 2010-05-26
Snippet from my log:
```
May 26 12:00:52 Computer kernel: [14564.526079] Inbound IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=92.48.118.34 DST=192.168.0.0 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=26235 DF PROTO=TCP SPT=80 DPT=55117 WINDOW=65535 RES=0x00 ACK URGP=0 
May 26 12:03:47 Computer kernel: [14739.750732] Outbound IN= OUT=eth0 SRC=192.168.0.0 DST=92.48.118.34 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=28286 DF PROTO=TCP SPT=44402 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
May 26 12:03:50 Computer kernel: [14742.750049] Outbound IN= OUT=eth0 SRC=192.168.0.0 DST=92.48.118.34 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=28287 DF PROTO=TCP SPT=44402 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
May 26 12:05:03 Computer kernel: [14815.877006] Outbound IN= OUT=eth0 SRC=192.168.0.0 DST=92.48.118.34 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=13326 DF PROTO=TCP SPT=44403 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
May 26 12:05:06 Computer kernel: [14818.870671] Outbound IN= OUT=eth0 SRC=192.168.0.0 DST=92.48.118.34 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=13327 DF PROTO=TCP SPT=44403 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
May 26 12:05:37 Computer kernel: [14849.475357] Inbound IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=92.48.118.34 DST=192.168.0.0 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=42587 PROTO=TCP SPT=80 DPT=55117 WINDOW=0 RES=0x00 ACK URGP=0 
```1 incoming (the trouble), 4 pings and 1 incoming.

Pinging my IP or localhost gives a TTL of 64 not 58.

---

### Post by AcidMoon on 2010-05-26
I feel an undercurrent in this thread that it is your system connecting to something. Which I believe is the case.
All my searching around that IP relates to a file sharing network gnutella.
Do you have any pending torrents / seeding files/ p2p or anything like that?

---

### Post by sisyphus1978 on 2010-05-26
> I feel an undercurrent in this thread that it is your system connecting  to something. Which I believe is the case.I understand.

> Do you have any pending torrents / seeding files/ p2p or anything like  that? No.

I've shutdown the weather applet in gnome-panel. I've shutdown empathy. I've shutdown gmail-notifier. There's not much else going on, on this machine.

---

### Post by sisyphus1978 on 2010-05-26
This is from tcpdump during an "event"

```
13:45:25.017183 IP ovalpowered.com.www > 192.168.0.0.55117: Flags [.], ack 3917212607, win 0, length 0
13:45:25.017260 IP ovalpowered.com.www > 192.168.0.0.55117: Flags [.], ack 1, win 65535, length 0
13:45:25.017486 IP 192.168.0.0.54566 > google-public-dns-a.google.com.domain: 6319+ PTR? 34.118.48.92.in-addr.arpa. (43)
13:45:25.059056 IP google-public-dns-a.google.com.domain > 192.168.0.0.54566: 6319 1/0/0 (72)
13:45:26.938938 IP 192.168.0.0.33616 > ww-in-f125.1e100.net.xmpp-client: Flags [.], ack 1, win 65535, length 0
13:45:26.970993 IP ww-in-f125.1e100.net.xmpp-client > 192.168.0.0.33616: Flags [.], ack 1, win 62920, length 0

```

---

### Post by cdenley on 2010-05-26
The full packets captured with the "-w" option would be more informative, such as what hostname it is sending to the server and what path it is requesting.

---

### Post by AcidMoon on 2010-05-26
At a loss sorry! Suspicious entries but your clearly not being haxxor'd or something cr.p like that! So I don't think you need to worry...BUT...
IMHO "something is connecting with the FTP site" firefox plugin? Music software?? GTK update???
Up to you friend you did post that re-installation is not really an option but short of config iptables to block the IP I can't think of another solution.
Well there is my quick solution or I'd recommend hold fire as long as your patience stands and see if some supremo tech TCP/IP guru can analyse your problem.
I'll keep researching the problem and PM you if I find a "silver bullet".

Edit. Just realised cdenley is acting on this. I remember reading his posts long ago. Guru. Just do what he says lol.

---

### Post by sisyphus1978 on 2010-05-26
Big thanks for all the effort in trying to work this one out. It just seems to me that if I'm taking responsibility for the system, then I better understand what's going on. And I don't at the moment...

```
bob@Computer:/etc$ sudo tcpdump -vv host 92.48.118.34
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
14:23:14.744191 IP (tos 0x0, ttl 58, id 5552, offset 0, flags [none], proto TCP (6), length 40)
    ovalpowered.com.www > 192.168.0.0.55117: Flags [.], cksum 0x132c (correct), seq 2097077954, ack 3917212607, win 0, length 0
14:23:14.744270 IP (tos 0x0, ttl 58, id 5551, offset 0, flags [DF], proto TCP (6), length 40)
    ovalpowered.com.www > 192.168.0.0.55117: Flags [.], cksum 0x132b (correct), seq 1, ack 1, win 65535, length 0
```I got a -w dump too, but I don't know what information is in there, and I don't know if it's that safe to share (I dumped to a file).

Somebody suggested it may be a problem with googletalk/empathy (PM). I still get it when empathy isn't running though...

Finally, maybe it's the remnants of a bittorent connection. I was reading somewhere that it might be a ghost connection? I haven't run transmission for a week (archiso - yeah right!) and I don't use it often.

I will point out again, that I can't find any mention of the same IP until I started installing texlive 2009 with the script install-tl.

---

### Post by cdenley on 2010-05-26
> **sisyphus1978 said:**
> I got a -w dump too, but I don't know what information is in there, and I don't know if it's that safe to share (I dumped to a file).

This command
```
sudo tcpdump -w data.cap host 92.48.118.34
```
would capture the full packets to/from 92.48.118.34. They would contain your IP/MAC, and of course any data being sent to/from that server. You can view it with wireshark.

> **sisyphus1978 said:**
> 
Finally, maybe it's the remnants of a bittorent connection. I was reading somewhere that it might be a ghost connection? I haven't run transmission for a week (archiso - yeah right!) and I don't use it often.

I don't think remnants of bittorrent connections would be coming from port 80.

---

### Post by sisyphus1978 on 2010-05-26
Attached is a data file. I checked it out with wireshark, but I couldn't find anything. I can provide more packets if necessary.

Thanks again.

---

### Post by cdenley on 2010-05-26
I found it. It apprently was texlive. I resolved all the [CTAN mirrors]("http://www.ctan.org/tex-archive/CTAN.sites"), which are used by texlive, and...
```

[COLOR="SlateGray"]cdenley@ubuntu:~$[/COLOR] **host ctan.sqsol.co.uk**
ctan.sqsol.co.uk has address 92.48.118.34

```

---

### Post by sisyphus1978 on 2010-05-26
Ha! Good detective work again in this thread!

I guess I can rest easy now. :)

All part of the learning curve. 

Thanks to all who helped out. Especially cdenley!

---

### Post by cdenley on 2010-05-26
FYI, I guess this would have been a better tcpdump command.
```

sudo tcpdump -w data.cap -s 4096 dst host 92.48.118.34

```
Also, wireshark can also capture network packets. I think I suggested tcpdump because I thought you may have been using a server.

---

