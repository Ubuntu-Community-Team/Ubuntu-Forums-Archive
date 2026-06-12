---
title: "Untraceable net use?"
date: 2010-01-29
forum: Security
---

### Post by bit mad on 2010-01-29
Suppose you want to wind up a mate, discuss something embarrassing on a forum, whistleblow, or just criticise your usual ISP without any possible comebacks....... :D

IP address trace? Solved by using a public Wifi hotspot *(bonus points for walking there in hooded top avoiding CCTV cameras, with mobile phone switched off!)*

Browser "fingerprint" techniques? Solved by using a Live CD/USB of a distro you don't normally use - User Agent won't match your usual surfing - browser variables cloaked with NoScript add-on - live boot leaves no trace afterwards.

MAC address? Hotspot access can't be tied to your laptop if you change the network adaptor address?

Is there anything else I've missed? Does that just about cover it? Thanks :)

---

### Post by cariboo on 2010-01-29
Here's a really radical idea, why not talk to your friend face to face in your, or his home. You always leave a foot print of some sort when you are on the internet.

---

### Post by openfly on 2010-01-29
There's plenty of methods for guessing what and where you might be based on a small amount of information being available.  

Personally I'm of the mindset that to avoid detection the best approach is not stealth, but deafening loads of false data / noise.

So throw up some flak.

---

### Post by tubbygweilo on 2010-01-29
Here's another really radical idea, why hide behind the cloak of anonymity? You can stand up an be counted by posting under your own name and this will assure others that you have the courage of your convictions. Far, far  better than hiding behind seven proxies...

---

### Post by bit mad on 2010-01-29
I know, I know... :P

But it's a technical question more than anything. I don't need to do anything dodgy online. I'm just interested in the theory & practicalities of how traceable we are, and curious about the hypothetical scenario.... 

if you *really* needed to post a forum message somewhere with no potential fallout *(because it might cost you your job or whatever)  *would what I described be enough?

Say you lived in some crummy country under a repressive regime *(that somehow allowed wifi hotspots in coffee shops!)* and you really wanted to get some information out into the world without disappearing into the saltmines never to be seen again...? :)

---

### Post by __p1n__ on 2010-01-29
Check out the experience of Evan Ratcliff:

[http://www.wired.com/vanish/2009/11/ff_vanish2/](http://www.wired.com/vanish/2009/11/ff_vanish2/)

---

### Post by bit mad on 2010-02-01
There's probably an easier way to get a new random MAC address but I felt the need to write a quick-n-dirty script for the challenge of it.

This seems to do the trick
```
#!/bin/bash

hex="0123456789ABCDEF"

function random_res(){
res=""
for lc in "1" "2" "3" "4" "5" "6" "1" "t" "3" "4" "5" "6"  # 12 :)
do
 if [ $lc == "2" ]; then   # can't have address with odd second char
  res=$res${hex:((RANDOM %8) *2):1}  # even digits only
 else
  res=$res${hex:(RANDOM %16):1}  # I'm Bit Mad
 fi
done
# res(ult) string will 12 random hex nums - now insert some ":"
res=${res:0:2}:${res:2:2}:${res:4:2}:${res:6:2}:${res:8:2}:${res:10:2}
}


random_res
new_eth0=$res
random_res
new_wlan0=$res

echo $new_eth0
echo $new_wlan0

sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo ifconfig eth0 hw ether $new_eth0
sudo ifconfig wlan0 hw ether $new_wlan0
sudo ifconfig eth0 up
sudo ifconfig wlan0 up

ifconfig

echo Press Enter
read a

```

---

