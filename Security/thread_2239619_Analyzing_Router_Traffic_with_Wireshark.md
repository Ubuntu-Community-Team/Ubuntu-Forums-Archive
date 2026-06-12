---
title: "Analyzing Router Traffic with Wireshark"
date: 2014-08-14
forum: Security
---

### Post by linuxyogi on 2014-08-14
Hi,

I am using [this router]("http://www.dlink.co.in/products/?pid=544"). This router has a feature called MyDlink which enables users to monitor and manage the network remotely. This service is not active on my router atm. 

I found [this post]("http://forums.dlink.com/index.php?topic=42165.msg148503#msg148503") today.

> Mydlink works because the mydlink capable devices constantly broadcast  to mydlink.com([COLOR=#0000cd]**regardless of if your register to mydlink or not**[/COLOR]), once  you register for a account it will match the device to your account by  the serial number

So I installed Wireshark to see if there is any outbound connection to mydlink.com but I didn't find any.

I haven't used Wireshark before so I am not sure if I am doing things correctly. I was capturing traffic on eth0.

My question is if these Dlink cloud routers really broadcast user activity to a particular server it must be doing it using its WAN interface but I am capturing eth0 which is on the LAN side. 

Is this correct ? If yes then how can I capture my router's WAN interface ? 

Like with nmap its really easy, coz users can use IP addresses both local and global.

But Wireshark captures by "interface".

---

### Post by TheFu on 2014-08-14
If the traffic doesn't go through your system running wireshark, then you will never see it.  You'll have to solve that issue first.

---

### Post by linuxyogi on 2014-08-14
> **TheFu said:**
> If the traffic doesn't go through your system running wireshark, then you will never see it.  You'll have to solve that issue first.

Yes, I guess to monitor the entire network one must run Wireshark on the router itself and thats not possible on the type of router I am using.

I don't know how to solve this. Lets see if if someone offers an idea.

BTW I visited the dd-wrt website today and found that they have released a firmware for my router.

I was all set to install it but after reading the installation wiki I changed my mind.

Its full of warnings that if something goes wrong the router may get "bricked".

I am 100% sure about my model and hardware version but still if the router gets bricked I don't know how to restore Dlink's firmware coz 

usually its pretty easy using the web interface which will be gone if the router is bricked.

---

### Post by uRock on 2014-08-14
If you could get a system with two NICs in between the router and modem, then you could monitor with Wireshark or TCPDump.

You can a cheap USB NIC from [Monoprice]("http://www.monoprice.com/Category?c_id=103&cp_id=10311&cs_id=1031102") if you want a second NIC for doing this.

---

### Post by linuxyogi on 2014-08-14
> **uRock said:**
> If you could get a system with two NICs in between the router and modem, then you could monitor with Wireshark or TCPDump.

You can a cheap USB NIC from [Monoprice]("http://www.monoprice.com/Category?c_id=103&cp_id=10311&cs_id=1031102") if you want a second NIC for doing this.

I am the the only user of this Internet connection so I don't want to monitor my own activity.

What I want is a way to know if my Dlink router is sending data about my network activity to any location like the user on the Dlink forum has suggested.

---

### Post by uRock on 2014-08-15
> **linuxyogi said:**
> I am the the only user of this Internet connection so I don't want to monitor my own activity.

What I want is a way to know if my Dlink router is sending data about my network activity to any location like the user on the Dlink forum has suggested.

You can set rules for Wireshark, TCPDump, or Snort to capture packets within certain IP ranges. Using the internal host, make adjustments to the settings on the DLink. After you make the changes to the DLink, watch the Wireshark/IDS host to see if it logs anything going to one of DLinks public IP ranges.

---

### Post by TheFu on 2014-08-15
There are a few ways to get access to the WAN traffic.
* place a computer between the WAN and internet running wireshark
* use a port replicator device like this: [http://acehackware.com/collections/hackware/products/throwing-star-lan-tap-fully-assembled](http://acehackware.com/collections/hackware/products/throwing-star-lan-tap-fully-assembled)

As to loading dd-wrt - we all had that same apprehension the first time.  The only way to bypass that is to do it. The first time, I thought I'd bricked my router too - getting tftp to work isn't hard.

---

### Post by linuxyogi on 2014-08-15
> **TheFu said:**
>  As to loading dd-wrt - we all had that same apprehension the first time.  The only way to bypass that is to do it. The first time, I thought I'd bricked my router too - getting tftp to work isn't hard.

[Flashing with Web GUI]("http://www.dd-wrt.com/wiki/index.php/Installation#Method_1:_Flashing_with_Web_GUI")

> 
[LIST=1]
[*] **Use [Hard reset or 30/30/30]("http://www.dd-wrt.com/wiki/index.php/Hard_reset_or_30/30/30").** 
[*]While not as preferable (this may cause problems down the line) you can reset to [Factory Defaults]("http://www.dd-wrt.com/wiki/index.php/Factory_Defaults") instead. 
[/LIST]


Which one did you do ? 30/30/30 or reset to factory defaults ?

If reseting to factory default increases the chance of the router getting bricked I will have to go for the [30/30/30]("http://www.dd-wrt.com/wiki/index.php/Hard_reset_or_30/30/30") but it I wont be able to do this alone.

> 
[LIST]
[*] With the unit powered on, press and hold the reset button on back of unit for 30 seconds 
[*][B] Without releasing the reset button, unplug the unit and hold reset for another 30 seconds 
[/B] 
[*]** Plug the unit back in STILL holding the reset button a final  30 seconds  (please note that this step can put Asus devices into  recovery mode...see note below!) ** 
[/LIST]


I will be needing somebody to assist me coz both my hand will be engaged.

---

### Post by linuxyogi on 2014-08-15
I did a factory reset. This router's default firmware is written is such a way that after every factory reset when I access 

the admin page (192.168.0.1) the first page is of network configuration. There seems to be no way to avoid this. So

the default network configuration (dhcp) gets written again.

Then when I tried to upload dd-wrt's firmware I got an error.

[IMG]http://ibin.co/w800/1WvtLrxRhvRV[/IMG]




[IMG]http://ibin.co/w800/1Wvu2xINQ1jw[/IMG]

---

