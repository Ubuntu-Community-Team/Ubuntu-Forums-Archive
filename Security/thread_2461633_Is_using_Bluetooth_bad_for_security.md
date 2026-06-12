---
title: "Is using Bluetooth bad for security ?"
date: 2021-05-04
forum: Security
---

### Post by linuxyogi on 2021-05-04
I rarely transfer files using bluetooth but I use my bluetooth headphone when I am using my PC during the night.

The web is full of articles which say bluetooth is very insecure. Example >> [Click here]("https://www.makeuseof.com/tag/3-ways-bluetooth-device-security-risk/")

So is bluetooth bad for security under Linux too  ?

---

### Post by scorp123 on 2021-05-06
> **linuxyogi said:**
> So is bluetooth bad for security under Linux too  ?

Yes. At least in theory, absolutely yes. The Bluetooth protocol isn't exactly known for being "very secure" and there's little your OS can do about it. BUT ...

What are your chances of actually getting hacked if ...

[LIST]
[*]You are only using Bluetooth devices in your own home?
[/LIST]
**-VS-**

[LIST]
[*]You are using Bluetooth devices in a public place where anyone could be a hacker ...
[/LIST]

Bluetooth doesn't have a very long range. So using it in your own home where nobody can sneak up on you and try to mess with it should be *relatively* safe. The chances of getting hacked there by someone who actually knows how to do that are rather small I guess?

Counter example:

I attended a hacker conference once. Thousands of people were there and many of them were IT security experts or they had equivalent skills. Chances of hackers with the needed skillset being present in the crowd: Extremely high. You can bet I turned off Bluetooth and WiFi the whole day when I was in there. Also on my train ride home I left it all turned off. The chance that some of the same people I just met at the conference might be riding with me in the same train was still rather high. Using Bluetooth-anything or trusting any public WiFi on *such* a conference!???  Extremely suicidal. You're basically begging to get hacked. You bet someone *can* and *will* do it.

Just be smart and aware where you are (at home where you have everything under control vs. in a public place where you have no control at all ...) and turn off / turn on Bluetooth accordingly.

---

### Post by linuxyogi on 2021-05-08
@scorp123
I am using Bluetooth under a Desktop so I am using bluetooth at home only. When I am not using my bluetooth I disable it, I started doing this because of fear of getting hacked.
You mention WiFi too. So WiFi is insecure too ? The worked "hacked" may mean multiples things. What I need to know is can someone hack my PC using WiFi & see all my personal data like my photos, music, movies, etc ? The only reason I use Linux is security.

---

### Post by scorp123 on 2021-05-08
> **linuxyogi said:**
>  You mention WiFi too. So WiFi is insecure too ?  

Short answer: Yes. :evil:

More detailed answer: Think about it? You're at a hacker conference. There are thousands of people around you, anyone of them could be a hacker and someone with the needed skills to ruin your life. In such a place... **Would you *really* trust any free + public WiFi network that's being offered!??? :-k Hell no. [-X ** There's no guarantee whatsoever that that "Free WiFi" you are connecting to wasn't setup by one of those guys and they are just waiting for a naive person to connect to their WiFi network so they can sniff on your network traffic, sniff out all logins and passwords you transmit over *their network* they have created and is under *their* control.

So yes ... if you attend such a conference the first thing you do is to turn off Bluetooth + WiFi and be 100% offline.

At home it's again a different story. 

In the part of the city where I live there are several dozen of houses around me. So ... I have neighbours. Hundreds of neighbours. I can see like 20-30 different WiFi networks around my house. And the same must be true for any of my neighbours: Yes, they can see my WiFi network too.

So I setup a strong WiFi password, I avoid weak WiFi algorithms such as WEP and set everything to something strong like WPA2 as far as possible .... and I also keep an eye on my WiFi logs and what devices are connected to it.

And I get extremely extremely paranoid when my own WiFi devices suddenly keep losing their connection and have to reconnect.... because that's one of the possible attack vectors how WiFi can be hacked.

How that attack works:

An attacker would bombard every WiFi device with a ***"DISCONNECT"*** signal. They don't even need to authenticate or know your WiFi password for that. That signal is part of the WiFi standards. 

The purpose of that packet was to signal a client device that it has moved out of range of the WiFi access point and that the WiFi signal has gotten so bad and weak that it's no longer useful to stay connected to this particular device. Imagine walking around in a very large building? e.g. a University? Or a company building? And there are dozens of WiFi access points everywhere... And you are walking around, e.g. moving from one lecture to another. Or moving from one meeting to another. And as you move through that large building you're constantly connected to the nearest WiFi access point. And as you move by ... you slowly but surely will get out of range. And here's where the *"DISCONNECT"* signal comes in: The WiFi access point you were connected to will send you the signal when it senses that your connection is getting too bad ... and your device will connect to a new WiFi access point.... whichever is the closest now.

Attackers can abuse that mechanism. As I said above they flood your WiFi channels with that signal. And your devices will do as the WiFi standard tells them: They will disconnect from your own legit WiFi network. And here's the attack: By that time the hacker will have setup their own WiFi network **[COLOR="#FF0000"]PRETENDING TO BE YOURS.[/COLOR]** It will have the same name.

Your devices will of course think *"Oh cool, we lost our previous connection but there's another WiFi access point that belongs to us too! Let's connect to it ... yay!!"* \\:D/ and your devices will transmit the correct WiFi password. ](*,)

A hacker can then sniff out the correct password for your actual network your device just sent them with the WiFi handshake. :twisted:

From here onwards they will be able to connect to your WiFi and sniff your network traffic, steal your data, steal your files, get into your bank account, ruin your life ....

**Again: Be smart.** Does your own WiFi at home have a strong and complex password? Good. Do all your WiFi devices usually work without problems? Good. But the second you experience never-seen-before mass-disconnects of every device in your home (... your laptop disconnects, your phone disconnects, your tablet disconnects ...) I'd say it's time to be paranoid and double-check that there are no unknown devices on your network afterwards. 

Since I live in a crowded area there is a certain chance that one of my bored neighbours sitting in quarantine just like me might try something like this.

If you live alone out in the desert somewhere somehow alone with rabbits and squirrels ... yeah, not likely to happen. Unless the local rabbits have it out for you? :D


> **linuxyogi said:**
>  The only reason I use Linux is security.

Wrong approach, my friend. "Security" is not something you can install and then never think about it again. "Security" is more about **you** and **what you do** and not so much what you install or not. Even an inherently rather insecure Windows 10 installation can be made very secure if you do it right. And even a rather secure OS such as FreeBSD or Ubuntu Linux can be made very insecure if you don't pay attention and have no idea what you are doing. "Security" is an ongoing process, a way of thinking, a way of doing certain things. It's never a product you can have or not have and then be done with it.

---

### Post by TheFu on 2021-05-08
The last time I was cracked was at a conference ... over bluetooth ~ 2015. I'd wiped the system the day before, did a fresh install and fully patched.  It was not connected to wifi or wired ethernet networks.  Newer versions of the protocol are more about saving battery power than being more secure.
I've heard it is fun to look for powered on BT speakers in hotels late at night, connect to them using 0000 or 1234 and blast some "Kill the Rabbit!" music from looney tunes.  That's what I hear.

As for wifi, all of the protocol versions have known hacks, including Wifi-6 which is just being released these days.  In short, only use wifi with a VPN.

The squirrels ARE out to get me.  They've enlisted a raccoon to aid in their plot. I've got video ... from the attic!
**_[SIZE=4]Busted![/SIZE]_**
[ATTACH=CONFIG]288435[/ATTACH]

---

### Post by scorp123 on 2021-05-09
> **TheFu said:**
>  The last time I was cracked was at a conference ... over bluetooth ~ 2015. 
Bingo!! :shock:

> **TheFu said:**
>  I've heard it is fun to look for powered on BT speakers in hotels late at night, connect to them using 0000 or 1234 and blast some "Kill the Rabbit!" music from looney tunes...  
Also works quite nicely at boring company meetings, e.g. you find that the meeting you're stuck in could use some "sprucing up" ... and one of the speakers boring you to death with sales figures and other non-technical nonsense left all their Bluetooth stuff turned on with a default PIN code of "0000" or "1234". It's not even "hacking" at this point... It's an open invitation to get pranked. :lol:

> **TheFu said:**
> 
They've enlisted a raccoon to aid in their plot. I've got video ... from the attic!


Whoa, you got some scary raccoons there. Have they figured out your WiFi password already and how Google works? Don't let them!! They'll learn how to build guns and go full on *"Rocket"* from *"Guardians of the Galaxy"*, and demand that you hand over the keys to your spaceship, at gunpoint. Having to explain to a rather irritated raccoon that those keys you have are not for a spaceship but rather for your car ... that's a discussion you rather don't want to have.  *".... But I've seen it on your Internet thing, human!!! .... "*  :lolflag:

---

### Post by linuxyogi on 2021-05-09
>  			 		 	 Wrong approach, my friend. "Security" is not something you can  install and then never think about it again. "Security" is more about **you** and **what you do** and not so much what you install or not.

@scorp123 / @TheFu

(1) UFW is enabled
(2) I check for updates everyday & install them asap. 
(3) I run all network facing apps like Firefox, Claws-Mail, Hexchat inside firejail.

Is that enough ? What else should I do ?

---

### Post by scorp123 on 2021-05-09
> **linuxyogi said:**
>  Is that enough ? What else should I do ?

Maybe check the list of LAN devices and DHCP leases in regular intervals, e.g. on your router: it should be able to produce a list of that. Are you 100% sure all devices listed there are yours? :-k  Keep an eye on that. 

Also: Do you use port-forwarding? e.g. you opened up SSH so you can have remote access to your PC? In that case I'd recommend something like **"fail2ban"** too.

My router at home can do geo-filtering, so I have blocked dozens of countries (e.g. USA, China, Russia ...) and even whole continents from accessing my network. I have no relationship whatsoever with those places, and thus those places have no business whatsoever of ever accessing my network, especially not via the Internet.

Screenshot:
[https://i2.paste.pics/3c62ea09dadcb83f3a37c3ed69c7fa3f.png]("https://i2.paste.pics/3c62ea09dadcb83f3a37c3ed69c7fa3f.png")

Because *"name and shame"* might be against forum rules :oops: and because some companies might interpret this as being harmful to their reputation and might thus feel provoked, I have removed all specific IP addresses and company names from that screenshot. I left the names of countries and continents though, for the reasons I specified above: I have no relationship with those places and thus no IP address from any of those countries or regions has any business accessing my network. You can see the number of outside connection attempts in the right column, e.g. 19446 attempted connections from IP addresses inside the *"Block North America"* rule, 7053 connection attempts from within the *"Block Asia"* rule, and so on.

My router also has an ad-filter (comparable to **"Pi Hole"** ...) and I use **"uBlock Origin"** in every browser. Ads can be harmful to your privacy and malware hiding inside ads is not unheard of... so if you can block ads, please do.

And if a website asks you to remove your Ad-Blocker because otherwise they won't let you in .... well, too bad for them. They get one less visitor in that case, but I will never ever deactivate or remove my Ad-Blockers because a website asks me to. And neither should you.  [-(

---

### Post by TheFu on 2021-05-09
> **linuxyogi said:**
> @scorp123 / @TheFu

(1) UFW is enabled
(2) I check for updates everyday & install them asap. 
(3) I run all network facing apps like Firefox, Claws-Mail, Hexchat inside firejail.

Is that enough ? What else should I do ?

I'm with scorp123, though I can't block the USA. ;)  That's where SquidbillyLand is located! [https://en.wikipedia.org/wiki/Squidbillies](https://en.wikipedia.org/wiki/Squidbillies)

Nothing is ever enough. No **useful** setup of tools will ever be fully secure. This is all about **risk management**.

1) enabled doesn't say anything about the settings, which services are open, or anything about other security aspects on the network under your control.  I want at least 2 layers blocking any attack vector.  Often, that is 1 on the router and one on each host.  Sometimes it is more like setting up different subnets for different types of access.

2) I think patching daily is foolish. There, I've said it.  **Risk management**.  There are risks in getting a patch that hasn't been fully vetted early.  There is risk that some patch will break workflows.  If a new patch that is working as planned, but breaks my workflows gets installed on Monday, then my work-week is screwed. I'll miss deadlines, possibly lose clients.  That is unacceptable.  I've got raccoons and squirrels to feed and shelter! I do change management on Friday evenings or over the weekend. 
In 2009, I was doing automatic updates until one of the packages decided that MariaDB wasn't allowed and I should be running MySQL.  It removed MariaDB, which took down a service (project management server) used by nearly everyone in the company.  Fortunately, it was early on a Saturday morning, during a published "maintenance window."  I still got 2 phone calls. 
I don't allow automatic patching since then. It is scripted and logged, but someone has to run a command on 1 system to cause all the patching to happen on nearly all the other systems.  They also have to answer "Y" for each system. This gives the admin a chance to look over the packages - though I have to admit I don't always look too carefully. That's what logs are used for, right?

3) Firejail isn't necessary for all apps.  **Risk mitigation**. How you limit the environment matters too. I use those same apps plus a few others, but only thunderbird, firefox, dillo and chromium run inside firejail.  Hexchat could, but because I run an IRC-bouncer server, I think that mitigates the risk. My hexchat connects to my IRC-bouncer. I suppose it wouldn't hurt.
* Running chromium inside firejail is only possible when NOT using a snap package. Chromium is my "danger, danger" browser, so it always runs in **firejail --private** mode.  This is a hassle, because I can't save any files, but sometimes use it for online brokerage account work.  That makes it hard to save exported transactions, for example. Security vs convenience.
* Dillo is a minimal browser without any javascript capabilities - and it doesn't validate any SSL connections, so beware. Dillo will support showing images and it is very light, however. 

There are all sorts of privacy and security settings for those programs too. Firejail doesn't help with those too much. Notice that I'm trying to manage risks vs convenience by which applications get run inside restricted environments. It doesn't hurt to revisit these choices if my use patterns change.

If your router hasn't been patched in 6 months, it probably has a major security problem. The same applies to NAS appliances.  All the major NAS vendors seem to have security faults almost monthly the last year.

Layered security.  Network security. Privacy options. Often a little inconvenience are required.  Use a password manager and 2FA when possible. Don't blindly allow access to your Contacts either, please.

We haven't thought at all about phone phone or tablet connections to our data. Those devices and most IoT/S devices are a privacy minefield, and not just for the device owner, but almost everyone in their contacts.

Think **risk management**, not "Security (Y/n):"

---

### Post by linuxyogi on 2021-05-09
> Maybe check the list of LAN devices and DHCP leases in regular  intervals, e.g. on your router: it should be able to produce a list of  that. Are you 100% sure all devices listed there are yours? :-k  Keep an eye on that. 

Also: Do you use port-forwarding? e.g. you opened up SSH so you can have  remote access to your PC? In that case I'd recommend something like **"fail2ban"** too.


Yes I do check my router to see what devices are connected. I didn't learn this technique by reading any article. I just guessed it myself. 
There is absolutely no open ports on my home network. No ssh, nothing. uBlock Origin is doing a very descent job in the ad blocking department.

> 1) enabled doesn't say anything about the settings, which services are  open, or anything about other security aspects on the network under your  control

```
$ sudo ufw status verbose
[sudo] password for homepc:           
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

```

```
$ nmap 192.168.225.21
Starting Nmap 7.70 ( https://nmap.org ) at 2021-05-09 20:48 IST
Nmap scan report for homepc (192.168.225.21)
Host is up (0.000079s latency).
All 1000 scanned ports on homepc (192.168.225.21) are closed

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds


```


>  I think patching daily is foolish. There, I've said it.  **Risk management**.  There are risks in getting a patch that hasn't been fully vetted early.  There is risk that some patch will break workflows.

This is my personal home PC. I really dont care if something breaks coz now we have this awesome tool called Timeshift.

> If your router hasn't been patched in 6 months, it probably has a major security problem. 

My router hasn't been patched for more than a year & there is nothing I can do about this. This is 4G router & no opensource firmwares like DD-WRT supports this device. 
Since we are planning to move to a new home soon I want to avoid changing my ISP at the moment coz if I do that then I will have to pay the "installation charges" twice.
Once we move I will be able to use PFsense as my new connection will be fiber.

---

### Post by DuckHook on 2021-05-09
> **TheFu said:**
> …The squirrels ARE out to get me.  They've enlisted a raccoon to aid in their plot.

[QUOTE=scorp123;14036929…Whoa, you got some scary raccoons there. Have they figured out your WiFi password already and how Google works? Don't let them!! They'll learn how to build guns and go full on *"Rocket"* from *"Guardians of the Galaxy"*, and demand that you hand over the keys to your spaceship, at gunpoint. Having to explain to a rather irritated raccoon that those keys you have are not for a spaceship but rather for your car ... that's a discussion you rather don't want to have.  *".... But I've seen it on your Internet thing, human!!! .... "* [/QUOTE]
How do you know it wasn't the raccoon who enlisted the squirrels? Hunh? Hunh?

In my experience, it's usually the raccoons who are the masterminds. They send the squirrels out as expendable scouts. Plausible deniability you see. You were lucky to glimpse the raccoon, They're usually more careful.

Then again, he could have wanted to be imaged. A false flag operation. Such cunning. Like scorp says, watch out for those car keys. Keep an eye on your cell phone and prosthetic leg too. They'll combine the parts to produce a quantum sub-singularity death ray, and they ain't interested in listening to anything that smacks of excuses.

---

### Post by mikesmith7 on 2021-05-09
A lot of manufactures just gave up, but essentially all devices without update will be (and stay) vulnerable. Personally I would consider not using BT if that's the case.

Edit: Provided that BT can even be disabled as feature, which is not always the case.

---

### Post by linuxyogi on 2021-05-10
> **mikesmith7 said:**
> A lot of manufactures just gave up, but essentially all devices without update will be (and stay) vulnerable. Personally I would consider not using BT if that's the case.

Edit: Provided that BT can even be disabled as feature, which is not always the case.

BT can be disabled under Linux.

[ATTACH=CONFIG]288437[/ATTACH]
(Click to enlarge)

---

