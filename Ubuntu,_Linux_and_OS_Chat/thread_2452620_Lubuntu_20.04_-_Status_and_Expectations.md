---
title: "Lubuntu 20.04 - Status and Expectations"
date: 2020-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by electrosteam on 2020-10-26
My first Linux experience was old version of Mandrake, then Re Hat for a short period, then Lubuntu 17.10, all on old (2002/4) hardware.
Now Lubuntu 18.04.2 on my new Hp Laptop, and loving it.

Got a 2012 desktop for my workshop and tried Lubuntu 20.04 on it.
It seems a bit sluggish, and FireFox crashes after 20 minutes.
Put 18.04.2 on it, and its fine.

I need to resolve the OS by April next year.
Should I wait for Lubuntu 20.4.1/2, or try other flavours ?

Keep well,
John.

---

### Post by guiverc on 2020-10-26
You've provided few details as to what the problem could be.

Lubuntu 20.04.1 has been released already, see [https://lubuntu.me/focal-1-released/](https://lubuntu.me/focal-1-released/)

My system is a 2009 dell, and currently is running Lubuntu *hirsute* (*what will become 2021.April in roughly six months*).

My system is *stable* for me, and has been since its installation (mid-2017).  I upgrade every six months as I sit on the *development* cycle.  But I know my hardware is good, and if I have a problem (*software configuration etc*) I usually explore & work out the cause and fix it.

If it's a desktop you didn't know, my first step is not to install an OS on it, but run ram tests for a couple of days to ensure it's pretty reliable & has no issues. If the RAM tests fail for any reason (be it faulty ram, or some other cause inc. *iffy* *caps* (*swollen capacitors*) it will show by a unreliable/crashed/frozen system (RAM is usually detected by errors). Did you do any of this to validate your hardware?  My first install is again just in testing, where I tend to again try nd push the hardware, before I fresh-install the system I intend to keep.

How much RAM do you have?   Myself I prefer this c2q-9400 desktop system over a newer  i5-m520 (laptop) as this outperforms it due to having more RAM, let alone the *form factor* aspects that I prefer.

My first question is did you evaluate the hardware in any way?   Like ram tests I mention, or did you open it up & visually inspect looking for issues like the *caps* I mentioned?

If 20.04 has issues, yet 18.04 was different; were you using the same kernel? ie. a Lubuntu 18.04.5 LTS with HWE enabled will be using the 5.4 kernel used by 20.04), however a Lubuntu 18.04.5 LTS system using the GA kernel will be using the 4.15 kernel. Which were you using?  (the ISO used to install the system will dictate if HWE is enabled by default, or the GA kernel is used). We don't have those specifics (*18.04.2 media will upgrade itself post-install to 5.4 though it starts with the 18.10 or 4.18 kernel at install time, but you weren't explicit on what you did*).

---

### Post by mastablasta on 2020-10-26
depends on what the issue is. if the issue is GPU drivers then newer version might resolve it or if computer is old it might continue with errors (because drivers are part of kernel). 

a good way would be to identify the issue, see if there is a solution and if there isn't (if there is a bug), report the bug to launchpad.

for example, Lubuntu moved to LXQT which is quite new and under heavy development. if the issue is related with desktop environment itself then it will gradually improve.but if the issue is because proper GPU drivers got dropped by manufacturer then it might never get resolved.

Have a look at this if you want to continue: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

right now, i am not sure what the issue is. you can always try a different desktop if this is what you think is causing the problem. ubuntu has:
Ubuntu Mate, Xubuntu, Kubuntu, Ubuntu Budgie...

There is also LXLE if you want to stay on Lubuntu (lubuntu with extended support)

if you are after light distros you can also look at AntiX and MX Linux. Bodhi linux is ubuntu based and very light using Enlightenmet.

if you want to stay in ubuntu environment, then Linux Mint with mate might be good option.

---

### Post by electrosteam on 2020-10-28
Thanks for the responses, I certainly did not expect any technical assistance in this part of the Forum.

I have taken everything said on board and tried to start assessing the hardware.
Any future questions I may have on the hardware I will post in the appropriate hardware section of the Forum.

But, I have completed 30 passes of the memtest86+ ( 45 hours ) without any errors.
And smartctl seems happy.
Investigations are continuing.

Perhaps I was a bit hasty in suggesting I try other flavours.
Lubuntu 18.04 has always done everything I need, and I am sure 20.04 will do that also if I give it a chance. 

Keep well,
John.

---

