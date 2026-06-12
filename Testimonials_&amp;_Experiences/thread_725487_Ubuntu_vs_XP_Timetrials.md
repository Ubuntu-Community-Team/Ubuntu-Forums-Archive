---
title: "Ubuntu vs XP Timetrials"
date: 2008-03-15
forum: Testimonials &amp; Experiences
---

### Post by myusername on 2008-03-15
well here are my specs:
pentium 4 2 ghz 512 mb ram 64 mb intel onboard video desktop

i just timed ubuntu and xp and here are my results:

                                            Ubuntu                  
Time Up:                             1Min 18Sec Seconds     
Ram usage on boot:          191.4 MB 4% CPU 
Ram w/  Firefox open        211.2 MB 4% CPU
Time Down:                       15.7 Seconds     

                                          Windows XP
Time up:                            54.1 Seconds
Ram usage on boot:         182.0 MB 0% CPU
Ram w/ firefox open:       210.0 MB 0% CPU
Time Down:                      40.2 Seconds


Why did ubuntu preform so badly in the time up and ram usage? are there any good tweaks that i don't know about? i only like gnome so xfce is out of the question

---

### Post by icechen1 on 2008-03-15
here are some tips:[http://howto.wired.com/wiki/Speed_Up_Linux](http://howto.wired.com/wiki/Speed_Up_Linux)

---

### Post by Can+~ on 2008-03-15
Weird? My desktop pc, both windows xp and ubuntu load in the same time, and xp untouched and ubuntu has like 1 year of usage.

My guess is:
a) Hardware support.
b) Did you consider that windows still loads once you login? This is a little trick they made for marketing, people gets to the desktop, but it continues to load, causing the impression that is faster, but it's a lie (like the cake).

---

### Post by myusername on 2008-03-15
ok i disabled a bunch of processes and a got the ram usage down to 140 mb ram in ubuntu ill go back and time the boot

edit the boot time is still pretty much the same

---

### Post by Afkpuz on 2008-03-15
Remember that windows tends to slow down the longer you use it.  It just gets weighed down and bloated. I'm assuming you're using a fresh windows install?

---

### Post by wasing on 2008-03-15
also windows could boot faster cause its probley using your hard disk cache. just a thought

---

### Post by myusername on 2008-03-15
i have had the windows install for about a month or too with all the programs i use on it...the ubuntu i reinstalled yesterday

---

### Post by MONODA on 2008-03-16
that's very weird, I have a desktop with similar specs and it boots in around 40 seconds...

---

### Post by jdrodrig on 2008-03-16
Just wondering when you say "Time up", is the time it becomes useful? or just to the log-in screen?

---

### Post by myusername on 2008-03-16
time its usable

EDIT WOOPS!! NOT 118 SECOND 1MIN 18SEC

---

### Post by p_quarles on 2008-03-16
That shouldn't be surprising at all. Windows XP is a lighter operating system than Ubuntu 7.10. GNU/Linux systems are vastly more scalable, yes, but Ubuntu's 2007 (which is a fully loaded system) can't be compared with Microsoft's 2001 release. There is also the issue of Firefox's code being optimized for Windows by design. 

It's entirely possible to set up Ubuntu in a way in which its speed will outpace XP's. The easiest way would be to start with a CLI installation using the alternate disk, and building your desired system on top of that. For best results, you would opt for the minimal Gnome package rather than ubuntu-desktop, which installs things like CUPS and Bluetooth support (whether you use it or not). The performance gain should be noticeable. 

For boot time, the usual recommendations are as follows:
1. Use sysv-rc-conf to disable unwanted startup scripts (tread carefully).
2. Use readahead (there's an excellent tutorial in the Tutorials & Tips section).
3. Disable a couple of TTYs (Ubuntu loads up 6 by default, which is likely excessive for the majority of desktop users -- even power users).

---

### Post by myusername on 2008-03-16
i have done all of that except the TTY thimg...

---

### Post by Lord Illidan on 2008-03-16
Regarding the RAM usage..


Ram usage on boot:          191.4 MB 4% CPU 
Ram w/  Firefox open        211.2 MB 4% CPU

Ram usage on boot:         182.0 MB 0% CPU
Ram w/ firefox open:       210.0 MB 0% CPU

So firefox on Ubuntu takes up 19.8 MB..while on Windows it takes up 28 MB.

I'm just doing simple subtraction here.

---

### Post by MNICY on 2008-03-16
> b) Did you consider that windows still loads once you login? This is a little trick they made for marketing, people gets to the desktop, but it continues to load, causing the impression that is faster, but it's a lie (like the cake). This is a very good point that i think not many people don't consider.
And i like the portal reference. (portal witch i can play on Linux using WINE :D)

---

