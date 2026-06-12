---
title: "htop vs top?"
date: 2012-07-11
forum: Server Platforms
---

### Post by d4m1r on 2012-07-11
Hey guys, I was recommended htop recently by an article online for those of us that like to monitor usage/processes in real time but noticing an issue with it....It is not reporting RAM usage correctly....or is it? :confused: Basically, top reports 350MB/512MB RAM usage, and while the diagram of RAM usage in htop seems to display the same thing, the actual value displays as "40MB" as shown in the screenshot below. What is going on or does anyone know how to fix htop? 


[IMG]http://i.imgur.com/rmJnxl.png[/IMG]

---

### Post by idoitprone on 2012-07-11
> **d4m1r said:**
> Hey guys, I was recommended htop recently by an article online for those of us that like to monitor usage/processes in real time but noticing an issue with it....It is not reporting RAM usage correctly....or is it? :confused: Basically, top reports 350MB/512MB RAM usage, and while the diagram of RAM usage in htop seems to display the same thing, the actual value displays as "40MB" as shown in the screenshot below. What is going on or does anyone know how to fix htop? 


[IMG]http://i.imgur.com/rmJnxl.png[/IMG]

```
man htop

NAME
       htop - interactive process viewer

SYNOPSIS
       htop [-dChusv]

DESCRIPTION
       Htop is a free (GPL) ncurses-based process viewer for Linux.

       It  is  similar  to top, but allows you to scroll vertically and horizontally, so you can see all the processes running on the system, along
       with their full command lines.

       Tasks related to processes (killing, renicing) can be done without entering their PIDs.
```

tat screenshoot report memory usage by percent

---

### Post by d4m1r on 2012-07-11
No, I don't believe the number at the top left is supposed to be a %. It's supposed to be the exact MB of current RAM usage.

Nor would 40% of 512MB be 350MB (which was the usage at the time of the screenshot).

---

### Post by Cheesemill on 2012-07-11
Whats the output of:
```
free -m
```
My guess is that top is including the cached RAM but htop isn't.

---

### Post by arrrghhh on 2012-07-11
htop's RAM display has always confused me... The visual representation that is.  I don't think the actual value has ever been off, however.  Here's mine:

[img]http://i.imgur.com/XI1Xg.png[/img]

and the output of free -m:
```
total       used       free     shared    buffers     cached
Mem:          3014       2515        499          0        196       1130
-/+ buffers/cache:       1189       1825
Swap:         4823        811       4012
```

---

### Post by d4m1r on 2012-07-12
> **Cheesemill said:**
> Whats the output of:
```
free -m
```My guess is that top is including the cached RAM but htop isn't.

It seems to agree with top and NOT htop:

```
damir@server3:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        338        156          0         88        209

```

Is there a way to get the cached RAM included in htop?

---

### Post by d4m1r on 2012-07-12
Thanks for the cached RAM mention, that's what it ended up being. Neither number is wrong per say, they just make 2 different assumptions.

top is reporting the first line of free -m which is basically RAM that is completely empty.

htop is reporting from the 2nd segment of free -m which is basically the RAM that might have non-important stuff loaded into it right now, and could be free'd up automatically if any applications actually needed it.

I still prefer top and figured out a neat trick, you can sort top by most intensive RAM usage processes at the top (whole reason I got htop) by simply launching it, and hitting shift + M. :D

---

### Post by Cheesemill on 2012-07-12
For anyone that wants to know what cached RAM is.....

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

