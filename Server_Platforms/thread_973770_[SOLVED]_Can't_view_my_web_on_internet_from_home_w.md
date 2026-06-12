---
title: "[SOLVED] Can't view my web on internet from home web server"
date: 2008-11-07
forum: Server Platforms
---

### Post by shanep-server on 2008-11-07
Ok i'm kind of new too linux... like 3 days new haha.

I installed Ubuntu 8.10 desktop to my computer in 1 room. Its the only os installed. I have 2 computers and 1 router for current home network.

I am trying to set up a linux server on extra computer to host a web site. ( for fun and experience ) I want this website visible to the outside world. I have dynamicIP from ISP. I followed a tutorial to installed LAMP from command line. I can view my index.html file from my 2nd computer, by typing the local ip address provide by router, into web browser. (i checked local ip address with "ifconfig") I forwarded port 80 to receive HTTP. I set up a dynamicDNS from dynamicDNS.org. used synaptic package handler to install ddclient. I used gedit with gksudo to edit ddclient.conf. I got a hostname from dynamicDNS. I set the hostname to host with IP Address option. I set the ip to my current router ip. 

when i type in my hostname (shanep-server.ath.cx) i get timed out. when i type in my router ip i get timed out. when i type in my local ip where LAMP is installed I view my index.html file. 

Now since I have port 80 forwarded for HTTP shouldn't i be able to type either my hostname provided by DNS or my external/router ip to access the index.html file?

Any help would be sweet. I'm rockin

Ubuntu 8.10
-gnome
most recent version "LAMP" installed command line 3 days ago
router
ISP-comcast
DynamicDNS.org

---

### Post by pgorillaman on 2008-11-07
Have you tried to ping your hostname to see if it resolves correctly. I was unable to ping the address you gave. Try ```
ping shanep-server.ath.cx
```
Another good tool is nmap.
```
sudo apt-get install nmap
```
You can use this tool to see if port 80 is open.```
nmap -p 80 shanep-server.ath.cx
``` or ```
nmap -p 80 localhost
```

---

### Post by shanep-server on 2008-11-07
i ran "ping shanep-server.ath.cx"

64 bytes from c-xx-xxx-xxx-xxx-.hsdl.mi.comcast.net (xx.xxx.xxx.xxx): icmp_seq=76 ttl=64 time=0.600 ms

xx.xxx.xxx.xxx = my external ip address

Not sure about  the nmap u suggested

---

### Post by pgorillaman on 2008-11-07
Nmap will tell us if apache is setup to listen for connection from the outside world.

---

### Post by shanep-server on 2008-11-07
nmap -p 80 shanep-server.ath.cx

starting Nmap 4.62 ( http://nmap. org ) at 2008-11-07 02:52 EST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.353 seconds

nmap -p 80 localhost

Starting Nmap 4.62 ( http://nmap.org ) at 2008-11-07 02:55 EST
Interesting ports on localhost (127.0.0.1):

PORT STATE SERVICE
80/tcp open http

Nmap done: 1 IP address (1 host up) scanned in 0.169 seconds

So i don't know what this means....

---

### Post by pgorillaman on 2008-11-07
It looks like your router isn't forwarding correctly but try this to make sure.

nmap -PN -p 80 shanep-server.ath.cx

---

### Post by shanep-server on 2008-11-07
Starting Nmap 4.62 ( http://nmap.org ) at 2008-11-07 03:10 EST
Interesting ports on c-xx-xxx-xxx-xxx.hsd1.mi.comcast.net (xx.xxx.xxx.xxx):
PORT STATE SERVICE
80/tcp filtered http

Nmap done: 1 IP address (1 host up) scanned in 2.533 seconds

---

### Post by pgorillaman on 2008-11-07
So either your router isn't configured correctly to forward all incoming connections on port 80 to your server or their is a firewall blocking port 80. What model router do you have?

---

### Post by shanep-server on 2008-11-07
netgear wgr614 54 mb wireless router with 4 wired plug-ins

---

### Post by pgorillaman on 2008-11-07
In your router's config under Port Fowarding/Port Triggering is there a rule to forward port 80 to the ip of your server?

Your router manual:
[http://kbserver.netgear.com/pdf/wgr615v_manual.pdf#xml=http://kbserver.netgear.com/inquira/default.asp?ui_mode=answer&prior_transaction_id=756358&action_code=6&highlight_info=352321914,12,23&turl=http%3A%2F%2Fkbserver.netgear.com%2Fpdf%2Fwgr615v_manual.pdf&answer_id=70798949]("http://kbserver.netgear.com/pdf/wgr615v_manual.pdf#xml=http://kbserver.netgear.com/inquira/default.asp?ui_mode=answer&prior_transaction_id=756358&action_code=6&highlight_info=352321914,12,23&turl=http%3A%2F%2Fkbserver.netgear.com%2Fpdf%2Fwgr615v_manual.pdf&answer_id=70798949")

---

### Post by shanep-server on 2008-11-07
i don't know exactly what u mean by rule.

 
  	# 	Service Name 	Start Port 	End Port 	Server IP 
  	 1	  HTTP	             80           80	       192.168.1.2

it looks like this though. is that what u were asking?

---

### Post by pgorillaman on 2008-11-07
Looks like it is working. According to your router manual, it will filter out localhost addresses from using the external IP (resolved via your dyndns host name). But since I'm not behind your router, I was able to see your default page at [http://shanep-server.ath.cx/](http://shanep-server.ath.cx/)

---

### Post by shanep-server on 2008-11-07
so you can see my index.html file? i can't see it becuz i'm on my network trying to access it? Does that mean that we went threw all of this for nothing LMFAO. If thats the case I still say you rock cuz i really wanted to figure this out. Thank you for your time I really appreciate it.

---

### Post by pgorillaman on 2008-11-07
Yup. Pretty lame of your router but here is an img link so that you can see what I see.
[http://tinypic.com/view.php?pic=2cj4gj&s=4]("http://tinypic.com/view.php?pic=2cj4gj&s=4")
Make sure you mark this thread as solved.

---

### Post by shanep-server on 2008-11-07
i'm a newb i don't know how to mark this thread as solved.

---

### Post by pgorillaman on 2008-11-07
Here is a better guide:
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6")

---

### Post by shanep-server on 2008-11-07
u really are awesome man... :D

---

### Post by MJN on 2008-11-07
As you've determined, your router doesn't support so-called 'NAT loopback'. As far as I can tell there is no firmware, official or not, that provides this functionality hence it is likely to be an architectural cause.
 
There are a couple of workarounds available to you though (aside from buying a new router!):
 
- Configuring a local DNS to host a 'local view' of your domain i.e. its records will all point to LAN addresses
- Manually editing each client's hosts file to include a mapping for your URL to the private LAN address of the server
 
If you've only got a handful of machines I'd be inclined to go for the latter as it is much simpler.
 
Mathew

---

