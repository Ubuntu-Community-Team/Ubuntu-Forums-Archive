---
title: "Ubuntu's efficiency"
date: 2010-10-20
forum: The Cafe
---

### Post by Oxwivi on 2010-10-20
How efficient is Ubuntu in terms of power consumption? How would it compare to other OS like Windows, Mac, et al?

If possible, please be as detailed as possible as this data is going to be used in presentations and whatnot.

[[IMG]http://brainstorm.ubuntu.com/idea/26192/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/26192/)

---

### Post by Npl on 2010-10-20
depends on the hardware & drivers. xorg, kernel and drivers all have various features and interfaces for power-managment which seem to be constantly changed, broken and turned incompatible to each other.

Other OSes have the big benefit of a single entity crafting a working model so it usually just works.

If you want an actual comparison: [http://www.phoronix.com/scan.php?page=article&item=linux_windows_part2](http://www.phoronix.com/scan.php?page=article&item=linux_windows_part2)

---

### Post by Oxwivi on 2010-10-20
This is discouraging. I was thinking of using this data to convert more people to Ubuntu, with a LoCo still in planning stage.

---

### Post by Spice Weasel on 2010-10-20
It's as efficient as you make it. That's the beauty of Linux. You want low power consumption, you install a lighter desktop environment, disable background processes and remove unneeded kernel modules and drivers.

---

### Post by NightwishFan on 2010-10-20
To be honest, if you have liked hardware, power consumption is great. My Asus laptop gets over an hour more than it's advertised battery life with Ubuntu.

As for workload efficiency, I doubt you will do better than Linux for getting rendering done, downloads, long uptime etc. Ubuntu also makes it easy to patch and compile software included for different purposes however that is for advanced users.

---

### Post by Oxwivi on 2010-10-20
Yes, I realise what makes Linux so great, but for the regular out-of-the-box users, they are unlikely be able to do such customisation to minimalise power consumption. And killing processes without shutting down the PC itself requires a level of expertise to know what does what, a level I've yet to reach myself.

Power consumption being what it is, I'm surprised it hasn't received any attention with all the world clamoring to prevent global warming and whatnot. If it's proven that Linux and Ubuntu is far more efficient than any other big OSes like Windows and Mac, it's gonna be a big puller. Global warming and other environmental factors are not the only thing that's making people efficiency-conscious, but also the costs.

---

### Post by NightwishFan on 2010-10-20
Generally on some machines it is not more power efficient, at least not without a bit of work. Some hardware does not support auto-suspend etc.. If you luck out and have the kind of hardware that all works, I am quite sure you can get some fairly good power saving.

Here is my laptop on maverick's current reading (over a 15 second period):
```
Power usage (ACPI estimate): 9.7W (4.6 hours)
```

---

### Post by Oxwivi on 2010-10-20
As I stated in my first post, I'm thinking of using a general data to convert people. So, for now, out-of-the-box efficiency matters to me.

I've posted an Ubuntu Brainstorm idea to support efficiency, I hope you guys will vote for it once it's approved.

---

### Post by NightwishFan on 2010-10-20
In my opinion the biggest upside right now is freedom of use and freedom to change. Our time will come where we can really rival an OS like Windows. It many ways we already do, however at the moment some folks just risk being frustrated.

From my experience people are not fair with blame. (When Windows has a problem its a computer problem, when Ubuntu has a problem its an Ubuntu problem)

---

### Post by red_Marvin on 2010-10-20
I would guess, without having data to back it up, that the hardware
chosen is much more important than the os when it comes to what
impacts the power consumption.
  However as linux can be made to run on a wider range of hardware, if one
only need to do low intensity computing, it would be possible to do so
comfortably on a power efficient, but low spec machine with linux, where
windows would not run.

But there isn't *one linux*, to compare with windows and mac, as linux
can be tailored to everything from clustered supercomputers to embedded single
chip computers, the power consumption will vary accordingly.

On the other hand, afaik motherboard manufacturers are still not playing
nice when it comes to acpi stuff, so most likely an average linux system
will be worse off than one with windows installed.
  On top of that, if you need flash, note that adobe's linux version often
makes the cpu run at 100% even if not needed. Depending on what one uses
the computer for that may have an impact.

---

### Post by Oxwivi on 2010-10-20
Even so, *Ubuntu*'s efficiency definitely needs working on. For regular users there's no way to just run a GUI and see what processes are running, and same goes for start up. System Monitor and the Startup Applications applet doesn't help in this. So there's no way I can just say that if you do this it becomes more power efficient than the alternatives, so Ubuntu us the best choice.

Ubuntu's out-of-the box settings really needs working on. Due to the lack of customisability on installation, it creates a software bloat with softwares some people are never going to use and thus affect processing and consumption. While I understand that this to keep true to the statement that there's free software for everything, they should also realise that not all of us do 'everything'. At this rate, it'll just turn out like Windows with loads of bloatware.

Furthermore, I get the impression that even with everything they are delivered, it could be a lot less chunky. Ubuntu is quite bloated compared to other distros.

---

### Post by NightwishFan on 2010-10-20
> **Oxwivi said:**
> Furthermore, I get the impression that even with everything they are delivered, it could be a lot less chunky. Ubuntu is quite bloated compared to other distros.

I disagree heavily. It has a similar package selection to Fedora, and less than OpenSUSE and Debian. You might consider a few things such as the USB Creator, System Testing, and Ubuntu One extra, however it is by no means bloat. Which is a ridiculous word anyway. :)

I think being clean and neat is fine, however it is quite a good bit of functionality out of the box for one cd.

---

### Post by del_diablo on 2010-10-20
> **Oxwivi said:**
> Yes, I realise what makes Linux so great, but for the regular out-of-the-box users, they are unlikely be able to do such customisation to minimalise power consumption. And killing processes without shutting down the PC itself requires a level of expertise to know what does what, a level I've yet to reach myself.

For most users, they will never reach that.
They will never reach that on Windows or OS X either, so the argument is .... moot?
Besides: It all falls on how poorly the BIOS is coded, and what drivers and firmware is availon.

---

### Post by 3Miro on 2010-10-20
We should also remember that no hardware comes with generic windows installed. Laptops that ship with windows usually have special drivers and settings made by the manufacturers/vendors. Any Linux distro can be adjusted/modified, however, this not a task for every user out there.

Only a few vendors sell Linux preinstalled. I got a System76 laptop, but it had an overall short battery life due to the great power consumption of the powerful video card and CPU. 

Ultimately, I think hardware makes a bigger difference in power consumption.

---

### Post by gvoima on 2010-10-20
> **del_diablo said:**
> Besides: It all falls on how poorly the BIOS is coded, and what drivers and firmware is availon.

That is true, linux has great support for standard based acpi and such powersaving rutines, it's just that most of the hardware makers do it as they see pleased and release a windows driver for it.
So the only thing left for the community is to reverse engineer and that's about it..
e.g. Intel is great at releasing its specs for the hardware, and linux has great support for it.

---

### Post by Simian Man on 2010-10-20
Yay for forming opinions and then only looking for data that supports those opinions.  If everyone took that approach, we'd still be in the dark ages.

---

### Post by nlsthzn on 2010-10-20
> **Simian Man said:**
> Yay for forming opinions and then only looking for data that supports those opinions.  If everyone took that approach, we'd still be in the dark ages.

Ah, I see Mr. Windows is here again... "Hello Mr. Windows..."

However I do agree with you here... what you say here is true, +1 for you...

As for the topic at hand unfortunately my first hand experience has been that the optimized drivers for my hardware means they run more efficient power-wise under Windows than GNU/Linux currently... there are exceptions to this rule but not many which I have found yet...

---

### Post by wojox on 2010-10-20
Don't try to convert anyone. Just make a few Live CD's and hand them out. :)

---

### Post by Oxwivi on 2010-10-20
> **wojox said:**
> Don't try to convert anyone. Just make a few Live CD's and hand them out. :)
LoCos would do nothing other than burn tons of CDs if that was enough...

---

### Post by cariboo on 2010-10-20
Hold install fests, if they want it they will come.

---

### Post by Oxwivi on 2010-10-20
And how would 'they' know of what Ubuntu is? Me and someone else are still discussing setting up the LoCo and the initial members would be numbering around five at most. I've been trying to convince him to conduct presentation at schools and doing other stuff, but he's still skeptical.

And for such presentations I created this thread intending on gathering data on how efficient Ubuntu would be and advertise it...

---

### Post by Simian Man on 2010-10-20
> **Oxwivi said:**
> And for such presentations I created this thread intending on gathering data on how efficient Ubuntu would be and advertise it...

But, Linux isn't any more efficient than Windows or OSX.  I don't believe in proselytizing (especially for something as mundane as an operating system), but if you do, at least don't lie!

---

### Post by Oxwivi on 2010-10-20
I was stating my intentions, of course now that I know I can't say UBuntu isn't efficient, my plans are dashed.

---

### Post by NightwishFan on 2010-10-20
It is, just not in a miraculous sort of way. :) Also take things said with a grain of salt. Yes, you can advertise Linux and Ubuntu. I agree do not lie though (not saying you were). There are many many reasons you could advertise GNU/Linux for. Something like this is a start:
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

---

### Post by whiskeylover on 2010-10-20
On my laptop, Windows gives me better battery life than Ubuntu.

---

### Post by NightwishFan on 2010-10-20
By default, same here I get about 3/4 the battery (I know someone with this laptop and w7 to compare to). With a few tweaks I get 5/4. :D

---

### Post by Oxwivi on 2010-10-21
What are those few tweaks? And the info was not only to draw attention to the OS, I was also planning to use it to fund the LoCo.

---

### Post by Oxwivi on 2010-10-21
Ah, I can use the Environment section on the link you provided, thanks.

---

### Post by NightwishFan on 2010-10-21
The program powertop enables a few tweaks once at runtime (reverted on reboot).

---

### Post by Johnsie on 2010-10-21
I think the problem with power managemenet on Ubuntu is that there isn't a centralised GUI tool to manage it properly. Windows has a much more user friendly way of managing power that is the same on nearly every machine.

I get more time when I use Windows on my netbook. Also, sometimes Ubuntu runs very hot on laptops and this can cause hardware failure to happen sooner.

---

### Post by Oxwivi on 2010-10-21
> **NightwishFan said:**
> The program powertop enables a few tweaks once at runtime (reverted on reboot).
Reverted on reboot? Just what changes does the software make?

---

### Post by NightwishFan on 2010-10-21
Powertop is a command line program made by Intel. It is in the repositories. It analyses your computer to reveal wakeups, such as a cpu/disk hungry app. It also does common tweaks such as enabling device autosuspend when unused, reduce wireless performance for power, etc. I can go from around 3:30 to 5:30 with the tweaks. Results may vary of course, I have the "friendly hardware" I spoke of.

---

### Post by Oxwivi on 2010-10-21
Tell me all you know about it, please. :)

---

### Post by mörgæs on 2010-10-21
When you say power consumption, are you thinking in a green perspective or is it a matter of getting longer battery life?

---

### Post by NightwishFan on 2010-10-21
I do not know much more. Basically just run it as root and press the corresponding key for it's suggestions every time you are on battery. Here is a faq: [http://linuxpowertop.org/faq.php](http://linuxpowertop.org/faq.php)

---

### Post by Oxwivi on 2010-10-21
> **mörgæs said:**
> When you say power consumption, are you thinking in a green perspective or is it a matter of getting longer battery life?
Both.

---

### Post by mörgæs on 2010-10-21
For the green perspective, what matters is the possibility of using old hardware rather than producing new. There is a heavy environmental footprint in building IT gear.

---

### Post by Oxwivi on 2010-10-21
Hmm... so far, other than the stock Ubuntu's power consumption, all the other factors are advantageous... Good!

---

### Post by Oxwivi on 2010-11-04
Please vote in my Brainstorm idea!

[[IMG]http://brainstorm.ubuntu.com/idea/26192/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/26192/)

---

