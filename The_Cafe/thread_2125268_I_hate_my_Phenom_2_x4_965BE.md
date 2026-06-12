---
title: "I hate my Phenom 2 x4 965BE"
date: 2013-03-13
forum: The Cafe
---

### Post by JayKay3OOO on 2013-03-13
So after annoying some friends today they told me to ask people who might actually know what to do.

I currently have two systems - I did have 3, but the scraptop went in the bin.

1) I have a system with a Pheonm 2 x4 965BE 3.4GHZ cpu that I've had a couple of years and it's great, but it uses too much power. The tdp is 145w and it uses nearly 200w rendering video.

I had thought about down-clocking it as for everyday stuff running it at 2.6GHZ does not degrade general performance too much, but whether it's using less power I don't know. Cool and quiet drops it to 800mhz idle. I'm not sure if it can be run on two cores to use less power.

My motherboard is AM3+ so I'm thinking of getting a bulldozer FX4100 for use with Linux preferably as the tdp is 95w. Anyone have experience of the power use of this chip?

2) I've got an E-350 dual core system that is good till you hit 720 + video in Linux - I think it works with Windows but have not had the energy to do this test. I have a contour roam so I need HD video to work. (Driver issues I thought were fixed or that's what I guess)

But then I thought... the e-350 board has space for a video card, so why not put the e-350 board in my full sized atx tower case and use the graphics card I know works with Linux in the machine. I've not done this yet as I have a giant zalman cooler on the am3 board and it has a 500w psu


[LIST]
[*]So what would you do? I'm trying to keep the power use of the computer down and need to be able to render at least 720p video (1080p preferred) while getting back to owning 1 'main' computer.
[/LIST]


Thanks for any advice. I'm leaning toward ebaying the e-350 machine and getting the bulldozer.

---

### Post by Gyokuro on 2013-03-13
Hi

I would go with the FX4100 system and maybe a new low power graphic card as I assume you do the rendering with your cpu and not the graphic card. Afterwards sell your E-350 system at a local computer store or ebay as I think you will save more money in the longterm to have only one good box. However I have to admit that I use only Intel systems but I thought maybe it is an idea for you.

---

### Post by pqwoerituytrueiwoq on 2013-03-13
you may just want to get a more efficient PSU (Seasonic makes good ones), and if you do go the route of a new cpu look at a FX-4300, very little price difference and it is faster with the same 95W TDP

The "AMD Phenom(tm) II X4 965 Processor" has 2 unlocked versions (aka black edition) one is a 125 TDP the other is a 140 TDP

In your BIOS be sure Cool n Quiet is enabled in your BIOS
you can use a cpu governor applet to watch the core GHz, they do scale you probably have 800Mhz, 2.2GHz, 2.7GHz,  and 3.4GHz, unless you are overclocking

to view your current cpu frequencies this command will work (the frequency changes depending on load)
```
cat -n /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq | awk '{print "Core "$1" is at "$2/1000" MHz"}'
```

on xubuntu i use the [genmon applet]("apt:xfce4-genmon-plugin"), i have attached the scripts i have them call

here is a screenshot of them (based on the gnome 2 applets for cpu govenor and sensors)
[IMG]http://i.imgur.com/o8p8ioL.png[/IMG]

i have included a php and a bash version of the cpu governor applet (which can be used to underclock using the userspace Governor)
the command you use 

you will need the [cpufrequtils]("apt:cpufrequtils") package to use the applet to change the governor (or mod the script to use the alternative command)
also in your /etc/rc.local you will need to have it chmod some stuff so it will be able to alter the setting
```
bash -c 'sleep 5;chmod 777 /sys/devices/system/cpu/cpu*/cpufreq/{scaling_setspeed,scaling_governor}' &
```

the command used in the genmon applet for the governor detector is 
```
cpu-freq-plugin 2
```
2 is the core number (starting at 0)
the one for the sensors is a bit more tricky
```
temp "CPU Temperature" cpu -C
```
"CPU Temperature" is the line that the temp appears on in the [FONT=courier new]sensors[/FONT] command
cpu is the icon file name
-C means display in Celsius
the order of the parameters is important

to install the attached stuff just extract it to /

---

### Post by prodigy_ on 2013-03-13
> **pqwoerituytrueiwoq said:**
> 140
Beats Smithfield (Q2/2005, 90nm, 95-130W).
Go AMD! /golfclap

---

### Post by nankura on 2013-03-13
ive never had a problem with my AMD 955 Black edition, runs fine, ive never checked how much power it uses because frankly, i dont care lol. i have no hardware issue's and havn't for the past 3-4 years, and its just plain and simply solid, along with running any program/game i need it to run

---

### Post by mastablasta on 2013-03-14
> **JayKay3OOO said:**
> 1) I have a system with a Pheonm 2 x4 965BE 3.4GHZ cpu that I've had a couple of years and it's great, but it uses too much power. The tdp is 145w and it uses nearly 200w rendering video.


Is it AM2/AM2+ socket? :D

> 


2) I've got an E-350 dual core system that is good till you hit 720 + video in Linux - I think it works with Windows but have not had the energy to do this test. I have a contour roam so I need HD video to work. (Driver issues I thought were fixed or that's what I guess)

But then I thought... the e-350 board has space for a video card, so why not put the e-350 board in my full sized atx tower case and use the graphics card I know works with Linux in the machine. I've not done this yet as I have a giant zalman cooler on the am3 board and it has a 500w psu


[LIST]
[*]So what would you do? I'm trying to keep the power use of the computer down and need to be able to render at least 720p video (1080p preferred) while getting back to owning 1 'main' computer.
[/LIST]


350 is not really good. it looks like "first try". 450 was much better. does it stutter even with proprietary drivers?

---

