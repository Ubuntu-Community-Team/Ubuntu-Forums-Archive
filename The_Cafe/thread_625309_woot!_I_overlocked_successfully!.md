---
title: "woot! I overlocked successfully!"
date: 2007-11-27
forum: The Cafe
---

### Post by nerdman978 on 2007-11-27
Yes! I overclocked my Intel Core 2 Duo E6400 from 2.13 Ghz to 2.2 Ghz! I have decided to try baby steps with my overclocking, I don't want to fry my nice new hardware, so I figure if I go very slowly and don't get too greedy, then I can overclock my computer to 2.5-2.7Ghz without frying anything. If I want more than that, I'll upgrade my heatsink.

Oh, and one random question. Is there a program that allows me to monitor temperatures inside my case (GPU, CPU, etc.)? I want to watch and make sure nothing is getting too hot. The computer I need to install it on is not connected to the internet and won't be (until I get a wireless card) so if this program exists can I get a .deb file and put that on a flash drive?

---

### Post by p_quarles on 2007-11-27
lm-sensors: [http://packages.ubuntu.com/gutsy/utils/lm-sensors](http://packages.ubuntu.com/gutsy/utils/lm-sensors)

Make sure you grab all the dependency packages, too.

---

### Post by nerdman978 on 2007-11-27
I went to
[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)
and download the tar.bz2 file for lm sensors.
now how do I install that?

---

### Post by p_quarles on 2007-11-27
> **nerdman978 said:**
> I went to
[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)
and download the tar.bz2 file for lm sensors.
now how do I install that?
You would have to use GCC to compile it. But, I gave you a link to the official Ubuntu package . . . why not use that?

---

### Post by John.Michael.Kane on 2007-11-27
This may help you configure it. [HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors")

Heres how you can read temps using conky with lm-sensors. Might have to adjust the cut numbers eg: -c13-16 to fit your cpu's
```
Core0..:: ${freq_dyn_g cpu0}Ghz ::: Usage: ${cpu cpu0}% ${cpubar cpu0 8,50} ${execi 8 sensors | grep -A 1 'Core0' | cut -c13-16 | sed '/^$/d'}C
```
```
Core1..:: ${freq_dyn_g cpu1}Ghz ::: Usage: ${cpu cpu1}% ${cpubar cpu1 8,50} ${execi 8 sensors | grep -A 1 'Core1' | cut -c13-16 | sed '/^$/d'}C
```

---

### Post by nerdman978 on 2007-11-27
Oops. I followed the link you gave to the page, but couldn't find an install file (which I just found) so I googled "lm sensors". But now I'm all set. 

Thanks.

---

### Post by ryanVickers on 2007-11-27
um, what on earth are you all doing!?!  You can just set processor speeds in your BIOS, no need for any complicated programs, compiling, etc....

---

### Post by nerdman978 on 2007-11-27
I know, I changed the clock speeds in the BIOS....

all I wanted was a program to monitor temperatures in my computer

---

### Post by ryanVickers on 2007-11-27
oh, you know there are lots of really good panel applets for that?

---

### Post by blithen on 2007-11-27
Or instead of all the compiling crap, it's in the repos

sudo apt-get install lm-senors

---

### Post by ahaslam on 2007-11-28
2.5GHz is realistic on the stock cooler. I wouldn't worry about frying it, you'll not do that without raising the voltage, which you shouldn't need to. With a Zalman CNPS9500, I'm lucky enough to get 3.15GHz at stock volts on a 1.86G E6300.

Don't forget to test the stability, use 2 instances of mprime in torture mode for several hours. This will find the smallest of instabilities & highlight any cooling issues.

Download: [http://www.mersenne.org/freesoft.htm](http://www.mersenne.org/freesoft.htm)
Just open 2 terminals & in each, navigate to the mprime dir, issuing, "./mprime -t".

P.S. It's always nice to see how far you've come: [ftp://pi.super-computing.org/Linux/super_pi.tar.gz](ftp://pi.super-computing.org/Linux/super_pi.tar.gz) ;)

---

### Post by Soarer on 2007-11-28
I have the same processor on a Gigabyte board which supports overclocking. I've never done it though. Can you see a difference with the change you made, or is it too small to notice?

---

### Post by ryanVickers on 2007-11-28
> **ahaslam said:**
> 2.5GHz is realistic on the stock cooler. I wouldn't worry about frying it, you'll not do that without raising the voltage, which you shouldn't need to. With a Zalman CNPS9500, I'm lucky enough to get 3.15GHz at stock volts on a 1.86G E6300.

Don't forget to test the stability, use 2 instances of mprime in torture mode for several hours. This will find the smallest of instabilities & highlight any cooling issues.

Download: [http://www.mersenne.org/freesoft.htm](http://www.mersenne.org/freesoft.htm)
Just open 2 terminals & in each, navigate to the mprime dir, issuing, "./mprime -t".

P.S. It's always nice to see how far you've come: [ftp://pi.super-computing.org/Linux/super_pi.tar.gz](ftp://pi.super-computing.org/Linux/super_pi.tar.gz) ;)

yes, but it's not just volts you have to worry about - too much heat, or even fast changes in heat frequently can be very bad too.  Also, since resistance obviously increases at the chip[ heats up, then slightly reduced processing speeds will occur at extreme temperatures (extreme isn't that high either.  And like I said, fast changes are BAD!!!! :p)

---

### Post by ahaslam on 2007-11-28
Ok, my 2nd sentence was poor advice, assuming too much. Don't let that detract from the second part of my post though - mprime will show you how hot it can *really* get, while testing cpu/mem/nb stability. 

;)

---

