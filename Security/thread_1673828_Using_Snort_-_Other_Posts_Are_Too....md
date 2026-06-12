---
title: "Using Snort - Other Posts Are Too..."
date: 2011-01-23
forum: Security
---

### Post by Toronto11 on 2011-01-23
Hi there,

I'm trying to use Snort to see what it does etc. after hearing about it, but I can't seem to interpret the alerts, if that's what they are, in the terminal.  I think I need to update my rules, but I'm not having any luck.

I run Snort using the command:

sudo snort -v -i eth0

And then I get this:

01/23-00:26:31.509173 99.000.000.000:631 -> 99.000.000.000:631
UDP TTL:64 TOS:0x0 ID:0 IpLen:20 DgmLen:171 DF
Len: 143

And there are a lot of these 'alerts', but I can't decipher them, nor can I tell if I'm getting too many or not enough.

I've read many articles and still can't seem to make heads or tales of this.

Thanks for any replies.

---

### Post by cariboo on 2011-01-24
A bump for the move.

---

### Post by uRock on 2011-01-24
There is usually a title line in the snort alert, if this alert has that, then can you post it?

I had one rule that was giving me lots of false alerts that I had to remove. Having the title helps find where the rule is stored.

---

### Post by Kinstonian on 2011-01-24
You're not running it in IDS mode.  To run it in IDS mode, you need to specify the snort config file using the -c option.  Right now, you're just seeing packet data in output similar to tcpdump.

To understand what it is showing you, try searching for information on various network protocols like [IP](https://secure.wikimedia.org/wikipedia/en/wiki/IPv4#Packet_structure), [UDP](https://secure.wikimedia.org/wikipedia/en/wiki/User_Datagram_Protocol#Packet_structure) and [TCP](https://secure.wikimedia.org/wikipedia/en/wiki/Transmission_Control_Protocol#TCP_segment_structure).

---

