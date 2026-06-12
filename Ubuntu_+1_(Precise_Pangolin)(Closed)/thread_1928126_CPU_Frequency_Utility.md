---
title: "CPU Frequency Utility"
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fjgaude on 2012-02-19
Is there a CPU freq utility that shows speed under Precise, for Intel CPUs?

---

### Post by williammanda on 2012-02-19
Also is there anything that will show the gpu utilization similar to system monitor for cpu's?

---

### Post by mc4man on 2012-02-19
There is indicator-cpufreq though it's a bit limited

---

### Post by fjgaude on 2012-02-19
> **mc4man said:**
> There is indicator-cpufreq though it's a bit limited

I'm looking to see how the CPUs change frequency as the load changes. indicator-cpufreq doesn't work with 12.04, yet, as far as I can determine, at least not for my Intel CPU. You know otherwise?

####
 
I take it back! I rebooted after installing and it worked. Thanks, mc4man, for the tip.

---

### Post by mc4man on 2012-02-19
> **fjgaude said:**
> 


 
I rebooted after installing and it worked.
I only wish it was able to show the cpu's individually like you could do in gnome2 by adding an applet for each cpu
 But you can't complain too much for something someone has created on their own time..

---

### Post by typhoon_tip on 2012-02-19
> **mc4man said:**
> I only wish it was able to show the cpu's individually like you could do in gnome2 by adding an applet for each cpu
 But you can't complain too much for something someone has created on their own time..

Instead I prefer this version, as an unbalanced heating CPU can create mechanical problems and uneven thermal flows (could even burn if one is not careful !). My only concern was that it was fixing only one CPU and not all together, instead is doing all at once, confirmed by monitoring them with a command in terminal (which I forgot... :P ).

---

### Post by mc4man on 2012-02-19
> **typhoon_tip said:**
> Instead I prefer this version, as an unbalanced heating CPU can create mechanical problems and uneven thermal flows (could even burn if one is not careful !). My only concern was that it was fixing only one CPU and not all together, instead is doing all at once, confirmed by monitoring them with a command in terminal (which I forgot... :P ).
Was wondering about that, good to hear.
Myself never would set the cpu's, ondemand works well here, was only interesting to see what was going on

---

### Post by typhoon_tip on 2012-02-19
> **mc4man said:**
> Was wondering about that, good to hear.
Myself never would set the cpu's, ondemand works well here, was only interesting to see what was going on

It is sometimes useful to me. I noted this mode does not only affect CPU, but bus as well, speed transfer between CPU/GPU for instance is also very much affected by this setting. Using it when playing full HD on my laptop, you can notice the difference as the playback is always fluid with full-performance set. :)

---

### Post by mc4man on 2012-02-19
> **typhoon_tip said:**
> It is sometimes useful to me. I noted this mode does not only affect CPU, but bus as well, speed transfer between CPU/GPU for instance is also very much affected by this setting. Using it when playing full HD on my laptop, you can notice the difference as the playback is always fluid with full-performance set. :)

i've had that issue at times where some videos weren't getting smooth playback because with ondemand the cpu's were staying at lowest or almost lowest speed. My solution for that was to adjust the default up_threshold for ondemand  from 95 to a more reasonable 70 or 75.

(- on this laptop there is now (starting in 11.10) an issue with compiz & my nvidia chipset's powermizer, it doesn't react or be 'told' to react fast enough in upclocking the gpu performance level 
So I've added a xorg section to have the gpu on max performance all the time on Ac where I usually am
Probably should think about a new laptop shortly, 4 years old, a so so nvidia 8400m

---

### Post by donniezazen on 2012-02-20
[http://trayfreq.sourceforge.net/](http://trayfreq.sourceforge.net/)

This might be of some use.

---

### Post by williammanda on 2012-02-20
> **mc4man said:**
> There is indicator-cpufreq though it's a bit limited

Is this a CL program? I can't find it.

---

### Post by philinux on 2012-02-20
> **fjgaude said:**
> Is there a CPU freq utility that shows speed under Precise, for Intel CPUs?

I switched over to conky.

---

### Post by williammanda on 2012-02-20
> **williammanda said:**
> Is this a CL program? I can't find it.

Does it show a selection of frequencies and a selection of conservative, ondemand, etc...?

---

### Post by fjgaude on 2012-02-20
> **williammanda said:**
> Does it show a selection of frequencies and a selection of conservative, ondemand, etc...?

Yes. It's only in 12.04 repository.

---

### Post by williammanda on 2012-02-20
So this doesn't actually reflect the current speed only a selection to set the frequency?

---

### Post by mc4man on 2012-02-20
> **williammanda said:**
> So this doesn't actually reflect the current speed only a selection to set the frequency?

It shows you graphically thru bars in the indicator, at least here is pretty accurate

---

### Post by fjgaude on 2012-02-20
> **williammanda said:**
> So this doesn't actually reflect the current speed only a selection to set the frequency?

You set the speed, but it doesn't actually show what the speed is.

---

### Post by zika on 2012-02-20
You can check speed with```
cat /sys/devices/system/cpu/cpuX/cpufreq/scaling_cur_freq
```...

---

### Post by fjgaude on 2012-02-20
> **zika said:**
> You can check speed with```
cat /sys/devices/system/cpu/cpuX/cpufreq/scaling_cur_freq
```...

```
frank@cutie:~$ cat /sys/devices/system/cpu/cpuX/cpufreq/scaling_cur_freq
cat: /sys/devices/system/cpu/cpuX/cpufreq/scaling_cur_freq: No such file or directory
```

Not yet on my 12.04 Unity box, no "cpu, cpuX, cpufreq".

Is there a utility that I could install.

---

### Post by zika on 2012-02-20
> **fjgaude said:**
> ```
frank@cutie:~$ cat /sys/devices/system/cpu/cpuX/cpufreq/scaling_cur_freq
cat: /sys/devices/system/cpu/cpuX/cpufreq/scaling_cur_freq: No such file or directory
```Not yet on my 12.04 Unity box, no "cpu, cpuX, cpufreq".

Is there a utility that I could install.
X is one of 0,1,2,... cores...
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
```

---

### Post by fjgaude on 2012-02-20
Thank you, zika, it works...

---

### Post by williammanda on 2012-02-21
Has anyone used the intel-gpu-tools?

---

