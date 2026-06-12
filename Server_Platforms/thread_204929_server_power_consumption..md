---
title: "server power consumption."
date: 2006-06-27
forum: Server Platforms
---

### Post by flash777 on 2006-06-27
Hi all,

I'm running Ubuntu 6.06 LTS on a HP a1100y desktop. It is a simple desktop with a 2.53GHz Celeron processor that I am using as a server. I am planning to run it 24x7 and 365 days.

The load on this machine for now will be real light. One or two users might access it occassionally. But I do want it to be available continuously.

I was wondering if I can do any optimizations with regards to its power consumption. One thing that comes to my mind is the Windows Standby mode that stops everything but keeps the RAM alive (and may be other things). Is there a similar thing that I can do on Ubuntu server? However, when there is work that needs to be done, it should wake up automatically. I'm talking about work such as serving a remote web request or serving an ssh session. I think we refer to this concept as wake on lan. Are there any other things that I need to do besides this? Do I need to install any special software packages?

By the way does anyone know how much it costs to run a machine like this in real dollars?

Thanks in advance for all the help!

---

### Post by lamego on 2006-06-27
WakeOnLan is about remotely turning a system on using a network message, it is powering-on the system (not removing from hibernation) and is only triggered by a special message (not by any network activity).
The question about the costs depends a lot on the country, talking about a single PC class server I guess on most of the countries the power consumption will be irrelevant compared to the bandwidth price.

---

### Post by flash777 on 2006-06-27
[QUOTE=lamego]WakeOnLan is about remotely turning a system on using a network message, it is powering-on the system (not removing from hibernation) and is only triggered by a special message (not by any network activity).
The question about the costs depends a lot on the country, talking about a single PC class server I guess on most of the countries the power consumption will be irrelevant compared to the bandwidth price.[/QUOTE]
 
Thanks for the reply. In my case I am not using the server for serious stuff. So no worries about bandwidth. I just want to know how to calculate how much it costs to run this machine. If it is too much I don't wanna do it. If it is reasonable then I'd like to continue running it.

---

### Post by Glut on 2006-06-27
It very much depends on the hardware. If you're running on something like a VIA CPU or laptop based hardware (such as say, mac mini) which have very small energy requirements then you wont use much. OTOH If you're running a quad cpu XEON with redundant power supplies and a whole bunch of scsi disks then you're going to be shelling out cash.

---

### Post by LordHunter317 on 2006-06-27
If the server is recent, the processors sohuld support the same power management features laptops use to throttle the CPU down.  Enable that.

---

### Post by joshchernoff on 2006-08-08
I'm worryed about burrning out my components such as fans and harddrives and eny other thing that should ware down after hevy long use. If you have a server thats not under use all day, but should be online all day what is the best way to keep power use and over all use to a minimum, such as wake from a sleep mode or something liike that. 

what should I look for, how do I set it up, and what will it do?
[-o<

---

### Post by MJN on 2006-08-08
You'll probably more likely get prematurely component wear/failure by power cycling than leaving them on all the time. It's thermal expansion that's to blame for a lot of physical failures (i.e. turning on things from cold etc) and so leaving them continuously on will mitigate this.
 
You also have to bear in mind the high power drains for spinning up hard disks from standing - considerably higher than that require to *keep* it spinning. Of course, this peak draw only occurs for a brief moment but then that's when you're stressing the components the most.
 
I've run a personal server for several years now and in all that time it's probably only been turned off for a few 10's of hours literally.
 
Mathew

---

