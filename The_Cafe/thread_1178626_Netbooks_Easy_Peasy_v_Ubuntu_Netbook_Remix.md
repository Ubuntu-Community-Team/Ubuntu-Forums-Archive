---
title: "Netbooks: Easy Peasy v Ubuntu Netbook Remix"
date: 2009-06-04
forum: The Cafe
---

### Post by mr-woof on 2009-06-04
lo all,

I'm currently using easy peasy on my eee900 and I honestly thought that was the ubuntu netbook remix until i actually looked for it on google ;)

What's the difference between the two? I'm just trying to get unetbootin to create me a live usb stick without much luck

---

### Post by snowpine on 2009-06-04
Easy Peasy is an unofficial Ubuntu "remix" designed specifically for the eee pc.

Ubuntu Netbook Remix is an official version of Ubuntu with a special interface designed for small screens (lots of big icons instead of a traditional "desktop"). It will not work with Unetbootin; you need to follow these instructions: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by LowSky on 2009-06-04
EP was originally designed around the EeePC unsing Ubuntu, while Ubuntu remix was designed around the Intel Atom processor that most Netbooks use, basically a more generic version of Easy Peasy. 

Other than that EP has apps like skype already installed, whereas Ubuntu need to install them because of the Ubuntu philosophy on hardware.

[http://en.wikipedia.org/wiki/Easy_Peasy](http://en.wikipedia.org/wiki/Easy_Peasy)

---

### Post by mr-woof on 2009-06-04
Hmm interesting, I'll have a look at that link cheers

So the next question then, which one is the best? I really like the interface in easy peasy, nice and easy on the eye

---

### Post by snowpine on 2009-06-04
> **LowSky said:**
> EP was originally designed around the EeePC unsing Ubuntu, while Ubuntu remix was designed around the Intel Atom processor that most Netbooks use, basically a more generic version of Easy Peasy.

Just a correction, Ubuntu Netbook Remix does NOT use the lpia kernel optimized for the Intel Atom processor. It uses the 'generic' i386 kernel that supports a much wider range of processors (including the Atom, of course). My theory is they originally considered using the lpia (low-power intel architecture) kernel but then realized that many, many netbooks (including the original Asus eee pc 700 series!) do not have Atom processors and therefore would not be supported. 

I have not used Easy Peasy, so I have no opinion which is "better," but if Easy Peasy is working great for you, why change? :)

---

### Post by drawkcab on 2009-06-04
neither / nor

eeebuntu is the way to go

---

### Post by LowSky on 2009-06-04
> **snowpine said:**
> Just a correction, Ubuntu Netbook Remix does NOT use the lpia kernel optimized for the Intel Atom processor.  


I'm pretty sure you can install the lpia kernel from synaptic... hmm need to check...

---

### Post by snowpine on 2009-06-04
> **LowSky said:**
> I'm pretty sure you can install the lpia kernel from synaptic... hmm need to check...

Negative, lpia is a separate, from scratch install (since i386 packages are not compatible with the lpia kernel, and vice versa).

[http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso](http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso)

I have tested Ubuntu lpia and do NOT recommend it... It would be my last choice behind "regular" i386 Ubuntu/Ubuntu Netbook Remix, Easy Peasy, Eeebuntu, Cruncheee, etc.

I'm of the "ain't broke, don't fix it" school, and Easy Peasy seems to be working fine for the OP.

---

### Post by don_quixote on 2009-06-04
> **drawkcab said:**
> neither / nor

eeebuntu is the way to go

Until Moblin is stable, that is.

---

### Post by t0p on 2009-06-04
Hmm... I'm currently using NBR on my Eee PC 701.  I hadn't heard of easy peasy until I read this thread.

I think NBR is quite a nice netbook OS.  It's good old Ubuntu, but with a GUI that goes very nicely on the Eee's little screen.  But now I learn that easy peasy is actually designed with the Eee in mind.  Ooh, what a dilemma... carry on with NBR or check out easy peasy...

I think I'm gonna go google up easy peasy's home page and have a look what's what.  Cheers for the heads-up, peeps!

---

### Post by CJ Master on 2009-06-04
> **drawkcab said:**
> neither / nor

eeebuntu is the way to go

eeebuntu IS Easy Peasy...;)

---

### Post by wmcbrine on 2009-06-04
> **CJ Master said:**
> eeebuntu IS Easy Peasy...;)No... Ubuntu Eee became Easy Peasy. Eeebuntu and Ubuntu Eee are different.

---

### Post by CJ Master on 2009-06-04
> **wmcbrine said:**
> No... Ubuntu Eee became Easy Peasy. Eeebuntu and Ubuntu Eee are different.

Ah, my mistake.

---

### Post by mr-woof on 2009-06-05
also while we are talking about the different buntu netbook distro's, you can't forget crunchbang. I've got it installed on a 4gb sd card in my eee900 and it's very nice, works really well. 

I plan to stick UNR on a usb stick tonight and have a play about with it

---

### Post by rulk on 2009-08-31
I have 2 EeePC 900's and 1 900a.

I have tried Easy Peasy, eeeubuntu and NBR...

NBR works great on the 900a but had real issues with the graphics when run on the 900 Eeepc's. It also did not have the task bar stuff on the top like the 900a did. (Switch programs or maximize/minimize programs etc.)

Easy peasy 1.1 worked as well as the NBR version on the 900's but is based off Ubuntu 8.10. 

I have Eeebuntu Standard running and it works as well on my 900's as the UBR does on the 900a. With the latest upgrade of the NBR distribution however it appears the Graphics performance has improved. I still do not see the task bar on top of the 900 computers as I do on the 900a...

Going to download and try the Eeebuntu NBR version and see if it fixes the task bar issues. I use these netbooks as my internet portals when I am at work. I teather them to my phone and use them on breaks and such where rapid booting is important and I don't need the full power of a desktop/laptop.   

The Eeebuntu standard looses some screen realestate when you compare to the Ubuntu NBR. Things that are combined in one line on the NBR versions are done on seperate lines on the standard version.

If the task bar issue is resolved in the Ubuntu NBR with my 900 I will likely use it as it is the most recent and best supported version out there.

---

### Post by speedwell68 on 2009-08-31
I have used both on my Acer One A150 and really couldn't find a lot between the two.  I have finally settled on stock install of Xubuntu 9.04, it is a brilliant netbook OS.  I have also run Xubuntu on a Asus EeePC 701 and it works a treat on there too.

---

