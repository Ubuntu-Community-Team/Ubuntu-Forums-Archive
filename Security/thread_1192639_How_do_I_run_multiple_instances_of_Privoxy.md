---
title: "How do I run multiple instances of Privoxy?"
date: 2009-06-20
forum: Security
---

### Post by kyfho23 on 2009-06-20
Hello, all
I've set up Privoxy/Tor, and it seems to be running fine. I've even used Vidalia to set up a Tor relay. 
My question is: How do I set up another instance of Privoxy ( or another config file) to use without Tor? I want to have another Privoxy just for blocking ads, without the Tor relay.
I'm not sure if I need a whole instance of Privoxy, or just another config file. But I'd like to have both options available at startup, if possible.

Thanks
Chris

---

### Post by kyfho23 on 2009-06-20
Found the answer here: [https://wiki.torproject.org/noreply/TheOnionRouter/RunTwoPrivoxys](https://wiki.torproject.org/noreply/TheOnionRouter/RunTwoPrivoxys)

after you've finished the directions there, you also have to create a new executable: sudo cp -a /usr/sbin/privoxy /usr/sbin/privoxy2

---

### Post by Dr Small on 2009-06-20
That to me seems the hard way. Probably just creating a new config file, and a new init file that uses the new config file would work.

---

### Post by Axel Mak on 2011-05-08
.

---

### Post by HunterThomson on 2011-11-08
> **Dr Small said:**
> That to me seems the hard way. Probably just creating a new config file, and a new init file that uses the new config file would work.

Nope, I tried it every which way. You have to copy the binary.

```
sudo cp /usr/sbin/privoxy /usr/sbin/privoxy2
```

What I did was setup one privoxy proxy that connects to the internet directly and uses the AdBlock Pluss EasyList lists. On Archlinux I installed the privoxy-blocklist script from the AUR which converts Adblock Plus blocklist to privoxy format.

Then I setup a second privoxy proxy that also blocks ad's but also forwards though TOR.

---

