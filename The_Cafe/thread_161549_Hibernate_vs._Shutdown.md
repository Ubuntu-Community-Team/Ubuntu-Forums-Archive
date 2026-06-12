---
title: "Hibernate vs. Shutdown?"
date: 2006-04-17
forum: The Cafe
---

### Post by Stealth on 2006-04-17
Can someone tell me why I would shutdown my computer over hibernate?

I've recently been using it a lot on my laptop and desktop (both on Windows, even though I use Ubuntu more on my laptop, its just hibernate doesn't work on it right now). The start up is immensely faster, and nothing needs to load again. So why even shutdown? I guess under *Windows* you might as well shutdown every once in a while, seeing as how its not as stable as Linux and such. But still, hibernate seems really cool, why isn't this the actual "default" shutdown (in general, I mean, Windows could've been doing this by default, still calling it "shutdown", and claimed to have the fastest boot/shutdown times)?

---

### Post by xXx 0wn3d xXx on 2006-04-17
Well, I have to shutdown because hibernetion doesn't work too well in breezy. I wish it had a suspend feature though...

---

### Post by Miguel on 2006-04-17
Well, today hibernation is not all that polished in linux but other than that, the only thing that could make you shotdown your computer would be a kernel upgrade... and I've read there is a new kernel feature to "hotplug" different kernels. For anything else... linux is stable enough.

---

### Post by hesee on 2006-04-17
So, will hibernation work better in dapper? I'm planning to buy a laptop, and that would be an important feature to have.

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=hesee]So, will hibernation work better in dapper? I'm planning to buy a laptop, and that would be an important feature to have.[/QUOTE]
When I used Dapper, yes it worked but this can vary from laptop to laptop. I think it is due to the new kernel. I am using the 2.6.17-rc1 kernel so let me see if hibernetion works on breezy with the newest kernel.

Edit: No, it doesn't work on breezy. It is the same as shutting down for me.

---

### Post by hesee on 2006-04-17
Sounds good. If I understand correctly, this is a feature provided by kernel and thus does not depend which distro you use (if you use the same kernel)? I mean, no reason to look for different distro, if there's probelm with hibernation?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=hesee]Sounds good. If I understand correctly, this is a feature provided by kernel and thus does not depend which distro you use (if you use the same kernel)? I mean, no reason to look for different distro, if there's probelm with hibernation?[/QUOTE]
Well, Dapper may use that feature in the new kernel.

---

### Post by aysiu on 2006-04-17
I shut down because hibernate has an annoying blinking light--this is true for both my Ubuntu/XP desktop and my wife's Mac laptop.

---

### Post by hesee on 2006-04-17
[QUOTE=aysiu]I shut down because hibernate has an annoying blinking light--this is true for both my Ubuntu/XP desktop and my wife's Mac laptop.[/QUOTE]

Would it be possible then to compile an own kernel with non-blinking hibernation light? :rolleyes:

---

### Post by aysiu on 2006-04-17
[QUOTE=hesee]Would it be possible then to compile an own kernel with non-blinking hibernation light? :rolleyes:[/QUOTE] Possible. Probably. Worth it? Not really.

I have an old computer (that I bought in the summer of 2005), and I shut that thing down every day, and it still works great. I don't see any reason not to shut down.

---

### Post by hesee on 2006-04-17
[QUOTE=aysiu]Possible. Probably. Worth it? Not really.

I have an old computer (that I bought in the summer of 2005), and I shut that thing down every day, and it still works great. I don't see any reason not to shut down.[/QUOTE]

Yeah, i was just joking. 

I think the main reason for hibernate in general would be to get computer really fast up/down.

---

### Post by aysiu on 2006-04-17
[QUOTE=hesee]Yeah, i was just joking.[/quote] Sorry. My sense of humor hasn't been working properly these past few weeks. Several Ubuntu Forum members have tried joking with me, and I just haven't gotten any of the jokes.

Apologies, all around.

---

### Post by hesee on 2006-04-17
No bad feelings, and that wasn't a good joke anyway. :)

---

### Post by Stealth on 2006-04-18
That's odd...hibernation should completely shutdown the computer, you guys sure that's not standby/suspend?

Hibernation *almost* worked in Breezy for me, but the Nvidia drivers for my laptop didn't let it start X properly...

---

### Post by lieut_data on 2006-04-18
[QUOTE=Stealth]That's odd...hibernation should completely shutdown the computer, you guys sure that's not standby/suspend?[/QUOTE]

That's exactly what I was thinking -- Hibernate is simply taking a snapshot of the system (kernel + applications) in memory, saving it to the harddrive, and halting. Hibernate allows one to remove the battery or disconnect the power for any length of time, and still be able to recover the system exactly as it was before hibernating.

On my system (Gentoo, mind you....), I hibernate exclusively, rebooting only to upgrade a kernel or resolve a hardware issue. In fact, I hibernate both Windows and Linux on this laptop: the last time either was rebooted would have been just over three weeks ago. [I use Linux 99% of the time]

---

### Post by hesee on 2006-04-18
[QUOTE=lieut_data]That's exactly what I was thinking -- Hibernate is simply taking a snapshot of the system (kernel + applications) in memory, saving it to the harddrive, and halting. Hibernate allows one to remove the battery or disconnect the power for any length of time, and still be able to recover the system exactly as it was before hibernating.[/QUOTE]

Yes, that was in my mind when i was also asking about hibernation. And someone said that it should work with new kernels...

---

### Post by pellgarlic on 2006-05-15
i have to say, i really like having a hibernate feature - i often have loads of windows open, and two or three programs running, which i don't want to have to closel, to have to re-open them again. in this situation, hibernate is really handy. 

unfortunately, i can't seem to get it to work in ubuntu!!  i don't want to turn this into another thread about that though - i think there are enough already about it... 

but yeah, hibernate is really useful for me - i use it on my xp machine at work all the time. i've usually got fireworks, dreamweaver, firefox, outlook, thunderbird and a handful of explorer windows all open at the same time. (bit of a multi-tasker, me! :) ) 

saves me a lot of hassle to just hibernate, then when i boot up the next morning, all my stuff is there, ready for me to start working again!

---

### Post by jason.b.c on 2006-05-15
> Can someone tell me why I would shutdown my computer over hibernate?


[QUOTE=aysiu]Possible. Probably. Worth it? Not really.

I have an old computer (that I bought in the summer of 2005), and I shut that thing down every day, and it still works great. I don't see any reason not to shut down.[/QUOTE]


Why **Shutdown** at all.???  

Why not just turn off your monitor at night when you go to bed..??  [SIZE="2"] ( desktop only )[/SIZE]

Shutting down ever day like that can be damaging ( wreak havok ) on your computer..!  

[SIZE="3"]Bad for the hard drive.[/SIZE]..;)

---

### Post by aysiu on 2006-05-15
[QUOTE=jason.b.c]Why **Shutdown** at all.??? 

Why not just turn off your monitor at night when you go to bed..??  [SIZE="2"] ( desktop only )[/SIZE]

Shutting down ever day like that can be damaging ( wreak havok ) on your computer..!  

[SIZE="3"]Bad for the hard drive.[/SIZE]..;)[/QUOTE] If I leave the computer on, it makes noise and generates a lot of heat. If I put it to sleep, it has an annoying blinking light. My parents leave their computers on all the time, and they've had their ROM fried by electrical surges. I have an old computer my wife and I bought in the summer of 2001, and it's been shut down just about once every day--no damage as far as I can tell.

If a computer can last five years being shut down all the time with no damage, then I think I'm not going to care if its lifespan is in some way shortened. My five-year-old computer is pretty much obsolete. Even with Xubuntu on it, it's a bit slow--speedy in general, but extremely sluggish with more than two applications running at once.

Thanks for your concern, but I think I'm good.

---

### Post by jason.b.c on 2006-05-15
> and they've had their ROM fried by electrical surges. 

Sounds like they don't have *surge protection*.?

> If a computer can last five years being shut down all the time with no damage, then I think I'm not going to care if its lifespan is in some way shortened. My five-year-old computer is pretty much obsolete.

Five years is a preaty good run, The thing i'm saying is **" I care "**.. I can't afford to buy a new one when this thing breaks down.

> My five-year-old computer is pretty much obsolete.

So is mine.  ( 6.5 yr old. )

---

### Post by aysiu on 2006-05-15
[QUOTE=jason.b.c]
Five years is a preaty good run, The thing i'm saying is **" I care "**.. I can't afford to buy a new one when this thing breaks down.[/QUOTE] Do what works for you. I'm going to shut down every day. And you'll hibernate. Personal choice is a great thing.

---

### Post by jason.b.c on 2006-05-15
[QUOTE=aysiu]Do what works for you. I'm going to shut down every day. And you'll hibernate. Personal choice is a great thing.[/QUOTE]


Nah, I don't do either one.  Mine runs 24/7.. The only time i shutdown is if their is a big thunderstorm coming my way, Then i shutdown and turn off my speakers, printer, etc.;) 
 
Unplug my phoneline ( even though it's surge protected ), Then i trip the breaker on my surge-p/power strip..

But thats about the only time i will.:eek: 

I've tried that *hibernation thing* and i don't really care for it, every time i did the picture on the monitor always came back all stupid..?:-k

---

### Post by BoyOfDestiny on 2006-05-15
[QUOTE=jason.b.c]Nah, I don't do either one.  Mine runs 24/7.. The only time i shutdown is if their is a big thunderstorm coming my way, Then i shutdown and turn off my speakers, printer, etc.;) 
 
Unplug my phoneline ( even though it's surge protected ), Then i trip the breaker on my surge-p/power strip..

But thats about the only time i will.:eek: 

I've tried that *hibernation thing* and i don't really care for it, every time i did the picture on the monitor always came back all stupid..?:-k[/QUOTE]

For my desktop same thing 24/7. I do turn off the monitor, and looks like dapper handles things like drives spinning down. I have an APC battery back up, which has helped greatly during brown outs. 

As for my laptop, I just shut it down. Old habits die hard.

---

### Post by Wallakoala on 2006-05-15
wait....so what exactly is hibernation supposed to do?

I tried it...and it basically shut down the computer. I turned it back on, and booted ubuntu from grub. When usplash came up, the bar didn't move, it just stayed in the same place for ~30 secs. Eventually, the screen started to flash until it was black, and my monitor said that there was no signal. I did a hard restart by manually pressing the power button on the computer, and it booted up normally.

Well...I had to restart my computer anyways.

---

### Post by ssam on 2006-05-15
[QUOTE=jason.b.c]The thing i'm saying is **" I care "**.. I can't afford to buy a new one when this thing breaks down.
[/QUOTE]

the cost of running 1 watt for 1 year is about $1 (very roughly). some computers use several hundred watts.

---

### Post by aysiu on 2006-05-15
[QUOTE=ssam]the cost of running 1 watt for 1 year is about $1 (very roughly). some computers use several hundred watts.[/QUOTE] From [Howstuffworks](http://computer.howstuffworks.com/question328.htm): > This is one of those questions where there is no single right answer. In other words, it depends on how you use your computer.

There are at least three situations that force you to leave your computer on 24 hours a day:

    * You are on a network, and the network administrators back up files and/or upgrade software over the network at night. If that is the case, and you want your machine backed up or upgraded, then you need to leave it on all the time.

    * You are using your machine as some sort of server. For example, HowStuffWorks has a machine that creates the images for the How Webcams Work article. It needs to be on 24 hours a day. If your machine acts as a file server, print server, Web server, etc., on a LAN (local area network) or the Internet, then you need to leave it on all the time.

    * If you are running something like SETI@home and you want to produce as many result sets as possible, you need to leave your machine on all the time. 

If you do not fall into any of these categories, then you have a choice about whether or not to leave your machine on.

One reason why you might want to turn it off is economic. A typical PC consumes something like 300 watts. Let's assume that you use your PC for four hours every day, so the other 20 hours it is on would be wasted energy. If electricity costs 10 cents per kilowatt-hour in your area, then that 20 hours represents 60 cents a day. Sixty cents a day adds up to $219 per year.

It's possible to use the energy-saving features build into modern machines and cut that figure in half. For example, you can have the monitor and hard disk power down automatically when not in use. You'll still be wasting $100 per year.

The argument for leaving your computer on all the time is that turning it on and off somehow stresses the computer's components. For example, when the CPU chip is running, it can get quite hot, and when you turn the machine off it cools back down. The expansion and contraction from the heat probably has some effect on the solder joints holding the chip in place, and on the micro-fine details on the chip itself. But here are three ways to look at that:

    * If it were a significant problem, then machines would be failing all the time. In fact, hardware is very reliable (software is a whole different story, and there is a lot to be said for rebooting every day).
    * I don't know a single person who leaves the TV on 24 hours a day. TVs contain many of the same components that computers do. TVs certainly have no problems being cycled on and off.
    * Most vendors will sell you a three-year full-replacement warrantee for about $150. If you are worried about it, spend some of the money you are saving by turning your machine off and buy a service contract. Over three years, you come out way ahead! 

---

### Post by jason.b.c on 2006-05-15
[QUOTE=ssam]the cost of running 1 watt for 1 year is about $1 (very roughly). some computers use several hundred watts.[/QUOTE]

Yea so.??  But it actually costs you more money when things are turned on and off all the time..

> * If it were a significant problem, then machines would be failing all the time. In fact, hardware is very reliable (software is a whole different story, and there is a lot to be said for rebooting every day).

That is a good point.

> * I don't know a single person who leaves the TV on 24 hours a day. TVs contain many of the same components that computers do. TVs certainly have no problems being cycled on and off.


Yea but a **TV** is alot more simple thing, Of a **" Less complex construction "**.. In other words, Built to handle that sort of thing. No hard drive, No operating system, No ram, etc
 
So of course they don't have a problem being " Cycled on and off "..:-D

---

### Post by Compucore on 2006-05-15
Its just a matter of preference on it. I prefer to shut down ocassionally over here. Just to get rid of any problems that might have not shut down properly over here on any one of my machines. If it fancys your computer to be in hibernation mode thats your thing. 

Compucore

---

### Post by pellgarlic on 2006-05-16
[QUOTE=jason.b.c]Why **Shutdown** at all.???  

Why not just turn off your monitor at night when you go to bed..??  [SIZE="2"] ( desktop only )[/SIZE]

Shutting down ever day like that can be damaging ( wreak havok ) on your computer..!  

[SIZE="3"]Bad for the hard drive.[/SIZE]..;)[/QUOTE]



Why **Shutdown** at all.???  

Why stop wasting energy and using up natural resources??  

I have never heard of anyone having hard drive problems from shutting down their computer. more likely that having it constantly on for long periods of time will damage it, imho...  unless it is really necessary for my computer to remain on (which is hardly ever), i turn it off.

[SIZE="3"]Bad for the Environment!!!!.[/SIZE].. :o

---

### Post by Bradley17 on 2006-05-16
[QUOTE=jason.b.c]Sounds like they don't have *surge protection*.?



Five years is a preaty good run, The thing i'm saying is **" I care "**.. I can't afford to buy a new one when this thing breaks down.



So is mine.  ( 6.5 yr old. )[/QUOTE]


wtf...Hardware is made to be shutdown ive got an old pc that i had 7 years it stils boots fine, Altho its utter shit in terms of power, and cannot run very much. 

The only reason home users have to leave thier computers running over night, is if they are needed for some sort of reason for example static adsl ip. running thier own webserver, email server, etc. etc, or even game server. Otherwise absoultly no reason, And people talking about how quick they fire up and down, I generally have to wait less than a minute for boot in both windows and linux, Im sure you can spare that time. 

An a reasonable pc costs around 300-400 quid to build, never by from shops, or anysort of retails, Only build ur self, you'll find it alot cheaper and your learn something ;D

---

### Post by 3rdalbum on 2006-05-16
Yeah, I can hibernate on Windows but unfortunately not on Ubuntu (it stops it from starting up).

Curiously though, hibernating on Windows makes GRUB start up really slowly.

---

### Post by jason.b.c on 2006-05-16
[QUOTE=pellgarlic]Why **Shutdown** at all.???  

Why stop wasting energy and using up natural resources??[/Quote] 
 

> I have never heard of anyone having hard drive problems from shutting down their computer. more likely that having it constantly on for long periods of time will damage it, imho...  unless it is really necessary for my computer to remain on (which is hardly ever), i turn it off.

Think** "Cold Boot"**.!  It's tougher for your computer to bootup when it is *cold*, Thus rough on the hard drive increasing the chance that you'll lose everything..

But i guess like **aysiu** said: "Do what works for you.."

> 
[SIZE="3"]Bad for the Environment!!!!.[/SIZE].. :o


Alot of things are bad for the environment, Alot of wich is worse than leaving your computer on all the time., cars, people, chemicals, so on and so forth.

---

### Post by pellgarlic on 2006-05-17
[QUOTE=jason.b.c]Alot of things are bad for the environment, Alot of wich is worse than leaving your computer on all the time., cars, people, chemicals, so on and so forth.[/QUOTE]
 agreed! - i walk rather than drive (unless unavoidable), recycle, choose what products to buy carefully, on the basis of enviromental soundness, so on and so forth... any little bit helps, inlcuding not leaving your computer on if it's not necessary to do so. 

point taken about the "cold boot" though, but regular backups are a good practice to adopt anyway. plus i'm sure there are also a lot worse things for a hard drive to endure than having to cold-boot, like intensive usage while editing multitrack audio with multiple real-time effects, or crashing - both of which i do a lot!

i don't want to turn this thread into an eco-rant, so let this be my last post in it - i've expressed my opinion on the "hibernate vs shutdown" question of the thread's title already anyway :)

---

### Post by Klaidas on 2006-05-17
> If I leave the computer on, it makes noise and generates a lot of heat. If I put it to sleep, it has an annoying blinking light.

Same here

---

### Post by Bradley17 on 2006-05-19
[QUOTE=Klaidas]Same here[/QUOTE]

If it bovers you that much jus dont attach your front panel lights to your motherboard/ or psu. FFS. And if you want a nice light on when ur computer is running by a simple LED, and plug it into power supply and place on the front panel. That way when the computer is running you get a nice light, and when the computer is stand by/hibernate, it wont be on simple

---

