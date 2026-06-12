---
title: "random open ports"
date: 2008-06-01
forum: Security
---

### Post by joeboentoe on 2008-06-01
If I do a port scan then I get random open ports. Every time I hit the button "scan" I get other open ports, except for the ipp 631 which is always open. see screens:

[portscan1.png]("http://users.telenet.be/tranceminded/linux/portscan1.png")
[portscan2.png]("http://users.telenet.be/tranceminded/linux/portscan2.png")
[portscan3.png]("http://users.telenet.be/tranceminded/linux/portscan3.png")


If I do netstat -lp 127.0.0.1 . I don't get the random open ports. Only the ipp 631 which is always there and has the STATE "LISTEN", and some udp which have an empty "STATE"

If I do nmap 127.0.0.1 I only get the ipp 631 port

So, what is going on? How can I find the processes that opens the random ports?

thanks

---

### Post by barboachtraner on 2008-06-01
Were you running a torrent client? I noticed a similar situation a while ago where I sometimes had a open connection on a seemingly random high numbered port, and it was apparently from connecting to torrent peers, even after I closed the client (Deluge) itself.

---

### Post by Mister.Vash on 2008-06-01
Open up a terminal window and input the following:

```

sudo netstat -tulpn

```

This will show the listening ports and the process that owns them

---

### Post by joeboentoe on 2008-06-01
I did run a torrent, but I rebooted since then.. , and the random ports are different from the ones I configured in my bittorrent client.

sudo netstat -tulpn shows the listeners, but the random ports aren't appearing here, I don't know why.:confused:

---

### Post by Mister.Vash on 2008-06-01
Running the gnome-nettool on my machine and hitting scan a few time, I can see the same behavior.  While doing this, I was also running netstat with the refresh option and didn't see any additional listening ports showing up.

You may want to ask here and see if anyone has an idea.  
[https://answers.launchpad.net/ubuntu/hardy/+source/gnome-nettool/+questions](https://answers.launchpad.net/ubuntu/hardy/+source/gnome-nettool/+questions)

It could be that the scan is picking itself up.  I ran a continuous port scan from another machine against this one for about 30 minutes and I didn't see anything new appear as a listening port so I don't think that the ports showing up via the gnome-nettool are actually open.

---

### Post by MythosLegend on 2008-06-02
My guess is the same as Mister.Vash's

I have the same situation. I would scan with the gnome tool several times. There is usually one consistent port open (unknown service) and new additional ports created each time. 

I would do a netstat -ta after each scan and notice that the consistent port would have localhost for Local Address and Foreign Address. The other random ports would sometimes show up and sometimes not. When the random ports do show, the ports are in a listening state (sometimes with a localhost for Foreign Address). 

The consistent port is most likely the local loopback port listening to itself. 

As a temporary test, I decided to block my local loopback with some iptables rules.

When I scan with gnome-nettool and netstat, I don't have any open ports.

---

### Post by joeboentoe on 2008-06-02
thanks for the replies, I will post it at launchpad too. Because I guess it's quiet confusing for a lot of people.

---

