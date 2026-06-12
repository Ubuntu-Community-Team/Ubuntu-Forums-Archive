---
title: "Conky is Funny"
date: 2008-06-20
forum: The Cafe
---

### Post by acelin on 2008-06-20
Correct if I am wrong, but dont most Conky users use it so they can measure how fast their computer is, and use it to figure out what apps are the fastest and what slows their computers down?

Why use another program that can slow your computer down? :lolflag:

---

### Post by RiceMonster on 2008-06-20
...or maybe they use it because they maybe, I don't know, just like it? I use it as a clock.

---

### Post by PrimoTurbo on 2008-06-20
Let me correct you then. Most users use it to display various information and conky is very light.

I use it for date, uptime, check for email msgs and weather.

---

### Post by easybake on 2008-06-20
It also adds some looks to boring desktops.

---

### Post by atomkarinca on 2008-06-20
> **acelin said:**
> Correct if I am wrong, but dont most Conky users use it so they can measure how fast their computer is, and use it to figure out what apps are the fastest and what slows their computers down?

Why use another program that can slow your computer down? :lolflag:

How can an application using 852 KiB of ram slow down your computer? It's useful, highly configurable and lightweight.

---

### Post by alexandremrj on 2008-06-20
Conky is a great tool for measuring almost everything, including filesystem use, network, and still getting a ligh footprint - if you use the system monitor you will use as much memory and have less information

---

### Post by kerry_s on 2008-06-20
> **acelin said:**
> Correct if I am wrong, but dont most Conky users use it so they can measure how fast their computer is, and use it to figure out what apps are the fastest and what slows their computers down?

Why use another program that can slow your computer down? :lolflag:

if it's slowing your computer down, your doing something wrong.
mine uses like .33 cpu & .78 memory, pic->

---

### Post by acelin on 2008-06-20
I am jsut saying- if some people use it to monitor stuff because they are really concerned about their speed, its doesnt make sense to run another program to do that, even if it takes up next to no ram.

---

### Post by wootah on 2008-06-20
> **kerry_s said:**
> if it's slowing your computer down, your doing something wrong.
mine uses like .33 cpu & .78 memory, pic->

Is that your actual processor? A 50 mhz cpu? :shock:

---

### Post by p_quarles on 2008-06-20
> **acelin said:**
> I am jsut saying- if some people use it to monitor stuff because they are really concerned about their speed, its doesnt make sense to run another program to do that, even if it takes up next to no ram.
I recently set up a very old laptop with Debian and Fluxbox. It uses Conky to monitor the battery level. Makes perfect sense to me. 

On my own machines, I use it to monitor a variety of things, not necessarily just things related to performance. It's an extremely flexible monitor -- I think you're comparing it to the types of tools that come with DEs, and that comparison doesn't hold.

---

### Post by OmniCloud on 2008-06-20
> **acelin said:**
> I am jsut saying- if some people use it to monitor stuff because they are really concerned about their speed, its doesnt make sense to run another program to do that, even if it takes up next to no ram.Well, your logic is a little flawed. 

How else are you going to know what apps are taking up the most memory if you don't setup some type of system monitor? If your computer is always blazing, you probably won't care. But what about the day its bogging down--some users want to know why?

Besides that, conky for some, is just a clock/date application. (a lot lighter than default one in Gnome that's for sure) For some, they insert there weather information. For some, it's a memory/ram usage app. 

Like i said, your logic is flawed because your not giving conky enough credit as a versatile application. it's more of a "DO WHATEVER" application--not just a system monitor. It wouldn't be so popular if it wasn't.

---

### Post by kerry_s on 2008-06-20
> **wootah said:**
> Is that your actual processor? A 50 mhz cpu? :shock:

:lolflag: no my cpu is 450mhz, but it throttles down as low as 7mhz when it doesn't need to use that much processor.

---

### Post by RedSquirrel on 2008-06-20
I find conky is handy for monitoring the CPU temperature and fan speed.

A while ago, I was having random segmentation faults while compiling programs and I wanted to make sure it wasn't the CPU overheating. I added a bunch of other stats since tinkering with conky is such fun. :)

It's so light that I never worried about the resources it was using.

---

### Post by acelin on 2008-06-20
Ahh that makes sense- see I never knew it could do that.

---

### Post by Toet on 2008-06-21
I use conky for:

Monitoring running processes (memory, cpu)

Incoming and outgoing connections (nice to see what is happening, especially if you have a port open for a game server or something like that)

Tailing system log file, to see if everything is ok. Some interesting errors can show up with Ubuntu.

So overall not for speed or something, just to check everything is ok.

---

### Post by Dr Small on 2008-06-21
I use conky for monitoring network connection, download usage, DNS servers, Date, Time, Kernel, CPU, processes and disk space. My system is quite capable of handling alot of processes, but I use it to fill my ever boring desktop.

Conky is lightweight too, so another reason I use it.

---

### Post by SomeGuyDude on 2008-06-21
I think a lot of people bloat up their conky with stuff they can't POSSIBLY actually be monitoring. 

Me, I have CPU/RAM/HD monitor, clock, network, battery, temp, and then weather/email/music. Very basic.

---

### Post by vishzilla on 2008-06-21
I use conky to monitor my internet usage, RAM, CPU usage. Its right there on the desktop to refer, a great tool.

---

### Post by spupy on 2008-06-21
Conky is the lightest mpd client! :)

---

### Post by pt123 on 2008-06-21
I mainly use it for task lists and calendar, see sig.

---

### Post by acelin on 2008-06-21
Hmm I can see where this would be quite useful... is there way to set a shortcut to make COnky come up and then disappear?

---

### Post by chris4585 on 2008-06-21
> **acelin said:**
> Hmm I can see where this would be quite useful... is there way to set a shortcut to make COnky come up and then disappear?

Yes, make a launcher on the panel, desktop, menu, etc.. killall conky and another one for conky :)

---

### Post by acelin on 2008-06-21
How about one key that opens and closes it? Is that doable?

---

### Post by chris4585 on 2008-06-21
> **acelin said:**
> How about one key that opens and closes it? Is that doable?

Well.. I know in openbox you can do that in ~/.config/openbox/rc.xml .. i'm sure there's a way in gnome somehow, i'm sure someone will give the gnome alternative

What i do (openbox) but you can easily do the same in gnome with the main menu tool

here's a screen:

---

### Post by spupy on 2008-06-21
> **acelin said:**
> How about one key that opens and closes it? Is that doable?

You need the wmctrl program:
```
wmctrl -r Conky -b toggle,hidden
```

---

### Post by kerry_s on 2008-06-21
```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky
```

---

