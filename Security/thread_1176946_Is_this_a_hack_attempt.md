---
title: "Is this a hack attempt?"
date: 2009-06-02
forum: Security
---

### Post by GettingBits on 2009-06-02
Hey everyone,

I have port 10001 port-forwarded to a machine on my network for bit torrent usage. The machine in question was just wiped and a fresh copy of 9.04 was installed. I haven't bothered to setup the bt client yet. I was messing with my router and noticed that a particular ip keeps hitting the open port. When I first noticed it the internal machine in question wasn't even running. I fired it up and installed wireshark. Here is what I am seeing:

The IP that keeps hitting port 10001 is based in china. a new connection attempt is made every minute or so. The port it originates from keeps going up. It started at 55220, went as high as 65419 and then started back at port 1366. According to the mac address, the device is a "Cisco-Li_35:e7:cb".

Any clue what this person is trying to accomplish? Why would you keep trying the same port but with different ports on your end?

---

### Post by statistic on 2009-06-02
That sounds like an attack to me.

When this attacker hits your router on an unforwarded port, your router rejects the connection outright. However when it forwards it somewhere and there isn't a response it just hangs until it gives up on waiting for the your machine to respond. I suppose this user is trying to guess which port your machine would expect the outgoing port to be since some protocols (I believe bitorrent is one of them, but I don't think that that is relevant right now) that sends packets out on one port to be received on another.

You could ping him back really hard for fun :), but that might start trouble. I suggest, if possible, to change your ip address and your forwarding port before firing up bt.

---

### Post by lovinglinux on 2009-06-03
Probably nothing to worry about, since it is hitting the torrrent port every time. You could close the port on the router to see if it hits other ports on your machine, which could indicate a port scanning activity. But the scenario you have is probably due to torrent ghost packets, specially if you have a static external IP address. Let me explain.

Your torrent client was configured to accept connections on port 10001 and you were probably using it before the fresh install. So at some point, your torrent client connected to a tracker to grab the list of peers sharing the same file and also to add your IP to the list, so other peers could request connections to you. If you have a static external IP address or didn't change it since you were torrenting, then the tracker you were using to share torrents might still have your IP listed for a particular torrent or a set of torrents. So the computer hitting you could be grabbing a list of peers from the tracker that are not updated. Additionally it could also be hitting you because the user configured his torrent client to scrape the tracker only a couple of times per day, then he would probably still have your IP on his peer list, even if your IP is not listed on the tracker anymore. He will stop hitting you once he updates his peer list by scraping the tracker.

But why it keeps changing the port source every time?

Simple. Torrent connections has always the same combination of IP/port in the destination side of the connection, but the source port will varies all the time, unless you also configure the torrent client to use a specific set of ports for outgoing connections (not all clients can do that). Basically you will send data to a peer on the port the remote user choose, but your client will choose whichever port is available at the moment to send the data from. The same applies to other side of the connection. The remote user will send data to you only on port 10001, but his torrent client will choose the first available port to originate the connection. Since peers connect to several users all the time, the number of ports used to originate the connection varies all the time.


If you don't have an static IP or did change it since the last time torrenting, then you might actually have someone trying to breach your system. Is not unusual to get several ghost packets from different users on the same destination port. This is the most common scenario of ghost packets for those who have dynamic IPs, because the ISP doesn't have the exact number of IPs based on number of costumers. So, they basically share a huge amount of IP's with all their costumers, because at a given time not all of them will be connected. So when you turn on your computer and connect to the ISP, they assign you the first available IP. This IP could be under use just a few seconds before you connected, so you might be assigned with an IP from someone that was previously using a p2p software or a service listening to a port. Nevertheless, being assigned with a new IP that was using the exact port for incoming connections as the one you have forwarded from the router is not a probability winner.

*UKeywords: 649167 2009 june ghost packet security port remote peer tracker torrent*

---

### Post by GettingBits on 2009-06-03
Thanks for the responses! I closed the port for now. Problem solved. I might open it again in a week or so to see if they are still knocking. My IP hasn't changed in quite a while so it's possible it's just someone trying to get me to seed 9.04 some more. Oh well.

---

### Post by bodhi.zazen on 2009-06-03
"hits" on ports are a dime a dozen. 

The solution is the same - learn to secure your server ;)

---

### Post by |{urse on 2009-06-03
the device is a "Cisco-Li_35:e7:cb". <-- thats a cisco switch, while those are hijacked by others quite commonly to do naughty things to unsuspecting users it's probably nothing. If you really want to be safe, set up iptables. If youre really worried, issue the "who" command to check to make sure youre the only one logged in,  run rkhunter to check for rootkits (not very effective, but might as well) then go pay a visit to this site *to check your system for security holes.*
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

