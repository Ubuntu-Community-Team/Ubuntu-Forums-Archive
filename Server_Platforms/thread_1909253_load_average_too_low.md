---
title: "load average too low"
date: 2012-01-14
forum: Server Platforms
---

### Post by suffeks on 2012-01-14
just testing 11.10 server, and i'm noticing the load is too low compared to cpu usage, below is screenshot

on the left we have a quad core server with debian lenny, on the right sandy bridge quad core with 11.10 server, server on the right is getting 2x web traffic as server on the left

i have tried nohz=off highres=off and there is no difference, any other suggestions??

and here is a video i made a while ago: [http://www.youtube.com/watch?v=KjSZ-D0XBBQ](http://www.youtube.com/watch?v=KjSZ-D0XBBQ)

[IMG]http://i.imgur.com/T1Yya.png[/IMG]

extra reading: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513848](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513848)

---

### Post by CharlesA on 2012-01-14
"load average" has little to do with cpu usage.

[http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages](http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages)

---

### Post by suffeks on 2012-01-14
> **CharlesA said:**
> "load average" has nothing to do with cpu usage.

[http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages](http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages)

i know what load average is, how about you can explain to me instead why we have the discrepancy above ;)

for instance, i resolved the issue on squeeze by turning off tickless and applying a special patch, i was hoping there would be a more elegant solution on ubuntu, it is clearly not reporting correctly

sometimes the load will just go down to 0.00, while the server is processing 5,000 requests per second

---

### Post by CharlesA on 2012-01-14
You might have better luck filing a bug on launchpad, if it's not reporting the correct load.

In any case with 8 CPUs/cores, a load of 2.xx means it's using about 25% of your overall usable processing power, which isn't a problem.

---

### Post by Buntumatic on 2012-01-14
Yes you can serve 5000 requests per second without significant wait time. What's the problem here? Even an i486 (40 MHz) was able to serve 50 requests per second with less than average 1 process waiting.

---

### Post by suffeks on 2012-01-14
they are heavy php/mysql requests each time, i'm not talking static

how about you please watch the video whoever has doubts, there **exists** a problem

---

### Post by CharlesA on 2012-01-14
> **suffeks said:**
> they are heavy php/mysql requests each time, i'm not talking static

how about you please watch the video whoever has doubts, there **exists** a problem
Guessing you made the post here: [http://www.unix.com/unix-advanced-expert-users/166325-load-average-squeeze-too-low.html](http://www.unix.com/unix-advanced-expert-users/166325-load-average-squeeze-too-low.html)

As well as the bug report that is discussed here:
[http://forums.debian.net/viewtopic.php?f=10&t=65301](http://forums.debian.net/viewtopic.php?f=10&t=65301)

Best bet would be to file a bug with launchpad. Ubuntu is based off of Squeeze (or at least 10.04 is..), so it may be a bug with the package that was pulled from there.

---

### Post by suffeks on 2012-01-14
ya i just added comment to ongoing bug report on launchpad, and updated that other forum post on unix.com

---

### Post by CharlesA on 2012-01-14
> **suffeks said:**
> ya i just added comment to ongoing bug report on launchpad, and updated that other forum post on unix.com
Which bug report on launchpad?

---

### Post by suffeks on 2012-01-14
> **CharlesA said:**
> Which bug report on launchpad?

the link i posted under screenshot in first post

basically this is what i'm getting at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513848/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513848/comments/8)

---

### Post by CharlesA on 2012-01-14
> **suffeks said:**
> the link i posted under screenshot in first post

basically this is what i'm getting at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513848/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513848/comments/8)
You'd be better off making a new bug report as that one is for Karmic (9.10), which is end of life.

---

### Post by Doug S on 2012-01-15
I was able to create the incorrect load averages as described in this thread on my systems. I modied one of my simple CPU loading programs to just run for a short time instead of forever (in forever mode the load average numbers were correct). Then I created a script to call it in a forever loop. Thus each little burst of cpu useage had a different process ID and would wouldn't span a complete kernel sampling cycle (at least I am guessing at that part). Sure enough the load average numbers became completely wrong. I had to make the program execution time quite long before the load average numbers to begin to be realisitc.
 
Done on two computers, Ubuntu server 10.10 and a rather pathetic 11.10 server.```

Linux doug-64 2.6.35-31-server #63-Ubuntu SMP Mon Nov 28 21:03:37 UTC 2011 x86_64 GNU/Linux
Linux test-smy 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 i686 i386 GNU/Linux

```

---

### Post by suffeks on 2012-01-16
ok i fixed the problem, recompiling kernel with CONFIG_NO_HZ=n does it, load is now correctly reported in my case

---

### Post by Doug S on 2012-01-16
suffeks: Thanks for reporting back that you solved the problem. Now that I read some about CONFIG_NO_HZ something odd from my experiments yesterday makes sense. My load average numbers were always fine if the CPU idle time was 0%. For my pathetic 11.10 server, I had to introduce a slight sleep in the calling script so as to create a bit of idle time, then the load averages went extremely wrong towards zero. Anyway, I learned something with this thread.
Please mark it as solved.
 
Edit: So what is the take away lesson from this?
For me, it is that, for the default kernels, the load average as given by the "uptime" and "top" commands, is pretty much useless.
 
Example (my 10.10 server, with 2 CPUs):
Process frequency: 1.03 Hertz: load average given is 0.10 (5%) to low. 
Process frequency: 2.08 Hertz: load average given is 023 (12%) to low. 
Process frequency: 4.17 Hertz: load average given is 0.37 (19%) to low. 
Process frequency: 8.33 Hertz: load average given is 0.78 (39%) to low.
Process frequency: 17 Hertz: load average given is 1.00 (>50%) to low. (Load showed as 0)
...
Note: I realize it is rediculous to list the load average to 2 decimal places. They were very long terms averages. At some frequencies there is a significant beat frequency modulation.

---

### Post by Doug S on 2012-02-14
An update for this thread: I have done a lot of work on this issue and have now proposed a solution via one of of the [existing launchpad bugs]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811").
 
I have communicated with suffeks, and he has agreed to test my proposed patch.
 
[My web notes on this subject]("http://www.smythies.com/~doug/network/load_average/index.html").
 
Finally I understand why the reported load averages never made sense when I was running large batch files that executed many programs per second.

---

