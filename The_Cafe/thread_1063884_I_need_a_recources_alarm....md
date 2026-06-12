---
title: "I need a recources alarm..."
date: 2009-02-08
forum: The Cafe
---

### Post by kevin11951 on 2009-02-08
is there anything i can run as a daemon, that will make the BIOS speaker beep at an interval (eg. once a second) if the CPU, memory, etc... reaches to high (eg. CPU running at 89%)?  I need the control of the limits to be change able though.  bear in mind, that this is a command line pc, so only daemons will work.

---

### Post by diablo75 on 2009-02-08
Your computer would be beeping left and right.  A CPU will hit 100% several dozens of times a minutes, either holding there constantly or spiking up while a program loads and dropping down when it's done loading and there little else to do.  That's just the way it works, and there's nothing wrong with a CPU running 100%.  If you were to convert a movie into an AVI, for instance, you'd be running at 100% for at least an hour or two and as long as your heat-sink and fan are decent, you don't have anything to worry about.  It's what the CPU was meant to do.  If your heatsink is inadequate, then you get a better heatsink for 15 bucks and move on.

You might consider adding the System Monitor applet to one of your panels so you can monitor CPU, RAM, Network activity, SWAP and Load in real time.  That way you can watch how your computers resources are used over time while you're using your computer.

---

### Post by xpod on 2009-02-08
> You might consider adding the System Monitor applet to one of your panels so you can monitor CPU, RAM, Network activity, SWAP and Load in real time. That way you can watch how your computers resources are used over time while you're using your computer.

I dont think there`s too many of them on the PC in question;)

> bear in mind, that this is a command line pc, so only daemons will work. 

---

### Post by Xbehave on 2009-02-08
i think lm-sensors is what you need. i used the kde front-end but i think the lm-sensors tools are quite powerful and lets you set warnings for cpu-load and cpu-temp. you probably want it to warn when the average cpuload over x minutes is 100% otherwise it will be beeping all day.

---

### Post by Ptero-4 on 2009-02-08
[QUOTE=diablo75]
You might consider adding the System Monitor applet to one of your panels so you can monitor CPU, RAM, Network activity, SWAP and Load in real time. That way you can watch how your computers resources are used over time while you're using your computer.
[/QUOTE]
Hi. Your idea won´t work because the OP specified that his PC is not gonna have Xorg installed.

---

### Post by MaxIBoy on 2009-02-08
> **kevin11951 said:**
> is there anything i can run as a daemon, that will make the BIOS speaker beep at an interval (eg. once a second) if the CPU, memory, etc... reaches to high (eg. CPU running at 89%)?  I need the control of the limits to be change able though.  bear in mind, that this is a command line pc, so only daemons will work.
First of all, you want your CPU running at 100% as much as possible, otherwise your computer isn't efficiently accomplishing its tasks. 

There's a statistic called the "load average." I don't quite understand it, but ideally, it should be equal to the number of CPUs you have. If it's less, your CPUs aren't being used fully, and if it's more, there is a backlog of tasks stacking up. 

As for memory, this is why swap was invented. If you're running out of memory *and* swap, your computer will hang. If you find yourself adding more than twice the amount of swap as you have RAM, that means you need  more RAM. Plain and simple.

---

### Post by Niksko on 2009-02-08
I'm going to assume that the OP knows what he's doing and just want's a solution.

I'd use a bash script. Top to get you the CPU and memory usage, pipe it to awk in order to parse and get the info you want and then use 'echo -e "\a"' for an alarm.

I'm at school at the moment and I can't really write the code off the top of my head.

Good luck

-Nik

---

### Post by kevin11951 on 2009-02-08
ok, how about this, if the memory reaches over 89%, run ~/alarm

is that possible?

EDIT: how would i test that, is there a command that will fill memory with garbage?

---

### Post by Niksko on 2009-02-08
Again, top reports memory usage. You'd probably have to do some arithemetic and divide used memory by total memory to get a percentage value.

If you can wait about 6 hours I'll be at home and if I've got time I can write up a script for you.

No idea how you'd test. Perhaps a c(++) program that dynamically allocates large chunks of memory. Maybe some sort of memory test? Possibly RUMT - [http://www.normalesup.org/~george/comp/rumt/](http://www.normalesup.org/~george/comp/rumt/)

Best of luck.

-Nik

---

### Post by Yes on 2009-02-08
> **kevin11951 said:**
> ok, how about this, if the memory reaches over 89%, run ~/alarm

is that possible?

EDIT: how would i test that, is there a command that will fill memory with garbage?

No sense in filling your memory with garbage, just change the percent where the alarm goes off to something low.  If it works, change it to 89% or whatever and you're good.

---

### Post by MaxIBoy on 2009-02-08
I just wrote a script that will fill up memory until you cancel it. The reason it's so long is that I tried to make it so that you could cancel it gracefully without it hanging.

---

