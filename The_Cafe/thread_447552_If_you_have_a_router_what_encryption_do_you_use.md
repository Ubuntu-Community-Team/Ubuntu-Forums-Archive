---
title: "If you have a router: what encryption do you use?"
date: 2007-05-18
forum: The Cafe
---

### Post by PartisanEntity on 2007-05-18
Just interested to know what the most common method of encryption currently is. (I use wpa).

---

### Post by afljafa on 2007-05-18
Wep - I don`t care.

---

### Post by kragen on 2007-05-18
yay! the first (and hopefully only) WEP user to register on the poll :D

Its WEP because one of my housemates has a portable WEP only deivce. To be fair it hasn't proven a problem yet, I do make sure I keep tab's on who'se been given a lease in the router config, (not that it's a foolproof system or anything), but as I said, Its not bee a problem yet and the router has been there well over a year now.

---

### Post by mills on 2007-05-18
wep, but only because i cant be bothered to figure out wpa

---

### Post by OffHand on 2007-05-18
Disable ssid broadcasting, allow only registered mac addresses and restrict the amount of leases. Use a strong password for your router.

---

### Post by Iceni on 2007-05-18
None at all. Too much hassle as long as none of the neighbours are wireless users.

---

### Post by public_void on 2007-05-18
None, at the moment because my wireless is currently disabled, when running its WPA.

---

### Post by Sunflower1970 on 2007-05-18
> **OffHand said:**
> Disable ssid broadcasting, allow only registered mac addresses and restrict the amount of leases. Use a strong password for your router.

This is what I do  as well, and also use WEP. I  haven't sat  down to figure out WPA yet. My only concern is I don't think my iPAQ would be able to connect then....I also turn the router off when I'm not using it.

---

### Post by a12ctic on 2007-05-18
Mines open, my neighbors are stupid, and I don't really care if someone gets on my network.

---

### Post by misfitpierce on 2007-05-18
Indeed I really have no use for encryption since noone really lives around me. I use WEP anyways though...

---

### Post by Outrunner on 2007-05-18
None, but I only let my computer and my laptop connect(based on MAC adress)

---

### Post by Pobega on 2007-05-18
WEP with MAC filtering.

---

### Post by zanglang on 2007-05-18
Hmm, I thought it was interesting how so many ubuntunistas here use WEP...

Anyway, WPA2 here.

---

### Post by slimdog360 on 2007-05-18
My wireless isn't in use at the moment but I have a WEP key on there. I wanted to set up the whole WPA thing but it seemed to hard. I guess another day.

---

### Post by PartisanEntity on 2007-05-18
For those of you who mentioned that setting up WPA was too hard, do you mean it is too hard in Ubuntu or too hard to set up on your router?

---

### Post by Buffalo Soldier on 2007-05-18
WPA and MAC access list.

---

### Post by zeny on 2007-05-18
First you CANNOT disable SSID, you can only surpress it. Second regardless it doesn't matter, and neither does secure mac address on those routers. 

For me I use WPA-PSK with 802.1X

---

### Post by slimdog360 on 2007-05-18
> **PartisanEntity said:**
> For those of you who mentioned that setting up WPA was too hard, do you mean it is too hard in Ubuntu or too hard to set up on your router?

too hard in general. well okay, its probably not that hard but I had a go at it for half an hour or so and couldn't get it. Keep in mind that before trying to set it up Id never had any experience with wireless stuff before. I think it was the concept of how it works that got me, with WEP it was simple, put in an encryption key on the router and the same key for the device. 

I also have MAC filtering and set my power signal strength just high enough to get it to where I want it to get to, so I guess that the WPA encryption would be pointless (for me), but still interesting.

---

### Post by Rinzwind on 2007-05-18
WPA with a rendered password. 
My router also has mac-filtering and everyone not in that list should end up at my NAS and not my Ubuntu laptop and/or desktop,

---

### Post by Gargamella on 2007-05-18
> **Iceni said:**
> None at all. Too much hassle as long as none of the neighbours are wireless users.

I have only a neighbour in 5 km from my house on the hillside, why should i encrypt?
I think it doesn't use internet at all.

---

### Post by hoagie on 2007-05-18
None of my neighbours has a computer, they are all a bit too old except from my firend that's 100 m away from me... So I don't use encryption.

---

### Post by matthinckley on 2007-05-18
WPA encryption here.. was using WPA with PEAP when I was running a W2k3 server as a radius server but since I've wiped it and made it into a LAMP server I'm just using TKIP now.. 

hmm.. now I'm wondering if I can set up my feisty server as a radius server.. and if so can I get my ubuntu machines to authorize logins against it? that would be cool..

---

### Post by compmodder26 on 2007-05-18
Should be doable.  There is freeradius in the repositories.

---

### Post by Enverex on 2007-05-18
> **PartisanEntity said:**
> Just interested to know what the most common method of encryption currently is. (I use wpa).

You mean "Wireless" rather than router...

I use WPA now that it's simple to set up in Ubuntu (it's normally a nightmare to get working in Linux).

---

### Post by theicyj on 2007-05-18
I use WPA here.

---

### Post by matthinckley on 2007-05-18
> **compmodder26 said:**
> Should be doable.  There is freeradius in the repositories.
well now I know what I'll be playing with this weekend.. :)

---

### Post by starcraft.man on 2007-05-18
I use WPA, WEP doesn't work at all. It's been broken so many times its laughable, and turning off SSID and mac address filtering both have work arounds that average users can use, so that doesn't make WEP anymore secure. I also always keep a wired line into my Ubuntu machine, can't get my wired line hijacked :p.

Oh and btw, I was reading above about some people thinking wpa is complicated and hard... from my experience, WPA is even easier than wep. You make one big password and then input it on every computer _once_ and your set for life (or however long you pass between changing passes), you never have to enter it again and its secure. :)

---

### Post by [h2o] on 2007-05-18
WPA2 - mixed.
I had no problem whatsoever with WPA2 in Feisty. Just clicked my network and put in the passkey and it worked.
The funny thing is that WPA2 doesn't work in Windows on the same computer, so the encryption falls back to WPA in that case. Funny but true.

---

### Post by %hMa@?b&lt;C on 2007-05-18
none. I got a free la fonera, hacked it and if any of my neighbors want to use it, go for it!

---

### Post by JerseyShoreComputer on 2007-05-18
Using WEP at home - cannot seem to get Ubuntu to connect to WPA so I continue with WEP. We use WPA-PSK at work...

---

### Post by reacocard on 2007-05-18
WPA. Only downside is that my DS can't connect. :(

---

### Post by PartisanEntity on 2007-05-18
> **starcraft.man said:**
> Oh and btw, I was reading above about some people thinking wpa is complicated and hard... from my experience, WPA is even easier than wep. You make one big password and then input it on every computer _once_ and your set for life (or however long you pass between changing passes), you never have to enter it again and its secure. :)

Exactly, and this is what surprised me when some said that WPA seemed too much of a hassle or too complicated.

I am not sure how WEP works, but in WPA you enter a password on the wireless router and then also the same password on your laptop for example, that's it.

What is it about WPA that seems harder than WEP ?

---

### Post by rickyjones on 2007-05-18
I use a simple WEP key at home and at my clients I use WPA-PSK. Works pretty well.

-Richard

---

### Post by kragen on 2007-05-18
> **PartisanEntity said:**
> What is it about WPA that seems harder than WEP ?

Hardware support - some older routers and network cards don't support WPA, or require an upgrade to the firmware first. It's definitely not an issue with any new gear, but cards and laptops that are several years old could cause problems.

---

### Post by PartisanEntity on 2007-05-18
> **kragen said:**
> Hardware support - some older routers and network cards don't support WPA, or require an upgrade to the firmware first. It's definitely not an issue with any new gear, but cards and laptops that are several years old could cause problems.

Hmm that would explain some of it, I had no idea, thanks for the info.

I thought the actual use of WPA was hard, which it really really is not.

---

### Post by afljafa on 2007-05-20
This might interest some.

I just picked up a new lappy and went for a drive around town last nite to run a few chores. In my 25km drive I picked up 120 access points and around 50 of them where running no encryption at all. I was able to pull up outside a few locations and browse the internet with little problems.

Loads of the AP`s where either using default ssid`s or really obvious ones (companies etc).

---

### Post by rsambuca on 2007-05-20
> **afljafa said:**
> This might interest some.

I just picked up a new lappy and went for a drive around town last nite to run a few chores. In my 25km drive I picked up 120 access points and around 50 of them where running no encryption at all. I was able to pull up outside a few locations and browse the internet with little problems.

Loads of the AP`s where either using default ssid`s or really obvious ones (companies etc).

What you did is actually illegal up where I live!  I hope you weren't breaking any laws where you live.;)

---

### Post by yatt on 2007-05-20
WEP. Only one of my neighbours actually uses encryption (I pick up four networks not including my own), so I doubt they are gonna be able to hack it.

---

### Post by guyraz on 2007-05-20
I use WPA from my place there is about 8 good signal open networks, I'm the only one encrypted

---

### Post by Pugwash on 2007-05-20
Isn't it a bit dangerous to just leave it open? I mean somebody could drive up near your house, pull out a laptop and start browsing for child porn or other stuff, and you'd be the first person the pigs come to check up on. I use wpa anyway.

---

### Post by joe.turion64x2 on 2007-05-20
I use a wired router, does it count in this pole? I trust more the security provided by a wire I can see and actually plug/unplug than any other 'invisible' encryption technology.

(I voted none).

Joe.

---

### Post by SishGupta on 2007-05-20
I use wep because of my DS. Before that I used WPA2.

Yes, I love my DS more than I do my security. So?

---

### Post by jpkotta on 2007-05-20
No encryption, with MAC filtering.

BTW, WEP can be cracked in under a minute.  If someone wants to use your wireless, and you use WEP, it is trivial for them to do so.

---

### Post by smdeep on 2007-05-20
Wpa

---

### Post by Enverex on 2007-05-20
> **jpkotta said:**
> No encryption, with MAC filtering.

BTW, WEP can be cracked in under a minute.  If someone wants to use your wireless, and you use WEP, it is trivial for them to do so.

True, but the packets are still encrypted and it means Miss Dim with her laptop can't just sit and play with your Wireless after Windows decides to auto-connect to it.

---

### Post by insane_alien on 2007-05-20
i use WPA. although with the number of unsecured wireless networks around here 80% of the time fiesty will connect to another by itself. If i do notice(like crappy download speeds) then i switch back to mine which usually happens. i've tried to show them how to put security on it but they don't want to know.

---

### Post by Cheese Sandwich on 2007-05-22
Question: How do you tell if someone's using your wireless network?

I use 62bit WEP but have just been reading about how easy it is to crack. Is 128-bit WEP much harder?

---

### Post by Luggy on 2007-05-22
Wireless security ( and really any form of digital security ) is a lot like trying to protect your car from getting stolen: if someone really wants to steal it, they can steal it. 

The trick is deterence. 

If you put a club on your steering wheel or an alarm system in your car, a car theif is going to try and steal a car without one because it's easier.

Is putting up WEP as good as putting up WPA. No, but it is enough of a deterence when there are a few stronger, un-protected networks near by.

---

### Post by Calash on 2007-05-22
WPA with SSID off, MAC address locking, and static IP's.

Strong password on the router to boot.

---

### Post by doobit on 2007-05-22
SSID not broadcast, MAC locked, strong password. I understand that someone can still read my packets if they wanted to, so nothing sensitive goes out over the wireless.

---

