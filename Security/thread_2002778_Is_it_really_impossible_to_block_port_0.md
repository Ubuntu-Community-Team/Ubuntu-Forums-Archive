---
title: "Is it really impossible to block port 0?"
date: 2012-06-13
forum: Security
---

### Post by zozza on 2012-06-13
How can I block all incoming traffic to port 0?

```

sudo ufw deny 0

ERROR: 'Bad port'

```

I am using 10.04.

Thanks.

---

### Post by roelforg on 2012-06-13
It's not an actual port.
It's a psuedo port that allows a server to bind to it and it will be assigned a random port >1023. It's easier then to try to avoid every port known to man to be in use. It's because programmers are lazy (i'm one too so don't get worked up about it, most people know that we program computers to do stuff we're to lazy (or inable) to do ourselves; It's human nature).

---

### Post by prshah on 2012-06-13
> **zozza said:**
> 
```

sudo ufw deny 0

ERROR: 'Bad port'

```

As explained, you cannot block virtual port 0. However, you can block ALL ports by default, and ALLOW specific ports as you require.

```
sudo ufw default deny
```

---

### Post by The Cog on 2012-06-13
That's an interesting point. It's not actually possible for an application to open port 0 for listening (as roelforg says, the OS will open a high unused port number instead) - asking to open port 0 is how applications say they don't care what port number they are given. But the TCP and UDP protocols can carry packets to/from port 0. I assume that the recipient will simply reply with a port unreachable message, since the port can never actually be open.

It is possible to block TCP or UDP port 0 using iptables, so I guess the "ERROR: 'Bad port'" message for port 0 is a minor bug in ufw.

---

### Post by zozza on 2012-06-13
Thanks for the suggestions.

I don't think the deny all then open specific ports would necessarily work as I use applications like Deluge (for torrents) which open a myriad of random ports.

I guess the way to do it is to learn iptables directly. 

The reason I wanted to block port 0 is because I ran Nessus HomeFeed scanner on my IP address and was astounded by the amount of information it gathered about my machine which included MAC address, internal IP addresses, operating system, etc.  

It did this through making tcp and udp connections to port 0 and was able to run commands like uname, netstat, and iptables on my machine.

However, I guess that this is only possible because I was running the scanner on myself (from my IP to my IP).

I cannot imagine it would be possible for an external IP address to run commands like iptables on my computer from over the Internet.

Opinions?

---

### Post by Cheesehead on 2012-06-13
> **zozza said:**
> ...astounded by the amount of information it gathered about my machine which included MAC address, internal IP addresses, operating system, etc.
That's all public information, and often included in (for example) http request headers. That's one way websites know your OS or approximate geographic location.


> **zozza said:**
> ...I use applications like Deluge (for torrents) which open a myriad of random ports.
The actual torrent connection on a random port need not be unblocked; deluge will initiate the outbound connection through the port, so the firewall will see the connection as permitted. Only deluge's normal ports need be unblocked.

---

### Post by The Cog on 2012-06-14
> **zozza said:**
> Thanks for the suggestions.

I don't think the deny all then open specific ports would necessarily work as I use applications like Deluge (for torrents) which open a myriad of random ports.

I guess the way to do it is to learn iptables directly. 

The reason I wanted to block port 0 is because I ran Nessus HomeFeed scanner on my IP address and was astounded by the amount of information it gathered about my machine which included MAC address, internal IP addresses, operating system, etc.  

It did this through making tcp and udp connections to port 0 and was able to run commands like uname, netstat, and iptables on my machine.

Opinions?
I very much doubt that this was done through port 0. What makes you think that it was?

I think it may be possible to get the MAC address by sending a packet to port 0 (provided you are on the same LAN) because of course any ICMP port unreachable message will have the sender's MAC address on in the ethernet header. This also confirms that the target IP address is present. But that's all.

Did you realise that ufw allows full connectivity from your machine to itself? When scanning your machine from itself, your firewall will not stop you.

---

### Post by dodo3773 on 2012-06-15
> 
I don't think the deny all then open specific ports would necessarily work as I use applications like Deluge (for torrents) which open a myriad of random ports.


Deluge should open only dynamic ports on your end unless you specifically configure it to do otherwise. This will not always be the same though when looking at the foreign traffic. In which case I agree with you. If someone is seeding a torrent to me on a port that does not make sense I just block that port (not the local port on my machine (I block the foreign incoming port)). This can be accomplished with either iptables or tcpkill (part of the dsniff package (well at least it used to be)). Tcpkill will block the traffic locally on that port as well.

To block just a foreign port in iptables it would look something like this:
```

-A INPUT -i wlan0 -p tcp --source-port 10252 -j DROP

```

and for a port range:
```

-A INPUT -i wlan0 -p tcp --source-port 6668:8079 -j DROP

```

To block a port in tcpkill it is simple as this:
```

sudo tcpkill -i wlan0 port 10055

```

or a port range:
```

sudo tcpkill -i wlan0 portrange 10080-10081

```

to run multiple expressions in tcpkill use "or":
```

sudo tcpkill -i wlan0 portrange 0-20 or port 22 or portrange 44-79

```

---

### Post by zozza on 2012-06-16
Thanks everyone for your help.

> I very much doubt that this was done through port 0. What makes you think that it was?

I guess it depends what you mean by port 0.

The Nessus scan result showed that netstat / unname / iptables commands were issued on port 0.

However, I now understand that the commands are actually issued on other ports and that port 0 simply means that the server should execute the commands on the appropriate ports.

I also appreciate that if I am scanning myself then it will generate more information than would be the case between networks.

And that the MAC addresses can only be obtained if Nessus is on the same network (which was the case).

Thanks again all!

---

### Post by dodo3773 on 2012-06-16
> **zozza said:**
> 
And that the MAC addresses can only be obtained if Nessus is on the same network (which was the case).


Your mac address can be obtained by anyone on your lan pretty easily. Just spoof your mac address. I have not broadcast my real one in over a year at least.

---

### Post by zozza on 2012-06-18
> Your mac address can be obtained by anyone on your lan pretty easily.  Just spoof your mac address. I have not broadcast my real one in over a  year at least. 	

Sure, but the key issue here is on the LAN.  It's not transmitted to a website located on the Internet.

It's also worth noting that sometimes MAC address filtering prevents the spoofing (unless I suppose you have always used one spoofed address from the first time you connected).

---

### Post by dodo3773 on 2012-06-18
> **zozza said:**
> 
It's also worth noting that sometimes MAC address filtering prevents the spoofing (unless I suppose you have always used one spoofed address from the first time you connected).

I used to use the same spoofed mac address all the time because I liked to have a static ip. Now I randomize it at every boot. I do disagree with you on the mac address filtering though because it is so easy to spoof your mac address.

---

