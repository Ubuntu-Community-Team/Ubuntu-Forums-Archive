---
title: "Fun with Ubuntu as part of a larger engineering experiment"
date: 2017-05-26
forum: The Cafe
---

### Post by xpeaceservant on 2017-05-26
I would like to say hello again to everyone.  Really appreciate the help I receive here and the community in general.

What I am doing with this old XP machine is attempting to breath a little life back into it.  My goal is to establish a little community radio station using donated goodies, that happens to include using the PC I'm typing from.  A buddy used to use this older machine just for games and kindly donated to my cause.  But knowing the vulnerabilities of Win XP, blah, blah, so I loaded up Ubuntu 14.04 LTS. Low cost is the goal; spent a whopping $150 on the broadcast experiment so far and expect the cost to remain low since I'm not shelling out money for new software, hardware, etc.

One point I'd like to stress is using Ubuntu is all part of this hobby broadcast engineering experiment.  I'm already an amateur radio person (KE0JIT), but that is merely a technical stepping stone to other matters in tech.  Once I get this Ubuntu loaded machine running with just three or four softwares I should be on the air with the flea-powered broadcast station.  The Ubuntu machine will run DJ software, etc. controlling the station and kit-built transmitter.  I guess what is exciting is that this is a great opportunity to learn something new with computers. I always wanted to learn some Linux stuff.  This gives me a must-do reason to learn it.

As a side experiment I will run an old-school bulletin board system with a telnet log-in.  Additionally, I hope learning Ubuntu will aid some minor robotics experimentation I'm working on locally.  That group emphases Raspberry Pi machines and Raspian.

Lastly, as I had stated in a prior thread, I had successfully loaded an Ubuntu flavor onto a small notebook and ran it with no problems.  Once I learn a wee bit more about the Ubuntu OS I plan to give out copies of the flavors with old machines.  I think I can win them over.

Many thanks.

---

### Post by Bucky Ball on 2017-05-26
Sounds great. My advice? Low spec machines, install Xubuntu 16.04 LTS, or better still, Xubuntu-core if you're a little more au fait. This will not only give you a faster experience as Xubuntu is more lightweight. One thing to remember, though, is that Xubuntu LTS releases have three years support, not five, but in your case, no biggy as both Xubuntu 16.04 and Ubuntu 14.04 are out of support in 2019. 

Hope that gets you further up the track. For what you want to do, Ubuntu is a waste of resources. You don't need it. Xubuntu-core will give you the xfce4 desktop and a few default Xubuntu things ONLY. You install the rest. So the machine would basically have the Ubuntu kernel, xfce4 desktop environment and whatever apps you need for radio. A simple, slick, speedy workhorse! ;)

All the best with it. :)

(PS: Ubuntu Studio uses the xfce4 desktop environment by default as it is lightweight and is built on either Xubuntu or a -core version. DON'T install Ubuntu Studio. Although it might contain some of the apps you need, it also has a TON of apps you don't and will never use. Another waste of resources. ;))

---

### Post by xpeaceservant on 2017-05-26
Would I still be able to load up Libre Office on Xubuntu?  I guess I'm not clear on how the install I have drains system resources.  Seems to run ok thus far.  And can I install the Xubuntu 16.04 LTS and have it done as an over-write to the Ubuntu I have now?

---

### Post by Bucky Ball on 2017-05-27
Absolutely everything you can install on Ubuntu is available on Xubuntu, and on any *buntu flavour for that matter.

They all use the same kernel and the same software repositories. ;)

You can do a clean install of Xubuntu in the disk space where you now have Ubuntu, but I wouldn't advise trying to add it to the current install. That won't get rid of bloat, that will add more and you'll end up with Ubuntu and Xubuntu mashed into one install which will include all default apps for both, redundancy and possible conflict. Don't go there.

You could also install Xubuntu on a separate partition and have that solely as your 'Radio Box' install.

PS: Your setup might be running okay now, but I suggest you do a 'real world' test if you haven't. Bring up and run everything you would under heavy studio operating conditions (all apps open you will be using, music playing, mic on and up, headphones happening, etc.) then open a terminal and run this single command:

```
top
```

That will show you how much memory (RAM) and CPU is being consumed. 'htop' gives a bit more information and is 'prettier', but you'll need to install that (sudo apt install htop). You can do a comparison by closing everything so you are just at a desktop and then check 'top'.

---

### Post by gordintoronto on 2017-05-27
+1 for Xubuntu 16.04.

---

### Post by xpeaceservant on 2017-05-29
Ok, going for the Xubuntu 16.04 LTS...
... installing ...

---

### Post by xpeaceservant on 2017-05-29
Oh great. I fumbled the password setting it up.

trying this... [https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

### Post by Bucky Ball on 2017-05-29
Yep, that's the way to do it. You should get back in once you've achieved that. Let us know (and write down the password!). :)

---

### Post by xpeaceservant on 2017-05-30
I fixed that.

So I'm pleased enough with Xubuntu and the whole PC system I have it installed on that I've moved it home. Built a small shelf to hold the monitor, etc. and have it all set up!

---

### Post by xpeaceservant on 2017-06-01
I'm quickly coming to the conclusion that an Ubuntu/Xubuntu how-to book will be helpful.

---

