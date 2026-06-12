---
title: "Cant block udp (quake) ports with iptables"
date: 2012-04-06
forum: Security
---

### Post by JohnMazurka on 2012-04-06
Hi

I've just started getting traffic through my server to port 27960 and 27962 (quake ports)
all heading to a destination address of 83.170.84.81. These all using UDP.
They all originate from different ip addresses

So have tried to block the host and its ports on udp protocol using iptables, but what ever i do they do not get dropped.

here's the line from iptables -L

DROP       udp  --  anywhere offendingaddress.co.uk udp dpt:27960 
DROP       udp  --  anywhere offendingaddress.co.uk udp dpt:27962 

and I have them as first in the list

here's the iptables commands i used:

iptables -A INPUT -d ip.add.re.ss -p udp --dport 27960 -j DROP
iptables -A INPUT -d ip.add.re.ss -p udp --dport 27962 -j DROP

I've tried all different combinations but still cant block them

have even tried blocking some of the source hosts, but that doesn't work either

any ideas anybody?

John

---

### Post by darkod on 2012-04-06
If you don't care about the destination, if you don't mind blocking those ports to all, drop the -d option:
iptables -A INPUT -p udp --dport 27960 -j DROP

Also, are you working with the iptables on the server receiving the traffic, or on a server that is like firewall/gateway in between? If the destination server is different machine, the traffic might get forwarded regardless of these INPUT rules because the INPUT is for traffic destined only for that server. You might also wanna try:
iptables -A FORWARD -p udp --dport 27960 -j DROP

That should block forwarding traffic too.

---

### Post by JohnMazurka on 2012-04-06
Hi Darkrod

cheers for suggestions. Have tried them already, but have put them in again.
However, still the traffic's still getting through.

---

### Post by JohnMazurka on 2012-04-06
sorry, spelt your name wrong.

most of the sources come from udp port 80
so I have dropped that in forwarding and they seem to have abated.
However, they come in spurts - so there might just be a lull in the traffic.

Will post updates.

John

---

### Post by JohnMazurka on 2012-04-06
Guess what - half an hour later and they are back!

dagnabit

john ;(

---

### Post by darkod on 2012-04-06
I am not an expert but I just worked on a firewall project and I think I can help. Mine works as expected (so far, knock on wood).

Explain in details (or better with pictures) the traffic flow and lets see what we have to work with. To protect yourself, use fake public and private IPs in the network diagram you post.

I didn't understand this with port 80. Is the source port 80 and destination port 27960? Can you post a few actual ACCEPT entries from the log? (again, change the IPs of your network)

---

### Post by JohnMazurka on 2012-04-06
yes port 80 is source and detination is 27960 or  (27962)

I'm monitoring traffic using the base/ snort interface
Between 13.52 and 13.59 I got 14 hits with different source ip's from port 80 connecting to another ip address (the same one for them all though) on port 27960 all using  UDP

Here's a snapshot from base
                    time                               source                      destination                 protocol
     2012-04-06 13:59:22     different.ip.address:80             offendingaddress.co.uk:27962     UDP
     2012-04-06 13:58:23       another.ip.address:80             offendingaddress.co.uk:27962     UDP
     2012-04-06 13:58:22     stillanother.ip.address:80             offendingaddress.co.uk:27960     UDP
     2012-04-06 13:57:23     more.ip.address:80               s            offendingaddress.co.uk:27960     UDP
     2012-04-06 13:57:22      evenmore.ip.address7:            offendingaddress.co.uk80 :27960     UDP
.
.
.

Here's my Iptables Forwarding 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             offendingaddress.co.uk 
DROP       udp  --  anywhere             anywhere            udp dpt:27960 
DROP       udp  --  anywhere             anywhere            udp dpt:27962 
DROP       udp  --  anywhere             offendingaddress.co.uk k udp dpt:27962 
DROP       all  -- xxxxx.xxx.pa.xxxx.net  anywhere            
DROP       all  --  servxxx.uxxx2net.com  anywhere            
DROP       all  -- xxxxx.socal.xxx.xxx.com  anywhere            
DROP       all  --  xxxxxx.xxxxxx.com    anywhere            
DROP       all  --  xxxx.clients.xx-xxxxx.de  anywhere            
DROP       all  --  xxxxx.xxxx.sky.com  anywhere            
DROP       udp  --  anywhere             anywhere            udp spt:www 

as you can see I've got a number of attempts in there 
and have tried dropping some of the incoming trafficand one of them is connecting to it at this minute.

I also have the offendingaddress.co.uk dropped (apparently) at the top of the input table too and at the bottom


Hope that explains it well enough,

John

---

### Post by Doug S on 2012-04-06
I'm having trouble following this thread. It is not clear to me why the focus is on the FORWARD chain. If the packets are unsolicited from the outside world, then they would fall into the INPUT chain. If the packets are in reply to a computer or computers on the LAN then is there a related/established bypass somewhere?
If my reply makes no sense, I say again, I'm having trouble to follow this one.
I don't know about base/snort interface. I would be using tcpdump or tshark or wireshark to monitor things at the packet level.
 
Edit: I missed your note at the bottom about the INPUT chain.

---

### Post by JohnMazurka on 2012-04-06
am not 100% certain as to INPUT or FORWARD really

but here's the input chain too

Chain INPUT (policy DROP)
target     prot opt source               destination         
DROP       udp  --  anywhere             offendingaddress.co.uk  udp dpt:27960 
DROP       udp  --  anywhere             offendingaddress.co.uk  udp dpt:27962

---

### Post by SeijiSensei on 2012-04-06
None of this traffic appears intended for your machine, right?  It's not uncommon to see traffic on your external interface with other destination addresses, especially UDP traffic.  

As long as you have DROP as your default iptables INPUT policy, there's nothing to be concerned about.

---

### Post by darkod on 2012-04-06
I don't know how base works, in my firewall I actually used UFW as front end for iptables and the entries are in ufw.log. In the log there is a remark like [UFW ALLOW] or [UFW BLOCK].

The part of the log you posted never says anything about allow or block. Are you sure that traffic was not blocked because even blocked traffic appears in the log? In that case you have nothing to worry about. The traffic was dropped.

Is your iptables on offendingaddress.co.uk? In that case you need to work with the INPUT chain, as I mentioned earlier.

But in any case first make sure what you are seeing in the logs is not blocked (dropped) traffic. Are you sure it passed the firewall?

---

### Post by Doug S on 2012-04-06
I agree with Seiji, and was just coming back to write the same.> 2012-04-06 13:59:22 different.ip.address:80 offendingaddress.co.uk:27962 UDP
2012-04-06 13:58:23 another.ip.address:80 offendingaddress.co.uk:27962 UDP
2012-04-06 13:58:22 stillanother.ip.address:80 offendingaddress.co.uk:27960 UDP
2012-04-06 13:57:23 more.ip.address:80 s offendingaddress.co.uk:27960 UDP
2012-04-06 13:57:22 evenmore.ip.address7: offendingaddress.co.uk80 :27960 UDP
another.ip.address and stillanother.ip.address etc. are not within your LAN, right?
 
For my ISP, I never get packets not destined for one of my IPs.

---

### Post by JohnMazurka on 2012-04-06
Yes, it seems to be going elsewhere other than my machine.
So are you saying it's just bouncing around the network and I shouldn't worry - seems quite a big leap of faith at the minute.

here's some of the out put from tcpdump
it might shed some light

15:59:27.632823 IP (tos 0x8, ttl 249, id 19145, offset 0, flags [none], proto UDP (17), length 42)
    connectingaddress > offendingaddress.co.uk.27960: UDP, length 14
15:59:27.632827 IP (tos 0x8, ttl 249, id 19146, offset 0, flags [none], proto UDP (17), length 42)
    connectingaddress > offendingaddress.co.uk.27960: UDP, length 14
15:59:27.632832 IP (tos 0x8, ttl 249, id 19147, offset 0, flags [none], proto UDP (17), length 42)
    connectingaddress > offendingaddress.co.uk.27960: UDP, length 14
15:59:27.632837 IP (tos 0x8, ttl 249, id 19148, offset 0, flags [none], proto UDP (17), length 42)
   connectingaddress > offendingaddress.co.uk.27960: UDP, length 14

cheers,

John

---

### Post by JohnMazurka on 2012-04-06
seems like the general consensus is to ignore it. It doesn't seem to be getting in as far as I can tell- perhaps just bouncing off.

OK, thanks everyone for your help - -I'll try ignore it ;)

---

### Post by SeijiSensei on 2012-04-06
This is especially common on systems connected via cable television circuits.  The topology of cable internet services means you're sharing the circuits with dozens or even a few hundred other households in your area.  In that case you'll see plenty of traffic for those other customers passing by your external interface.

---

### Post by JohnMazurka on 2012-04-06
Thanks for the info SeijiSensei

---

