---
title: "Ubuntu server 18.04 GUI fail"
date: 2020-08-14
forum: Server Platforms
---

### Post by math492m on 2020-08-14
so i installed GUI on my ubuntu 18.04 server

but after the reboot that should apply the gui 

it just dosnt do anything 

the screen has frozen to a pink ish state and has a frozen mouse curser you cant move 

i have tried the ctrl + alt +f1 and f7

what can i do to make the GUI work or get back to therminal

---

### Post by ajgreeny on 2020-08-14
What hardware do you have? Which GUI did you add to the server?
Show us the output of terminal command```
inxi -Fzx
```and we can move on from there.

---

### Post by math492m on 2020-08-14
i cant get in to terminal and its a physical hp se326m1 server 

and its ubuntu desktop as gui

---

### Post by ajgreeny on 2020-08-15
> **math492m said:**
> i cant get in to terminal and its a physical hp se326m1 server 

and its ubuntu desktop as gui
What do you mean when you say you can't get into terminal? Presumably you have a command line screen?  

Use that instead of a terminal-emulator such as gnome-terminal; the output will be the same.

Why do you want a GUI for a server anyway? Servers are much better configured and used with command line only, though if you really must have a GUI of some sort try something much less resource hungry than ubuntu-desktop; maybe using just a window manager like openbox or fvwm.

---

### Post by TheFu on 2020-08-15
> **ajgreeny said:**
> Servers are much better configured and used with command line only, though if you really must have a GUI of some sort try something much less resource hungry than ubuntu-desktop; maybe using just a window manager like openbox or fvwm.

+1.  

The specific instructions followed would be helpful too.  Vague, "I did something and what I expected didn't happen" is ... vague.
Better to just use the console or ssh to manage a Linux server.

---

### Post by math492m on 2020-08-17
when the server starts up and loads 

it will boot into GUI automaticly and i cant do a thing 

and is unresponsive 

and my boss wanted to have a GUI.... dont know why

---

### Post by sudodus on 2020-08-17
Please specify the **brand name and model of the graphics chip/card** in the computer. The problem may be that the built-in linux drivers cannot manage the hardware for graphics.

Sometimes the boot option [FONT=Courier New]**nomodeset**[/FONT] will provide some basic graphics, and then you might be able to install a proprietary graphics driver.

---

### Post by math492m on 2020-08-17
intel xeon l5640

---

### Post by ajgreeny on 2020-08-17
> **math492m said:**
> intel xeon l5640
Well that's the cpu; what about all the other hardware, particularly graphics, or is that just the integrated gpu in the processor?

---

### Post by math492m on 2020-08-17
yes its integrated greapchics 
it also have 8gb of ecc ram and 2x300gb sas disk

---

### Post by math492m on 2020-08-17
an the os is running in raid 1 on the 2 disks if you need to know

---

### Post by TheFu on 2020-08-17
```
inxi -Fzx
```
was requested above.  Can you not boot into a "Try Ubuntu" desktop environment, run that, post the results here?

Nobody wants to ask for information 50 times.

---

### Post by math492m on 2020-08-17
thanks for your help but i fixed it myself in grub

---

### Post by TheFu on 2020-08-17
> **math492m said:**
> thanks for your help but i fixed it myself in grub

How?  The next person would really like to know.
Also, please mark this thread "SOLVED" using the Thread Tools button to people looking for answers and those wishing to help don't waste time.

---

### Post by ajgreeny on 2020-08-17
Yes; please tell us the solution and then mark the thread as SOLVED from the Thread Tools menu up top.
It's a great help to other users who may be searching for answers to similar problems.

---

