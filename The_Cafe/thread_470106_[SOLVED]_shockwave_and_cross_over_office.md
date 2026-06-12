---
title: "[SOLVED] shockwave and cross over office"
date: 2007-06-10
forum: The Cafe
---

### Post by scrooge_74 on 2007-06-10
Just to comment on something that just happen to me.

I have to help my wife complete one of those Rosetta Stone interactive courses for a exam, but the program requieres Shockwave to run. Since I have Cross Over Office already installed and IE6, I was thinking to just install it through Cross Over.  It would install ok, but seems the system would try to run, but IE6 would end up crashing.

By cheer luck (or mistake) I had the same page from which I needed to launch the Shockwave program opened on Firefox and  I just cliqued on by error, it open an extra window and on top it said it needed to install a plugging (obviously it was asking for Shockwave), but I said no since I know there is no Shockwave for Linux. For my surprise I see the Shockwave logo bar loading something and I decided (what the heck!) to let if finish and see what happened.

To my surprise it seems Firefox opens the extra window for the Rosetta Program and is probably launching Cross Over because Shockwave is working and is letting me do the exam even though Firefox asked me for the pluggin.

Any body has had  a similar experience? Is this something worthy of reporting?

I was almost ready to give up and go get another PC we have that has windows install in order to do the exam.

---

### Post by init1 on 2007-07-24
> **scrooge_74 said:**
> Just to comment on something that just happen to me.

I have to help my wife complete one of those Rosetta Stone interactive courses for a exam, but the program requieres Shockwave to run. Since I have Cross Over Office already installed and IE6, I was thinking to just install it through Cross Over.  It would install ok, but seems the system would try to run, but IE6 would end up crashing.

By cheer luck (or mistake) I had the same page from which I needed to launch the Shockwave program opened on Firefox and  I just cliqued on by error, it open an extra window and on top it said it needed to install a plugging (obviously it was asking for Shockwave), but I said no since I know there is no Shockwave for Linux. For my surprise I see the Shockwave logo bar loading something and I decided (what the heck!) to let if finish and see what happened.

To my surprise it seems Firefox opens the extra window for the Rosetta Program and is probably launching Cross Over because Shockwave is working and is letting me do the exam even though Firefox asked me for the pluggin.

Any body has had  a similar experience? Is this something worthy of reporting?

I was almost ready to give up and go get another PC we have that has windows install in order to do the exam.
Weird. I can't explain that.

---

### Post by scrooge_74 on 2007-08-23
Update on this, IE works under cross over can manage the Rosetta website after a fix I was sent and under the next update of Cross Over.  Still Firefox keeps using Shockwave no problem for this site

---

### Post by Antman on 2007-08-31
> **scrooge_74 said:**
> Update on this, IE works under cross over can manage the Rosetta website after a fix I was sent and under the next update of Cross Over.  Still Firefox keeps using Shockwave no problem for this site

Hmm... I wonder if it will work for shockwave on the Cosmeo.com site?!? I have to install Crossover and try it...

Thanks,

Ant

---

### Post by Syke on 2007-08-31
For Shockwave, I use a standard WINE install from the Ubuntu repositories, run the Windows FireFox installer, then run the Shockwave installer for Windows FireFox. No need to buy anything. Works great.

---

### Post by SunnyRabbiera on 2007-08-31
> **Syke said:**
> For Shockwave, I use a standard WINE install from the Ubuntu repositories, run the Windows FireFox installer, then run the Shockwave installer for Windows FireFox. No need to buy anything. Works great.

yeh there are times normal wine will work better then crossover, and sometimes its the other way around.
But wine has gotten a lot better lately if you ask me, its a lot better then it used to be for beginners as some of its newer tools are great... still would have a copy of crossover on the side of course as I personally think wine still needs some brushing before I can use it fully.

---

### Post by scrooge_74 on 2007-08-31
In most cases I just use wine (but since I paid for CXO I just use it).  Last year Peachtree accounting was working fine on wine, a few updates later it was not working any more, but CXO was working.  Lately bugs are less in Cross Over so it works better.

I few games run better in wine still

---

### Post by Andrewie on 2007-08-31
I haven't used cross over office in awhile but I believe it provides all your windows plugins to your native Linux browsers

---

### Post by scrooge_74 on 2007-09-01
> **Andrewie said:**
> I haven't used cross over office in awhile but I believe it provides all your windows plugins to your native Linux browsers

That will seem right since i was able to use Shockwave on Firefox

---

### Post by lns on 2007-09-27
> **scrooge_74 said:**
> That will seem right since i was able to use Shockwave on Firefox

I found this thread searching for the same type of thing - I run a fairly elaborate setup - Ubuntu Server (AMD64) as an LTSP server for 35 student lab computers (i386 chroot).

In researching the Shockwave/Linux issue, all I got before was that, with Wine, you had to install the Windows version of FF for it to run. I thought this was kind of bogus...then I heard that with Crossover Office you could run Windows browser plugins under Linux browsers..I installed the trial version of CXOffice Pro, and to my amazement, Shockwave seemed to be working great under Firefox (again, running from a 64-bit server to 32-bit clients!). It couldn't have been easier...the thing is, with the amount of licenses we need, the bill will be pretty hefty.

Does anyone know of a way to do the same thing under Wine?

---

### Post by Andrewie on 2007-09-27
> **lns said:**
> I found this thread searching for the same type of thing - I run a fairly elaborate setup - Ubuntu Server (AMD64) as an LTSP server for 35 student lab computers (i386 chroot).

In researching the Shockwave/Linux issue, all I got before was that, with Wine, you had to install the Windows version of FF for it to run. I thought this was kind of bogus...then I heard that with Crossover Office you could run Windows browser plugins under Linux browsers..I installed the trial version of CXOffice Pro, and to my amazement, Shockwave seemed to be working great under Firefox (again, running from a 64-bit server to 32-bit clients!). It couldn't have been easier...the thing is, with the amount of licenses we need, the bill will be pretty hefty.

Does anyone know of a way to do the same thing under Wine?

I believe they have a server version that you can use for all of your clients, I but I'm not 100%

---

### Post by lns on 2007-10-15
Not really what I was looking for...I'm talking about getting Windows Shockwave plugin working under wine/LINUX version of Firefox... The Crossover plugins work great, but the licensing fees...well, we might as well go buy Windows licenses at that point.

> **Andrewie said:**
> I believe they have a server version that you can use for all of your clients, I but I'm not 100%

---

### Post by TechZilla on 2007-12-26
> ...well, we might as well go buy Windows licenses at that point.

ok i honestly do not belive that the licence for crossover office is ANYWHERE neer the price for windows itself.  but with that aside....

unfortunatly nobody has programmed a "wine" browser pugin like the crossover one.  it just has not been done yet......with all the licensing costs combined you could prolly pay a programmer to write the plugin Open Source.

---

