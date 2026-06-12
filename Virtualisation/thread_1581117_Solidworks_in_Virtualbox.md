---
title: "Solidworks in Virtualbox"
date: 2010-09-24
forum: Virtualisation
---

### Post by jwh02017 on 2010-09-24
I've been doing lots of reading on how to run Solidworks in Ubuntu.  As many of you know, this is not a simple thing to accomplish.  Since I'm pretty hard headed, I wanted to give it a try myself.  I just build a new computer with a quad core processor and 8GB of ram... full specs are in the video.  I had pretty good luck as you can see in the video, but for some reason when I try to create a new part solidworks will crash every time.  I have a couple things I'm going to try and a little more testing I need to do to see if it's really "useable".  

I'm a complete newbie when it comes to ubuntu.  As most of you here, I'm sick and tired of micro$oft.  I first installed ubuntu 9.10 around a year ago and I really liked it, but since I had to run CAD/CAM software I was still tied to windows.  So I continued to run windows and just "played" with ubuntu off and on.  About a month ago I installed ubuntu 10.04 and I started doing research on how to run solidworks and cam software in ubuntu.  Since my hardware was about 3-4 years old I decided to build a new computer to give solidworks and ubuntu a real try.  I'm now about 95% completely switched over to ubuntu :):)  Sure solidworks and my CAM software will still have to run in windows while in virtualbox, but I can live with keeping windows caged in a box :)  

Hopefully I can get the bugs worked out of the Solidworks/Virtualbox setup and start using ubuntu full time :):)

I'll keep this thread updated as I make progress.

Here's the video... [http://www.youtube.com/watch?v=uuZqfO4YHn4]("http://www.youtube.com/watch?v=uuZqfO4YHn4")

Justin

---

### Post by dwelshon on 2010-09-26
Any progress?  I have XP and Lucid dual booted on my computer and am trying to do the same thing.  Is it possible to clone my XP partition and run THAT as the virtual machine, since it already has SW, OrCad, MPLAB and some other engineering programs loaded onto it?

---

### Post by jwh02017 on 2010-09-27
> **dwelshon said:**
> Any progress?  I have XP and Lucid dual booted on my computer and am trying to do the same thing.  Is it possible to clone my XP partition and run THAT as the virtual machine, since it already has SW, OrCad, MPLAB and some other engineering programs loaded onto it?I've been busy all weekend so I haven't had much time to play with the setup any more.  Late Friday afternoon I was able to install and run Surfcam which is my CAM software.  I'm also able to save files in solidworks, but I can't create new files yet.  I'm thinking about running the solidworks install again in case something got corrupt during that install.  I don't think you can take your current HDD partition and run it in virtualbox.  At least not that I know of. 

Justin

---

### Post by CrazyCasta on 2011-07-21
By looking in many of the log file it looks like it's an exception caused by the combination of Windows WPF and VBox drivers. According to [http://www.virtualbox.org/ticket/4587](http://www.virtualbox.org/ticket/4587) it might be fixed in 4.1. I haven't had a chance to try 4.1 yet because I'm running some simulations that can't be stopped (terrible program design).

---

### Post by CrazyCasta on 2011-07-22
I can confirm that after upgrading to 4.1.0 and fighting with SolidWorks for another 2 hours or so that it now works. I have no idea what I did, because I started it up 2-3 times and it didn't work. Then when I went to report the error (my way of getting the detailed crash log) it didn't crash (as it had the last 2-3 times I had gotten logs from it). So the good news is, it works. The bad news is, I have no idea how to fix it if it doesn't just work after upgrading to 4.1.0.

---

