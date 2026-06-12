---
title: "Ubuntu At My Workplace."
date: 2011-12-05
forum: The Cafe
---

### Post by Roasted on 2011-12-05
My "workplace" is referencing Penn Manor School District in Pennsylvania where I am a member of the IT staff. I think many of you may be interested in reading how the Ubuntu idea spawned and how it's been working for us in the classrooms.


Part 1 - [http://www.pennmanor.net/techblog/?p=817](http://www.pennmanor.net/techblog/?p=817)
Part 2 - [http://www.pennmanor.net/techblog/?p=841](http://www.pennmanor.net/techblog/?p=841)
Part 3 - [http://www.pennmanor.net/techblog/?p=891](http://www.pennmanor.net/techblog/?p=891)
Part 4 - [http://www.pennmanor.net/techblog/?p=992](http://www.pennmanor.net/techblog/?p=992)

Personal side note: **I love my job.**

---

### Post by IWantFroyo on 2011-12-05
Congrats! Do you think the computers would have been running Ubuntu if Apple didn't kill the standard Macbook line?

I'm waiting to see what the school I go to will do with the computers. We have ancient Dell laptops that run XP Pro and need a huge battery pack to wheeze through the day. Plus, they all have "Windows Vista" stickers, meaning the school may have had to buy Windows twice for each laptop.

---

### Post by nmaster on 2011-12-05
that is awesome!  it makes me happy that you're showing the benefits of linux and open source.  

you mention briefly that the thinkpad x120e didn't work perfectly out of the box on 11.04.  does it work on 11.10? how often do you upgrade?  i have zero experience with large scale deployments like this and wondering how the logistics work out...

---

### Post by keithpeter on 2011-12-05
Hello Roasted

This is excellent stuff. I'm assuming you are using Xubuntu 11.04?

I'd like to know what training and support the teaching staff needed to make the transition from Mac OS X to XFCE, and for the change in applications.

Any plans to investigate the Unity interface when 12.04 comes on stream? Or will you simply upgrade to Xubuntu 12.04?

---

### Post by Roasted on 2011-12-05
> **nmaster said:**
> that is awesome!  it makes me happy that you're showing the benefits of linux and open source.  

you mention briefly that the thinkpad x120e didn't work perfectly out of the box on 11.04.  does it work on 11.10? how often do you upgrade?  i have zero experience with large scale deployments like this and wondering how the logistics work out...

From what I understand, what didn't work properly was the wireless for some reason. The packaged drivers out of the box (Realtek if memory serves me) were problematic and they had to dig them off of Realtek's site somewhere. The initial deployment was prior to me starting my position, but if memory serves me, that's what the scoop was.

I have an X120e running dual boot, with an 11.04 image that we run in classrooms along with 11.10 that I use often. Aside from the obvious proprietary ATI driver issue that came about recently, I've seen no graphical issues running Gnome Shell with the open source ATI drivers. I cannot seem to get HDMI out to work using the open source drivers, however that's a feature we are likely to never utilize in our environment. It was more of a curiosity thing on my part. Wirelessly speaking, I've had no issues with 11.10.

Since this idea was fresh and new, 11.04 was chosen since that was the most recent at the time. It's likely that 12.04 will be with us for quite a long time once it is released and has been out for a few weeks/months, especially considering 12.04 introduces a 5 year support cycle.

> **IWantFroyo said:**
> Congrats! Do you think the computers would have been running Ubuntu if Apple didn't kill the standard Macbook line?

I'm waiting to see what the school I go to will do with the computers. We have ancient Dell laptops that run XP Pro and need a huge battery pack to wheeze through the day. Plus, they all have "Windows Vista" stickers, meaning the school may have had to buy Windows twice for each laptop.

I don't think it would have made a difference. Speaking strictly from personal opinion here: I think the educational discount train simply left the Apple station at a time when districts needed them most. Apple gear is decent, nobody can deny that, but the price to support it is very difficult to do, especially now with all of the cut-backs educational institutions are trying to come to terms with. Couple the fact that Linux based software and countless open source alternative applications are free or very cheap along with the fact they're rock solid and you have a "what do I have to lose?" situation on your hands.

About the Windows situation: It's likely they paid for Windows twice. I believe my last job essentially did the same thing, as systems were coming with Vista and 7 as part of the price when we were formatting them to XP Pro. I think most businesses don't look at it as double payment, though, due to the fact most places consider a 500 dollar Dell to be a 500 dollar Dell with Windows included for free, which is not necessarily the case. However, my previous job which was also a school district, received very nice discounts from Microsoft, which negated a lot of the double-payment worry in my opinion. After all, most people want something that they could trust worked. XP Pro was more reliable than Vista and the newly released Windows 7 at the time, so that's the route we took then.


> **keithpeter said:**
> Hello Roasted

This is excellent stuff. I'm assuming you are using Xubuntu 11.04?

I'd like to know what training and support the teaching staff needed to make the transition from Mac OS X to XFCE, and for the change in applications.

Any plans to investigate the Unity interface when 12.04 comes on stream? Or will you simply upgrade to Xubuntu 12.04?

The teachers received a "crash course" on the interface and some basic ins/outs of the operating system. As of now, Ubuntu is not in the hands of teachers, only student laptops and a few student labs. I personally have done 4-5 small group trainings so far. The enthusiasm and dedication to learning I am experiencing from these teachers has been great. Of course, there has been a little resistance from users who are huge fans of the Apple gear, but overall most people are very accepting of learning something new, **just as long as it works.** Since most of our applications are web based and/or cross platform, it makes a LOT of the transitional steps far easier. Applications like OpenShot, for example, requires a little more attention since teachers aren't as likely to have used OpenShot being Linux only as opposed to something like Audacity, that is cross platform.

We're not using a straight Xubuntu install. We're using the actual Ubuntu ISO with XFCE installed. Members of the IT staff brewed up a custom theme which was a good mix between what you see on OSX vs Windows 7. 

I have a strong inkling that XFCE will be the interface of choice for the future. If you think about our situation, it's a mixed environment, with bits and pieces of Windows 7 floating around along with heavy OSX integration. To have an interface that is similar as the other platforms as possible makes everybody's life easier. I personally like Unity, and I absolutely love Gnome Shell, but I'm thinking elementary students might find it a little too distracting with the effects both interfaces can produce. What we come up with down the road is hard to say, but my personal opinion is to keep it simple, functional, and decent looking, and XFCE fits that bill.

---

### Post by lykwydchykyn on 2011-12-06
Great story!

Did you have challenges getting the IT staff on board for this, or was everyone pretty open to the idea?

---

### Post by betterhands on 2011-12-06
very cool--thanks for the post.  trying to expose some of the folks at my son's elementary school to Edubuntu so they can see they have other, valid choices for their OS.

---

### Post by Roasted on 2011-12-06
> **lykwydchykyn said:**
> Great story!

Did you have challenges getting the IT staff on board for this, or was everyone pretty open to the idea?

At my previous job, yes I had difficulty. We had our budget cut and implemented thin clients in an almost completely unusable lab since the HP desktops we had in there were just awful, even with XP and Office running on them with a brand new fresh image. The clients were running off of a pretty powerful Dell server... 24gb of RAM, two quad core processors, 4 gigabit NICs, etc. I cannot put into words how badly this thing ran. It needed to be rebooted almost daily, and when it was rebooted, it needed approximately 30 minutes to bring all clients online. We ended up trying 3 different Windows-based thin client solutions on this same server, no dice. The server itself was in good shape since we had utilized it for other services previously and, as I'll get to in a few minutes here, I ended up using it with Ubuntu LTSP later on where it worked fine.

At this point, some heads were on the chopping block. I didn't like the Windows thin client idea from day 1 but I also wasn't calling the shots. I took that chance to be a squeaky wheel... one of those "how much worse could it possibly get even if Linux thin clients fail?" scenarios. I got the approval and was given 3 days, THREE DAYS, to implement Linux-based thin clients utilizing our existing Pentium 4 hardware. By 10am on day 2, I had it done. :D I was running the lab off of a much less powerful HP server, with two dual core processors, 12gb of RAM and 1 gigabit NIC. That sucker flew with these clients and it wasn't rebooted during the remainder of my time there, which was around 7 or 8 months. This setup was running 30 clients in the same lab as the original server.

Later, I utilized the original problematic Windows server I spoke about above for a thicker implementation, where we brought 70 clients on that server alone instead of 30 clients like we had originally done. Even with 70 clients running at full tilt on that system (Firefox, Gimp, entire Libre Office suite, Audacity, all running at the same time) and only utilizing 2 of the 4 gigabit network cards (granted we were also running on a gigabit network), I wasn't able to crash the server or overload it to the point of it being unbearable. It ran rather exceptionally considering it was a 1 vs 70 scenario with the server doing all of the processing.

> **betterhands said:**
> very cool--thanks for the post.  trying to expose some of the folks at my son's elementary school to Edubuntu so they can see they have other, valid choices for their OS.

Edubuntu was actually the OS I used on the LTSP (thin client) servers. Edubuntu came with an option to install LTSP on the fly, so I ran with it. Plus I figured some of the educational software that was pre-packaged could benefit users if they were curious enough to try it out and see what they thought. 

It's been a very fun experience. I've learned a lot and I expect Linux integration to only get thicker in my place of work as well as several area school districts nearby.

---

### Post by lykwydchykyn on 2011-12-06
> **Roasted said:**
>  I ended up using it with Ubuntu LTSP later on where it worked fine.


That's great!

My biggest Linux deployment outside the server room is an LTSP setup running browser terminals for the public library.  Runs 17 clients.

We had to do a lot of hardware upgrades when I upgraded it to Lucid + LTSP5 this past year, unfortunately; so it isn't quite the shining money-saving success story it was originally, but it's served well.

My biggest trouble is that I'm about the only one at work really into using Linux; it's a hard sell for anything outside my own little fiefdom.

---

### Post by Roasted on 2011-12-06
> **lykwydchykyn said:**
> That's great!

My biggest Linux deployment outside the server room is an LTSP setup running browser terminals for the public library.  Runs 17 clients.

We had to do a lot of hardware upgrades when I upgraded it to Lucid + LTSP5 this past year, unfortunately; so it isn't quite the shining money-saving success story it was originally, but it's served well.

My biggest trouble is that I'm about the only one at work really into using Linux; it's a hard sell for anything outside my own little fiefdom.

I hear ya. When there weren't any severe money pinches, it was a hard sell. It's like being a millionaire driving a Hummer. Why would you bother going down the street to where gas is 2 cents a gallon cheaper? Because if you're a millionaire in a Hummer, it doesn't matter to you and it's hard to care about the cost savings. That's what, well, every Windows environment I personally ever saw was dealing with. We have sustainability, and that's okay because it works. But when budgets start getting cut and you realize the technology we know and love is dwindling within our sights, you begin to get into survival mode and dig around for alternatives.

The big area where LTSP saves money is the fact that the clients can be every day computers that would have otherwise been thrown out. The server doesn't need a ton of power. Granted, mine did, but I was serving 70 clients. If you're serving a batch of 10 or so, a simple server does fine. I ran 10 clients off of an HP AMD 1.8ghz dual core with 4gb of DDR2 ram. It ran beautifully.

Now if you want to get crazy with cost savings, there's always Atom based nettops, like what ASUS has. Those little boxes sip power (with wattage in the teens during peak and single digits during idle) as compared to an older HP P4 box which in my experience idled around 95 and easily sat at a steady 125-150 when in moderate use. Sure, might not matter at home, but take 2,000 systems and that's a couple grand a year in power savings. :D

---

### Post by lykwydchykyn on 2011-12-06
> **Roasted said:**
> 

The big area where LTSP saves money is the fact that the clients can be every day computers that would have otherwise been thrown out. The server doesn't need a ton of power. Granted, mine did, but I was serving 70 clients. If you're serving a batch of 10 or so, a simple server does fine. I ran 10 clients off of an HP AMD 1.8ghz dual core with 4gb of DDR2 ram. It ran beautifully.


Yeah, my original setup was a bunch of geode-based thin clients with 233 MHz processors and 128 MB of RAM being served by a P4 workstation with 1 GB of RAM.  Dapper Drake and LTSP 4.1 ran beautifully on that setup for about 12-15 clients.

When we upgraded to a good server and the newer LTSP, it all fell apart.  The clients were useless, I spent weeks shaving down the image and desktop session to make it run, and even then it ran horridly and crashed periodically.  It was educational, at least.

We'd have used old workstations or police laptops, but were constrained by the cabinetry at the kiosks and had to buy something thinclient-sized.  I ended up going with Zotac Z-boxes, and so far they've worked well.

You'd think saving money would be a good selling point at any time, especially in small governments, but "not-from-Microsoft"
seems to creep out too many people.

---

### Post by Roasted on 2011-12-06
> **lykwydchykyn said:**
> 

You'd think saving money would be a good selling point at any time, especially in small governments, but "not-from-Microsoft"
seems to creep out too many people.

Agreed. I've spoken to some people leading IT departments who walk a fine line. "I shall use what the industry uses which is the majority of the marketshare which directly results it is a better product with far more support."

Yeah, okay. I suppose Justin Bieber selling out Madison Square Garden in a half hour also suggests he's exceptionally talented? :-k

---

### Post by OrangeCrate on 2011-12-06
Interesting thread.

:popcorn:

---

### Post by Roasted on 2011-12-06
> **OrangeCrate said:**
> Interesting thread.

:popcorn:

It's just gotten a little more interesting. There was a board meeting last night, and it seems the local news caught wind:

[http://lancasteronline.com/article/local/545640_Penn-Manor-s-tech-team-cuts-costs.html](http://lancasteronline.com/article/local/545640_Penn-Manor-s-tech-team-cuts-costs.html)

---

### Post by rudihawk on 2011-12-07
Very nice thread!

---

### Post by Artemis3 on 2011-12-07
So, you are installing Ubuntu minimal and then XFCE? Not straight Xubuntu?

50 secs to boot sounds a bit too much.

Ah, the need for speed... I always use option ```
noatime
``` in fstab, i don't understand why this is not a default, relatime doesn't cut it, use noatime, nobody uses mutt anyway, and we don't want writing every time we read something, even if delayed by relatime, it will write that stupid access time to all files you ever read, all the time; seriously dropping performance (desktop distros should be addressing these defaults).

I personally use option ```
data=writeback
``` in /etc/fstab, but that needs adding ```
rootflags=data=writeback
``` in /etc/default/grub

You could mount /tmp and /var/tmp in ram using the tmpfs options. Firefox can simply be told not to use disk cache and you can fix the amount of ram cache it uses in about:config

There is also some sort of untold secret involving /usr/lib/pm-utils/power.d/journal-commit . When pm-utils is not installed, you can simply use a commit=nnn in fstab, but it doesn't work when pm-utils is present, and instead the value is overwritten by this script (also when you plug/unplug ac). Default commit time (0) is actually 5 secs, this is too quick and a killer for a desktop/laptop, i increase this value to 300 secs (5 mins) in said script, you can check with the "mount" command what the commit time has been set to.

If you use swap, low the swappiness to 10 or something small (i don't use swap), but on machines i installed (specially old) the response difference is dramatic when you lower the swappiness. Something like:
```
vm.swappiness=20
vm.vfs_cache_pressure=50
``` in /etc/sysctl.conf

My last personal tip, might not apply to you if plymouth works perfect, and you can ctrl-alt-n to your consoles and back to x just fine. It doesn't with with my nvidia (makes all consoles blank) so... i disable this modesetting junk in /etc/default/grub using ```
GRUB_GFXPAYLOAD_LINUX=text
``` to go back to sanity and 80x25 text consoles (i also remove splash but that might look a little unpretty to students).


Hope your project succeeds and serves as example for others. Everytime Microsoft detects this, they go knocking doors offering free licenses... Expect them; they don't like institutions teaching something other than Windows exists.

---

### Post by Roasted on 2011-12-07
I believe we're also talking from a press of the power button to seeing the desktop. The systems are on a 10 second automatic login with a local account, which might very well factor in to the boot process, along with the whole POST section as well. I personally haven't sat around with a stopwatch to see what they boot at. I always felt as though they boot comparatively well to a Macbook of even slightly higher spec. Students have commented on them in a positive manner as well, referring to them as "snappy" to use.

---

