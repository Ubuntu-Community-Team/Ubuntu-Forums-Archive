---
title: "Question:Does it saves power if you use lighter desktop environment on your linux box"
date: 2009-02-11
forum: The Cafe
---

### Post by imlinux on 2009-02-11
just a question in my mind,if we use lighter desktop environment like lxde,fluxbox,openbox,xfce etc does it helps in saving power consumed by your computer,as its less resource hogging.
In  corollary to this if its true does linux computers save more power than windows or mac computer.
i always see my cpu light on most of the time while on windows but while using linux it is rarely lighted,as if cpu was doing hell lot of work in windows 
(it is not that power is consumed in LED as some might say so,but its how much hard does your cpu has to work while operating in different operating systems and environment)

---

### Post by mihai.ile on 2009-02-11
except for compiz which will use more power even at idle, I don't think it is noticeable. Of course if gnome or xcfe, whatever, has a process that takes moderate cpu usage repeatedly you could notice a difference but again this has more to do with the services you use than what desktop environment.

---

### Post by ArtF10 on 2009-02-11
> **mihai007 said:**
> ... compiz which will use more power even at idle..

If you don't want it ON all the time, it's easy enough to manage it(turn it ON/OFF) using fusion-icon.  As simple as clicking a button really......

---

### Post by meborc on 2009-02-11
whatever uses cpu uses power...

whatever uses gpu uses even more power...

buy a meter to measure the current in the power outlet you use for the computer, if i'm not mistaken, phoronics has an article or two on the issue

---

### Post by imlinux on 2009-02-11
so if this is true then windows or mac computers have more energy consumption than linux computers,and thats definitely  not environmental friendly.

---

### Post by meborc on 2009-02-12
> **imlinux said:**
> so if this is true then windows or mac computers have more energy consumption than linux computers,and thats definitely  not environmental friendly.

that is not so simple... some distributions have cpu scaling out of the box, some don't

some linux machines will use less power and some more

---

### Post by mr.propre on 2009-02-12
Probably but ironically a lighter environment is made for 2 big reasons.

A) Slow machines
B) Machines that need to do heavy work, like a server.

---

### Post by Ub1476 on 2009-02-12
Power consumption (at least for newer laptops) is based upon the quality (and compatibility) with the kernel, hal, xorg, graphic driver etc. In my experience, the DE hasn't much to do about it.

---

### Post by phen on 2009-02-12
compiz needs more power, because it needs more gpu, even at idle. mihai said it before..

on older machines, the gpu cooler will turn on because of compiz, this is the proof: if the gpu is hotter (more energy dissipates into heat) more power is needed.

---

### Post by binbash on 2009-02-12
Choose a stable desktop.You can save more power with a stable desktop because you won't see high cpu usage or high cpu jumps etc, that saves a lot of power  :)

---

### Post by Koori23 on 2009-02-12
I understand the concept, it's logical. I think it's splitting hairs though. Regardless of what distro you're using or what Desktop Enviroment you're using your computer is still on. The fans are running, your power supply is functioning and the harddrive is still spinning and your monitor is still on. We're talking more about the physical entities that are hooked up to your computer as opposed to the DE you're running on your computer.

You have to start at the beginning, the Power Supply Unit. Where that baby goes from the wall socket to your machine is key. I'll leave out the fact that you're powering your LCD or CRT Monitor, and have your USB harddrive attached and on. All of which require power OUTSIDE of the computer itself.

Your power supply's purpose in life is to convert AC power to DC power so that things connected to your mobo will work.

Maxium Wattage ratings on Power Supplies is Manufacturer specific, therefore, more or less isn't always better. It's based on what temperature the manufacturer deems as safe maximum operating voltage. Power Supplies (I'm sure for warranty reasons) don't operate at 100%.

I said all that to say this. Say your powersupply is rated at 300W. You use LXDE as your enviroment.  A 300W powersupply is only capable of drawing 300W of electricity. If your system is idle most of the time, then you aren't using it's maximum capacity, so less draw. If you're hosting webpages and messing around with video a lot, that's going to demand more resources.

None of these things are specific to a particular Desktop Enviroment, they all relate to HOW the system is used and not what's installed necessarily.

Your resources that CAN be used are finite. It's whether or now you use them to the fullest extent your system can process instructions.

What difference does it make what DE you're using when you're converting Flash video's to DIVX. That'll require a lot of CPU time regardless. Blow away the GUI all together, it won't make a difference. 

Install Xubuntu using the text based Interface, it'll still use 100% CPU while installing.. Without a GUI.

Whatever difference you do record, it'll be nominal. It's not the DE, it's what you're requiring the computer to do. More instructions equals more power draw.

You'd be better served recycling your soda cans. That does make a difference that's measurable and isn't splitting hairs (5 Watts here or there).

---

