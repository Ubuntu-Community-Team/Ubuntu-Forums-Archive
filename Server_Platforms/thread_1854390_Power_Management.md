---
title: "Power Management"
date: 2011-10-04
forum: Server Platforms
---

### Post by elite1967 on 2011-10-04
Hi all,
Finally I managed to set-up my first Ubuntu server replacing a WHS!!

My configuration:
Ubuntu Server 64bit 10.04
Atom D510 Gigabyte
2GB RAM

But there is one thing that I haven't been able to do, so far:

1) how do I set up a Power Management feature to SHUTDOWN the server after being idle for 30 minutes?
I mean, something that automatically shuts down the server if there is no activity for 30 minutes.

I know that I could connect using SSH and sending a *shutdown *command. But that is NOT what I need.

Thanks for any help.

---

### Post by lcman on 2011-10-04
> **elite1967 said:**
> Hi all,
Finally I managed to set-up my first Ubuntu server replacing a WHS!!

My configuration:
Ubuntu Server 64bit 10.04
Atom D510 Gigabyte
2GB RAM

But there is one thing that I haven't been able to do, so far:

1) how do I set up a Power Management feature to SHUTDOWN the server after being idle for 30 minutes?
I mean, something that automatically shuts down the server if there is no activity for 30 minutes.

I know that I could connect using SSH and sending a *shutdown *command. But that is NOT what I need.

Thanks for any help.

You're gonna have to make a script that'll do that for you and set it up in crontab.

---

### Post by elite1967 on 2011-10-04
> **lcman said:**
> You're gonna have to make a script that'll do that for you and set it up in crontab.

Hi lcman, 
thanks for your input.

Can you help me writing this script, as I am newbie...

Thanks again

---

### Post by elite1967 on 2011-10-05
> **elite1967 said:**
> Hi lcman, 
thanks for your input.

Can you help me writing this script, as I am newbie...

Thanks again

Hi again,
can someone help me writing this script please?

Very appreciated.

---

### Post by elite1967 on 2011-10-06
> **elite1967 said:**
> Hi again,
can someone help me writing this script please?

Very appreciated.

Hi all,
anyone?

thanks

---

### Post by DavidBeijer on 2011-10-06
I suggest you go read up on bash-scripting, and a small tutorial on cronjobs.

You can find these here:
- [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
- [https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

This may all sound very complicated, but if you want to learn about running a server you will find this matarial is actually not that difficult, and also very useful! 

If you have more specific questions about these matters you can always return here.

Good luck!

---

### Post by egpetrich on 2011-10-06
There's a package named "powernap" that allows you to configure the conditions under which your system will suspend itself. Its control structure is pretty simplistic, but you can at least set it up to suspend if no one is logged in for some number of minutes. Search for "powernap" under aptitude (or whatever package manager you use).

I had to search to find it again, but there was a recent thread discussing how to put the server to sleep if no other computers on the network are active. That thread is here:

[http://ubuntuforums.org/showthread.php?t=1062356](http://ubuntuforums.org/showthread.php?t=1062356)

Waking your computer up is another matter. There have been several threads associated with wake-on-lan (assuming your motherboard supports it). Here are a few:

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939)

---

### Post by Vegan on 2011-10-07
I found power management was not well supported with all configurations. Seems more work on the kernel is needed, Lots of it.

For that reason I use Hyper-V which imposes power management on all of the virtual machines including Linux VMs I have installed.

Hyper-V also solves the problem of using multiple x64 distributions.

Now I have tested Linux on other machines and some do work OK. On those I could use anybody as a hypervisor. I use what works best on my metal.

---

