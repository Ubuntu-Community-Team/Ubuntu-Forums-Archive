---
title: "viewing browsing history remotely"
date: 2010-01-09
forum: Security
---

### Post by Fika on 2010-01-09
What are all the ways you could think of that someone could view your browsing history, upstream from your machine? They don't have physical access, there's nothing on the computer itself  and the person trying to hack has skill so I'm thinking like monitoring a proxy somehow, using the ip address somehow, compromising the modem in some way, possibly having access to google account etc. 

I am new to ubuntu and have really dug it so far but I want to figure how this is/was being done. Any ideas?

---

### Post by iponeverything on 2010-01-09
> **Fika said:**
> What are all the ways you could think of that someone could view your browsing history, upstream from your machine? They don't have physical access, there's nothing on the computer itself  and the person trying to hack has skill so I'm thinking like monitoring a proxy somehow, using the ip address somehow, compromising the modem in some way, possibly having access to google account etc. 

I am new to ubuntu and have really dug it so far but I want to figure how this is/was being done. Any ideas?

What makes you think it is happening to you?

An electronic wire-tap order.

---

### Post by running_rabbit07 on 2010-01-09
Just a simple scan though the capabilities of your router will show that it is easy to set up web logging. The router/switch in the building or manhole up the street from you may have even more capabilities. It is doubtful that your ISP has set up any logging though.

---

### Post by Fika on 2010-01-09
I don't have a router just a cable modem connection with ufw firewall enabled. 

Let's just say someone has proven in the past they can see my browsing history and emails. Since moving to ubuntu I think the computer is more secure but I'm just checking to see what y'all think.

---

### Post by Flyers2391 on 2010-01-09
> **Fika said:**
> I don't have a router just a cable modem connection with ufw firewall enabled. 

Let's just say someone has proven in the past they can see my browsing history and emails. Since moving to ubuntu I think the computer is more secure but I'm just checking to see what y'all think.

Do they have access to anything on your network?  They could just be sniffing traffic with wireshark

---

### Post by Fika on 2010-01-09
No network access that I know of.

---

### Post by Fika on 2010-01-09
How much info could wireshark give? I don't think enough so they would know everything I'm doing online.

---

### Post by adam814 on 2010-01-09
If you use wifi and they're in range they could do packet capture, even in monitor mode (esp. if you use unencrypted or WEP).  If they're actually on your network they could ARP cache poison you and route your traffic through their machine to snoop.  On Windows there are enough exploits out there someone could compromise it.

Even upstream of your network your ISP and any routers between you and your destination have at least logging capabilities whether they use them or not.

The main point is anything that isn't encrypted all the way between you and your destination can probably be read somewhere and even then the server you've connected to may be, just not the content.

---

### Post by running_rabbit07 on 2010-01-09
> **Fika said:**
> How much info could wireshark give? I don't think enough so they would know everything I'm doing online.
Wireshark shows every packet moving on the network. It shows send and receive protocols, MAC addresses as well as IP addresses. If you enter wireshark into the search field in Synaptic, you can click on it and see what the description says about it. I use it for my college classes and though I don't know the programs full capabilities, I know that it is a well written, awesome program.

---

### Post by Fika on 2010-01-09
> **adam814 said:**
> If you use wifi and they're in range they could do packet capture, even in monitor mode (esp. if you use unencrypted or WEP).  If they're actually on your network they could ARP cache poison you and route your traffic through their machine to snoop.  On Windows there are enough exploits out there someone could compromise it.

Even upstream of your network your ISP and any routers between you and your destination have at least logging capabilities whether they use them or not.

The main point is anything that isn't encrypted all the way between you and your destination can probably be read somewhere and even then the server you've connected to may be, just not the content.

  How about if I'm on a ethernet connection, no router, and they are in another state. Do I need to set up some kind of secure encryption for my pc? I though the encryption settings in firefox were sufficient but that probably just shows my naivety about internet security.

---

### Post by FuturePilot on 2010-01-09
People seem to be missing the fact that there is **no router**. The OP is connected directly to the Internet. Therefore it isn't very likely that someone is sniffing your traffic. Do you have VNC or any other type of remote access enabled?

---

### Post by adam814 on 2010-01-09
That sounds highly unlikely without some sort of malware/rootkit.  If it still seems to be happening you could try using tor and privoxy, but after hearing about snooping around exit nodes I don't know how much privacy that actually adds.

---

### Post by running_rabbit07 on 2010-01-09
Every internetwork goes to a router.

---

### Post by FuturePilot on 2010-01-09
> **running_rabbit07 said:**
> Every internetwork goes to a router.

Yes, but there is no local/home router involved.

---

### Post by Fika on 2010-01-09
> **adam814 said:**
> That sounds highly unlikely without some sort of malware/rootkit.  If it still seems to be happening you could try using tor and privoxy, but after hearing about snooping around exit nodes I don't know how much privacy that actually adds.

 I have thought about using tor with ubuntu but didn't want to go through the whole setup process.   Remote desktop is disabled. Not sure about VNC but I didn't set up any vnc myself.

---

### Post by running_rabbit07 on 2010-01-09
With the right stuff, one could sniff the upstream packets, but it is out of our hands to even worry about. PBS recently did a special on how all traffic goes through the NSA's data centers and anything with certain keywords is stored for future reference.

---

### Post by BkkBonanza on 2010-01-09
As long as someone hasn't got control of your machine and is monitoring right on the machine then you can use an encrypted tunnel out to a server somewhere remote. You can very easily proxy through that to the net. You can rent a ssh account on a server for about $3-4/mo. and run your traffic through that. It is very unlikely that anyone, other than the government, would be able to tap into that server. Some companies offering them also do not log traffic so that it cannot be supeoned - well, so they claim anyway.

This is as easy as a ssh command and setting your browser to use a SOCKS5 proxy.

The command is,

ssh username@server_address -D 8080 -N

then set your browser to use localhost:8080 as SOCKS proxy.

I use this very often here because I am on a very insecure apartment building network. Because it's SOCKS proxy it works for any program that can talk to SOCKS, which includes most email clients, Skype, torrents, most anything nowadays. I'd love to hear about someone tracing your traffic after you're running a secure tunnel like this.

It is very good for wifi traffic at web cafes and schools when you don't trust the network.

There is also a gui program called gSTM in Synaptics that lets you set this up point and click style.

The only thing you need is a ssh account out there on the internet, or several if you want to bounce around. I also have a free one at [nic-nac-project.de]("http://nic-nac-project.de") which I use from time to time. You send him a postcard and he sets up an account for you to ssh to. Not so fast but it works in a pinch. Anyway, there are lots of places to get a ssh account and most VPS accounts work great too, but cost more.

Note that your server account can be in a foreign country. That nic-nac one is in Germany. I have some in other countries too.

Last comment, some of these places run ssh on port 443 as well, so it looks pretty much like https traffic and most firewalls will let that thru.

---

### Post by Fika on 2010-01-09
should I use a free shell account like [http://freeshell.org/](http://freeshell.org/) or pay for one

---

### Post by BkkBonanza on 2010-01-09
Whatever suits your needs. Some of the free ones will restrict usage and may not allow proxying. If used lightly they may not mind but if you make heavy use like torrents or lots of downloads they would likely block it as it consumes their bandwidth at double the rate (in + out) you use.

I have used my nicnac account for browsing and not had problems, but I stay away from heavy downloading. If I need that I use my paid vps account. I have it for my web server anyway so it's no added cost for me to use it for this.

Sometimes the free ones aren't very stable or robust. You probably need to explore it a little to know for sure.

*[COLOR="Gray"]I looked at the freeshell.org info and they don't seem to mind SOCKS5 proxying as they describe how to use it in their docs. So try it out. I wouldn't push it too hard as they do have a policy that if you adversely affect other users they may block you. Otherwise, it sounds useful.[/COLOR]*

Edit: I joined freeshell to test it. I can ssh in but it will not do socks proxying. I don't know if that's something you have to donate to get a higher ability or if it's just not possible at all. Looks like you can't do much there unless you donate. It's not much but I don't need to as I already have other accounts. Oh well.

A couple paid services I know of but haven't used,
[http://www.santrex.net/proxyhosting.php](http://www.santrex.net/proxyhosting.php)
[http://www.sh3lls.net/proxy/index.html](http://www.sh3lls.net/proxy/index.html)
[http://www.quadspeedi.net/?page=services](http://www.quadspeedi.net/?page=services)

---

### Post by BkkBonanza on 2010-01-10
I just thought I'd mention something that occurred to me today.

You could easily use **Amazon EC2** for this type of ssh access. You probably don't need many hours each day so it would end up being pretty cheap. EC2 works on a pay as you go hourly basis and they have a cool thing called "spot prices".

The normal price is 8.5 cents/hour so for when you need a secure tunnel it may not work out too much per month. Of course, it's way overkill - you have a full virtual machine at your disposal and your'e only doing a bit of proxying.

With their "spot price" scheme you can bid on server time and pick up unused time at a lower price. Using the price history chart over the last few weeks spot prices have been running around 3 cents/hour. So say 2 hours/day/month would end up being about $1.80 total. 

The main thing is you don't have to commit to monthly or yearly terms. Pay as you go.

---

### Post by llawwehttam on 2010-01-10
If you really want to be secure then have a look at TOR.

---

### Post by BkkBonanza on 2010-01-10
Tor has known vulnerabilities at entry/exit nodes as far as I heard. I think it may be ok for anonymity but I'm unsure about security.

I just tried out a spot price EC2 instance for this and it works great. Easy to start from the EC2 Management console. I'm editing this page thru ssh right now. Costs me 3 cents.

I'm also going to try out Bluelock (vCloud) - another known cloud service. Free beta...

---

