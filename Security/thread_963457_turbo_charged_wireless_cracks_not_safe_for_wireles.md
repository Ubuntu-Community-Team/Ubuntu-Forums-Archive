---
title: "turbo charged wireless cracks not safe for wireless anymore?"
date: 2008-10-30
forum: Security
---

### Post by sdowney717 on 2008-10-30
[http://www.theregister.co.uk/2008/10/10/graphics_card_wireless_hacking/](http://www.theregister.co.uk/2008/10/10/graphics_card_wireless_hacking/)

I use wep which is poor. But now even wpa is no good with the tools available. 

So what is the risk and can a monitor somehow watch your network to see when a nonauthorized computer attaches to your network?
How about using mac addresses to allow only preapproved connections?

why not write a tool for this?

---

### Post by kosmiciatakuja on 2008-10-30
This article is very interesting and I have heard about this earlier too. 
I'm far from being an expert, so I'll just try to answer some of your questions the best I can:

[LIST=1]
[*]Breaking your WEP or WPA security means that A. somebody can connect to your network and watch the traffic you are generating. If you send clear text passwords, they will be intercepted. But if you, for example, log in to your bank account using https protocol then it is safe. And I think 100% of banks use https so no worries there. And B. that person would probably be able to connect to your wireless router to use your internet connection. If this person is malicious, your internet connection could be used for some things you would probably not like being traced back to you (such as break-in attempts or spam sending)
[*]Now, breaking WPA and WPA2 requires somebody to have some specialized Russian software that is not available to anybody and definitely quite expensive. On the other hand WEP can be cracked pretty quickly using available software by you neighbour's kids. So by all means change that WEP to WPA ASAP!!! There's no excuse!
[*]Since there is no better wireless security than WPA2 at this moment, you can't just upgrade, sorry. BUT you can pay attention to which sites offer you https security and use those for sharing sensitive information. Use SSH for remote logins. Don't use insecure (=free usually) email (POP3 and SMTP) but opt for SSL encrypted email service. Also, check GPG for email and file encryption. And so on - many services can be encrypted and secured. SSH/SSL is not that easy to crack at this point (I don't know if anybody even managed that yet). And there's the VPN idea, but I haven't researched this yet.
[*]MAC address restriction is the easiest one to break. It's kids play to change your mac address and you can do it with one simple command on the console. You would not secure anything. And besides - the possible intruder would be able to listen to your traffic anyway (1.A.), you would just *try* to prevent 1.B. 
[*]However, if somebody is using your router (see 1.B. above) then you can probably spot this in your router configuration (usually available under something like 192.168.1.1 but this depends on your network configuration) but how to do this depends on the particular router, check your manual.
[/LIST]

---

### Post by sdowney717 on 2008-10-30
there should be a way to monitor the router connections and say flag it when another computer joins the network. Right now it is silent.
My dhcp clients table only shows my 4 devices connected, but you would never know.

---

### Post by bodhi.zazen on 2008-10-30
Moved to security discussions.

As always , security is a cat and mouse game.

The problem with wireless will always be that somebody does not need to "connect" to your network to capture packets (packets are transmitted like radio signals, so they can be captured, period, end of story). If packets can be captured they can be decrypted.

This is why the truly paranoid do not use wireless. If you use wireless please use the strongest encryption possible.

---

### Post by Sarmacid on 2008-10-30
Some routers have the option to report many things to syslog, so you configure the router to do that and set up a script to alert you.

---

### Post by Old_Grey_Wolf on 2008-11-06
According to this article in InfoWorld. [http://www.infoworld.com/article/08/11/06/Once_thought_safe_WPA_WiFi_encryption_is_cracked_1.html](http://www.infoworld.com/article/08/11/06/Once_thought_safe_WPA_WiFi_encryption_is_cracked_1.html)

---

### Post by hyper_ch on 2008-11-07
still, wpa2 is considered to be safe (from that article):
> 
A new wireless standard known as WPA2 is considered safe from the attack developed by Tews and Beck, but many WPA2 routers also support WPA. 


---

