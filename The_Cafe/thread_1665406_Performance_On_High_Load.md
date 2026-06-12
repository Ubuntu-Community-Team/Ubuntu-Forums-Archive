---
title: "Performance On High Load"
date: 2011-01-12
forum: The Cafe
---

### Post by NightwishFan on 2011-01-12
I just had a run in with an out of control process on my laptop; Which is fairly low end (for today) with only 2ghz 2x cpu and 3gb of ram. I was doing a kernel compile, and queuing about 18 jobs on Handbrake, on nice 19 and 15 respectively. At the time I also was web browsing and tabbing on and off between a movie I was watching on VLC. I am using the stock Ubuntu kernel only with a swappiness of 100.

I noticed right away there was a problem as my sound cut out, and my disk began to churn, which usually means something is hitting swap. The mouse gets a little choppy. I was unable to interact with the gui much to debug the problem, but I was able to get myself to a console. However by the time I got to the console which did not take long, my swap filled up, and the blessed OOM killer swooped in and had slain the out of control process, which happened to be VLC oddly enough. My desktop was back to responsiveness within 30 seconds.

I normally am wary of desktop performance with Linux however this was quite up to my standards. I was not forced to reboot to get back to working order, and both my handbrake and kernel compile continued as if they were not interrupted. (Though I might debug the results of both to see if any kind of corruption occurred).

Regardless, the point of this thread is really a "glorious exposition comrade" and I wondered if anyone else ever had to deal with a run away process and how their system stood up to it. I suppose the worst case would be a process that pages just enough that it will not be killed, and everything stays slow until you manage to get to a console to wipe it out. It also seems to point that the virtual memory subsystem is something to be looked at in desktop performance, not just cpu/preemption.

---

### Post by MooPi on 2011-01-12
Not so similar but some time ago I was attempting to rip a dvd from my library of shows. I started the process and proceeded to listen to some music and browse some news sites. Like you something did't feel right and I checked htop to see my swap being over run by the ripping process. Couldn't stop it with F9 in htop so a quick xkill did the trick. Disney movie was the problem.

---

### Post by NightwishFan on 2011-01-12
Yeah, lsdvd (mencoder) sometimes chokes on them, I think it is intended. They fill up the ram to full and start swapping. You need something that scans the titles in a manual way or else it will just crash the system, I learned to check system monitor while it starts so if my ram spikes I can kill it before it hits swap.

I actually stopped using BFS/Ck patches because I love having balanced performance with a lot of load since I actually use my system more like a server when it is plugged in. Not that bfs is even bad at those loads, it actually does quite well, but I really am not too interested in everything being hyper responsive.

---

### Post by ssam on 2011-01-12
sounds like exactly the workload that would benefit from the "200 line patch".
[http://lwn.net/Articles/415740/](http://lwn.net/Articles/415740/)

---

### Post by NightwishFan on 2011-01-12
No, I actually had it enabled, I backported it to .35. VLC was not running from a TTY and my compile and video conversions were already nice processes. They had no impact on my foreground processes. So for now, my custom kernels (I make a multimedia one, and a batch task one) both are not going to use the autogroup patch. I only have my own patch, which merely sets swappiness to 100 by default. Otherwise it is 100% ubuntu sources.

---

### Post by ssam on 2011-01-12
have you tried getting all the background tasks (CGG and handbrake) into a single cgroup?

also maybe look at ionice

---

### Post by NightwishFan on 2011-01-12
Playing around with cgroups sounds like a good idea. However I would like something automated if I dive into that, and the autogroup patch has issues with me and does not help any more than nice _in it's current form_. I have high hopes for it in the future despite the overhead of cgroups.

Using mainline cfs and cfq just nicing a process automatically ionices it as well, so if I nice them to 19 or 20 (idle) they already have almost zero impact on the system. CK also has the sched_idleprio to do this as well, though I prefer the mainline way as it is more flexible. (Processes like pulseaudio are by default nice -11, so they have higher priority io access automatically).

My issue is not really with performance; Any batch jobs just make it yield to the less nice processes (all of userspace is nice 0 except pulseaudio which is -11). I just noticed that regardless of nice level a process that hogs the virtual memory is going to hurt. I have no solution for this except to use cgroups to put a hard limit on certain processes. Which at the moment is far too manual for a very uncommon situation and incurs overhead. General responsiveness is excellent for day to day use.

Thanks a lot for the tips though. For now I actually recommend to disable the autogroups as I seem to have a lot of stuttering on media playback with it enabled, which I will debug. (Giving too many timeslices to my jobs in a tty? I assume nicing them to 19 means only among processes in the same cgroup?)

If I run these same loads with autogroup off and have no media problems, I will wait for it to be more clever (sorts by a better heuristic than by tty) before I enable it. Again, thanks for the input. :)

---

### Post by ssam on 2011-01-13
maybe this would help
ULatencyD
[http://www.phoronix.com/scan.php?page=news_item&px=OTAwNQ](http://www.phoronix.com/scan.php?page=news_item&px=OTAwNQ)

---

