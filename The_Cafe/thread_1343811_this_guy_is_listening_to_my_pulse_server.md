---
title: "this guy is listening to my pulse server"
date: 2009-12-02
forum: The Cafe
---

### Post by nerdy_kid on 2009-12-02
so i get on the web, and my internet slows to a freaking crawl -- my router is working its butt off.  i promply shutoff my web server, as its downloading at 150 kbs.  My laptop is uploading at 150 kbs, and a wireshark scan tells me that my laptop is proceding to send my audio over the web to some freaking jerk at  224.0.0.56
?????????????
a brief nmap scan shows nothing, and the IP is not in the whois database.  I am ticked.

---

### Post by mkvnmtr on 2009-12-02
I would like to hear more about this. With more details of what you were doing at the time and what you find about the address.

---

### Post by nerdy_kid on 2009-12-02
i was trying to help somebody out with Xorg issues -- no networking stuff set up, and i did not forward those ports.  I hit the refresh button on the post i was helping, and i realized that i had, in effect, a DOS attack on me.  I changed the username and password (on my router) to something totaly random with special chars.  Im gonna go and unforward those ports, and both my pc are running ufw now.

---

### Post by akudewan on 2009-12-02
Very interesting. Perhaps you could prank this person if it happened again...

---

### Post by RiceMonster on 2009-12-02
Damn it, why'd you shut it off? I was listening to that!

[color=white]In case you didn't figure it out, I'm joking[/color]

---

### Post by nerdy_kid on 2009-12-02
> **akudewan said:**
> Very interesting. Perhaps you could prank this person if it happened again...

yeah :D time to pull out the exploiting books... lol

jk btw i cant hack

---

### Post by nerdy_kid on 2009-12-02
> **ricemonster said:**
> damn it, why'd you shut it off? I was listening to that!

[COLOR=white]in case you didn't figure it out, i'm joking[/COLOR]
lol

oh nice one with the white text!

---

### Post by nerdy_kid on 2009-12-02
this happened yesterday too, i unplugged the router and it fixed it for then...this guy would pay if i could make him!

---

### Post by Sam on 2009-12-02
The 224/8 IP range are multicast addresses. ([http://en.wikipedia.org/wiki/IP_multicast#IP_multicast_addressing_assignments](http://en.wikipedia.org/wiki/IP_multicast#IP_multicast_addressing_assignments))

Run paprefs and disable Multicast/RTP sender.

---

### Post by nerdy_kid on 2009-12-02
yeah i disabled the RTP sender.

> 
The 224/8 IP range are multicast addresses. ([http://en.wikipedia.org/wiki/IP_mult...ng_assignments]("http://en.wikipedia.org/wiki/IP_multicast#IP_multicast_addressing_assignments"))
sorry, but im not the best with networking stuff -- what is multicasting?  what does this imply?

[edit] wikipedia expains that in to complicated terms for noobs like me to understand ;)

---

### Post by phrostbyte on 2009-12-02
It means you are broadcasting a signal to a bunch of computers on your network.

---

### Post by RiceMonster on 2009-12-02
> **nerdy_kid said:**
> yeah i disabled the RTP sender.

sorry, but im not the best with networking stuff -- what is multicasting?  what does this imply?

[edit] wikipedia expains that in to complicated terms for noobs like me to understand ;)

It's a way of sending packets to multiple hosts. Basically in one instance, you'll send a message once that will go out to all of them at the same time, rather than individually sending to each of them.

---

### Post by nerdy_kid on 2009-12-02
> 
It means you are broadcasting a signal to a bunch of computers on your network.


you mean im broadcasting to my own pcs????

wow.

now everyone knows what an idiot i am! *waves* :D

---

