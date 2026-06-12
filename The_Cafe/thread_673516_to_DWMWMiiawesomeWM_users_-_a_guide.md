---
title: "to DWM/WMii/awesomeWM users - a guide?"
date: 2008-01-20
forum: The Cafe
---

### Post by shearn89 on 2008-01-20
I had a pm from Fedex1993, asking for me to write a guide to awesomewm. I think this is a good idea, although i haven't done loads of searching on the forums already. I just wanted to throw out the question to anyone who uses it (or any of its parent WMs) - what do you think i should include?
I figured:

basic installation
customisation
the .awesomerc file
tags
some useful keybindings i use

not sure how to integrate it with gdm, as i don't use it, but someone who's installing a tiling wm is probably a light-n-fast type person and has already ditched gdm/kdm right? If not, someone else may have to write that section...


Any ideas/feedback/ridicule appreciated!

---

### Post by Tenken on 2008-01-20
This is a great idea, I just started messing around with awesome today and the learning curve it pretty high.

As for a login manager I used [SLiM]("http://packages.ubuntu.com/gutsy/x11/slim"), it works by reading your ~/.xinitrc file. so just add

```
exec awesome
```

---

### Post by shearn89 on 2008-01-21
yeah - slim is good, and (with splashy) provides quite a nice light graphical start to things.

I'll write up what i know either this afternoon or sometime tomorrow, and then post it here as a first draft before submitting it to the Tutorials forum.

---

### Post by fuscia on 2008-01-21
it might be good to include some introduction to the concept of tiling wm's, as most people are probably coming from the usual float style wm/DE's.

---

### Post by mali2297 on 2008-01-21
Good idea, the awesome window manager needs better documentation.

Don't forget to tell which version (2.0?) that the guide covers. The configuration file format seems to change with each version.

---

### Post by fuscia on 2008-01-21
there is already a pretty good guide available for wmii - [http://www.suckless.org/wiki/wmii/docs/guide](http://www.suckless.org/wiki/wmii/docs/guide)

---

### Post by Gigamo on 2008-01-21
I find this a very good idea. It will sure help more people get it up and running as I myself wouldn't have been able to learn it on myself.

---

### Post by corney91 on 2008-01-21
Brilliant idea - I look forward to it. I've had Awesome installed for ages but haven't had time to sort customizing out.

---

### Post by herbster on 2008-01-21
I could really use this. I love flux and open so much but always want to give other options a fair shot as I never know what I'll end up liking maybe even more. However, awesome is a bit mysterious. Perhaps you could include dzen2 setup/config in the guide as well, if you are a user/versed with it.

---

### Post by shearn89 on 2008-01-21
Cool. Thanks for all the feedback so far - expect a first draft in the next few days (possibly tomorrow)!

---

### Post by Lostincyberspace on 2008-01-21
once you get it up I will follow it through to see if it works correctly and then try to make as many mistakes because of being vague as possible.

---

### Post by shearn89 on 2008-01-22
UPDATE: I've submitted it to the Tutorials section of the forum. Hopefully it will be okay'd, and I can get you guys to do a quick check over for me... I can post a copy as a text file here if you want a sneaky preview...

---

### Post by shearn89 on 2008-01-23
UPDATE 2: Approved! Link here:
[http://ubuntuforums.org/showthread.php?t=675292](http://ubuntuforums.org/showthread.php?t=675292)

---

### Post by Onyros on 2008-01-23
Count me in, I'm getting my hands dirty on v2.1 right now, configuring it to my liking and drooling at the Fibonacci spiral. Now I can get perfection on my desktop as well. :P

---

### Post by shearn89 on 2008-01-23
I just tried to compile 2.1 and keep getting an error. Something about "no rule to make target awesome.1"

apart from that, i think its all good.

---

### Post by rjmdomingo2003 on 2008-01-23
I've tried wmii but have kept coming back to flux. I am eager to dive into awesome.

I saw your guide and would try awesomeWM ASAP!

You could include a Troubleshooting section for when Mr. Murphy comes up.:)

---

### Post by shearn89 on 2008-01-23
yeah - i might do. I'm going to go build a VM and try it out myself this afternoon, until then, post any problems here, and i'll try and help work through them.

---

### Post by Gigamo on 2008-01-23
I just posted an addition to your guide for the GDM bit.

---

### Post by rjmdomingo2003 on 2008-01-23
> **shearn89 said:**
> I just tried to compile 2.1 and keep getting an error. Something about "no rule to make target awesome.1"

apart from that, i think its all good.
I'm getting the same error.. What should be done next?

Thanks in advance.

---

### Post by Gigamo on 2008-01-23
> **rjmdomingo2003 said:**
> I'm getting the same error.. What should be done next?

Thanks in advance.

Try reading the README and see which dependencies are needed.

libcairo2-dev is one of them.

---

### Post by rjmdomingo2003 on 2008-01-23
> **Gigamo said:**
> Try reading the README and see which dependencies are needed.

libcairo2-dev is one of them.
Tried apt-get installing however it says that it's already the latest version.

---

### Post by Gigamo on 2008-01-23
> **rjmdomingo2003 said:**
> Tried apt-get installing however it says that it's already the latest version.

I would suggest taking a look at the README in awesome-2.1 folder. It says in there which dependencies you need.

---

