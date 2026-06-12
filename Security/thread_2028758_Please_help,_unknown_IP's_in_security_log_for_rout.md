---
title: "Please help, unknown IP's in security log for router."
date: 2012-07-18
forum: Security
---

### Post by Chronic Roots on 2012-07-18
I have quite a few ip's and im not exactly sure what to make of it.
none of them are computers in this house, although for some reason my 
public ip shows up a lot from diff pc's in the house im assuming? that last
digit varies from 1-7. Anyway the ones im worried about are the strange
ones that I do not know. I have a good alphanumerical password for
the router, and the same measures were taken for the admin password
on the router. can anyone help me? I am sort of worried. Thanks for taking
the time to read.

---

### Post by The Linuxist on 2012-07-18
Have you got WPS turned on? That makes the router really easily hackable.

---

### Post by pe7er on 2012-07-18
Do you have a mobile smart phone?

There's a nice app called **Overlook Fing** that you can use to analyze all devices that are connected to your modem/router:
[http://overlooksoft.com/fing](http://overlooksoft.com/fing)

Android: [https://play.google.com/store/apps/details?id=com.overlook.android.fing&hl=en](https://play.google.com/store/apps/details?id=com.overlook.android.fing&hl=en)
iPhone: [http://itunes.apple.com/us/app/fing-network-scanner/id430921107?mt=8](http://itunes.apple.com/us/app/fing-network-scanner/id430921107?mt=8)

Hopefully you'll discover that you only forgot that you had connected your own Raspberry Pi, XBMC Media Centre, your refrigerator, your friends laptops, etc to your network :P

---

### Post by Chronic Roots on 2012-07-18
wpa2 is the security protocol i have activated at the moment.

---

### Post by Chronic Roots on 2012-07-18
actually  yes i do, droid x, ill give it a go. thanks.

---

### Post by Chronic Roots on 2012-07-18
> **pe7er said:**
> Do you have a mobile smart phone?

There's a nice app called **Overlook Fing** that you can use to analyze all devices that are connected to your modem/router:
[http://overlooksoft.com/fing](http://overlooksoft.com/fing)

Android: [https://play.google.com/store/apps/details?id=com.overlook.android.fing&hl=en](https://play.google.com/store/apps/details?id=com.overlook.android.fing&hl=en)
iPhone: [http://itunes.apple.com/us/app/fing-network-scanner/id430921107?mt=8](http://itunes.apple.com/us/app/fing-network-scanner/id430921107?mt=8)

Hopefully you'll discover that you only forgot that you had connected your own Raspberry Pi, XBMC Media Centre, your refrigerator, your friends laptops, etc to your network :P


Im not sure what im supposed to do with it lol, but when i clicked my wireless network
on fing, it showed my phone and router....that was it.

---

### Post by pe7er on 2012-07-18
> **Chronic Roots said:**
> Im not sure what im supposed to do with it lol, but when i clicked my wireless network
on fing, it showed my phone and router....that was it.
It should show all devices that are currently connected to your router.
Doesn't it show your PC? It should also show the Ethernet devices that are connected with a cable to your router.

Something else: maybe you could do a WHOIS on the IP addresses that you found in your router.
Maybe they belong to your ISP that checked/updated your modem firmware?

---

### Post by Chronic Roots on 2012-07-18
> **pe7er said:**
> It should show all devices that are currently connected to your router.
Doesn't it show your PC? It should also show the Ethernet devices that are connected with a cable to your router.

Something else: maybe you could do a WHOIS on the IP addresses that you found in your router.
Maybe they belong to your ISP that checked/updated your modem firmware?

well....its my pc, the ipad, a laptop, the ps3 all connected, only showed my phone and the router though, was weird....but im used to seeing like 5 things connected. its weird ip's i dont like. i traceroute and reverse dns some, i think i even found one was an adress on my street hahahah. but some were like china dns's and colo-edu, other weird places. im learning more in depth about computers so this is helping me i guess =) im learning about wifi thats for sure lol, and i LOVE linux now. used to be so scared til i tried this. ubuntu is great. and thanks for help by the way.

---

### Post by Chronic Roots on 2012-07-18
> **The Linuxist said:**
> Have you got WPS turned on? That makes the router really easily hackable.

oh i just found the WPS part, and yes its enabled, i should disable?
Only use the wpa2 security?

---

### Post by Chronic Roots on 2012-07-18
figure you should see this, maybe you will understand what i mean better. 



```
Firewall log:
Tues Jul 17 17:03:03 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 17:15:02 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 17:26:55 2012  1 Blocked by DoS protection 192.168.2.3 
Tues Jul 17 17:27:01 2012  1 Blocked by DoS protection 192.168.2.3 
Tues Jul 17 17:28:37 2012  1 Blocked by DoS protection 192.168.2.3 
Tues Jul 17 17:43:42 2012  1 Blocked by DoS protection 192.168.2.4 
Tues Jul 17 17:49:42 2012  1 Blocked by DoS protection 192.168.2.3 
Tues Jul 17 17:59:17 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 18:12:07 2012  1 Blocked by DoS protection 192.168.2.4 
Tues Jul 17 18:13:51 2012  1 Blocked by DoS protection 192.168.2.3 
Tues Jul 17 18:15:01 2012  1 Blocked by DoS protection 192.168.2.4 
Tues Jul 17 18:15:26 2012  1 Blocked by DoS protection 192.168.2.4 
Tues Jul 17 18:26:59 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 18:35:39 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 18:35:41 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 18:48:06 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 19:12:06 2012  1 Blocked by DoS protection 192.168.2.4 
Tues Jul 17 19:12:07 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 19:15:24 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 19:23:39 2012  1 Blocked by DoS protection 192.168.2.2 
Tues Jul 17 20:36:56 2012  1 Blocked by DoS protection 192.168.2.5 
Tues Jul 17 20:40:25 2012  1 Blocked by DoS protection 192.168.2.5 
Tues Jul 17 21:47:36 2012  1 Blocked by DoS protection 60.8.224.242 
Wed Jul 18 00:29:54 2012  1 Blocked by DoS protection 190.22.121.167 
Wed Jul 18 00:52:52 2012  1 Blocked by DoS protection 60.8.224.242 
Wed Jul 18 01:00:52 2012  1 Blocked by DoS protection 222.87.49.251 
Wed Jul 18 06:51:28 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 07:11:15 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 07:24:08 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 07:27:25 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 07:27:27 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 07:35:15 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 08:01:15 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 08:25:15 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 08:25:17 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 09:19:43 2012  1 Blocked by DoS protection 192.168.2.5 
Wed Jul 18 09:27:13 2012  1 Blocked by DoS protection 192.168.2.5 
Wed Jul 18 09:40:50 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 09:43:47 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 10:07:03 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 10:15:42 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 10:32:24 2012  1 Blocked by DoS protection 129.82.138.32 
Wed Jul 18 10:40:08 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 10:51:18 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 11:19:01 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 11:19:28 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 11:28:54 2012  1 Blocked by DoS protection 193.152.184.172 
Wed Jul 18 11:55:53 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 12:03:41 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 12:15:44 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 12:19:04 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 12:31:53 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 12:39:41 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 12:39:44 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 12:52:06 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 13:07:54 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 13:39:44 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 13:55:04 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 13:55:28 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 14:03:16 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 14:03:18 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 14:03:41 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 14:31:54 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 14:39:16 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 14:43:26 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 14:55:03 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 15:07:04 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 15:07:53 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 15:15:19 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 15:16:06 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 15:16:09 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 15:31:29 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 16:28:08 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 16:47:44 2012  1 Blocked by DoS protection 192.168.2.4 
Wed Jul 18 16:48:50 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 16:51:57 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 16:51:57 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 16:55:16 2012  1 Blocked by DoS protection 192.168.2.4 
Wed Jul 18 17:01:16 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 17:11:28 2012  1 Blocked by DoS protection 192.168.2.4 
Wed Jul 18 17:11:46 2012  1 Blocked by DoS protection 192.168.2.4 
Wed Jul 18 17:14:18 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 17:19:17 2012  1 Blocked by DoS protection 192.168.2.4 
Wed Jul 18 17:30:17 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 17:33:43 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 17:41:01 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 17:42:33 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 17:45:43 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 17:49:28 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 17:56:23 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 18:01:54 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 18:03:43 2012  1 Blocked by DoS protection 193.77.83.39 
Wed Jul 18 18:06:26 2012  1 Blocked by DoS protection 192.168.2.3 
Wed Jul 18 18:12:00 2012  1 Blocked by DoS protection 192.168.2.6 
Wed Jul 18 18:13:54 2012  1 Blocked by DoS protection 192.168.2.2 
Wed Jul 18 18:22:59 2012  1 Blocked by DoS protection 192.168.2.6 
Wed Jul 18 18:23:01 2012  1 Blocked by DoS protection 192.168.2.6 
Wed Jul 18 18:23:13 2012  1 Blocked by DoS protection 192.168.2.6 
Wed Jul 18 18:23:15 2012  1 Blocked by DoS protection 192.168.2.6 
Wed Jul 18 18:23:25 2012  1 Blocked by DoS protection 192.168.2.6 
```

---

### Post by Ms. Daisy on 2012-07-19
The IP addresses in your log that begin with 192.168. are internal IPs.  I'm assuming the NAT IP address of the router is 192.168.2.1. Is that correct?

So for some reason your router thinks that the internal devices are DoS'ing it.  That log doesn't indicate whether the traffic was inbound or outbound.  The only way to see what the traffic is would be to use wireshark or something to get details on the packets.  If I had to guess, I would think the router is categorizing multicasting and network discovery hits as DoS maybe.

It's not terribly unusual to see an occasional block of a DoS from outside IPs, so I wouldn't worry much about those.  They're getting blocked so you're safe.

---

### Post by Ms. Daisy on 2012-07-22
It just occurred to me that your router might think the machines on your network are DoS'ing it if the machines are sending IPv6 network discovery packets to the router, but the router isn't IPv6-enabled.  

This would be easy enough to test if you can check your router specs to see if it's IPv6-capable.  Then see if your machines are sending IPv6 packets to the router.  If you want to do that, post back and I can give you instructions on how to disable IPv6 on the machines.

---

