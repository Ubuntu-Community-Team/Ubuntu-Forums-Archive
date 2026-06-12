---
title: "What security for wpa2 hotspot? Ubuntu 12.04"
date: 2012-09-21
forum: Security
---

### Post by chipmcd on 2012-09-21
Ubuntu newbie here.  And maybe a little paranoid concerning security.

The building where my office is located offers free wifi for its tenants (wpa2 - tenants are given the network password.)  I'm still leary of using it because I'm not sure what kind of security I should be running on my laptop using Ubuntu 12.04.  To me, it kind of feels like an "open" network among us tenants.

I have firestarter running on my laptop but understand it is a basic firewall and may not be as robust as I need.  What should I be running or doing to keep my computers safe at work?

---

### Post by CharlesA on 2012-09-21
You should be fine. If you are sure the access point in WPA2, random people off the street would be unable to connect to it.

Now, because you do not own that network, assume anything you do on it is monitored. I would not use "Free wifi" for work related stuff.

If it was me, I would be using a net connection in the office building itself, not some "free wifi" offered by the building owners, but call me paranoid.

---

### Post by BrianBlaze on 2012-09-21
> **CharlesA said:**
> You should be fine. If you are sure the access point in WPA2, random people off the street would be unable to connect to it.

Now, because you do not own that network, assume anything you do on it is monitored. I would not use "Free wifi" for work related stuff.

If it was me, I would be using a net connection in the office building itself, not some "free wifi" offered by the building owners, but call me paranoid.

Agreed, As long as it for sure is WPA2 you are safe from randoms I would also make sure no services are running (ssh, etc) or if they are you have good passwords. 

A nice way for you to protect yourself is find out the range of IP's given by the router and make yours a static IP. Makes it much harder for the router or anyone monitoring to know your computer name (although the ycan see your MAC address you can always change that :)

---

### Post by CharlesA on 2012-09-21
> **BrianBlaze said:**
> Agreed, As long as it for sure is WPA2 you are safe from randoms I would also make sure no services are running (ssh, etc) or if they are you have good passwords. 

A nice way for you to protect yourself is find out the range of IP's given by the router and make yours a static IP. Makes it much harder for the router or anyone monitoring to know your computer name (although the ycan see your MAC address you can always change that :)
Wouldn't do much good if someone was actually sniffing on the network. They can find your IP fairly easily, even with a spoofed MAC address.

---

### Post by chipmcd on 2012-09-21
> **CharlesA said:**
> You should be fine. If you are sure the access point in WPA2, random people off the street would be unable to connect to it.

Now, because you do not own that network, assume anything you do on it is monitored. I would not use "Free wifi" for work related stuff.

If it was me, I would be using a net connection in the office building itself, not some "free wifi" offered by the building owners, but call me paranoid.


Not paranoid... careful.

I'm not sure I'm understanding what you are meaning when you say a net connection in the office building itself vs. free wifi offered by the building owners.  I probably didn't explain it clearly.  The building/owners have supplied free wireless access for 2 of the 4 floors in the building (2nd and 3rd floor each have their own access)  It's a service that is offered to all of it's tenants only.  Tenants receive the password from the owners/management for access.

I guess I'm just afraid of the mischievous tenant (users inside) in the building. At home, I've never thought of having to worry about someone on my network (me) hacking into my computer.  

And as for work related stuff, our stuff needs to see the internet.  But I'm just worried about someone being able to access files on these computers if they do happen to get connected to the internet for say looking up information or whatever.



It's got me concerned that I'm worried about just logging in for my yahoo mail.

---

### Post by CharlesA on 2012-09-21
> **chipmcd said:**
> I guess I'm just afraid of the mischievous tenant (users inside) in the building. At home, I've never thought of having to worry about someone on my network (me) hacking into my computer.  

And as for work related stuff, our stuff needs to see the internet.  But I'm just worried about someone being able to access files on these computers if they do happen to get connected to the internet for say looking up information or whatever.

Set up a dedicated internet connection there. That would be the safest way to do it, because you aren't on a "random" person's network.


> It's got me concerned that I'm worried about just logging in for my yahoo mail.

If you do have to use the wifi for some reason, it is a good idea to tunnel your traffic via vpn or ssh, so it is unreadable in case someone is capturing packets on said network.

---

### Post by Welly Wu on 2012-09-24
I would recommend that you consider WiTopia personal VPN pro: [http://www.witopia.net](http://www.witopia.net). I paid $72 USD for 1 year of service. I am at a public library with an open 802.11 G Wi-Fi hot spot and I am connected to the WiTopia VPN gateway. This is probably the next best solution to purchasing an ISP and installing a wireless router in your apartment. That would still be the best solution. Combining your own ISP and VPN would be the best solution for home users that need remote access to your work if you are allowed to telecommute.

---

### Post by Lyfang on 2012-11-04
A private VPN can protect against other people intercepting one's data traffic, which is good for one's privacy.

---

