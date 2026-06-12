---
title: "Pangolin Performance"
date: 2010-03-24
forum: System76 Support
---

### Post by bgrohe on 2010-03-24
I have been interested in the Pangolin Performance but I have a few main concerns:

1: How long does the battery last (I heard about 2 hours) and is there any 9 cell batterys available. even from a third party? 

2: How does the i5 core perform?

3: Has anyone tweaked there computer to get better battery life.

4: Has anyone tested it with 10.04

5: What is the range of the WIFI

6: How well does the bluetooth work?

---

### Post by isantop on 2010-03-24
bgrohe:

In our testing environment, we do get about 2 hours on the Pangolin battery. I also own one myself (the most recent, the panp7) and I always get at least 90 minutes off of one charge. I'm sure there are things you can do to increase battery life, such as throttling/slowing down the CPU and reducing the screen brightness when running on battery. Good battery care will also help preserve the life of any rechargeable battery too, so always use a full charge cycle (no partial charges), don't run the computer on AC with a fully charged battery, and run the battery down to about 10% or so before plugging it in again.

Based on personal experience, I can get about 100-200 feet from my Pangolin wireless card.

In my opinion, the Bluetooth works well. I have connected mine to both a wireless mouse and my cell phone with no major trouble.

The core i5 is a good match for the rest of the hardware in this computer. I use my computer all the time, and it is always providing more power than I need. You can also adjust the clock speed to control both temperature and noise by simply pressing a button next to the keyboard.

I haven't personally tested my computer with Lucid yet, but I may soon, and we are set to test it in-house as well. I do know a couple of people who have used lucid on their pangolins, and from what I have heard, it works quite well. Needless to say, we will support 10.04 on the pangolin when it is released next month, and installing it on an existing system will not void your warranty or disqualify you for tech support. 

If you have any other questions, feel free to ask about them. :)

---

### Post by bgrohe on 2010-03-25
Thanks you have answered most of my questions:D, but I was wondering if there were any larger batteries available. and I heard that the placement of the mic is near the touch pad rather than the webcam. Is this true? Also what happened to the Darter Ultra? Is it being refreshed or being discontinued? 
Thanks is advance.

---

### Post by samalex on 2010-03-26
I have the PanP5 which was out last summer, but I think the specs are close enough between my system and the PanP7 for me to also put in some comments about your questions.

1: How long does the battery last (I heard about 2 hours) and is there any 9 cell batterys available. even from a third party? 

As others have stated 90 minutes is pretty much par for the course, though I've gotten almost two hours a few times with some tweaks like lower screen brightness and so forth.  Unfortunately last time I checked there was no 9 cell battery available.

3: Has anyone tweaked there computer to get better battery life.

Linux automatically scales CPU utilization so you can tweak that, which is what I do to help increase battery life.  There's a Gnome add-in I run that lets me set each CPU Core to On Demand or to only run at say 800Mhz to conserve power.  Doing this along with lowering the display brightness, not using CD-ROM, and even disabling the wifi card (if network is unneeded) can definitely increase battery life.

4: Has anyone tested it with 10.04

I'm testing 10.04 but it's via VirtualBox.  It works pretty well and I plan on doing a clean install when it's released since I'm still running Jaunty which shipped with my laptop.

5: What is the range of the WIFI

I've never tested this per say, but I've gone WAY far from my wireless router and it always works.  Also in our apartment I pick-up about 8 wireless routers, most of them pretty strong, and I know for sure one is in another building which is more then a stones throw away.  So I'd say it's pretty good.

6: How well does the bluetooth work?

VERY well.  I've connected numerous cell phones to download content, plus I've setup a bluetooth network between my PanP5 and my wife's iBook when I accidentally uninstalled some packages that were required for networking.  I was very impressed how easy it was to configure and how well it worked.

Also outside of your questions the computer works great when connected to an HDTV television.  We watch LOTS of shows via Hulu on our TV, though I use VGA instead of HDMI since Jaunty has some problems with audio over HDMI which are supposedly fixed in 9.10.  

The webcam works great, but the onboard mic isn't the best.  For Skype I'd recommend using an external microphone.  

Anyway just some thoughts ...

Sam

---

### Post by nobodysbusiness on 2010-03-29
> **samalex said:**
> There's a Gnome add-in I run that lets me set each CPU Core to On Demand or to only run at say 800Mhz to conserve power.

What's the name of the Gnome utility? I'd like to try it out.

---

### Post by satsujinka on 2010-03-29
For battery life you may also wish to try an environment that has less things going on (such as xfce or lxde.) There's also a program called powertop that will tell you what's eating up your cycles (and thus power.)

---

### Post by thomasaaron on 2010-03-30
> I was wondering if there were any larger batteries available.

There are no other batteries available for this model.

---

### Post by edwinbmiller on 2010-04-06
clevo w765cuh has 9 cell factory option

i'm pretty sure the pangolin is a repackaged clevo 765cuh/sager np7652

[http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=232#](http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=232#)

---

### Post by samalex on 2010-04-07
> **nobodysbusiness said:**
> What's the name of the Gnome utility? I'd like to try it out.

Sorry, week late and i just saw your note ...  The utility I was referring to is actually an add-on to the Gnome panel called CPU Frequency Scaling Monitor.  I have two of them on my panel, one per processor, and they show the current state of each processor.  Plus to update it I can just click on each and increase, decrease, or change the performance level.  

Normally if I'm on battery I'll kick it down to either 800Mhz or PowerSave mode, but if on power I'll bump both up to full 2.53ghz especially if I'm running VBox or other intense apps.

Take care --

Sam

---

### Post by linusr on 2010-04-07
> **samalex said:**
> 
The webcam works great, but the onboard mic isn't the best.  For Skype I'd recommend using an external microphone.  
Sam

mic issue or alsa/pulse audio issue? Dell/HP laptops had same mic issue (very low volume) in Ubuntu

---

### Post by eddietours on 2010-04-07
i would like to ask is this model here for the next few months i would hate to buy and the next think is there a new model coming out

---

### Post by thomasaaron on 2010-04-08
Yes, this model (the PanP7) is fairly new. It won't be going away for a while.

---

### Post by eddietours on 2010-04-08
Thanks good to know :)

---

### Post by nobodysbusiness on 2010-04-09
> **edwinbmiller said:**
> clevo w765cuh has 9 cell factory option

i'm pretty sure the pangolin is a repackaged clevo 765cuh/sager np7652

[http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=232#](http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=232#)

Hey, that's some good info. Do you think that it's possible for one of us to order one of those 9-cell batteries from Clevo? Depending on cost, I might be willing to try being the guinea-pig in this experiment. I'd love to get a 9-cell battery.

---

### Post by bgrohe on 2010-04-10
> **nobodysbusiness said:**
> Hey, that's some good info. Do you think that it's possible for one of us to order one of those 9-cell batteries from Clevo? Depending on cost, I might be willing to try being the guinea-pig in this experiment. I'd love to get a 9-cell battery.

Can someone from System76 Confirm this?

---

### Post by Eldera on 2010-04-10
Thomasaaron can probably give you official and more up to date information Monday. However, a long time ago (a year ago last February) someone spotted a 9-cell battery listed on a Clevo spec sheet and when everybody started following through, it was not available. Just a false listing. :confused: 

[http://ubuntuforums.org/showthread.php?t=1077772&highlight=Battery](http://ubuntuforums.org/showthread.php?t=1077772&highlight=Battery)

Wouldn't it be great if Tom could tell us that my information is way out of date? This is one case where I would love to be wrong. Eldera

---

### Post by nobodysbusiness on 2010-04-11
I checked the bottom of my Pangolin, and it seems to be a W76CU model. I sent Clevo an e-mail about the 9-cell battery. I'll let you know if I learn anything.

---

### Post by ranjan_mg on 2010-04-20
I have a pangolin6 laptop. I tried the latest live CD of lucid.

I found a couple of issues

1) Sound preferences does not recognise internal microphone
2) closing the lid does not suspend. screen turns blank even though power options are set to suspend.

---

### Post by isantop on 2010-04-20
I can confirm that this issue is not a problem in Lucid Beta 2 on Pangolin Performance 7 (PanP7) systems. I'm not sure on a solution for the PanP6's out there, but it may be ironed out by the time it's released.

---

