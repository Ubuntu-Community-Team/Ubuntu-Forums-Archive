---
title: "Limiting bandwidth and total data transfer for VPN clients."
date: 2009-08-04
forum: Server Platforms
---

### Post by avkmedia on 2009-08-04
I have an Ubuntu VPN server setup (using PPTP) where users connect to the server using a username/password.

My goal would be to limit the bandwidth of these users (for example to 150 KB/sec per user) as well as limiting the total amount of data transfer (for example 10GB/month/user).

Ideally I would be able to set these limits on a username basis (to give some users more transfer for example).

Is there an easy way I could accomplish this?

Thanks in advance.

---

### Post by Gigcsjcx on 2009-11-20
I have the same requiries.

---

### Post by crankyadm1n on 2009-11-20
Using OpenVPN would be a better choice with RADIUS doing the transfer limit i.e Cut user off after 10GB, with firewall/gateway limiting speed via traffic shaping, most of these products can be hooked into RADIUS to do it on a per user basis.

Wallgardened is a good term to google for.

Regards

---

### Post by David006 on 2011-11-17
I'm researching a similar issue (with TC as a possible solution) for: **Ubuntu 11.10 (Oneiric)** and **Ubuntu 10.04.3 LTS ..**


( Will report back .. )

---

### Post by FiFE on 2011-11-20
Same problem here. I've tried to use wondershaper pppiface down up in /etc/ppp/ip-up but the result was appalling.

---

### Post by David006 on 2011-11-20
> **FiFE said:**
> Same problem here. I've tried to use wondershaper pppiface down up in /etc/ppp/ip-up but the result was appalling.

I did find this:

[http://wiki.openwrt.org/doc/howto/tc/tc.theory](http://wiki.openwrt.org/doc/howto/tc/tc.theory)

( still studying ... )

---

### Post by FiFE on 2011-11-20
Managed to make it work with this: 
[http://www.topwebhosts.org/tools/tc.bash.txt](http://www.topwebhosts.org/tools/tc.bash.txt)
For each client (a ppp interface in my case) in the script that is executed when the interface is set up, I've added this script (adapted, of course) and declared the proper values. 

TC=/sbin/tc
IF=eth0		    # Interface <-- replaced with ppp interface                  variable
DNLD=1mbit          # DOWNLOAD Limit
UPLD=1mbit          # UPLOAD Limit 
IP=216.3.128.12     # Host IP   <- replaced with the variable that defines ppp iface address

 U32="$TC filter add dev $IF protocol ip parent 1:0 prio 1 u32"

 $TC qdisc add dev $IF root handle 1: htb default 30
    $TC class add dev $IF parent 1: classid 1:1 htb rate $DNLD
    #$TC class add dev $IF parent 1: classid 1:2 htb rate $UPLD
    $U32 match ip dst $IP/32 flowid 1:1
    #$U32 match ip src $IP/32 flowid 1:2
$TC qdisc add dev $IF handle ffff: ingress
$TC filter add dev $IF parent ffff: protocol ip prio 50 u32 match ip src \
   0.0.0.0/0 police rate $DNLD burst 100k drop flowid :1


There is a twist. Outgoing packets were routed before they hit the filtering rules so I wasn't able to adjust upload speed. For this it's necessary to use ingress. Ingress policy is applied before packets hit the IP stack according to documentation.

---

