---
title: "Pangolin Fan and Heat Question"
date: 2008-12-26
forum: System76 Support
---

### Post by thetofucube on 2008-12-26
Hello,

I received my new Pangolin yesterday. I've been running it for a couple of hours and I've noticed two things: the system gets hot pretty quickly with very little going on - a web browser and terminal window are open; and the system fan never seems to stop.

I installed the gnome sensor applet to see the machine's running temperature is and I get the following results: CPU 49C, temp1 49C, and GPU 61C. 

CPU usage is about 5%. 

The system is a Pangolin with: a 2.4ghz core 2 duo; 4gb of ram; 320 gb HD; and the stock 8.10 ubuntu which System76 provides.

Is it normal for the system to feel this hot? and is it normal for the fan to always be on? The system is running like my old p4 Inspiron 5100--blowing fans and lots of heat when the CPU is maxed out. In this case, however, the CPU is almost idle.

Please advise.

thanks!

---

### Post by Guille Damke on 2008-12-26
Hi,

I have also noticed that, I think that the web browser (Firefox) forces the computer to run the CPU at high speed. What I have done, is to install the "CPU Frequency Scaling Monitor" (right click in the top bar and 'add to panel'). You have to click on it to change the settings (and give your password to unblock it). The default is set to run it using the "Ondemand" profile, but when I am running Firefox and a few extra applications I usually set it to "Conservative" and the CPU runs slower (and cooler) but the performance is not affected at all. I hope it helps you.

---

### Post by thetofucube on 2008-12-26
Hi Guille,

Thanks for the tip. I will go ahead and try that. I'll write back as soon as I see what happens.

---

### Post by thomasaaron on 2008-12-26
thetofucube,

As CPUs and GPUs go, those temps aren't very hot, and they're a long way from overheating. From a tech support perspective, I'd have to say they're quite normal.

How are you using the computer? Are the heat vents obstructed in any way? Or are you using it on a hard surface?

---

### Post by thetofucube on 2008-12-26
Hi,

I'm using the machine on a hard surface with nothing obstructing the vents. The table's surrounding surface area around the vent also gets very hot as does area on the laptop on top of the vent.

I've tried the cpu frequency scaling as suggested above with the conservative settings and the temperatures drop about 10deg C for both CPUs and the GPU. The fan, however, still seems to be turning on and off a lot.

Also with the CPU frequency scaling set to conservative I notice the system isn't as responsive.

---

### Post by Guille Damke on 2008-12-26
Hi theofucube,
I think, as Thomas said, as far as your vents are not obstructed your system should be fine. I think what you say about the fan turning on and off (a lot) is normal, I also see it on my Pangolin. If you are running some applications that demand CPU, or you notice that the system is slower, you have to run it using the ondemand settings, but sometimes the conservative setting is more than enough for what I am doing as the ondemand setting makes the cpu to run too fast.
Also you can put something under your laptop that dissipates heat better, for example I have noted that wood surfaces generally are not really efficient to dissipate heat as metal ones are.
cheers,
Guille.

---

### Post by Lee_Machine on 2008-12-27
Just to add my two cents I have the same laptop and I too at first thought I was having heat issues. But the temps you posted are what my run as. 

You should also go to synaptic and install ubuntu-laptop-mode.

This run scripts that spins down your hard drive but this also has its down sides. Yes it does save battery power but it will lower the life of your hard drive. In essence the mechanical parts will break down faster cause its going off, on, off, on....

From what I have read from user exp the life will do down to about a year. This of course only when you are running on battery power. This mode is not running when your on AC power. (most of my laptop use is)


This tool along with the CPU scaling got me another 30 minutes of battery life....the battery is already losing its life as 10-12 minutes of that are gone. I've had this laptop for about 3 months now, but I use it many hours a day.

enjoy :P

---

