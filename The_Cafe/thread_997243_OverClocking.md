---
title: "OverClocking"
date: 2008-11-29
forum: The Cafe
---

### Post by Oliver.BS on 2008-11-29
Does any one know if its possible to over clock a Dell Latitude d610 ?

---

### Post by smartboyathome on 2008-11-29
Well, I would recommend to install cpufrequtils from the repos, then run:

For intel processors:
```
sudo modprobe acpi-cpufreq
```
For AMD processors:
```
sudo modprobe powernow-k{6,7,8}
```

Then after that, run:
```
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_powersave
```

Now you can run cpufreq-info to see if its able to be overclocked.

---

### Post by Kain000 on 2008-11-29
sorry, 
dell (like HP compac apple, ect) does not allow you to overclock your hardware period.    a general rule of thumb would be if you bought it pre built, you mostlikely will not be able to overclock it.   

They dont want people screwing with the voltages and core clocks in the event they damage somthing and that person tries to return or warranty it.

if you want to overclock anything you will have to buy another motherboard, as that is where the locks are kept.... (unless you can figure out how to over wright dell's BIOS firmware with one that will work and allow you to change settings, I wouldnt know where to start tho.

I have upgraded my BIOS before but never tried to over wright with a different company's.

---

