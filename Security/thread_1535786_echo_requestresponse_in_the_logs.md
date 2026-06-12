---
title: "echo request/response in the logs"
date: 2010-07-21
forum: Security
---

### Post by vangop on 2010-07-21
Hi guys,
I see in my syslog each minute some echo req/response.
```
Jul 21 16:35:41 zoidberg pptp[4205]: anon log[logecho:pptp_ctrl.c:677]: Echo Request received.
Jul 21 16:35:41 zoidberg pptp[4205]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
```

Should I be worried? Is it somebody pinging me? Why if I ping this PC from another PC on the lan the pings are not reflected in the logs?
Thanks!

---

### Post by bodhi.zazen on 2010-07-21
Why would an echo request / response worry you ?

---

### Post by endotherm on 2010-07-21
I notice that the process is a pptp channel. VPN tunneling clients are often configured to constantly send hello pings to keep the tunnel active and responsive, as well as to allow either end to evaluate performance at any given time. 
I would ignore it. if you blocked it, it is quite likely that your vpn would cease function. you are recieveing the logs from the pptp process, not the networking stack, which is not configured to log pings, so thats why manual pings don't show in the log

---

### Post by vangop on 2010-07-23
Thanks for the reply! I was worried as  I know there's some icmp based attacks. And I noticed eth0 going down soon after the pings.
Found the piece of log:
```
Jul 19 21:43:14 zoidberg pptp[24534]: anon log[logecho:pptp_ctrl.c:677]: Echo Request received.
Jul 19 21:43:14 zoidberg pptp[24534]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
Jul 19 21:43:17 zoidberg kernel: [100470.585281] iptables drop: IN=ppp0 OUT= MAC= SRC=113.146.32.70 DST=x.x.x.x LEN=131 TOS=0x00 PREC=0x00 TTL=105 ID=10181 PROTO=UDP SPT=25661 DPT=16471 LEN=111 
Jul 19 21:43:27 zoidberg kernel: [100480.298450] tg3: eth0: Link is down.
Jul 19 21:43:27 zoidberg NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 19 21:43:29 zoidberg NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Jul 19 21:43:29 zoidberg kernel: [100481.959699] tg3: eth0: Link is up at 100 Mbps, full duplex.
Jul 19 21:43:29 zoidberg kernel: [100481.959707] tg3: eth0: Flow control is off for TX and off for RX.
Jul 19 21:43:29 zoidberg kernel: [100482.148112] iptables drop: IN=ppp0 OUT= MAC= SRC=93.51.245.39 DST=x.x.x.x LEN=131 TOS=0x00 PREC=0x00 TTL=107 ID=23347 PROTO=UDP SPT=16632 DPT=16471 LEN=111 
Jul 19 21:43:41 zoidberg kernel: [100494.056096] iptables drop: IN=ppp0 OUT= MAC= SRC=78.26.128.152 DST=x.x.x.x LEN=58 TOS=0x10 PREC=0x20 TTL=117 ID=22938 DF PROTO=UDP SPT=6500 DPT=48120 LEN=38 
Jul 19 21:43:54 zoidberg kernel: [100506.989219] iptables drop: IN=ppp0 OUT= MAC= SRC=178.93.144.221 DST=x.x.x.x LEN=131 TOS=0x00 PREC=0x00 TTL=118 ID=46863 PROTO=UDP SPT=10681 DPT=33697 LEN=111 
Jul 19 21:44:10 zoidberg kernel: [100523.385123] iptables drop: IN=ppp0 OUT= MAC= SRC=174.118.66.100 DST=x.x.x.x LEN=131 TOS=0x00 PREC=0x00 TTL=103 ID=44683 PROTO=UDP SPT=63748 DPT=16471 LEN=111 
Jul 19 21:44:11 zoidberg pptp[24534]: anon log[logecho:pptp_ctrl.c:677]: Echo Request received.
Jul 19 21:44:11 zoidberg pptp[24534]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
Jul 19 21:44:18 zoidberg kernel: [100531.597079] tg3: eth0: Link is down.


```

---

### Post by iponeverything on 2010-07-23
> A ping to the endpoint of your pptp has to be originating on the other end of the point-to-point connection -- as the the endpoints should not be reachable from anywhere except the directly connected devices.


I take this back ^ The pptp can have a public address. Though this does look like a failed status check.. Is your endpoint address public or private?

If you always see this pattern:

```
Jul 19 21:44:11 zoidberg pptp[24534]: anon log[logecho:pptp_ctrl.c:677]: Echo Request received.
Jul 19 21:44:11 zoidberg pptp[24534]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
Jul 19 21:44:18 zoidberg kernel: [100531.597079] tg3: eth0: Link is down.
```

I would say that ping is a failed pptp integrity check which causes the remote endpoint to change the link status of the pptp connection to down.  (pptp_ctrl is good clue)

If the connection resets itself as it should, I don't think you have anything to worry about.

---

### Post by vangop on 2010-07-23
> **iponeverything said:**
> 
I would say that ping is a failed pptp integrity check which causes the remote endpoint to change the link status of the pptp connection to down.  (pptp_ctrl is good clue)



But it was eth0 going up/down not ppp0 :)
Well I don't see this happening anymore, so I assume it could have been caused by the unplugged cable  or something... I'll just ignore the pings :)

---

