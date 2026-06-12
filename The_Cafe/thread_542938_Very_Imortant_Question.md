---
title: "Very Imortant Question"
date: 2007-09-04
forum: The Cafe
---

### Post by fourthdimension on 2007-09-04
Hey all

I've got a really important question for you:  I have a server in my basement I wanted to set up to host a website for a project I'm working on.  Since I'm new to server security, I figured I'd better do a bit of research on cracking techniques/prevention.  Before I go on, let me say that I am strictly white hat with whatever knowledge I have.  OK, so a few links into my search I found myself in a honey pot.  My questions are:
1)  Did I just set myself up to be viewed as a criminal cracker and legally treated as such?
2)  What can be done to change my ip address and get rid of whatever tracks I left on my computer?
3)  Is there something I haven't thought of yet that I should do?

Thanks a lot.

---

### Post by Dr Small on 2007-09-04
Whitehat is "OK". I am a whitehat hacker myself.
1.) Cracking your own box (if you own it) is not illegal. It is your's, so you can do what you want with it. If you were to gain "unauthorized access" to some other system than your own, then it is considered illegal.

So, I think you are in the safe zone.

2.) You needn't worry about changing your IP address and all, if you are cracking your own box... Just use 127.0.0.1 ;)

3.) Block all open ports except 80, 443, 22 and 21 (HTTP, HTTPS, SSH & FTP).

Dr Small

---

### Post by fourthdimension on 2007-09-04
Thanks for the quick reply!  
Well, I didn't actually crack into anything.  I ended up in an index of some sort with files related to users and admins and passwords and things of that sort, which kind of freaked me out because I navigated to that site looking for ways to protect that information, not access it.  Then I went to click "back" on my browser, but then a phrase caught my eye that said something like "this is a honeypot.  thanks to google and (some other people) for helping out" or something like that.  So even though I wasn't cracking or doing anything illegal, I'm still worried that my information was logged and the site admins think I'm a criminal or something...  I don't know if anything legal could follow since I'm still new to a lot of this, so that's probably what worries me the most.

---

### Post by p_quarles on 2007-09-04
It ultimately depends upon the laws of the country in which you live. In most of the democratic world, possessing knowledge is not a crime. 

Besides, what you're doing is what every (good) sysadmin does: proactive security by figuring out what the bad guys could do to you. It's too common a practice to raise any eyebrows.

---

### Post by Dr Small on 2007-09-04
I wouldn't sweat it. Most likely they won't look you up, but if they do, just tell the truth, and tell them you stumbled across it by accident. If it is freely accessible for the general public on the internet, it can't be illegal...

But if you want to "learn to hack" the safe way (entirely legal), check out [HackThisSite.org](http://hackthissite.org). Lots of good articles, tips and info on there for securing yourself and you can even play missions of hacking basic web applications, all legal.

Dr Small

---

### Post by happysmileman on 2007-09-04
> **Dr Small said:**
> But if you want to "learn to hack" the safe way (entirely legal), check out [HackThisSite.org](http://hackthissite.org). Lots of good articles, tips and info on there for securing yourself and you can even play missions of hacking basic web applications, all legal.

+1 for HackThisSite, there are also a few others (HellboundHackers.org, EnigmaGroup.org) but they tend to be full of "OMG I r t3h 1337" people, in HackThisSite there seem to be a lot more people who are doing it for legal reasons or at least keeping quiet about it and not annoying everyone

---

### Post by Dr Small on 2007-09-04
[quote=happysmileman]... in HackThisSite there seem to be a lot more people who are doing it for legal reasons or at least keeping quiet about it and not annoying everyone[/quote]

Well, no matter where you go, you will always find some 1337 |<|\|0\/\/ 1t 4|_|_z
Hackthissite is just my favorite since I grew up there :p

Dr Small

---

### Post by dentaku65 on 2007-09-04
When you finished to install the server, you can do a tiger check of the vulnerabilities of the machine (Tiger is good for the desktop too)

```
sudo apt-get install tiger
```

The complete test it takes about 1/2 hour
```
sudo tiger -H
```

The -H switch creates an html file with all the report well described


Den

---

