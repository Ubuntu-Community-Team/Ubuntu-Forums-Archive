---
title: "Can Ubuntu be stealthed?"
date: 2008-08-09
forum: Security
---

### Post by k3lt01 on 2008-08-09
I have gone through my laptops security today, will do my desktop another day as it hardly gets turned on lately, and checked it against the "Shields Up" site. Everything is all well and good, as I new it would be, but it was doing something odd. I checked all Ports a few times after doing different things and each time the Stealth ports were different. All up about 5-10% of the ports were stealth and others were closed but it kept changing what ports were stealth.

Now to my question, can I stealth my Ubuntu? If yes how? If no, well.... why not? I know this is a Windows mindset thing but to my mind security is important and also I just want to play with it to see if I can stealth my machines.

BTW when I used XP many moons ago, I got it stealthed, it was hard work but I did it. Could never do it with Vista.

---

### Post by brian_p on 2008-08-09
> **k3lt01 said:**
> I have gone through my laptops security today, will do my desktop another day as it hardly gets turned on lately, and checked it against the "Shields Up" site. Everything is all well and good, as I new it would be, but it was doing something odd. I checked all Ports a few times after doing different things and each time the Stealth ports were different. All up about 5-10% of the ports were stealth and others were closed but it kept changing what ports were stealth.

These 'different things'. Any detail to offer?

> Now to my question, can I stealth my Ubuntu? If yes how? 

Netfilter (iptables) and DROP.

---

### Post by Oldsoldier2003 on 2008-08-09
> **k3lt01 said:**
> I have gone through my laptops security today, will do my desktop another day as it hardly gets turned on lately, and checked it against the "Shields Up" site. Everything is all well and good, as I new it would be, but it was doing something odd. I checked all Ports a few times after doing different things and each time the Stealth ports were different. All up about 5-10% of the ports were stealth and others were closed but it kept changing what ports were stealth.

Now to my question, can I stealth my Ubuntu? If yes how? If no, well.... why not? I know this is a Windows mindset thing but to my mind security is important and also I just want to play with it to see if I can stealth my machines.

BTW when I used XP many moons ago, I got it stealthed, it was hard work but I did it. Could never do it with Vista.

Unless you have a direct connection to the internet, grc.com is testing your gateway/router. On a shared internet connection , all shields up is testing is your NAT device, unless you have forwarded specific ports to a specific machine on your home network.

---

### Post by mczonie on 2008-08-09
> **k3lt01 said:**
> I have gone through my laptops security today, will do my desktop another day as it hardly gets turned on lately, and checked it against the "Shields Up" site. Everything is all well and good, as I new it would be, but it was doing something odd. I checked all Ports a few times after doing different things and each time the Stealth ports were different. All up about 5-10% of the ports were stealth and others were closed but it kept changing what ports were stealth.

Now to my question, can I stealth my Ubuntu? If yes how? If no, well.... why not? I know this is a Windows mindset thing but to my mind security is important and also I just want to play with it to see if I can stealth my machines.

BTW when I used XP many moons ago, I got it stealthed, it was hard work but I did it. Could never do it with Vista.

After I installed Firestarter, I did a shields up scan and all ports were stealthed.

---

### Post by k3lt01 on 2008-08-09
> **brian_p said:**
> These 'different things'. Any detail to offer?tested system, installed firestarter-tested system. uninstalled firestarter-tested system. installed Gufw-tested system. for each difference the stealth ports were different.

> **brian_p said:**
> Netfilter (iptables) and DROP.iptables is installed by default, it is part of Linux as far as I was aware. I am assuming Netfilter is a gui like Gufw and Firestarter are giu's for iptables.

---

### Post by k3lt01 on 2008-08-09
> **Oldsoldier2003 said:**
> Unless you have a direct connection to the internet, grc.com is testing your gateway/router. On a shared internet connection , all shields up is testing is your NAT device, unless you have forwarded specific ports to a specific machine on your home network.I haven't forwarded anything but firestarter showed Shields Up trying to chat to my laptop so something was getting through. If I can stealth my machines I'll be happy if I can't its not the end of the world.

---

### Post by lukjad on 2008-08-09
Have you ever heard of Nbuntu? It's supposed to be a really secure version of Ubuntu. This may be of some interest to you. Even if you don't want to installed instead of Ubuntu you can always try and  make some of the changes Nbuntu has made to your Ubuntu installation.

---

### Post by brian_p on 2008-08-09
> **k3lt01 said:**
> I haven't forwarded anything but firestarter showed Shields Up trying to chat to my laptop so something was getting through. If I can stealth my machines I'll be happy if I can't its not the end of the world.

From my limited acquaintance with netfilter (which is not a GUI)

```
iptables --flush
```

removes all existing filtering rules, and

```
iptables -A INPUT -j DROP
```

drops all incoming packets to any port, producing so-called stealth ports. Test with Shields Up.

If the results from grc are not what you expect the chances are post #3 applies.

---

### Post by k3lt01 on 2008-08-09
> **lukjad007 said:**
> Have you ever heard of Nbuntu? It's supposed to be a really secure version of Ubuntu. This may be of some interest to you. Even if you don't want to installed instead of Ubuntu you can always try and  make some of the changes Nbuntu has made to your Ubuntu installation.
Thanks lukjad, I read about it a little while ago, it looks interesting for people who are into security in a big way, I think its a bit to techie for me. I'll take another squiz at it and see if there is anything in it I can understand, lol.

---

### Post by k3lt01 on 2008-08-09
Brian: I know post 3 isn't correct. I have checked my router and it isn't set to forward anything, it also isn't set to stop anything either so I will fix that later.

Is netfilter available in the Repo's? I had a look but couldn't see it.

---

### Post by brian_p on 2008-08-09
> **k3lt01 said:**
> Brian: I know post 3 isn't correct. I have checked my router and it isn't set to forward anything, it also isn't set to stop anything either so I will fix that later.

The first sentence of Oldsoldier2003's post is correct though. The grc scans are telling how your router, not your laptop, is seen from the internet.

> Is netfilter available in the Repo's? I had a look but couldn't see it.

It isn't a package.

[http://www.netfilter.org/](http://www.netfilter.org/)

---

### Post by solitaire on 2008-08-09
This usually works for me:
```
sudo ufw enable
```
Shields UP marks me as full stealth.. :D

---

### Post by k3lt01 on 2008-08-09
> **brian_p said:**
> From my limited acquaintance with netfilter (which is not a GUI)

```
iptables --flush
```

removes all existing filtering rules, and

```
iptables -A INPUT -j DROP
```

drops all incoming packets to any port, producing so-called stealth ports. Test with Shields Up.Tried this and it stopped everything, I couldn't even connect to the net lol.

---

### Post by k3lt01 on 2008-08-09
> **solitaire said:**
> This usually works for me:
```
sudo ufw enable
```
Shields UP marks me as full stealth.. :D
Tried this to and no difference.

---

### Post by k3lt01 on 2008-08-09
> **brian_p said:**
> It isn't a package.

[http://www.netfilter.org/](http://www.netfilter.org/)Thanks Brian, I'll take a look.

---

### Post by jerome1232 on 2008-08-09
ufw enable won't do anything by itself you would have to add after running ufw enable:

```
ufw default deny
```
Which does the same thing as the iptables commands you issued already. Denying incoming connections shouldn't impact your ability to get online though that's strange that it did.

The only reason I can think of that would cause ports to show up as not being "stealthed" is if the router has UPnP enabled on it, this allows apps to tell the router to forward ports to them.

---

### Post by k3lt01 on 2008-08-09
I have it set to deny in Gufw so I would assume that's the gui version of what your referring to.

---

### Post by cariboo on 2008-08-10
I am more worried about wireless security that whether shields up can detect open ports on my router. If you are a normal user and have not set up port forwarding on your router you have nothing to worry about. Sometimes I think grc.com is nothing but a way to get people to look at Gibson's retail products.

Jim.

---

### Post by k3lt01 on 2008-08-10
I used to use GRC for windows installs so I could help friends out, that was after I got my own setup working ok. Now I am using Ubuntu exclusively this is something for me to learn with for a few reasons. One is just for fun, two is I travel around a bit (for work and uni) so I use networks that I am not able to check their security, for that reason I really like to know that my own equipment is as secure as it can be and being stealth (i.e. unseen) is as good as you can get.

For the life of me I can't seem to figure out Netfilter with the way it is explained on the site. I'll keep googling and see what I find.

---

### Post by jerome1232 on 2008-08-10
Honestly, I just ran that scanner on the grc website, and it showed me as all stealthed, funny thing is I have a server in DMZ mode, with ports 22,25,143,993 open and actively listening, all other scanners show those ports as open. lol maybe try a better firewall scanner.

---

### Post by Oldsoldier2003 on 2008-08-10
> **jerome1232 said:**
> Honestly, I just ran that scanner on the grc website, and it showed me as all stealthed, funny thing is I have a server in DMZ mode, with ports 22,25,143,993 open and actively listening, all other scanners show those ports as open. lol maybe try a better firewall scanner.

Personally I have no faith in Shields up. I have extensively tested my network with it in the past an its results are completely useless. I can scan my network and be in full stealth mode regardless of which machines I have connected. Like you I have services open and listening ... 

Shield up is in my opinion, a largely useless and alarmist website designed to spread FUD and drum up business for GRC. If it scares people into taking a closer look at their security that may not be a bad thing. But honestly, folks should take a couple moments to understand what is really going on instead of blindly accepting Shields up results as gospel.

---

