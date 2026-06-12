---
title: "Firestarter and ICMP attacks"
date: 2009-10-02
forum: Security
---

### Post by hockeytux on 2009-10-02
I had switched Firestarter off for a few minutes earlier today and had a 'serious' inbound event during that time (ICMP protocol).

My computer didnt crash or reboot and BitTorrent was on and working normally, with normal connection speeds, so no overload or overwhelming of the network happened.

The port of the event is listed as 'Unknown' by Firestarter.

Do I need to be worried about this at all or was it just an error message (as expected in ICMP)?

---

### Post by ApEkV2 on 2009-10-02
I use torrent also and that happens all the time. It's normal.
You also have nothing to fear from icmp either, in fact if you configured firstarter to drop all icmp inbound/outbound, your golden.

---

### Post by lovinglinux on 2009-10-02
Do you really need Firestarter?

Read the security section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

If you really need a firewall manager, then install [gufw](apt:gufw) and forget about monitoring connections. It's just a waste of time.

BTW, those ICMP packets are completely normal and are related to the BitTorrent traffic.

---

### Post by hockeytux on 2009-10-02
Thanks. :popcorn:


So you would recommend replacing Firestarter with gufw for good?

---

### Post by lovinglinux on 2009-10-02
> **hockeytux said:**
> Thanks. :popcorn:


So you would recommend replacing Firestarter with gufw for good?

Yes, gufw (ufw) is the recommended firewall manager these days. UFW comes installed by default, but not enabled. If you want a GUI, then you have to install gufw.

---

### Post by kevdog on 2009-10-02
ufw comes installed but with no rules by default -- the default stance is not ACCEPT all incoming/outgoing packets.  It needs to be configured to work properly.

---

### Post by Lars Noodén on 2009-10-03
> **ApEkV2 said:**
> I use torrent also and that happens all the time. It's normal.
You also have nothing to fear from icmp either, in fact if you configured firstarter to drop all icmp inbound/outbound, your golden.

ICMP is needed for feedback, such as to tell the other machine to slow down and not transfer so fast, among other things.  Dropping ICMP breaks  your portion of the Internet and will adversely affect your ability to upload or download.  

A solution that allows a working Internet but mitigates abuse would be to rate-limit incoming ICMP.  Here's a line that limits incoming Echo Request (aka [ping](http://ftp.arl.army.mil/~mike/ping.html))

```

iptables -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 5/s -i eth0 -j ACCEPT

```

Other ICMP message types should AFAIK be handled by the connection states Established or Related.  

```

iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

---

### Post by hockeytux on 2009-10-04
> **Lars Noodén said:**
> ICMP is needed for feedback, such as to tell the other machine to slow down and not transfer so fast, among other things.  Dropping ICMP breaks  your portion of the Internet and will adversely affect your ability to upload or download.  

A solution that allows a working Internet but mitigates abuse would be to rate-limit incoming ICMP.  Here's a line that limits incoming Echo Request (aka [ping](http://ftp.arl.army.mil/~mike/ping.html))

```

iptables -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 5/s -i eth0 -j ACCEPT

```

Other ICMP message types should AFAIK be handled by the connection states Established or Related.  

```

iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

Thanks guys... I got rid of Firestarter, installed gufw and added the ICMP ping limitations.

However internet worked rightaway with the firewall enabled. I thought it would block everything?

> ufw comes installed but with no rules by default -- the default stance is not ACCEPT all incoming/outgoing packets. It needs to be configured to work properly

I remember this from Guarddog on my Kubuntu machine. The firewall was total and I had to punch holes in myself by adding exceptions like http, https, ICMP...

Maybe they changed the default setup for gufw now...

---

### Post by lovinglinux on 2009-10-04
> **hockeytux said:**
> Thanks guys... I got rid of Firestarter, installed gufw and added the ICMP ping limitations.

However internet worked rightaway with the firewall enabled. I thought it would block everything?



I remember this from Guarddog on my Kubuntu machine. The firewall was total and I had to punch holes in myself by adding exceptions like http, https, ICMP...

Maybe they changed the default setup for gufw now...

ufw does not block outgoing connections, only incoming.

---

### Post by hockeytux on 2009-10-04
> **lovinglinux said:**
> ufw does not block outgoing connections, only incoming.

Thanks. :KS

Thread marked as solved.

---

