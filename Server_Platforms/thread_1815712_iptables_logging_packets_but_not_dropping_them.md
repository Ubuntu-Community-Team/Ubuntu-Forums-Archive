---
title: "iptables logging packets but not dropping them"
date: 2011-07-31
forum: Server Platforms
---

### Post by adam35413 on 2011-07-31
I am trying to create some simple iptables DOS protection rules for my web server.  I was doing testing on the following rules:

```
iptables -N LOGDROP > /dev/null 2> /dev/null
iptables -F LOGDROP
iptables -A LOGDROP -j LOG --log-prefix "LOGDROP "
iptables -A LOGDROP -j REJECT
    
iptables -I INPUT -p tcp --dport 8000 -i eth0 -m state --state NEW -m recent --set
iptables -A INPUT -p tcp --dport 8001 -i eth0 -m state --state NEW -m recent --set
    
iptables -A INPUT -p tcp --dport 8000 -i eth0 -m state --state NEW -m recent --update --seconds 1 --hitcount 4 -j LOGDROP
iptables -A INPUT -p tcp --dport 8001 -i eth0 -m state --state NEW -m recent --update --seconds 1 --hitcount 4 -j LOGDROP

```

I created a script on a separate machine to do a wget and then sleep for .2 seconds.  I launched this script at port 8000 and 8001, and as expected I saw drop messages start to appear in my /var/log/messages:
```

    Jul 30 20:03:57 Server kernel: LOGDROP IN=eth0 OUT= MAC=08:00:27:d5:52:24:08:00:27:6d:cf:2f:08:00 SRC=192.168.56.102 DST=192.168.56.101 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=31049 DF PROTO=TCP SPT=44071 DPT=8000 WINDOW=14600 RES=0x00 SYN URGP=0
    Jul 30 20:04:00 Server kernel: LOGDROP IN=eth0 OUT= MAC=08:00:27:d5:52:24:08:00:27:6d:cf:2f:08:00 SRC=192.168.56.102 DST=192.168.56.101 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=63571 DF PROTO=TCP SPT=38876 DPT=8001 WINDOW=14600 RES=0x00 SYN URGP=0
    Jul 30 20:04:00 Server kernel: LOGDROP IN=eth0 OUT= MAC=08:00:27:d5:52:24:08:00:27:6d:cf:2f:08:00 SRC=192.168.56.102 DST=192.168.56.101 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=63984 DF PROTO=TCP SPT=44075 DPT=8000 WINDOW=14600 RES=0x00 SYN URGP=0

```
Everything appears to be great, except when I checked wireshark I found that the connection from source port 44071 was successful, meaning I saw a full tcp handshake, HTTP GET, and socket close.  The other two entries in the log were successfully dropped, meaning I saw just a SYN packet in wireshark.

Anyone know why the connection on source port 38876 would be logged as denied but not actually dropped?

---

### Post by Doug S on 2011-08-01
I think forum readers might need a bigger context to be able to help. The packet paths are not clear from only the sub-segment of the iptables given. Anyway, I added your rules to my test ubuntu server and it worked as expected. I had to change to port 80, because I don't use 8000 and 8001 (they would be refused anyhow), and I changed the "recent" timeout from the 1 second listed to 300 seconds, just so that I could type things slower and not bother with a script. I captured and observed everything with tcpdump.
I do notice that your one set rule is via "insert" and the other is via "append". so they could end up in completely different locations in the INPUT rules, depending on how many other rules were already there (the "insert" one will go at the start and the "append" one will go at the end). I also notice a 3 second gap in the log entry times, which was plenty of time for the 1 second to expire, thus allowing successful "wget"s again until the hitcount counter limit kicked in again.
Was it port 44071 or port 38876 that was successful and are you certain those were the ports? While it is not my intent to sound confrontational, with the information given, it does not seem possible to have had the log entry without the subsequent REJECT.

---

### Post by adam35413 on 2011-08-01
I noticed while looking at Wireshark that I was actually seeing the requests listed above get blocked, my script was just reusing the sockets. As a result any blocked socket entry in my log would have  multiple initial SYNs in the packet capture.

I did find a separate issue with the above rules.  I needed to add a --name attribute to each of the iptable lines. Without --name, all connections from the same IP address apply against the hitcount regardless of what port it arrived on.

In summary, the issue was different than I thought, but I did resolve it.

---

### Post by Doug S on 2011-08-01
Thanks for the follow up notes. Before your original posting I didn't know that not providing a name for the recent stuff was even possible. And yes, I did notice in my trials that without a name, it just calls it "DEFAULT", and thus both ports tally to the same hitcount. Glad you got it sorted out.

---

