---
title: "[SOLVED] CPU Scaling - plz allow more frequencies + easy Nvidia install"
date: 2008-05-16
forum: Ubuntu Brainstorm
---

### Post by Brinstar on 2008-05-16
Simple as that. The current number of frequencies supported by the power management daemons is just not as good as WinXP (a 7-year-old OS). 

WHY?

This may not seem so serious, but it causes my (and several other peoples') CPU to run at unnecessarily high speeds. This *damages* the CPU in the long run.

Why can WinXP run so quietly and not Ubuntu? I am typing this from XP as I have had enough of this stupid problem along with the annoyance of installing Nvidia drivers (official drivers or using Envy-ng which does not always work) that I felt I was getting more from XP.

Please fix these issues for Ibex and I will gladly return. 

P.S. Please include a good OpenGL game so I can test my graphics properly once installed :) I nominate Armagetron Advanced.

---

### Post by smartboyathome on 2008-05-16
Nvidia is easy to install. All I had to do was use the device manager. Also, CPU scaling should be enabled in the GNOME panel, the tool IS helpful.

---

### Post by CrazyGuy123 on 2008-05-16
I believe some CPU's only have two frequencies - 100% frequency and 50% frequency.  Thats certainly the case for many AMD64's.  Windows makes it look like you've got other frequencies by rapidly switching between frequencies, which Ubuntu also does as well.

I guess if it's noisy you've got a problem that it's not scaling at all, or it's not controlling the fans correctly.  If you give the make and model of the PC someone here might have the same system and a solution.  If you find a solution remember to post a bug report with the solution in so it can be fixed for the next release.

PS.  I fully agree on the fully OpenGL game - we need a simple game to include by default thats < 1MB of code because it has to fit on that ever tighter CD.

---

### Post by Ripfox on 2008-05-16
Ubuntu runs quietly on all my machines. Nvidia installs in one click.

---

### Post by Brinstar on 2008-05-17
> **CrazyGuy123 said:**
> I believe some CPU's only have two frequencies - 100% frequency and 50% frequency.  Thats certainly the case for many AMD64's.  Windows makes it look like you've got other frequencies by rapidly switching between frequencies, which Ubuntu also does as well.


Sorry friend, but that is just not the case. Winxp definitely can switch between more frequencies. Maybe this has something to do with driver/manufacturer support, because the optional Toshiba Power Saver for XP definitely has 6 CPU levels. I don't have it installed right now, but later I could take a screenshot as proof.

On Ubuntu or Linux I can only get 3-4 frequencies in comparison.

My machine is a Toshiba Tecra M3 (2005).

---

### Post by NilsHG on 2008-05-17
i am glad windows works for you.
good luck.:popcorn:

---

### Post by Sukarn on 2008-05-17
> **CrazyGuy123 said:**
> PS.  I fully agree on the fully OpenGL game - we need a simple game to include by default thats < 1MB of code because it has to fit on that ever tighter CD.

Can't you just use glxgears for that?

---

### Post by CrazyGuy123 on 2008-05-17
> **Brinstar said:**
> On Ubuntu or Linux I can only get 3-4 frequencies in comparison.

How can you be sure windows isn't just switching between (for example) 50% and 100% very quickly, and therefore showing 75%.  I know for sure that windows Vista averages the CPU speed when you view it onscreen so it looks like it can go at any speed, when in fact that isn't the case.

If you're right and Ubuntu isn't doing CPU scaling correctly, it would be great if you could collect a list of the possible levels from windows, and the same from linux, compare the two, identify the frequencies that Ubuntu doesn't allow, and report it as a bug together with all the relevant logfiles and as much information about your system you can find.

PS. have you tried turning compiz (desktop effects) off?  It might make the fans considerably quieter.

> **Sukarn said:**
> Can't you just use glxgears for that?
Well glxgears aint much fun...

---

### Post by smartboyathome on 2008-05-17
So, testing graphics doesn't need to be fun. It just needs to test them.

---

### Post by Sukarn on 2008-05-18
Not really relevant here, but I just want to add that I did not check XP to see what frequencies it scaled my CPU to back when I was using it, but Ubuntu scales my CPU between 55% (not 50%) and 100%.

---

### Post by Brean on 2008-05-18
I don't know if you use cpufreqd.conf, but when you do there is a file called cpufreqd.conf where you can add new rules with different speed steps. (take a look at the man page of cpufreqd.conf for more help)

---

### Post by Brinstar on 2008-05-19
> **Brean said:**
> I don't know if you use cpufreqd.conf, but when you do there is a file called cpufreqd.conf where you can add new rules with different speed steps. (take a look at the man page of cpufreqd.conf for more help)

Thanks for that, will try it out when i get time to install Ubuntu again. good to see people making constructive comments, was beginning to lose faith in the Ubuntu community...

> **CrazyGuy123 said:**
> How can you be sure windows isn't just switching between (for example) 50% and 100% very quickly, and therefore showing 75%.  I know for sure that windows Vista averages the CPU speed when you view it onscreen so it looks like it can go at any speed, when in fact that isn't the case.

If you're right and Ubuntu isn't doing CPU scaling correctly, it would be great if you could collect a list of the possible levels from windows, and the same from linux, compare the two, identify the frequencies that Ubuntu doesn't allow, and report it as a bug together with all the relevant logfiles and as much information about your system you can find.

PS. have you tried turning compiz (desktop effects) off?  It might make the fans considerably quieter.

Again, thanks for the compiz advice, it probably was the extra load that compiz brings. But I am pretty sure about the frequencies as there is a way to list the available frequencies on your CPU. don't remember the command at the moment, but its something obvious, i'm sure. good idea about reporting as a bug though, thanks again.

---

