---
title: "Receiving packets non-stop..."
date: 2005-05-01
forum: The Cafe
---

### Post by YourSurrogateGod on 2005-05-01
Ok, here's the problem. I got one of those connection properties windows opened up and I looked at the traffic that goes through. For some reason, I'm getting alot of packets comming in! Why is this happening?

I'm not downloading anything and the only thing that I have running right now that's  connected to the internet is firefox. What gives?

---

### Post by nad on 2005-05-01
Any other machines on your network? Your router (if you have one) is responsible for some of that traffic. Also realize that depending on the sites that you are connected to, all sorts of ad servers, flash objects etc are continuously generating considerable traffic.

Run ethereal (as root) to see in real time what is going on.

---

### Post by YourSurrogateGod on 2005-05-01
[QUOTE=nad]Any other machines on your network? Your router (if you have one) is responsible for some of that traffic. Also realize that depending on the sites that you are connected to, all sorts of ad servers, flash objects etc are continuously generating considerable traffic.[/quote]
Nope, just my HP. That and I don't go to sites that could possibly generate so much traffic.
[quote=nad]Run ethereal (as root) to see in real time what is going on.[/QUOTE]
I typed in ethereal and it said that the command isn't found...
```
# ethereal
bash: ethereal: command not found
```

---

### Post by YourSurrogateGod on 2005-05-01
The below is a screenshot of how bad it has gotten...

---

### Post by nad on 2005-05-01
Use synaptic to install the package. You may need to enable universe.

You will be surprised at how much unrequested traffic is generated if it is not a connection issue.

Edit: What period of time does that properties window cover?

---

### Post by HungSquirrel on 2005-05-01
[QUOTE=YourSurrogateGod]The below is a screenshot of how bad it has gotten...[/QUOTE]
 I was about to say that's not unusual to see, but I notice your sent traffic is very very low.  If you were doing normal browsing to get that much inbound traffic, your outbound traffic would be higher methinks.

---

### Post by YourSurrogateGod on 2005-05-01
[QUOTE=nad]Use synaptic to install the package.[/quote]
I couldn't find anything called ethereal in synaptic.
[quote=nad]You may need to enable universe.[/quote]
Universe?
[quote=nad]Edit: What period of time does that properties window cover?[/QUOTE]
About 2 hours or so.

---

### Post by YourSurrogateGod on 2005-05-01
[QUOTE=HungSquirrel]I was about to say that's not unusual to see, but I notice your sent traffic is very very low.  If you were doing normal browsing to get that much inbound traffic, your outbound traffic would be higher methinks.[/QUOTE]
Yeh, that's what has me scratching the back of my head :wink: . I don't understand why it's doing that.

---

### Post by HungSquirrel on 2005-05-01
[QUOTE=YourSurrogateGod]Universe?[/QUOTE]
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by YourSurrogateGod on 2005-05-01
Ok, I got ethereal working, but when I tried to start a new capture session I got the below error...
```
The capture session could not be initiated (socket: Operation not permitted).
Please check to make sure you have sufficient permissions, and that
you have the proper interface or pipe specified.
```

---

### Post by YourSurrogateGod on 2005-05-01
I think that the rate at which the packets are comming has decresed, nevertheless it's still quite high, imo.

---

### Post by YourSurrogateGod on 2005-05-01
Ok, finally got it to output something useful, it seems that ARP is sucking up a good chunk of the bandwith, as does IPX and UDP. There's also "Other" that is eating up around 20% of the bandwith. Can I shut-down some of the applications that are using these protocols or something?

---

### Post by WildTangent on 2005-05-01
maybe someones ping flooding you, like a DoS. unlikely, but possible

-Wild

---

### Post by YourSurrogateGod on 2005-05-01
[QUOTE=WildTangent]maybe someones ping flooding you, like a DoS. unlikely, but possible

-Wild[/QUOTE]
Doubt it, in XP, the rate of incoming packets is normal.

---

### Post by benplaut on 2005-05-01
if you were running windows, it would almost definately be a virus  :roll:

---

### Post by occy8 on 2005-05-01
you could install firestarter firewall. 
Then you can see where the packets are coming from and perhaps blocking the DNS.
I had something similar once. I couldn't browse or get email though but I still received constant packets.
It was a problem with my ISP. Virus from Windows affecting Ubuntu? I don't think so.

---

### Post by nad on 2005-05-01
Ethereal is showing you where the packets are coming from. Arp issues indicate connection problems. Try disabling ipv6 in firefox (about:config is the address to go to). IPX is the novell protocol. Combined with udp traffic it looks like your gateway is trying to resolve addresses any way it can. Take a look at its' configuration.

---

### Post by YourSurrogateGod on 2005-05-09
[QUOTE=nad]Ethereal is showing you where the packets are coming from. Arp issues indicate connection problems. Try disabling ipv6 in firefox (about:config is the address to go to). IPX is the novell protocol. Combined with udp traffic it looks like your gateway is trying to resolve addresses any way it can. Take a look at its' configuration.[/QUOTE]
I've tried disabling ipv6 in firefox, but that didn't do the trick :( . ARP is still out of control. I have the IP address of the source of the packets, how would I block it?

---

### Post by Sam on 2005-05-09
Maybe you can find something by doing
```
$ netstat -t -u
```

---

### Post by YourSurrogateGod on 2005-05-09
[QUOTE=Sam]Maybe you can find something by doing
```
$ netstat -t -u
```[/QUOTE]
I got this...
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        1      0 ool-43571ad7.dyn.:32999 64.21.33.9:www          CLOSE_WAIT
tcp        1      0 ool-43571ad7.dyn.:33000 64.21.33.9:www          CLOSE_WAIT
tcp        0      0 ool-43571ad7.dyn.:33001 82.211.81.130:www       TIME_WAIT
tcp        0      0 ool-43571ad7.dyn.:32815 caim-m05b.blue.aol:5190 ESTABLISHED
tcp        0      0 ool-43571ad7.dyn.:32993 64.233.161.104:www      ESTABLISHED
tcp        0      0 ool-43571ad7.dyn.:32994 64.233.161.107:www      ESTABLISHED
tcp        0      0 ool-43571ad7.dyn.:32813 64.12.26.144:5190       ESTABLISHED
tcp        0      0 ool-43571ad7.dyn.:32814 oam-d03a.blue.aol.:5190 ESTABLISHED
tcp        0      0 ool-43571ad7.dyn.:32812 cs32.msg.dcn.yahoo:5050 ESTABLISHED
tcp        0      0 localhost.localdoma:ipp localhost.localdo:32804 ESTABLISHED
tcp        0      0 localhost.localdo:32804 localhost.localdoma:ipp ESTABLISHED
```

---

### Post by YourSurrogateGod on 2005-05-09
Unfortunately according to ethereal, ARP is still hogging most of the bandwith...

---

### Post by nad on 2005-05-09
To block an ip address, simply redirect it to your own computer. In the /etc/hosts file, add a line: 127.0.0.1   ip_address

---

### Post by YourSurrogateGod on 2005-05-09
[QUOTE=nad]To block an ip address, simply redirect it to your own computer. In the /etc/hosts file, add a line: 127.0.0.1   ip_address[/QUOTE]
Silly question... but when you say 127.0.0.1, you mean that I should put the desired IP-address in place of the localhost ip?

---

### Post by nad on 2005-05-09
The first parameter is the target address (to look for the requested content), the second parameter is supposed to be a canonical address (after all this was originally designed to allow you to remember hostnames and not dotted quads) but any form of ip address will do, of the website you wish to redirect. Now, when a site requests content from for example ad .doubleclick. net, your browser will look for it at localhost and not finding the content, ignore it.

---

### Post by YourSurrogateGod on 2005-05-12
Crap, I don't think blocking will work. I've run ethereal again and I see a bunch of ip addresses inside, instead of just one. Can I turn ARP off somehow? What would be your suggestion?

---

### Post by nad on 2005-05-12
Address resolution is necessary to...resolve addresses.

If you do not have a hardware firewall (router, etc) I suggest you install a software firewall.

Look up the source of those addresses and maybe take up the issue with your isp.

---

### Post by YourSurrogateGod on 2005-05-13
I just sent an e-mail to my ISP...
[QUOTE=nad]If you do not have a hardware firewall (router, etc) I suggest you install a software firewall.[/QUOTE]
I thought that it came automatically with Ubuntu when I installed it? If not what would be your suggestion on a good one that I can get from synap?

---

### Post by nad on 2005-05-13
I am not familiar with software firewalls (I supply and install managed routers, hardware firewalls and censorwalls), however I have heard firestarter mentioned. Configuring any of these to your requirements is an art.

---

### Post by YourSurrogateGod on 2005-05-13
:sigh:

Isn't there any simple firewall that can be installed rather easily available for Ubuntu?

---

### Post by nad on 2005-05-13
Discussion of firestarter and shorewall.

[http://www.ubuntuforums.org/showthread.php?t=33706&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=33706&highlight=firestarter)

---

### Post by B.Ati on 2005-12-26
[QUOTE=YourSurrogateGod]:sigh:

Isn't there any simple firewall that can be installed rather easily available for Ubuntu?[/QUOTE]

Hi, I got the very same situ here in Hungary. Spent 3 weeks:(  studying the problem. Used Ethereal, it says that Im receiving 200 ARP packets/sec when there should be a silence. Firestarter is a GREAT and easy firewall. I looked up the iptables it makes. I culdnt do it better manually ( yet...).  
But here is my undertanding of the problem: 
Firewall will protect you fom nasty TCP Samba UDP etc. packets, but not from ARP flooding ( poisoning). Arp is below that level, i ARP is necessary even if you are directly connected to your ISP an no local net. It is necessary to establish a connection with DHCP but when the ISP got your ip address and your computer got the ISP addresses there should be an ARP silence until these entries expires in ARPtables.  Oh yes there is an ARP-table utility in your system so theoretically you shold be able to forbid a lot of answering to ARP-requests. 

But again, that is not the real solution. The situ is somewhat like if you are in a crowded marketplace and trying to make conversations with dozens of people but you have to use an interpreter (middle man, your ISP) and some nasty guys out there are constantly yelling to your interpreter questions like : 
- are you living at 25. Oxford street?  Tell it to 85. Harvard street 2. floor No.4....
- is your door open ? tell it to....
- Is your neighboors window open? tell it ...

The poor stupid interpreter ( your ISP) is transferring all this questions to you. You have to tell every time: 
- Im not going to reply, Im not going to.... 
So no harm done if you protect yourself, but the time-consuming nuissance is still there. If you install a hardware firewall (again linux for no money) you would see a nice clean connection. 

But the only real solution would if your middle man - the ISP would sort out these stupid ARPs. 

In my case ARPs are coming from a location owned by ISP an targeted to my eth0 broadcast. But they may be spoofed.  If they are ISP is not responsible but still the key is in his hands. Remember, all other packets can come and go from anywhere to anywhere but ARP is intended to be a Hardware to CLOSEST HARDWARE communication. Things just became more complicated with  Virtual Private Networking and other stuff which allow ARPs travelling all around. 

I wrote an 'angry' letter to my ISP yesterday - still waiting for reply. Being XMAS and NewYear coming dont expect it soon. Im goin to be real tough with them, but if it doesnt work, then installing a HW firewall will alleviate the problem. 

Oh, In my case definitly no virus. Run antivirus programs on both XPWindows ( the dirty one, and clean one on which eth card is always disabled). I have Ubuntu, and UHU-Linux (hungarian kind of distro) all of theese on separate discs placed in removable rack. 
The ARP-poisoning was there in all cases.  So it is up to ISP. Some piece of their hardware or software is confused by my card, or they are not doing their job with filtering. 

So much for now.

---

