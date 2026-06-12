---
title: "webfilter for family"
date: 2007-03-05
forum: Ubuntu Christian Edition
---

### Post by wussywokkie on 2007-03-05
Hello

I'm kinda newish to the whole filtering the web kinda deal.. I work in a place that has up and running websense...and i love the idea for my home.. i have the following kids at home 8/6/2/bun in oven....

What i would like to do..

wifey is running small home based business.
kids will be getting when age premits own pc's laptops, currently have own logins on my laptop home pc.

what i wanna do

cable modem.  webfilter/firewall/lamp/ssh/backup/samba/dansguardian/

what i would like to know. 

If, at all possible have an permissions based logins..meaning... I don't want the 8 year old looking into da pron, but, wife and i can <if wanted>... I would like to have one network, but am able to run more then on.
example:
kid1   filterd to the max, no pron, no bad language, no myspace/freindster moniter aim
kid2   same as above
parent 1, no filters, but all traffic logged
parent 2  same as above.

is this possible...is it easyish to maintain <less then 4 hours a month>.

THanks in advance.

wookie

---

### Post by amborle on 2007-03-05
If I had kids, I would go about it another way than the 1984-way...

---

### Post by doobit on 2007-03-06
Dansguardian with the new GUI is very easy to operate. Yes, it's set up so only the administrator can control it, so you need to be logged on as administrator to set it up, but the GUI makes it very easy and fast to do. It only takes seconds to log on, set it up and log off, then log on your next user. I'm sure you only need to worry about one user setting at a time right? It's also not a bad thing for parents to be present, at least part of the time, when the kids are on the computer.

---

### Post by wussywokkie on 2007-03-06
> **doobit said:**
> It's also not a bad thing for parents to be present, at least part of the time, when the kids are on the computer.

we plan to be there...but..it's an added level of protection, as although i wish i could be everywhere at once.. not going to happen.. the main pc that the kids will use is going to be in kitchen/dinning area..

but..

some of my son's 8year old friends, already have laptop computers... i wanted some extra level..  I don't' care if someone uses my connection to the internet..but when it's kids.. i want some protection.

---

### Post by andytof47 on 2007-03-07
I have this exact setup,

It basically comes down to 
A) having the pron filter setup

B) having the correct firewall rules - can give you an example file - the beauty about iptables is you can specify filtering by mac address ipaddress username or interface - your choice but it's very flexible

check this [**_howto_**]("http://ubuntuforums.org/showthread.php?t=370563") - I don't recommend using the dansguardian proxy way with Tinyproxy because it not A transparent proxy setup - meaning you would need to setup each computer to go through the proxy



however transparent proxying means that as it goes through the filter machine the firewall passes it through the content filter

once the software is setup it is a matter of physically securing access to the router box and the adsl modem if it has Ethernet ports. I actually went ot the hardware store and bought some plastic boxes for the smaller hardware and chucked some padlocks on it then drilled a plate to the back of my system to prevent the network cable being removed physically from the computer to the modem

sounds psychotic however one of the first principles pf network security that is overlooked is physical access


what type of hardware do you have? if you don't have a wireless card make sure you get an atheros chipset  

hope that helps

---

