---
title: "Decrease the swap use"
date: 2015-12-18
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2015-12-18
hey everyone,

been reading about the decrease of swap and its advantages. 
i can see where maybe it would offer a speed increase where you only have low amount of ram. 
what if you have 3.0 gb or more ram would you really see any noticeable difference as an end user or would any noticeable difference only be seen in benchmark testing.
is decreasing the value of swap really that important.

thanks.

---

### Post by v3.xx on 2015-12-18
Want to see if it makes a difference?

Turn swap off and run like that.  A partition manager (gparted) is needed.

```
sudo apt-get install gparted
```

Open it up and right click on your swap partition and turn it off.  If swap is working properly you should not see any difference.  If you run any programs that eat up your ram, your computer will crash with swap off.

There is also swappiness, that may or may not help.  Again, if its running right with the default setting then tweaking it will probably not help.

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by poorguy on 2015-12-18
this is what i am referring to it is from easy linux tips project.

**[SIZE=3][B]Decrease the swap use (very important!)**[/SIZE][/B]

 This is especially noticeable on computers with relatively low RAM  memory (512 MB or less): they tend to be far too slow in Ubuntu, and  Ubuntu accesses the hard disk too much. Luckily, this can be helped.

On the hard disk there's a separate partition for virtual memory, called  the swap. When Ubuntu uses the swap too much, the computer slows down a  lot.

Ubuntu's inclination to use the swap, is determined by a setting. The  lower the setting number, the longer it takes before Ubuntu starts using  the swap. On a scale of 0-100, the default setting is 60. Which is much  too high for normal desktop use, and only fit for servers.

A detailed explanation can be found [here]("http://rudd-o.com/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that") (link dead? Then download [this pdf file]("https://sites.google.com/site/easylinuxtipsproject/file-closet/swappiness.pdf?attredirects=0&d=1") with the same content).

i made the change and don't see any difference which is why i question the importance of this with 3.0 gb or more ram.

---

### Post by deadflowr on 2015-12-18
^^ You can turn swap on or off with
```
sudo swapoff -a
```
to disable all swap partitions, or
```
sudo swapon -a
```
to enable all swap partitions listed in /etc/fstab.

I think, though, that standard method/way is to increase swappiness when you have less ram.
Simply because you will hit the max capacity the ram can use faster with less ram.
And if you set it to move the memory to swap at the last possible moment it'll bottleneck.
whereas if you move swap more constantly with less ram it'll run a lot smoother.

---

### Post by poorguy on 2015-12-19
i couldn't tell any difference between the changed value of 10 from the[COLOR=#000000] default setting of 60. therefore i changed back to the original default setting of 60.

thanks.[/COLOR]

---

### Post by buzzingrobot on 2015-12-19
I'm pretty skeptical about those articles suggesting that playing with swappiness will deliver a magical performance boost.

If a machine is swapping regularly, either add more RAM or make less use of the existing RAM.

Seems to me that turning off swap entirely is fine until you max out RAM and a process asks the kernel for more RAM. That's precisely when swap comes into play. If it isn't there, it can't be used.

---

### Post by poorguy on 2015-12-19
that is just it i am not turning swap off because i do know it is there for a reason.

i was just curious about any noticeable change if any there might be any by decreasing how often swap occurred with more than 3.0gb of ram. i tried and i couldn't tell any change so i went back to the default setting of 60.

its one of those things that if one never tries then one will never know. i tried and now i know.  
i have read lots of articles on how to speed up ubuntu and so far i haven't noticed any difference at all and some have broken my ubuntu but that is tuition for the price of an education. also a very good learning experience.

---

### Post by v3.xx on 2015-12-19
I did not see any instance results, but my laptop with 4G of ram would go to swap on occasion, for no good reason.  Setting swappiness to 10 and cache_pressure to 50 was the solution.  My desktop is still running default settings without issue.  If swap ever kicks in on my desktop machine, I will do the same to it.

---

### Post by poorguy on 2015-12-19
i just have to try things that i read about so i learn first hand.

i have 3.0 gb ram and my desktop runs perfect with factory default settings and never had any issues with [COLOR=#000000]swappiness.[/COLOR]
[COLOR=#000000]tried the setting swappiness to 10 and cache_pressure to 50 didn't notice any change. i have read that that is a [/COLOR][COLOR=#000000]solution for accessing swap to often.[/COLOR]

keep an image handy so if i do break my linux desktop i can restore back in a matter of minutes.

---

### Post by sammiev on 2015-12-19
Have you tried HTOP or System Monitor? 

It will show you what's in memory, how much swap is left and memory available.

My swap is never used unless I use suspend or hibernate.

---

### Post by poorguy on 2015-12-19
i have system monitor that comes in ubuntu.

not yet but i think i will looks to be a useful tool.

thanks.

---

### Post by poorguy on 2015-12-19
can download HTOP but can't seem to get it to run.

---

### Post by sammiev on 2015-12-19
> **poorguy said:**
> can download HTOP but can't seem to get it to run.

I usually use Synaptic to install HTOP but any installer or package manager should work.

Just click on the icon or from terminal type:

```
htop
```

---

### Post by poorguy on 2015-12-19
so it will only run from the terminal. i see.

thanks.

---

