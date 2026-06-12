---
title: "Home Servers &amp; Energy Conservation"
date: 2007-05-16
forum: Server Platforms
---

### Post by odelay on 2007-05-16
I'm in quite a conundrum right now--I've always been a proponent of saving energy, both to save money and the environment, but I recently became interested in setting up a home server.  My motivation for doing so was largely academic, but I'm also quite interested in being able to access my files (say, my music library) from any computer.  It also opens many new creative possibilities for me in terms of web development and file sharing between my friends and family.  In short, I like where this project is going and don't want to give up on it.

However, I'm starting to get a guilty conscience.  My "server" is a 7-year-old G3 Powermac.  It's a tank.  The fan is static...it's currently a headless server running as few tasks as possible, but you can still hear the blasted fan a mile away.  I need to hook it up to a meter to confirm, but I'd say it's a safe bet that leaving this guy running 24/7 is consuming tons of electricity.

I was hoping to generalize this discussion a little and get some ideas from you guys on how to simultaneously run a file or web server and keep your electricity bill to a minimum.  I'm very (as in 5 days) new at this whole server thing, but here were a few ideas I was pondering over:

* Install a new fan.  This one is a little tricky; if I install a fan with a lower volumetric flowrate, my computer is fried.  However, I still think I could find a more efficient fan--I mean this thing is a wind tunnel, and the output air is practically room temperature.

* Here's a crazy one that won't apply to most of you.  Since my server project is very small in scope, and isn't intended to server the general public (as of now), I really don't need it on 24/7.  In fact I barely need it on at all.  Here's my situation: I live in an apartment 3 hours from the server, so I can't just press the power button whenever I want.  I can, however, remotely power off or restart the server ("sudo shutdown -P now" or -r, etc. via ssh), but I can't remotely power on the server.  This seems rather hopeless, but is there anyway to do this?

Well as I said, I'm new at this, and have many more questions than answers.  Either if you have some tried & true secrets, or if there's something you've had in the back of your head, please feel free to share.

---

### Post by dannyboy79 on 2007-05-16
> **odelay said:**
> I'm in quite a conundrum right now--I've always been a proponent of saving energy, both to save money and the environment, but I recently became interested in setting up a home server.  My motivation for doing so was largely academic, but I'm also quite interested in being able to access my files (say, my music library) from any computer.  It also opens many new creative possibilities for me in terms of web development and file sharing between my friends and family.  In short, I like where this project is going and don't want to give up on it.

However, I'm starting to get a guilty conscience.  My "server" is a 7-year-old G3 Powermac.  It's a tank.  The fan is static...it's currently a headless server running as few tasks as possible, but you can still hear the blasted fan a mile away.  I need to hook it up to a meter to confirm, but I'd say it's a safe bet that leaving this guy running 24/7 is consuming tons of electricity.

I was hoping to generalize this discussion a little and get some ideas from you guys on how to simultaneously run a file or web server and keep your electricity bill to a minimum.  I'm very (as in 5 days) new at this whole server thing, but here were a few ideas I was pondering over:

* Install a new fan.  This one is a little tricky; if I install a fan with a lower volumetric flowrate, my computer is fried.  However, I still think I could find a more efficient fan--I mean this thing is a wind tunnel, and the output air is practically room temperature.

* Here's a crazy one that won't apply to most of you.  Since my server project is very small in scope, and isn't intended to server the general public (as of now), I really don't need it on 24/7.  In fact I barely need it on at all.  Here's my situation: I live in an apartment 3 hours from the server, so I can't just press the power button whenever I want.  I can, however, remotely power off or restart the server ("sudo shutdown -P now" or -r, etc. via ssh), but I can't remotely power on the server.  This seems rather hopeless, but is there anyway to do this?

Well as I said, I'm new at this, and have many more questions than answers.  Either if you have some tried & true secrets, or if there's something you've had in the back of your head, please feel free to share.

i would say if you want to quite her down just spend some money and get a more expensive fan with the same flow rate or whatever but uses less wattage. i am sure they are out there.

as far as it being on all the time and wanting to turn it off, see if you're ethernet card supports and you can actually wake the computer using a wake on lan program. not sure on the details but I am always curious regarding this as well. just gogle and you'll find a million answer. or even try in herer first and I am sure you'll find it.

---

### Post by odelay on 2007-05-16
> **dannyboy79 said:**
> as far as it being on all the time and wanting to turn it off, see if you're ethernet card supports and you can actually wake the computer using a wake on lan program. not sure on the details but I am always curious regarding this as well. just gogle and you'll find a million answer. or even try in herer first and I am sure you'll find it.

Thanks for pointing me in the right direction.  This is definitely what I'm looking for...however I don't think my old Powermac G3 (2000, yosemite) supports WOL.  I suppose I can always try to find a PCI ethernet card that supports it, but that's a very long, dark road to travel down.  It seems that WOL-supported motherboards became pretty much standard around 2002.  I can't confirm that WOL isn't built in on my PowerMac, I'm just making an educated guess.  At least I know the technology exists now, thanks.

---

### Post by MJN on 2007-05-17
Another simple (and cheap) way of turning the server on/off, albeit without remote on-control, would be a simple timer plug - many (most?) BIOS's allow you to specify what happens when power is applied to the system - either <stay off>, <turn on>, or <stay at last state>. Of course, for the turning off you'd want a cron job to shut the server down gracefully before the timer finally kicks in and pulls the plug!
 
However, before looking for a solution you need to measure the extent of your problem - use a power meter to measure the average consumption. You might find you're imagining it to be higher than it is due simply to the amount of noise it's making. If it was completely silent you might have a different perspective on things?
 
Remember also there is perhaps more to this than first appears - for example there may be other ways of saving the same amount of power (to 'offset' the server usage) and, depending on your local climate, the heat from the machine may not actually be wasted as it will be contributing to heating your house. Of course, if you're in a hot climate then this won't be a benefit, and indeed if you're running aircon it'll be even worse...
 
My server, a PIII 1GHz with 3 hard drives (although 2 sleep most of the time) consumes roughly 85W whilst under 'average' load. Hence it uses around 2.04kWh per day, or 745kWh per year. Here in the UK I currently pay £0.1055 ($0.2086 or 0.1541EUR) per kWh hence it costs me roughly £80 ($158 / 115EUR) a year to run. For six months of the year we have a requirement for heating (no aircon in the summer) hence the 'wasted' heat is still utilised for that period (although at 7x the price of gas, electric heating is not overly cost-effective).
 
Given the server used to live in our bedroom, where my girlfriend would complain if even the cat snored, it had to run *dead* silent.... This involved lining it with sound-deadening material and running three temperature-controlled 'silent' fans - end result is indeed near-as-dammit silence with a safe average system temperature of 30degC. The hard disk and CPU temperatures are monitored to stay well within limits - if they get too high all fans would run at full speed but it never gets to that stage. As mentioned above, it doesn't 'feel' like it's using much power at all due to the fact it's so quiet. Of course, as the sums illustrate it does however I don't consider it excessuve and indeed I doubt I could pay £80 to a third party anyway to provide equivalent functionality, particularly given part of the usage is for automated CCTV surveillance.
 
Mathew
 
P.S. Just to complicate matters further, it is arguable that a machine running 24/7 will outlive one turned on/off everyday due to the lack of thermal cycling - the main cause of long-term component failure hence leaving it on *may* mean that replacement won't be due for longer hence saving in the energy/environmental 'costs' of manufacture/disposal...

---

### Post by odelay on 2007-05-17
> **MJN said:**
> Another simple (and cheap) way of turning the server on/off, albeit without remote on-control, would be a simple timer plug - many (most?) BIOS's allow you to specify what happens when power is applied to the system - either <stay off>, <turn on>, or <stay at last state>. Of course, for the turning off you'd want a cron job to shut the server down gracefully before the timer finally kicks in and pulls the plug!
I started thinking about this last night.  I could probably only have it go on at peak hours, for a few hours, then shut off.  I'm definitely going to look into this option a little more.
 
> Remember also there is perhaps more to this than first appears - for example there may be other ways of saving the same amount of power (to 'offset' the server usage) and, depending on your local climate, the heat from the machine may not actually be wasted as it will be contributing to heating your house. Of course, if you're in a hot climate then this won't be a benefit, and indeed if you're running aircon it'll be even worse... 
Florida! :-({|=
 
I definitely plan on getting a power meter--not just for this project though; I'm always wondering how much power little devices consume.  I read somewhere that things like cell phone chargers, even when "idle" and not attached to a phone, can cost nearly $100/yr if left plugged in.  That sounds a little extreme to me, but I definitely want to go around the house and find out for myself.
 
> P.S. Just to complicate matters further, it is arguable that a machine running 24/7 will outlive one turned on/off everyday due to the lack of thermal cycling - the main cause of long-term component failure hence leaving it on *may* mean that replacement won't be due for longer hence saving in the energy/environmental 'costs' of manufacture/disposal...
Another good point.  The only thing is, once this computer dies, there probably won't be a replacement.

This project was intended to be mostly free.  I have a difficulty spending $40 or so on a decent fan, when I could barely sell the whole box for $100.  Same goes for an ethernet card, or large HD's, or anything.  But at the same time, I don't feel right about recycling a perfectly capable and beautiful piece of hardware.  Perhaps it's just a Mac user being overly nostalgic, but the craftsmanship on this computer is impeccable (especially since it's 7 years old).  What to do, what to do...

---

### Post by Ventajou on 2007-05-17
Hi!

Since you don't need a speed demon, here are a couple suggestions for you.

!. Use a laptop as your server. An older one (P3/P4) shouldn't cost too much and would deliver as much power as a Mac G3. Those things are made to use as little energy as possible to begin with. You could even use one with a broken screen/backlight since you can always plug it to a monitor to set it up. Just get enough ram for your needs and a big enough disk.

2. Build a server around an Epia board. Affordable, fanless and supports all kind of hardware. Check out [http://www.mini-itx.com/projects/cluster/?p](http://www.mini-itx.com/projects/cluster/?p) and you'll see the kind of crazy things that are possible with some cash and enough spare time.

3. Get a NSLU2 ([http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)) It's a small Linksys device used to connect USB drives to your network. But some crazy hackers got their hands on it and now you can run linux on it and do all kinds of things.

Hope this helps!

---

### Post by [h2o] on 2007-05-18
I am going to build a small home server based on a VIA EPIA board as well. I saw tests on Silent PC Review stating that the idle power usage was around 17-20W when using a HDD and CD-drive. I won't have the CD-drive though so I expect to land somewhere around 17 W :)

As for powering on the server remotely I read a swedish article about a guy who took an old GSM-phone and connected it to the power-on-sensor (or whatever you call it). So, the only thing he had to do was call the number of his computer and when the phone started ringing it made the computer boot up. Guess it needs a little knowledge about what you're doing, but it seemed to be a quite easy installation.

---

### Post by Xbehave on 2007-05-18
you could save a bit of power(probably not too much) by underclocking your system. im not sure how apple work but most companies produce products then test them to pick a compromise between performance and livetime/power if you dont need full performance then you can drop voltages and use less power

or you could offset the damage by running a seti-like project for environmental simulations, i cant rember the name but its on the same project as seti bonic or something

the phone idea seams like a good option as well the power button on your computer is a really simple mechanism, its just making an electrical connection between two pins(when working on computers i regularly use pens and stuff instead of wiring up buttons)

---

### Post by MJN on 2007-05-18
> **Xbehave said:**
> or you could offset the damage by running a seti-like project for environmental simulations, i cant rember the name but its on the same project as seti bonic or something
 
Isn't there something ironic about thousands of otherwise idle computers all using extra power investigating global warming issues? In 10 years time the simulator will spew out the answer as to the likely cause of global warming...
 
T... o... o...    m... a... n... y...    c... o... m... p... u... t... e... r... s...
 
and SETI-BOINC will be quietly closed down.... ;)
 
Mathew

---

### Post by Cheese Sandwich on 2007-05-18
You may be able to go fanless by removing the chassis cover & sitting the motherboard upright such that thermal convection would keep a steady flow of air drifting over the CPU.

---

### Post by dannyboy79 on 2007-05-18
> **Cheese Sandwich said:**
> You may be able to go fanless by removing the chassis cover & sitting the motherboard upright such that thermal convection would keep a steady flow of air drifting over the CPU.


there's a much safer and way better way than that to going fanless! it's called a heatsink at a minimum.

---

### Post by odelay on 2007-05-18
> **MJN said:**
> Isn't there something ironic about thousands of otherwise idle computers all using extra power investigating global warming issues? In 10 years time the simulator will spew out the answer as to the likely cause of global warming...
 
T... o... o...    m... a... n... y...    c... o... m... p... u... t... e... r... s...
 
and SETI-BOINC will be quietly closed down.... ;)

Hahaha!  That's great.

I want to keep the discussion going anyway...hopefully someone will find a useful tip or two, however there's a recent update in my situation.  While pondering how to get my PowerMac G3 running as an environmentally friendly server (ignore the blatant contradiction), I was kinda thinking the same thing: Too Many Computers!!!

So then it hit me that we recently got a MacMini from a friend, and it is currently being used for everyday tasks--nothing imperative.  It's almost always left running too.  While I couldn't install a Linux server on it, I did some searching around in OS X.  Sure enough, Apache, FTP, SSH, SFTP, VNC, whatever was already installed & configured on OS X (mind you, this isn't the server edition).  All I had to do was go to SysPrefs > Sharing & check the boxes of the services I wanted to enable.

The mini also supports WOL if needed.  While it only has an 80 GB internal, there's already a 500 GB firewire drive attached.  Since the mini is more or less a laptop in a box, power consumption is minimal.  And as icing on the cake, the machine was being left on 24/7 to begin with (without my knowledge, of course).  Granted, while this isn't really a good option if I wanted to run a Web or FTP server (there's only one user on the mini), it works fine for SSH & SFTP across the internet.  There's also a great Mac client for using DynDNS.org.

I just wish SFTP was built into web browsers, to make it easier to share files with the general public.  I basically just want a "drop box" that I can throw a few files in and share to anyone, anywhere.  Telling someone to get a SSH PC client is too much work, but I don't think it's safe to leave a Web server on 24/7 just to share a few files.  I guess I could always enable/disable it with VNC whenever I needed to share something, but that's kind of ridiculous.  Anyway, sorry for getting off topic there.

---

### Post by tturrisi on 2007-05-19
[http://michaelbluejay.com/electricity/computers.html](http://michaelbluejay.com/electricity/computers.html)
It will cost approx 200 bucks/yr to keep that computer on 24/7.

---

### Post by Fr0ns on 2007-05-19
I'm currently using an old Toshiba laptop with an Intel Celeron 650 MHz cpu as a webserver. Now I know laptop's aren't recommended as a server I'm still going to try it. I've disonnected the battery since it'll only run for like 10 mins.

The fan only starts once in an hour or so for 10 seconds. The only thing that scares me is the hard drive making creepy noises. Just'll have to wait how long it'll live..

---

### Post by odelay on 2007-05-19
> **tturrisi said:**
> [http://michaelbluejay.com/electricity/computers.html](http://michaelbluejay.com/electricity/computers.html)
It will cost approx 200 bucks/yr to keep that computer on 24/7.

I don't see any mention of a Mac Mini in that article.  I did find [this]("http://www.amug.org/amug-web/html/amug/reviews/articles/intel/macmini/") article, that lists the Mini as idling at 17 Watts and performing between 20 and 37 Watts.  That would put it at $25/yr at $0.14/kW-hour, which is rather reasonable.

BTW, it just occurred to me you were probably talking about the G3 Powermac!

---

### Post by tturrisi on 2007-05-20
> **odelay said:**
> I don't see any mention of a Mac Mini in that article.  I did find [this]("http://www.amug.org/amug-web/html/amug/reviews/articles/intel/macmini/") article, that lists the Mini as idling at 17 Watts and performing between 20 and 37 Watts.  That would put it at $25/yr at $0.14/kW-hour, which is rather reasonable.

BTW, it just occurred to me you were probably talking about the G3 Powermac!

yeah, 25 bucks/yr is very reasonable.  My bathroom light costs more than that!

---

### Post by hinge on 2007-05-23
Great and relevant discussion.

I have a headless server on my addict running ftp, mysql, nfs, samba - I've had it for 2 years now and I cant live without it !!!!

But I do worry about the power consumption - not so much because of the money - mainly because I want to be a better person ;) 
It is running at approx 70watts at normal load. I have hdparm activated and use wakeonlan when possible.
Is there anything else that I can do, using software (and ultimately HW) how about ACPI. I have been looking for a great ubuntu guide on that but no luck.

Are there any sleep-on-lan available ? turn off or put the computer to sleep over ethernet ?

---

### Post by odelay on 2007-05-23
> **hinge said:**
> Are there any sleep-on-lan available ? turn off or put the computer to sleep over ethernet ?

I don't know if this is what you are looking for, but if I wanted to turn off my computer over the LAN or WAN, I would just ssh into it then execute something like "sudo shutdown -h -P now".  I'm not positive about the switches though--I think it's -h to "halt" and -P to force "power" off.  I could be wrong, and there might be a more "proper" command for a complete shutdown.  I don't know about remotely putting to sleep.

---

