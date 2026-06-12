---
title: "SMP software"
date: 2007-03-28
forum: The Cafe
---

### Post by Compucore on 2007-03-28
Hi All,

I was wondering about something here within the ubuntu sofware that you can get through Synaptic software package manager. Are there any software within the list that will us dual or quad processors? The reason that I am asking this is that I may be getting a old server to tinker around with that has dual PIII 800 MHZ its an older proliant ML 370. And I figure if anyone here knew off hand here or had read in the dscriptions of the software that they had installed through Synaptic if they had seen any software like that to try out on a dual processor machine.

I haven't so far. But I am curious to find out what ind of applications. Besides Ubuntu, and the hidous windows OS will use the CPU. But I have not seen with the exeption of animation programs that render cgi, Are there other applications besides that will use the capabilities. It is for basic try and see what you can do with it you know. 

Compucore

---

### Post by Compucore on 2007-03-31
Small update here I was looking in Oracle over here. I have an active account withthem when I was learning programming over here. And it seems like they have a developers edition of 10 G that will use dual CPU withthe software they have there. I am currently using their 10G express which is a very light very of their software and works well on a single cpu and is free to download as well. THe other 10 G regular will work with a dal processor. I haven't found any other software that will handle a dual CPU still with theexception of the main operating systems.Or some really specialized applications like Oracle 10 G, CGI animatio that will take advantage of dual processors.

Compucore

---

### Post by RandomJoe on 2007-04-01
Mencoder (part of Mplayer) will use it if you give it the appropriate switch.  I added threads=2 to my mencoder commandline on my C2D machine, and it makes for a decent increase in encoding framerate.  If you have a DVD drive to use with that machine, you could try encoding it with/without the threads switch to see the difference.  (It doesn't use 100% of both CPUs when I do it, and it doesn't double the framerate, but it's a noticeable improvement over just a single core.)

For the most part, there aren't a whole lot of programs that *need* that much CPU, and the key is that the OS will distribute the running tasks evenly across the two CPUs.

---

### Post by Compucore on 2007-04-01
Well with this machine it is a rack mounted ML370 server that was decommissioned from the computer room. It is still usable for something else like for home use. I had worked with Oracle in my studies a few years ago when I was learning programming and databases with Oracle. So for me that was the only Applications that I knew right off the bat that was aminimum of a dual core minimum application. You could imagine me running Oracle 9i on a slow PII -233 MHZ took forever to load up. The 10G express is only good for a single the enterprise edition from oracle. ([http://otn.oracle.com](http://otn.oracle.com)) you can easily download them from there for free. 

Right now. I am just looking into trying some other specialized apps that will take advantage of a SMP machine that are freely available under ubuntu. For me its just for the fun of it of trying something out like that. 

Compucore

---

