---
title: "How-to block firefox for a few hours"
date: 2007-08-01
forum: The Cafe
---

### Post by norman_ on 2007-08-01
Hi all

So here's my problem. How do I block firefox for a few hours so that I won't go surfing (like now) and avoid working on my things? My productivity is really decreasing and I have absolutely no will power...

Thanks in advance!

Vince

---

### Post by WastingBody on 2007-08-01
Disconnect from the internet?

---

### Post by Nikron on 2007-08-01
sudo ifconfig eth0 down && sleep 3h && sudo ifconfig eth0 up

---

### Post by DoctorMO on 2007-08-01
If your productivity requires the internet you could just block port 80 in iptables or do what I do and use hosts.conf to point all those bad sites at my local ip; any time I try and visit groklaw or theregister I'm pointed back to my work :-)

---

### Post by matthinckley on 2007-08-01
you could set up access rules in your router.. linksys routers have policies you can set up so you can block internet access certain hours of the day.. I run Tomato firmware and it has very useful features that do stuff like that

---

### Post by bread eyes on 2007-08-01
Get more will power.

---

### Post by tcpip4lyfe on 2007-08-02
Sudo apt-get remove firefox

---

### Post by swoll1980 on 2007-08-02
> **bread eyes said:**
> Get more will power.

addictions are what they are. easy to start hard to stop. surely you have at least one drinking, smoking, food, sex, working on a car,  Jesus. His addiction to the internet are no different than yours

---

### Post by ~LoKe on 2007-08-02
If you can't restrain yourself, then anything you put in place to do so will only fail.

---

### Post by RomeReactor on 2007-08-02
Hi. The downside to setting up your own restrictions is that, when your  urge to open Firefox and browse a few sites reaches a certain level, you could very well find yourself bypassing the restrictions you set up earlier. Resisting that temptation is very hard to do, and I know no amount of sympathy will make you more productive or feel any better about it. My recommendation is to try and make your work environment a little more interesting, so you don't wander off--so to speak--to other activities; try listening to your favorite music while at work, remember to take a few breaks so it doesn't become too stressful or tedious.

I know this is all very basic advice, and you didn't ask for it, and maybe you're already doing all of this, or you've tried it before; I don't know. Just posted this in the hopes of trying to offer a bit of help. Addiction to the internet is very serious indeed, particularly when it interferes with relationships and work.

---

### Post by curuxz on 2007-08-02
> **Nikron said:**
> sudo ifconfig eth0 down && sleep 3h && sudo ifconfig eth0 up

that is such a cool command, never thought of using the sleep thing like that! HA, all sorts of fun could be had making people do this :D

---

### Post by bobbocanfly on 2007-08-02
> **tcpip4lyfe said:**
> Sudo apt-get remove firefox


Or even better:

```
sudo apt-get remove firefox && sleep 3H &&sudo apt-get install firefox
```

---

### Post by bvanaerde on 2007-08-02
> **bobbocanfly said:**
> Or even better:

```
sudo apt-get remove firefox && sleep 3H &&sudo apt-get install firefox
```

Are you sure this is possible? After 3 hours, you will surely be asked to enter your password again, right? I'm tempted to try it out though :)

---

### Post by bobbocanfly on 2007-08-02
> **bvanaerde said:**
> Are you sure this is possible? After 3 hours, you will surely be asked to enter your password again, right? I'm tempted to try it out though :)
I have absolutely no idea though i think it should work :D Just thought id post it to see if anyone was mental enough to give it a go. Might try it on conky or something a little less critical than firefox when i get back from work.

---

### Post by Martje_001 on 2007-08-02
You have to put in in a script.

```
#! /bin/bash
sudo ifconfig eth0 down && sleep 3h && sudo ifconfig eth0 up
```

save it an run it:
```
./script &
```
Now close the terminal...

---

### Post by %hMa@?b&lt;C on 2007-08-02
wow, clever usage of sleep.  never really envisioned using it like that.

---

### Post by bread eyes on 2007-08-02
> **swoll1980 said:**
> addictions are what they are. easy to start hard to stop. surely you have at least one drinking, smoking, food, sex, working on a car,  Jesus. His addiction to the internet are no different than yours

Actually I can't think of any.

---

### Post by vambo on 2007-08-02
> **norman_ said:**
> Hi all

So here's my problem. How do I block firefox for a few hours so that I won't go surfing (like now) and avoid working on my things? My productivity is really decreasing and I have absolutely no will power...

Thanks in advance!

Vince


```
sudo apt-get install willpower
```

:)

---

### Post by sailor2001 on 2007-08-02
sudo apt-get remove week-will person

---

### Post by ThinkBuntu on 2007-08-02
Spend a few minutes in Craigslist's Rants n Raves. Either your productivity will go through the floor, or you'll be so disgusted by the internet that you'll steer clear of it for a long time.

---

### Post by forrestcupp on 2007-08-02
> **Nikron said:**
> sudo ifconfig eth0 down && sleep 3h && sudo ifconfig eth0 up

Everyone is raving about your idea, but your sig says "Disregard anything I post."

---

### Post by picpak on 2007-08-02
Well, the topic clearly says "How-to block firefox for a few hours", so why not try:

```
sudo chmod -x /usr/bin/firefox && sleep 3h && sudo chmod +x /usr/bin/firefox
```

That will prevent Firefox from being able to open, and then let you be able to open it again in three hours.

---

