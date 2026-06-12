---
title: "How to perform a WPA crack on Ubuntu"
date: 2010-08-22
forum: Security
---

### Post by sanhedrin on 2010-08-22
My good friend has asked me to help him out and access his WPA key on his wireless router.  There are several things plugged into it already and I have tried to unplug it but he refuses to let me do so.  Therefore, he asked me to do it remotely with my laptop.

I need to patch my wifi card into the system - How would I do this?
Since this is my first real experience with Ubuntu, I am not too sure how to go about this task.  Please help me if you can :p.

Andrew.

---

### Post by Zzl1xndd on 2010-08-22
rather then attempting to crack the WPA password, wouldn't it be easier to log in with a machine that is connected to the router and just change the settings as needed? 

Although if you do need to crack it you might want to check out 

[http://aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=2535ce58ae914ab3415d4133117de40d](http://aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=2535ce58ae914ab3415d4133117de40d)

---

### Post by sanhedrin on 2010-08-22
> **tweakedenigma said:**
> rather then attempting to crack the WPA password, wouldn't it be easier to log in with a machine that is connected to the router and just change the settings as needed? 

Although if you do need to crack it you might want to check out 

[http://aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=2535ce58ae914ab3415d4133117de40d](http://aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=2535ce58ae914ab3415d4133117de40d)

Thanks for the link!  And...

Yes, it would be, if he had remembered what the login for the router was.  It is no longer the original admin password.  It was changed and he doesn't remember that either...which is why this is an enigma on my part.  No pun intended on your sn.

---

### Post by Zzl1xndd on 2010-08-22
If that is the case I would simply reset the router. Most have a small button (normally need a pin or something to hit it) on the back that will reset all settings to factory. Best to start from scratch and have full control of the router.

---

### Post by sanhedrin on 2010-08-22
Good point.  I shoulda thought of that...

---

### Post by anewguy on 2010-08-22
Resetting the router would be best.  Just remember that for any other machines that connect will need to know what ever you choose for a new WPA password/passphrase (since you apparently don't know the existing one).

Although I'm sure we can point you to off-site links for cracking, a search of the net would do just as good.  I don't know the forum rules on this, but my personal view is to not provide such tools and instead let the OP find them themselves.  Why?  The request may be legitimate, or it may not.  But providing them with the tools also provides any one out there with the tools, and just me personally don't think that's a good thing.

Any way, if you're using WPA, why not go to WPA2-AES/PSK (I think that's what it's called) and add MAC filtering on the router.  I *think* that provides about as much security as you can on the router for the wireless side.

Dave

---

### Post by Ernie S. on 2010-09-19
You can also disable essid bradcasting or "cloak" the router. This could be problematic if there are alot of ap's in the area AND the owners of those ap's know and care enough about channel separation, as they wouldn't be able to see your friend's router to know what chennel it's on, but I don't think most people know/care enough about seting up their ap's to segregate them for best throughput. Just my 2c.
Cheers

---

### Post by bodhi.zazen on 2010-09-19
Moved to the security section.

---

### Post by rhigmus on 2010-09-20
> **anewguy said:**
> [...]and add MAC filtering on the router.  I *think* that provides about as much security as you can on the router for the wireless side.

While this may seem like a good idea, there really isn't any added 'layer' of security from doing this. MAC ACL's may prevent a little scriptkiddie out, but an experienced cracker can spoof a mac quickly and easily. 

From my own experience I will point out also that MAC ACL's are really flippin annoying, because every time one of your friends, friend's friend, sister/brother's friend or parents (or whatever!) add a new device then its time for you to go to work :mad:.

> **Ernie S. said:**
> You can also disable essid bradcasting or "cloak" the router.

Also mildly pointless for security since wardrivers/wifi-scanners can pick this out too. In fact WinXP has this great "feature" that broadcasts SSID's in plaintext when connected to "cloaked" networks. Why were you cloaked again?

---

### Post by Ernie S. on 2010-09-20
You are right, it is security through obscurity and pointless if you were trying to keep people out of your ap at a hackercon. But for the average neighborhood, i.e. I want to keep my neighbor's kid from downloading a bunch of porn on my bandwidth, it works most of the time. I'm not saying someone should rely on cloaking as a sole means of security. Just realize though that the people in this forum are *much* more knowledgeable than your average windoze zombie. As an example the neighborhood I just moved in to has 6 ap's within range of my laptop and all but 1 are WEP. The one that isn't is OPEN! I'm actually debating how to approach my new neighbors without them getting paranoid and suspicious of me.

---

### Post by aBaldrich on 2010-09-20
Just be careful and don't crack somebody else's WAP ;)

---

### Post by niteshifter on 2010-09-21
> **Ernie S. said:**
> ... if you were trying to keep people out of your ap at a hackercon. But for the average neighborhood, i.e. I want to keep my neighbor's kid from downloading a bunch of porn on my bandwidth, ...

Might not be as much of a difference as you think ;)

I was the very first to operate a wireless AP in my neighborhood several years back. Now: There are many APs, some secured, some not. I see from analysis of my kismet logs many, many attempts at intrusion - not mere innocent attempts to connect, but serious attempts at intruding (packet injections, for example). The open APs get hammered.

Change the key frequently and at random times is a good defense.

If the router is hackable (like older Linksys WRT54's or WRT54GL) dialing down the transmit power is helpful.

> **Ernie S. said:**
> ... As an example the neighborhood I just moved in to has 6 ap's withn range of my laptop and all but 1 are WEP. The one that isn't is OPEN! I'm actually debating how to approach my new neighbors without them getting paranoid and suspicious of me.

Good luck. Been there, done that. Didn't work.

---

