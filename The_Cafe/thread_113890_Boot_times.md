---
title: "Boot times"
date: 2006-01-07
forum: The Cafe
---

### Post by Jimmy_r on 2006-01-07
Lets talk about booting times :) 
I have an old computer with win 95 installed. The other day i powered it up just for fun, and one thing that hit me was that it felt really speedy booting up, so i clocked it and compared to my ubuntu computer...
The oldie (200 MHz pentium MMX , 32MB ram) with windows 95 took(from pushing power button to fully started) 40 sec and to shut down it took 2 sec.
Now, my shiny new ubuntu-computer(1800MHz AMD Athlon64, 1 Gig ram) took 83 sec to start and it took 26 sec to power down.(About the same time as it took when i used Win XP, i may add, so i am not complaining on ubuntu in any way :p )

I just got curious, perhaps someone can tell me what is causing this.
Ok i do understand that WinXP and Ubuntu are...slightly :p more advanced than win 95, but really...i can imagine the boottimes i would get if i managed to get ubuntu onto the oldie ...brr...

So what are the super-duper thingys that these new operating systems do when they start? I mean, X just takes a couple of seconds to start so what is the rest?
Win 95 must also be mounting filesystems and detecting hardware and all these things so where is the difference that makes my new shiny computer take twice the time to boot as my almost ten year old comp?

Also the time to shut down. Win 95 just died when i clicked on the button to turn it off.
Ubuntu(and linux in general, i guess) seems wery concerned about killing printing services and deactivating this and that(Opposed to winXP that saved personal settings for half a minute sometimes... :) )
So, why is it so important to kill everything before the computer shuts down?
I mean, Win 95 almost acted as if i had unplugged the cable or something and still it does not seem as anything get damaged, either hardware or software...
And again, i am not complaining or anything, just curious.

---

### Post by Strife on 2006-01-07
My guess would be that there are a lot of services that you have that need to startup and then shutdown. Take a look in /etc/rc2.d to see what services are booted up (in numerical order).

If there are things which you can do without (highly likely), you can use update-rc.d to prevent them from running. Some of the stuff you may not need would be PCMCIA support (unless you're on a laptop and use that, but who still does these days?).

---

### Post by otake-tux on 2006-01-07
you can reduce ubuntus boot time with [initng]("http://http://ubuntuforums.org/showthread.php?t=80423&highlight=initng")

---

### Post by Jimmy_r on 2006-01-07
Yes, but i was wondering why those services need to be stopped before the computer shuts down. I mean, what would happen if for example cupsd was not killed prior to the computer powers off?
Edit: And i dont really need it to power up/down faster, i am just curious to what makes it differ so much:
Lets say my current computer is five times faster than the oldie. That makes ubuntu ten times as slow to load as win 95. That is a lot of time to start a few extra services.
What i am getting at is :What &#252;berthings are done on bootup nowadays that was not done 10 years ago?

---

