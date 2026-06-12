---
title: "easy way to learn what outbound traffic GUFW is blocking?"
date: 2011-06-09
forum: Security
---

### Post by nrundy on 2011-06-09
If one activates GUFW to prevent outgoing connections, is there a program or way to learn of what traffic is being blocked?

For example, say user has blocked all outgoing traffic. When one opens a web browser and tries to go online, is there a way to learn that port 80 is receiving outbound requests but is being blocked?

---

### Post by uRock on 2011-06-09
Scroll down to logs [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

```
sudo ufw logging on
```> The above log will also appear in /var/log/messages, /var/log/syslog, and /var/log/kern.log. 

---

### Post by nrundy on 2011-06-09
Is there a log that just shows internet connections? The logs you direct me to look enormously complicated. They seem to be covering a lot more than port connections etc.

Maybe I need a log analyzing tool? Could you kindly explain how I might simplify the logs to focus on finding blocked connections?

---

### Post by uRock on 2011-06-09
System> Admin> Log File Viewer may do what you want. I'm not in Ubuntu at the moment to see what it shows.

---

### Post by nrundy on 2011-06-09
Thanks for pointing that out.

Do you know where I might read up on how to make sense of these logs? Hard to know what you're looking at? In the UFW log tab I see MAC addresses and stuff but I don't see ports or IP addresses. 

Maybe in the future you might post back if there's a way to learn of these blocked ports that is compatible with noobs? ;)

Thanks for your help so far URock :)

---

### Post by uRock on 2011-06-09
I denied outgoing for a second to get a log entry under the "messages". The actual entry ```
Jun  9 18:15:44 uRock-desktop kernel: [ 3677.200729] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.1 DST=16.15.128.11 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=10040 DF PROTO=UDP SPT=45967 DPT=53 LEN=42
``` Now I'll break it down for you,
**Jun  9 18:15:44**     [COLOR="Red"]Date of entry.[/COLOR] 
**uRock-desktop**     [COLOR="red"]Computer Name[/COLOR] 
**kernel: [ 3677.200729]**     [COLOR="red"]Though it was listed in "messages" it is still a kernel log entry[/COLOR]
**[UFW BLOCK]**     [COLOR="red"]Application creating the log entry[/COLOR] 
**IN=**     [COLOR="red"]In has nothing after it because the packet was outbound[/COLOR]
**OUT=wlan0**     [COLOR="red"]Shows the outbound interface as wlan0[/COLOR]
**SRC=192.168.1.1**     [COLOR="red"]Source IP of the packet[/COLOR]
**DST=16.15.128.11**     [COLOR="red"]Destination IP of packet[/COLOR]
**LEN=62**     [COLOR="red"]Legth of packet header[/COLOR]
**TOS=0x00**     [COLOR="red"]Type of service[/COLOR]
**PREC=0x00**     [COLOR="red"]Me not sure of this one[/COLOR]
**TTL=64**     [COLOR="red"]Time to live. This tell routers and switches how many times to forward the packet before dropping it[/COLOR]
**ID=10040 DF**     [COLOR="Red"]Not sure what the ID # is, but DF means Don't Fragment[/COLOR]
**PROTO=UDP**     [COLOR="red"]This packet uses the UDP protocol[/COLOR]
**SPT=45967**     [COLOR="red"]Source port[/COLOR]
**DPT=53**     [COLOR="red"]Destination port (this is a DNS packet)[/COLOR]
**LEN=42**     [COLOR="red"]length of packet data[/COLOR]

As for making this newb friendly, I am not sure that will happen unless someone implements the brainstorm idea in your signature. As we know, there are loads of apps that can use the DNS packet shown here as well as many other outbound communications. 

The easiest way to figure this out is to get the info above, use the whois command with the dest IP and find where it is going,then use the dest port to figure out what service it is. We already know the is a DNS packet headed to my ISPs DNS server.

---

### Post by Toz on 2011-06-09
> **nrundy said:**
> Is there a log that just shows internet connections?

You can install **iptstate** to get a top-like view of active connections. > Description: top-like interface to your netfilter connection-tracking table
 IP Tables State (iptstate) was originally written to implement
 the "state top" feature of IP Filter (see "The Idea" below) in
 IP Tables. "State top" displays the states held by your stateful
 firewall in a top-like manner.
 .
 Features include:
  - Top-like realtime state table information
  - Sorting by any field
  - Reversible sorting
  - Single display of state table
  - Customizable refresh rate
  - Display filtering
  - Color-coding
  - Open Source (specifically I'm using the zlib license)
  - much more...

This will show you currently active connections, but you will still need to view the logs to see what is being blocked.

---

### Post by nrundy on 2011-06-10
> **uRock said:**
> I denied outgoing for a second to get a log entry under the "messages". The actual entry ```
Jun  9 18:15:44 uRock-desktop kernel: [ 3677.200729] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.1 DST=16.15.128.11 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=10040 DF PROTO=UDP SPT=45967 DPT=53 LEN=42
``` Now I'll break it down for you,
**Jun  9 18:15:44**     [COLOR="Red"]Date of entry.[/COLOR] 
**uRock-desktop**     [COLOR="red"]Computer Name[/COLOR] 
**kernel: [ 3677.200729]**     [COLOR="red"]Though it was listed in "messages" it is still a kernel log entry[/COLOR]
**[UFW BLOCK]**     [COLOR="red"]Application creating the log entry[/COLOR] 
**IN=**     [COLOR="red"]In has nothing after it because the packet was outbound[/COLOR]
**OUT=wlan0**     [COLOR="red"]Shows the outbound interface as wlan0[/COLOR]
**SRC=192.168.1.1**     [COLOR="red"]Source IP of the packet[/COLOR]
**DST=16.15.128.11**     [COLOR="red"]Destination IP of packet[/COLOR]
**LEN=62**     [COLOR="red"]Legth of packet header[/COLOR]
**TOS=0x00**     [COLOR="red"]Type of service[/COLOR]
**PREC=0x00**     [COLOR="red"]Me not sure of this one[/COLOR]
**TTL=64**     [COLOR="red"]Time to live. This tell routers and switches how many times to forward the packet before dropping it[/COLOR]
**ID=10040 DF**     [COLOR="Red"]Not sure what the ID # is, but DF means Don't Fragment[/COLOR]
**PROTO=UDP**     [COLOR="red"]This packet uses the UDP protocol[/COLOR]
**SPT=45967**     [COLOR="red"]Source port[/COLOR]
**DPT=53**     [COLOR="red"]Destination port (this is a DNS packet)[/COLOR]
**LEN=42**     [COLOR="red"]length of packet data[/COLOR]

As for making this newb friendly, I am not sure that will happen unless someone implements the brainstorm idea in your signature. As we know, there are loads of apps that can use the DNS packet shown here as well as many other outbound communications. 

The easiest way to figure this out is to get the info above, use the whois command with the dest IP and find where it is going,then use the dest port to figure out what service it is. We already know the is a DNS packet headed to my ISPs DNS server.

URock, this is great info. It is noob-understandable. Thanks so much; this is a big help. 

Another question I have is what level of logging do I need? Considering the reasons I'm going to be looking at the logs (primarily to make sure a port that's being blocked is not one that should be allowed for outbound traffic), what level of logging do I need?

You mentioned sudo ufw logging. Can I turn "sudo ufw logging" off and just set logging from the GUFW settings? Or should I disable GUFW settings and leave "sudo ufw logging on". Or should I set them both to be on???  If GUFW, what level of settings should I set: Low, Medium, High, Full. A LOT of logs can pile up. And if I'm not really needing all the LOGS, it seems I should only configure for what I understand and will be looking at.

---

### Post by nrundy on 2011-06-10
> **Toz said:**
> You can install **iptstate** to get a top-like view of active connections. 

This will show you currently active connections, but you will still need to view the logs to see what is being blocked.

This is Great!

Thanks so much for pointing it out.

You guys have been a big help. Wish the application name was listed in these lists, but otherwise these are a huge help :p

---

### Post by uRock on 2011-06-10
> **nrundy said:**
> URock, this is great info. It is noob-understandable. Thanks so much; this is a big help. 

Another question I have is what level of logging do I need? Considering the reasons I'm going to be looking at the logs (primarily to make sure a port that's being blocked is not one that should be allowed for outbound traffic), what level of logging do I need?

You mentioned sudo ufw logging. Can I turn "sudo ufw logging" off and just set logging from the GUFW settings? Or should I disable GUFW settings and leave "sudo ufw logging on". Or should I set them both to be on???  If GUFW, what level of settings should I set: Low, Medium, High, Full. A LOT of logs can pile up. And if I'm not really needing all the LOGS, it seems I should only configure for what I understand and will be looking at.

When the UFW logging command is run, you will see the check box for logging in GUFW toggle on. I don't know anything about the levels of logging. I will take a look at the GUFW wiki and see what I can find when I get some free time.

---

### Post by Toz on 2011-06-10
About logging levels, **man ufw** says the following:
> LEVEL  may  be  'off', 'low', 'medium', 'high' and full. Log levels are
       defined as:

       **off**    disables ufw managed logging

       **low**    logs all blocked packets not matching the default  policy  (with
              rate limiting), as well as packets matching logged rules

       **medium** log level low, plus all allowed packets not matching the default
              policy, all INVALID packets, and all new connections.  All  log&#8208;
              ging is done with rate limiting.

       **high**   log  level medium (without rate limiting), plus all packets with
              rate limiting

       **full**   log level high without rate limiting

       Loglevels above medium generate  a  lot  of  logging  output,  and  may
       quickly  fill  up your disk. Loglevel medium may generate a lot of log&#8208;
       ging output on a busy system.

Specifying 'on' simply enables logging at log level 'low' if logging is
       currently not enabled.


From experience I can tell you that you are going to see a ton of crap hitting the firewall regularly - you will never be able to stay on top of it at the higher levels of logging. I usually keep logging turned off unless I'm specifically looking for something, at which point I turn it on to the level appropriate to what I'm looking for.

---

### Post by nrundy on 2011-06-10
> **Toz said:**
> About logging levels, **man ufw** says the following:


From experience I can tell you that you are going to see a ton of crap hitting the firewall regularly - you will never be able to stay on top of it at the higher levels of logging. I usually keep logging turned off unless I'm specifically looking for something, at which point I turn it on to the level appropriate to what I'm looking for.

What is "Rate Limiting"?

If I set it to Low, I was thinking I could periodically check it to learn of any blocked connections. Or if a program is not working, I could check log to make sure I don't need to allow a port for it. What do you think?

---

### Post by Toz on 2011-06-10
> **nrundy said:**
> What is "Rate Limiting"?
In the sense of logging, it means to limit the display/recording of simultaneous events. If, for example, you get 100 connection attempts a minute that are being logged, rate-limiting will only display/record a small number of those instead of all of them. Saves on log sizes. 

> If I set it to Low, I was thinking I could periodically check it to learn of any blocked connections. Or if a program is not working, I could check log to make sure I don't need to allow a port for it. What do you think?
It really is a matter of preference - there is no right or wrong. Give it a try and see how it goes. You can always reset the level whenever you want.

---

