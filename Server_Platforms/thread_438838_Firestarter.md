---
title: "Firestarter"
date: 2007-05-10
forum: Server Platforms
---

### Post by mandela on 2007-05-10
Hello ppl! I'm just a bit puzzled. I read everywhere that it isn't all that necessary to run an antivirus or firewall on Linux Os (including Ubuntu) but I do run the firestarter firewall and on checking the events menu where it shows list of blocked connections ( and my oh my..its a very long list)! what does that mean, that someone is trying to break into my system? if yes then what happens if I don't run the firestarter? and under inbound, it shows 1 serious event.

---

### Post by rbalfour on 2007-05-10
This all depends on how you have you network setup. Is your computer connected directly to the internet 'pppoe' or dialup?

and what is the serious event? Can post more info.

---

### Post by mandela on 2007-05-10
> **rbalfour said:**
> This all depends on how you have you network setup. Is your computer connected directly to the internet 'pppoe' or dialup?

and what is the serious event? Can post more info.

its connected to the 'pppoe'

---

### Post by rich.bradshaw on 2007-05-10
That's just people bouncing off you - no need to worry - by default nothing is "open" anyway, so all firestarter is doing is showing you the connections that are attempting to connect to nothing.

If you want to easily stop people attempting to connect multiple times then:

sudo apt-get install fail2ban

this bans people who attempt to connect without the correct password multiple times for a few mins, stopping bruteforce attempts to connect.

As I said though, unless you are running ssh, apache, vino (or any vnc) etc then you don't have to worry. You will know if you have decided to run these services!

---

### Post by mandela on 2007-05-10
> **rich.bradshaw said:**
> That's just people bouncing off you - no need to worry - by default nothing is "open" anyway, so all firestarter is doing is showing you the connections that are attempting to connect to nothing.

meaning that someone is actually trying to connect to my computer right..to cause damage? are you saying that I dont need to run firestarter at all? 

I'm not running apache, vino etc...

---

### Post by rbalfour on 2007-05-10
> **mandela said:**
> meaning that someone is actually trying to connect to my computer right..to cause damage? are you saying that I dont need to run firestarter at all? 

I'm not running apache, vino etc...

Well, if it's pppoe, then yes. Someone is trying, but most likely it's some bot scanning whole ranges.
Keep the firewall up and you'll be okay.

---

### Post by mandela on 2007-05-11
> **rich.bradshaw said:**
> If you want to easily stop people attempting to connect multiple times then:
sudo apt-get install fail2ban

I have installed the package..but do I have to run it all the time and how do I run it if I have to. Thankx

---

