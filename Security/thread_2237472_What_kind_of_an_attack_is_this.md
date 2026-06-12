---
title: "What kind of an attack is this ?"
date: 2014-08-02
forum: Security
---

### Post by linuxyogi on 2014-08-02
My ISP provides Internet connection using Ethernet. Its simply a LAN connection so using a router is not mandatory from connectivity point of view.

I took this connection 3 months back. Before this I was using DSL which as you know requires router.

While using this broadband connection just out out of curiosity I every now and then typed dmesg |tail and saw ufw blocking a lot of UDP stuff coming from different sources.

Day before yesterday I installed [this router]("http://www.dlink.com/us/en/home-solutions/connect_us/routers/dir-600l-wireless-n-150-home-cloud-router"). Now when I do dmesg|tail I still see incoming UDP packets although much less in number. 

```
[ 1222.623582] [UFW BLOCK] IN=enp0s7 OUT= MAC=40:61:86:tu:3c:a2:d0:c5:54:de:56:16:08:00 SRC=95.211.213.46 DST=192.168.0.100 LEN=131 TOS=0x00 PREC=0x00 TTL=116 ID=29763 PROTO=UDP SPT=56828 DPT=7881 LEN=111 

```

Please explain ^^ that. The above output is from my Manjaro installation. I am dual booting Lubuntu and Manjaro. It doesn't matter because I am seeing the same thing on both distros.

---

### Post by TheFu on 2014-08-02
Is the public IP yours or not? Appears to be in Amsterdam at a cloud server provider.

Usually UDP packets getting through a firewall should be 
* DNS
* VPN
* SIP
* NTP

How is it getting through the dlink?  Did your system initiate the connection?

---

### Post by linuxyogi on 2014-08-02
> **TheFu said:**
> Is the public IP yours or not? Appears to be in Amsterdam at a cloud server provider.


Are you asking about 95.211.213.46 ? No its not my IP. 


> **TheFu said:**
> 

Usually UDP packets getting through a firewall should be 
* DNS
* VPN
* SIP
* NTP

How is it getting through the dlink?  Did your system initiate the connection?

I have set these 2 DNS addresses on my router 128.199.248.105, 106.186.17.181 [(OpenNIC)]("http://www.opennicproject.org/").

I have no idea if the connection was initiated from my system. 
[h=4][/h]

---

### Post by TheFu on 2014-08-02
Are there any outbound packets sent to 95.211.213.46?
After all, if you don't allow UDP inbound through the dlink (and most people shouldn't), then the firewall there should block all inbound traffic, unless it is a response from an outbound request from the system on your LAN.  Right?  Am I missing something?

I've seen ad tracking networks initiate outbound traffic (thank you javascript) to get the firewall open, but didn't know they could use UDP.  That would be my guess at this point, lacking any other proof.

I have heard of firewalls failing (allowing a few packets through) when really busy - but those were under heavy attack and for DoD contractors. Doubtful you are under that sort of attack.

---

### Post by linuxyogi on 2014-08-02
> **TheFu said:**
> Are there any outbound packets sent to 95.211.213.46?


Sorry never had to find out so I don't know the command. What will print that ? 

> **TheFu said:**
> 
After all, if you don't allow UDP inbound through the dlink (and most  people shouldn't), then the firewall there should block all inbound  traffic, unless it is a response from an outbound request from the  system on your LAN.  Right?  Am I missing something?

However, I have heard of firewalls failing (allowing a few packets  through) when really busy - but those were under heavy attack and for  DoD contractors.

I used DSL for like 8 years and I noticed this same thing. I don't know if routers can be trusted from a security point of view. I don't understand why people keep sying dont connect to the Internet directly. IMHO iptables is far superior to a router firewall.

---

### Post by TheFu on 2014-08-02
Linux-based routers run iptables ... uh ... just like your Linux desktop. Same code.  ufw is just a CLI interface into iptables.
BSD-based routers run pf ... and are generally considered better since BSD gets slow, but doesn't crash under load.

We all need a router to protect our networks. Security is layered, right?  Belts AND suspenders.

The same firewall that logs the blocked inbound connections can log outbound requests. There is a setting to make that happen - you can do it either on the firewall OR on your system.  I'd google "log all traffic ufw" - if that doesn't return anything - s/ufw/iptables/ and google again.

---

### Post by linuxyogi on 2014-08-02
> **TheFu said:**
> Linux-based routers run iptables ... uh ... just like your Linux desktop. Same code.  ufw is just a CLI interface into iptables.
BSD-based routers run pf ... and are generally considered better since BSD gets slow, but doesn't crash under load.

We all need a router to protect our networks. Security is layered, right?  Belts AND suspenders.

The same firewall that logs the blocked inbound connections can log outbound requests. There is a setting to make that happen - you can do it either on the firewall OR on your system.  I'd google "log all traffic ufw" - if that doesn't return anything - s/ufw/iptables/ and google again.

Found the command in the ufw man page.

```
$ sudo ufw logging HIGH
```


```
$ sudo ufw status verbose
Status: active
Logging: on (high) << this was low before 


```


Yes, the routers runs Linux too but we hardly update the firmware. On the the other hand we get kernel updates regularly. May be this a stupid question but don't you think it matters ?  Totally agreed about the 2 layered security approach.

Since everything is getting logged now I will keep checking and write back.

---

### Post by SeijiSensei on 2014-08-02
If you ran something like dd-wrt or tomato on your router you could update your firmware as needed.

---

### Post by linuxyogi on 2014-08-02
> **SeijiSensei said:**
> If you ran something like dd-wrt or tomato on your router you could update your firmware as needed.

It seems like dd-wrt has no support for my router Dlink Dir 600 L ](*,)


[IMG]http://ibin.co/1VRljlh00E3n[/IMG]

---

### Post by linuxyogi on 2014-08-03
@TheFU

[FONT=arial]Changing ufw's logging mode to high didn't work. [COLOR=#000000]The idea was to find if there was any outbound request[FONT=arial][COLOR=#000000] 

sent[/COLOR][/FONT]  to [/COLOR][/FONT]95.211.213.46 from my LAN but ufw is set to "default deny incoming". 
[FONT=arial][/FONT][FONT=arial]Therefore doesn't log outbound connections on my configuration.[/FONT] 

[FONT=arial]I guess each of us is facing the same situation. I mean few packets will penetrate the router.

I have never used pfsense I will have to try someday to see how it performs.

If you read my first post I was not really hoping to stop these packets from coming 

I wanted to know when I see ufw blocking a UDP packet what does that mean. 

What kind of an attack is that ?

I guess its not that easy. May one needs to be a hacker to know that.
[/FONT]

---

### Post by TheFu on 2014-08-03
The short answer is that it probably is NOT an attack at all.

---

### Post by bashiergui on 2014-08-03
> I wanted to know when I see ufw blocking a UDP packet what does that mean. 


What kind of an attack is that ?


I guess its not that easy. May one needs to be a hacker to know that.You just need to put the packet into context. You're trying to extract a novel from a sentence. If you really want to figure out what it is, then capture packets and get the whole picture. What other packets come from that IP? What were you doing at the time? 

A blocked packet doesn't necessarily indicate an attack. It blocks lost and misdirected packets. And there are plenty of routine scanning of the internet by malicious and benign people constantly. If you have gotten a new DHCP IP address recently, the packet could be coming from someone trying to communicate with whomever had your IP before you. The possibilities are endless, hence you have to get more data to come to any meaningful conclusion.

---

### Post by linuxyogi on 2014-08-03
> **bashiergui said:**
>  What other packets come from that IP? What were you doing at the time? 


I saw multiple entries of only UDP coming from that IP. I was browsing the web with Firefox. 

> **bashiergui said:**
> 
A blocked packet doesn't necessarily indicate an attack. It blocks lost  and misdirected packets. And there are plenty of** routine scanning** of the  internet by malicious and benign people constantly. 

When I was not using a router I had configured psad but surprisingly didn't receive a single Email about my IP getting scanned.

> **bashiergui said:**
>  If you have gotten a  new DHCP IP address recently, the packet could be coming from someone  trying to **communicate** with whomever had your IP before you. The  possibilities are endless, hence you have to get more data to come to  any meaningful conclusion.

You used the word communicate. This is exactly what I want to know, that is methods do they use ? So that I can counter that. 

Problem is I have never seen packets coming from the same IP once my global IP changes it becomes very difficult.
If I learn how to analyze the network I will have to it within that session.

---

### Post by SeijiSensei on 2014-08-04
> **linuxyogi said:**
> It seems like dd-wrt has no support for my router Dlink Dir 600 L 

Or, more accurately, D-Link chooses not to design its routers to work with open firmware.

---

### Post by linuxyogi on 2014-08-04
> **SeijiSensei said:**
> Or, more accurately, D-Link chooses not to design its routers to work with open firmware.

Which brand is open firmware friendly ? I will choose that next time.

---

### Post by vasa1 on 2014-08-04
From the little I read, Netgear has a good rep in this regard. Nice to see what others will suggest.

---

### Post by linuxyogi on 2014-08-04
> **vasa1 said:**
> From the little I read, Netgear has a good rep in this regard. Nice to see what others will suggest.

I was planning to buy Netgear but I guess its unlikely that people will suggest Netgear. See [this post]("http://ubuntuforums.org/showthread.php?t=2233892&p=13070791#post13070791") from one of my other threads.

---

### Post by vasa1 on 2014-08-04
> **linuxyogi said:**
> I was planning to buy Netgear but I guess its unlikely that people will suggest Netgear. See [this post]("http://ubuntuforums.org/showthread.php?t=2233892&p=13070791#post13070791") from one of my other threads.Came across this: [Ask HN: Best current model routers for OpenWRT, DD-WRT, Tomato, etc.?]("https://news.ycombinator.com/item?id=6828699"). It's about a year old but may give you some pointers.

---

### Post by linuxyogi on 2014-08-04
> **vasa1 said:**
> Came across this: [Ask HN: Best current model routers for OpenWRT, DD-WRT, Tomato, etc.?]("https://news.ycombinator.com/item?id=6828699"). It's about a year old but may give you some pointers.

So its [COLOR=#000000]Ubiquiti and [COLOR=#000000]the Linksys WRT54Gx series. [/COLOR][/COLOR][COLOR=#000000]I don't think Ubiquiti routers are available in India. I 

searched on both Flipkart and Ebay.   [/COLOR]

---

### Post by SeijiSensei on 2014-08-04
See my post here with a link to an article on routers available in India: [http://ubuntuforums.org/showthread.php?t=2219419&p=13000869#post13000869](http://ubuntuforums.org/showthread.php?t=2219419&p=13000869#post13000869).

---

