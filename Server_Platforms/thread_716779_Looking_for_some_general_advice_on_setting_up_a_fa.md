---
title: "Looking for some general advice on setting up a fairly complicated system."
date: 2008-03-06
forum: Server Platforms
---

### Post by kaens on 2008-03-06
Well, complicated for me at least.

Alright, here's my situation and what I would like to accomplish:

I have a dsl connection in my apartment, and a wireless router. I have no problem with allowing other people near me use my internet access (in fact, I would prefer to allow them to), however I don't know everyone around here, and I'd like to be able to exert some rather fine-grained control over people using my connection.

Mainly, I don't want people downloading torrents without capping their upstream and making it so that no one can browse the net. (I'd also like to do some bandwidth limiting in general for downloads. . . ).

Anyhow, I'd rather not just cut off net access for everyone - especially since I'm in a poor area of town, and most of the people around me probably can't afford a net connection consistently. 

I'd like to be able to set up the connection with a hardware firewall of sorts in between the modem and wireless router that behaves like so:

First time someone tries to access the internet, they get redirected to a page explaining that I really don't have a problem with them using it and requesting that they please be polite with the connection, otherwise they will get limited and possibly banned.

I'd like to be able to dynamically monitor bandwidth and protocol usage, and redirect people to warning screens if they pass a certain threshold.

I'm not sure if I should do something with usernames and passwords like a free net portal, or if I should (or can) do things like this automatically based on MAC addresses.

I'm rather rusty on my network configuration skills, but I'm more than willing to brush up. 

Does anyone have any suggestions on what I should be reading up on, or ideal ways to accomplish something like this? Is this a stupid idea in general?

This whole idea makes me sound like something of an authoritarian jerk, which I don't mean to come off as. I don't want to scare people, or spy on them. I want to share the internet connection that I pay for - but I want to be sure that people use it in a manner that doesn't hinder other people who are also using it.

---

### Post by smileypaul on 2008-03-07
Don't quote me on this..

but, if you hav ea linksys wrt54g router, i believe you can flash it with DD-wrt. I believe this software has similar functionality of what you're looking for (ie: pull up a webpage saying "its ok..but.."  )... do some research on it.

I use the firmware the have a wireless bridge between 2 routers, but have never looked into what you're doing.

You may also be interested in IPCop.. again, i havent used it, but its worth checking out.

Good Luck.

---

### Post by sciurus on 2008-03-13
Look at [NoCatSplash]("http://nocat.net/"), [WiFiDog]("http://dev.wifidog.org/"), and [Chillispot]("http://chillispot.org/"). If you have a compatible router, you should be able to run these on the router using the [OpenWRT]("http://openwrt.org/") firmware. There's a router firmware that called [CoovaAP]("http://coova.org/") that integrates Chillispot for you.

---

