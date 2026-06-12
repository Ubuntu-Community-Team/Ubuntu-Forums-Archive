---
title: "Why does Ubuntu slow down after long use?"
date: 2008-06-05
forum: The Cafe
---

### Post by PrimoTurbo on 2008-06-05
I noticed after installing some applications, unzipping some files my computer comes to a crawl. I cannot use it, I have to restart.

Does this happen to anyone else?

---

### Post by D.Sync on 2008-06-05
Perhaps it's your computer spec?

Been using Ubuntu 8.04 for almost a week now and it's running fast too.

---

### Post by barbedsaber on 2008-06-05
when it is slow as hell, post the result of

```
top
```

(it will keep changing, don't worry about that, it is normal)

---

### Post by klange on 2008-06-05
On rare occasions I've had major slow downs, it's usually because a notoriously naughty app went zombie.

---

### Post by beercz on 2008-06-05
I've been using Ubuntu since Warty, almost daily, and I haven't noticed any slowdown at all.

---

### Post by melrom on 2008-06-05
the only time Ubuntu starts running slow for me is when my computer gets really hot, which would cause Windows to slow down too. Anyway, with Gutsy, I felt that my computer was psuedo-overheating, but with Hardy, I don't experience this at all.

---

### Post by Sealbhach on 2008-06-05
For me, Firefox is very slow starting up, other than that it's quite fast.


.

---

### Post by Ozor Mox on 2008-06-05
I've found that this is usually an application that has gone a bit crazy and is eating all the system resources. Just ten minutes ago, applications were taking several seconds to switch, music was skipping, the screen wasn't redrawing properly etc. Quick check of top showed that Nautilus was taking up 80% of my 1 GB of RAM even though it wasn't even open on my desktop, as I had crashed it earlier. One sudo kill -9 later and everything was back to being nice and fast again!

---

### Post by Bungo Pony on 2008-06-05
I had this problem in Gutsy. I had a lot of problems in Gutsy. After moving to Hardy, things seem to be behaving better.

---

### Post by MaximB on 2008-06-05
I advise you to add "system monitor" to your panel.
(mice over top panel >> add to panel >> chose system monitor).
And also as been said before when your PC is crawling post the "top" output.

---

### Post by Keith Hedger on 2008-06-05
when using top I find it best to use ```
top -bn1
``` as this gives a snapshot of whats happening and then exits (otherwise u have to CNRL-C to quit top)

---

### Post by lobo-tuerto on 2008-06-07
I never had this kind of problem with Gutsy, but now I'm experiencing severe slowdowns everynow and then.

The offending process seems to be a combination of whatever is running and xorg.

For example xorg and firefox, xorg and nautilus, xorg and transmission, xorg and rythmbox.

I don't know what to do :(

---

### Post by Sam on 2008-06-07
> **beercz said:**
> I've been using Ubuntu since Warty, almost daily, and I haven't noticed any slowdown at all.

Same here.

---

### Post by PmDematagoda on 2008-06-07
I've been using Ubuntu 7.04 for about 8 months or so, and I don't think anything has suffered more that that particular system had. The amazing thing is that the OS still works(really surprising) and it works at the same speed it did when it was in mint condition. The only slowdown it has experienced is in the boot-up process where it has to load a huge conundrum of different and useless modules(I need to clean that up someday).

---

### Post by FuturePilot on 2008-06-07
I've never had Ubuntu slow down on me. The only way it might slow down slightly after a lot of use is if you're using a lot of swap. Then it might take a little longer to load stuff since you have to reload it from swap.

---

### Post by sports fan Matt on 2008-06-07
I havent had any slowdowns either.  The only slowdowns I've had are when sites like [www.wgnradio.com](www.wgnradio.com) just stay at a connecting state, but thats Dave Manzullo's fault (their webmaster) .  They must be updating the website as far as connections and such.

---

### Post by DM was on fire! on 2008-06-07
I'm on 6.06 Dapper and I haven't experienced any slowing down.

---

### Post by isaacj87 on 2008-06-07
> **melrom said:**
> the only time Ubuntu starts running slow for me is when my computer gets really hot, which would cause Windows to slow down too. Anyway, with Gutsy, I felt that my computer was psuedo-overheating, but with Hardy, I don't experience this at all.

Same here for me...I notice that my lappy starts to drag when it gets a little hot.

---

### Post by tasos on 2008-06-11
I installed feisty when it was first released (about 1,5 year ago??) and then I upgraded to gutsy and i'm using this installation ever since. I am experiencing slow downs during my session load not boot-up. I checked my start-up programs but they didn't explain the slowdowns..

ps the first 8-12 months I didn't have slowdowns..but after that..slowly..you get the point:-P
when i have time I'll upgrade to hardy and see if there is difference in speed

---

### Post by Robux the great on 2008-06-11
I have been using Ubuntu for a couple of years noe and I have never had a problem with the OS slowing down.

Regards

Rob

P.s Buy some decent hardawre

---

### Post by BDNiner on 2008-06-11
The only time ubuntu runs slow for me is when i turn it on for the first time. I can hear my HDDs spinning as i guess the system is trying to cache the desktop in memory. For example i have no icons in my gnome menu at first but after about 4 seconds they appear. The first time i open an application this is repeated. But after that things run smoothly.

---

### Post by init1 on 2008-06-11
Ubuntu is extremely slow for me. It takes about a minute and twenty seconds to boot, and apps take forever to launch. I get far better performance from Debian Etch.

---

### Post by fsantos on 2009-04-04
I have just started trying Ubuntu and because I know nothing about Linux I've installed it on a older PC, cause I didn't want to mess with my laptop.
The Pc is a AMD Athlon xp 1800+ with 755MB of RAM (not DDR), and ubuntu was installed in a partition of 10GB and a swap memory of 713MB was created.
I'am getting huge problems with slow downs. After awhile it gets really slow, to the point that it's unusable.

In other partition of the same pc i run Win XP fine.

Maybe ubuntu doesn't support very well this old system. Does any one Know?

---

### Post by billgoldberg on 2009-04-04
> **PrimoTurbo said:**
> I noticed after installing some applications, unzipping some files my computer comes to a crawl. I cannot use it, I have to restart.

Does this happen to anyone else?

I don't like the title of this thread.

You seem to be implying that Ubuntu slows down, Windows style,  after using it for a while. 

That off course isn't true.

Unzipping big files could cause slowdowns, that will stop when the file is ready unzipping.

---

### Post by mamamia88 on 2009-04-04
haven't noticed any slow down here

---

### Post by wolfen69 on 2009-04-04
> **fsantos said:**
> 
Maybe ubuntu doesn't support very well this old system. Does any one Know?

there are 100's of other distros out there. don't be afraid to try something else. [www.distrowatch.com](www.distrowatch.com)

and please, don't compare xp's performance to a modern OS. when xp first came out, a lot of people still had 128mb ram. it's almost 9 yrs old.

---

### Post by leandromartinez98 on 2009-04-04
I have Ubuntu running on a Pentium 4 with 500 mb of RAM and it works. We have machines running Ubuntu for months now without rebooting and there is no slowdown. The point is: if you are experiencing slowdowns, you either have a software or hardware problem, so please post what people is asking you for:

1 - The result of the "top" command during a slowdown. By the way, if there is no job consuming CPU at this point, you probably have a hardware problem.
2 - Check if your CPU is not overheating.

Otherwise, this thread is useless. Ubuntu, or any other disto, should not slowdown normaly.

---

### Post by Mason Whitaker on 2009-04-04
I've been running Ubuntu for about a year now, and no noticeable decrease in speed.

You must have a hardware problem

---

### Post by Dale61 on 2009-04-04
I've been running 8.04 since the day of it's release, and have never had any 'slow down' of my system, but, on occasion, I have had Firefox shut down unexpectedly, and without warning.

---

### Post by Mattatk on 2009-04-05
> **klange said:**
> ...it's usually because a notoriously naughty app went zombie.

Wow, now I'm intrigued. How exactly exactly does an app go zombie, and what does it do to your system? Ubuntu has run relatively smooth for me.(sometimes booting speed differs, but likewise with windows.)

---

### Post by xtracool_protik on 2009-04-05
Hi,
 Here is my experience - 
 I had same issue and top revealed that it was majorly due to firefox.
 Keep firefox open for a night (maybe with some flash and java script
 working or around 25-30 tabs open). And u'll find CPU usage 90-98%.
 Also few effects of compiz (fire circle around mouse pointer)does the same
 thing but its not as severe as firefox.

 So now I do is compulsorily close all the tabs and firefox while putting laptop in the hands of boinc and that helps a lot, U may wanna try it

---

### Post by pbpersson on 2009-04-05
> **Mattatk said:**
> Wow, now I'm intrigued. How exactly exactly does an app go zombie, and what does it do to your system? 

An application can get stuck in a loop or can have a memory leak.

It would cause your system to slow down or perhaps even eventually crash.

One would hope that in the 21st century one application could not crash your entire system.

You should NOT need to reboot the system.  People here have up times measured in months.

You can use system monitor to view the applications using the most resources.  Then you can right-click on the application and kill it.  Warning - this might cause a loss of data if the application has files open.

---

### Post by diablo75 on 2009-04-05
It might have something to do with the programs you've installed.  I remember using Ubuntu Ultimate 1.2 (or was it 1.3) a few years ago as the very first Ubuntu I installed on my computer (and first Linux distro since SuSE 6).  Come to think of it, the only reason I liked Ubuntu Ultimate at the time was because Automatix actually did something useful back then.  But a while after I gained confidence in installing software myself, installed a clean official copy of Ubuntu 7.04 and was shocked by how much faster it was by comparison.  The non-official Ultimate was just weighed down by too many extra services running in the background, I guess.

Anyway, since I started using Ubuntu over three years ago, I'm happy to say I've never experienced a slowdown that is typical Windows PCs after a year or more of regular usage.

---

### Post by kimason on 2009-04-05
I have just recently installed Ubuntu in my laptop for the sake of trying it as a means of something new. So far I have not had similar problems such as you have. I guess its a problem of system specification in your computer that is.

---

### Post by ssam on 2009-04-05
if apps are slow to start, make sure you have at least 1GB of RAM and install [preload]("apt:/preload")

---

### Post by fsantos on 2009-04-05
I know that under normal circumstances I cannot compare the performance of win xp with the latest version of ubuntu. The only reason i did it was because I felt that something wasn't right. If a OS is to heavy for an old system it should be from the start, i think, and when ubuntu starts on my desktop it's ok, for a while. I didn't open lot's of applications to make it run slow, just things like a firefox single tab and a mp3 playing was enough one time, and didn't took a long time like the topic says. I have also tried ubuntu from the boot on my laptop and no slow down. And I must mention that on the laptop (Pentium M 1.8Ghz 1GB RAM DDR) it run with the environment visual effects and on the old desktop ubuntu wouldn't even let me select that option. 
So that's why I thought my desktop wasn't able to run ubuntu smoothly, and why I searched for info and read that more people were having similar problems.
I hope that people reading these posts don't get the idea the ones posting this problems here are trying to say that ubuntu is crappy, I don't think that. I just wanted to understand the problem.

I have to say that I like ubuntu environment very much and I'm just starting myself in linux. I'm going to replace my old desktop soon and probably use it's 40GB hard drive on the new one for ubuntu. Hope then things go well. :-P

---

### Post by hessczoo on 2009-04-05
You see the Linux kernel isn't like the Windows kernel. The Windows NT kernel caches all your RAM and then keeps it, and applications have a hard time getting at it. So that is why it slows down, and why you have to restart to speed back up. Never in all my experience has Ubuntu slowed down at all. Try running ```
top
``` in a terminal and see what application is eating up all your resources.

---

### Post by leandromartinez98 on 2009-04-05
Depending on your video card the desktop effects should not be activated, that can slowdown your system. Anyway, if you continue to have the slowdown problem, that means, the computer starting fast and getting slower with time, please post the result of the "top" command, so someone can help you to identify it.

---

### Post by majamba on 2009-04-05
don't know but the applications and boot time seems to be running pretty fast. offcourse 9.04 blazzing fast

---

### Post by t0p on 2009-04-05
> **DM was on fire! said:**
> I'm on 6.06 Dapper and I haven't experienced any slowing down.

Dapper's really old.  That "6.06" means it was released in June 2006.

I'd suggest Hardy - that's the latest LTS.

---

