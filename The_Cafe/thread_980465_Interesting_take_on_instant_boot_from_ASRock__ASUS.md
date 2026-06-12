---
title: "Interesting take on instant boot from ASRock / ASUS : Boot Vista in four seconds"
date: 2008-11-12
forum: The Cafe
---

### Post by Jags_FL on 2008-11-12
This [**Slashdot article**]("http://tech.slashdot.org/tech/08/11/12/2249253.shtml") has an interesting take on instant boot from ASRock / ASUS.

YouTube link: [http://www.youtube.com/watch?v=BucIjXZVxXo](http://www.youtube.com/watch?v=BucIjXZVxXo) 

But what I found more interesting was [**this comment**]("http://tech.slashdot.org/comments.pl?sid=1027377&cid=25740939") on Slashdot by 'swillden':


 It seems like it'd be really easy to do this with an open source OS. I think I may have just found a nifty little project for this weekend. All it should take is:

    * Add an inittab runlevel (7?) for "shutdown to instant boot".
    * Add an /etc/rc7.d with a script that writes a file that records the fact that we're in "shutdown to instant boot" state, then switches to runlevel 6.
    * Add an init script in late in the normal startup sequence that checks for "shutdown to instant boot" state. If it finds that state, it removes the file and then initiates suspend or hibernate, depending on a configuration option.

At that point "sudo init 7" should cause your machine to shut down to "instant boot" state. Hitting the power button will then "instant boot" it.

"sudo init 0" or "sudo init 6" will do a normal shutdown or a normal reboot.

The final step would be to modify the "shutdown" command to go to runlevel 7 when given some new option, and then to modify the GUI-based shutdown tools to provide the instant-boot option as well, and maybe make it the default. Oh, and maybe modify the ACPI script that's executed when the power button is hit so that the power button does a "shutdown to instant boot" by default.

---

### Post by kevin11951 on 2008-11-12
that would be really cool, can i help somehow?

---

### Post by kevin11951 on 2008-11-12
Why isnt anyone else interested?!

---

### Post by Jags_FL on 2008-11-12
kevin11951

Thanks for the reply and yes, I'm wondering myself that why there arn't many replies...

Now I'm a Linux newbie and doesn't know how to write a script or something, as described by 'swillden'.

I was anticipating that some Ubuntu/Linux pros would be interested in booting Ubuntu in 4 seconds but I guess "Boot Vista in four seconds" part in the title keeping geniuses away from the thread...

---

### Post by Eisenwinter on 2008-11-13
This is awesome.

---

### Post by handy on 2008-11-13
Give it some time, you must remember the forum user population's time zones.

---

### Post by Jags_FL on 2008-11-13
Eisenwinter, handy

guys thanks for your replies... I've wrote to 'swillden' requesting if he would elaborate further about the script he has described at Slashdot on this thread.

---

### Post by niccholaspage on 2008-11-13
Awesome! I need my laptop and desktop to boot up in 4 seconds.

---

### Post by smartboyathome on 2008-11-13
If I understand this correctly, what its basically saying is that it would create a new folder called /etc/rc7.d and put a lot of really light startup software in it along with a minimal amount of processes, then starts it with those.

---

### Post by Jags_FL on 2008-11-13
Excerpts from the Slashdot comments:

[Tacvek]("http://tech.slashdot.org/comments.pl?sid=1027377&cid=25740611"):
"they just shift the boot time to be part of the shutdown time, so when you arrive at your computer again, and turn it on, you are just unsuspending it, or are loading an unusually clean hibernation file. This is a very interesting idea, but it is one that doe not need motherboard support. This can be done by the OS alone"

[crt]("http://tech.slashdot.org/comments.pl?sid=1027377&cid=25740323"):
"They never show the shutdown process - my guess is that **when you shutdown, it actually reboots, then right after Windows boots it puts it to sleep or hibernate (S3/S4)**. When you turn it back on, it wakes it and looks like you "just" booted up. [ [**ACPI system states**]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#System_states") ]

Not really a bad idea I suppose - moves the boot time from boot to shutdown, when you are less likely to care.

Of course you can get the same effect yourself by rebooting then just putting your machine to sleep when you want to shutdown. Someone could probably even write a simple software solution for this rather than requiring a whole new motherboard."

[Egotistical Rant]("http://tech.slashdot.org/comments.pl?sid=1027377&cid=25740465"):
"This is EXACTLY what it does. The "[**more images for this article**]("http://www.custompc.co.uk/images/slideshow/107946")" section at the given link has a flowchart of the process...it's just a reboot and suspend."

---

### Post by mssever on 2008-11-13
> **Jags_FL said:**
>  It seems like it'd be really easy to do this with an open source OS. I think I may have just found a nifty little project for this weekend. All it should take is:

    * Add an inittab runlevel (7?) for "shutdown to instant boot".
    * Add an /etc/rc7.d with a script that writes a file that records the fact that we're in "shutdown to instant boot" state, then switches to runlevel 6.
    * Add an init script in late in the normal startup sequence that checks for "shutdown to instant boot" state. If it finds that state, it removes the file and then initiates suspend or hibernate, depending on a configuration option.

At that point "sudo init 7" should cause your machine to shut down to "instant boot" state. Hitting the power button will then "instant boot" it.

"sudo init 0" or "sudo init 6" will do a normal shutdown or a normal reboot.

The final step would be to modify the "shutdown" command to go to runlevel 7 when given some new option, and then to modify the GUI-based shutdown tools to provide the instant-boot option as well, and maybe make it the default. Oh, and maybe modify the ACPI script that's executed when the power button is hit so that the power button does a "shutdown to instant boot" by default.
I haven't looked at the links, but the suggestion you quoted looks like nonsense to me. The poster seems to think that you can simply order Linux to boot in 4 seconds and have it do so. In reality, there are many things that would have to be done. A while ago, I ran across a website that described a project to get a 5-second boot from the time when grub turns over control to when the CPU and disks are idle. I don't remember the particular distro, but it required a lot of custom hacking that simply wouldn't work for a normal distro. Remember, too, that Ubuntu has put a lot of work into speeding up boot time. So if they haven't gotten four seconds, then it's probably not easy to do.

There are three basic ways to improve boot time (all three of which would have to be considered and used as appropriate):
[LIST=1][*]Adjust the order in which stuff starts. However, you can only do this so much, since some programs depend on others.
[*]Don't start unnecessary stuff. But for a general-purpose distro, this isn't easy to do given the wide variety of hardware it has to work with and the wide variety of things people use it for.
[*]Optimize the programs that start up. I understand that Xorg wastes a fair amount of time starting up. However, there are a lot of programs to optimize.
[/LIST]As you can see, there's a lot more to it then simply adding a runlevel.

However, if your hardware works with hibernation, then this issue is moot. Who cares how long boot takes if you only reboot once evry several months?

---

### Post by handy on 2008-11-13
> **mssever said:**
> 
However, if your hardware works with hibernation, then this issue is moot. Who cares how long boot takes if you only reboot once evry several months?

How does Linux handle RAM fragmentation under those circumstances?

I've noticed that the distro's handle RAM in a vastly superior fashion than windows does, or at least did.  I can fragment my RAM in Linux & on the Mac. 

Do Linux kernel based systems have a built in method of RAM defrag'?

---

### Post by mssever on 2008-11-13
> **handy said:**
> How does Linux handle RAM fragmentation under those circumstances?

I've noticed that the distro's handle RAM in a vastly superior fashion than windows does, or at least did.  I can fragment my RAM in Linux & on the Mac. 

Do Linux kernel based systems have a built in method of RAM defrag'?
I don't know, since my hardware won't resume from hibernation. However, my desktop (which I use as a server) stays up for months at a time with no problems.

---

### Post by Jags_FL on 2008-11-15
I'm still not clear on what kinda shutdown 'swillden' was describing...

If it's a 'complete shutdown', like after shutting down PC the way he had described, when you hit the power button you get to see the bios screen > grub > you can boot any installed OS (and can go back & forth between OSes on subsequent reboots), but if you select the OS in which you have activated "*inittab runlevel (7?) for "shutdown to instant boot"*", you can boot-up the OS in 4 seconds (from the grub),  would be really awesome. 

With hibernation/suspend you can log back into the same OS only.

---

### Post by vishzilla on 2008-11-15
hilarious video. looks like a cue from an asian movie.

---

### Post by Bölvaður on 2008-11-15
How to boot in 5 seconds:
[http://lwn.net/Articles/299483/]("http://lwn.net/Articles/299483/")

Video of it: (genuine)
[http://www.youtube.com/watch?v=s7NxCM8ryF8](http://www.youtube.com/watch?v=s7NxCM8ryF8)


Read the article on how it was done. There was a thread about it here also somewhere:
[http://ubuntuforums.org/showthread.php?t=930579&highlight=boot+fedora+eee]("http://ubuntuforums.org/showthread.php?t=930579&highlight=boot+fedora+eee")

---

### Post by Jags_FL on 2008-11-15
@ Bölvaður

thanks for the links. I'm pretty sure that we'll see alot of 'fast-boot' related improvements in Ubuntu starting with Jaunty.

Loved this quote from Arjan van de Ven:

"And don't make all users wait because a few people run a filesystem that requires a module or sendmail on their laptops. Make it so you only pay the price if you use the feature."

---

### Post by Martje_001 on 2008-11-16
> **Jags_FL said:**
> it's just a reboot and suspend."
So practically they're just faking it? 

We can do that better! 5 seconds booting and no faking!

---

### Post by Jags_FL on 2008-11-16
I just started this thread with a comments from 'swillden' hoping someone at Ubuntuforums would figure out & write a script or something from what he has described... Obviously I'm not that qualified to know whether if its doable/feasible or would have started working on it myself  :)

---

### Post by Martje_001 on 2008-11-16
It shouldn't be that hard, but I don't have time for it unfortunately, otherwise I would have started a new project right away! ;)

---

### Post by mssever on 2008-11-16
> **Martje_001 said:**
> It shouldn't be that hard, but I don't have time for it unfortunately, otherwise I would have started a new project right away! ;)

After watching the video and reading the slashdot pages the OP linked to, it seems quite apparent to me that there's special hardware involved. You can't do a clean boot of a fully-functional desktop system in 3-4 seconds on standard hardware. It would take longer than that just to read the necessary files off the hard drive. Perhaps they're storing the necesary files in flash or some other fast storage medium--or maybe even using RAM-like persistent storage.

So if you have one of their mobos and are able to determine how their system works, it shouldn't be terribly difficult to modify Linux to work with it. But without one of their mobos, this is just a pipe dream. Speeding up the boot process further on standard hardware isn't easy, else it would have been done already.

---

### Post by Jags_FL on 2008-11-16
> **mssever said:**
> it seems quite apparent to me that there's special hardware involved. 

Perhaps they're storing the necessary files in flash or some other fast storage medium--or maybe even using RAM-like persistent storage.

Very likely that it's hardware assisted, great observation.

---

