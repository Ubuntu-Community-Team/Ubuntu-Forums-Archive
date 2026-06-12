---
title: "Don't Like Silent APPS!"
date: 2010-04-04
forum: The Cafe
---

### Post by Doctor Mike on 2010-04-04
This is the about the fifth time since I started testing the beta (lucid) that some silent app starts up. System monitor shows no app running, but in system monitor, however, CPU and Memory suddenly start getting sucked up and HDD activity is audible (IDE), but system monitor shows nothing about the disk activity. If it's something built into the OS I want it showing up in system monitor, so I can identify and or kill it if I don't want it.

Anyone know of a better monitoring tool I can use to see what's happening in the background. I don't trust what I can't see...

---

### Post by Lightstar on 2010-04-04
i often use the terminal's " ps -A "  command to see what's running instead of the system monitor, I'm not sure if it picks up more things though.

Maybe it's a memory leak, but that usually doesn't take all the cpu, as far as I know.

---

### Post by Mr. Picklesworth on 2010-04-04
> **Doctor Mike said:**
> This is the about the fifth time since I started testing the beta (lucid) that some silent app starts up. System monitor shows no app running, but in system monitor, however, CPU and Memory suddenly start getting sucked up and HDD activity is audible (IDE), but system monitor shows nothing about the disk activity. If it's something built into the OS I want it showing up in system monitor, so I can identify and or kill it if I don't want it.

Anyone know of a better monitoring tool I can use to see what's happening in the background. I don't trust what I can't see...

System Monitor should be able to list everything; there's no such thing as a hidden process. It could be something running as another user (eg: root), so head to the View menu and choose All Processes. There's also this wonderfully cool Dependencies view, which sorts child and parent processes.

If your system is acting like a tree chipper, a nice tool is "top". Just head to a terminal and run that command; it'll give you a nice list of the top 10 resource chewing processes at the moment.

As for having lots of programs running in the background, you'll find it's just how the system works: lots of little processes whispering to one another to solve problems (as opposed to one enormous one). They shouldn't be noticeable, though :)

---

### Post by FuturePilot on 2010-04-04
iotop is nice to see what is accessing the disk. It's like top only it measures disk activity.

---

### Post by juancarlospaco on 2010-04-04
*On development versions some apps and daemons runs with --verbose or --debug*

---

### Post by MaxIBoy on 2010-04-04
In the system monitor, select "view->all processes."

---

### Post by Doctor Mike on 2010-04-04
> **MaxIBoy said:**
> In the system monitor, select "view->all processes."
Thanks MaxIBoy and everyone else. I originally had it set to view all processes, but I must have either toggled it by mistake or it was reset at update. Just chalk it up to MS induced paranoia. Trust is still a word I find hard to use with regard to any OS, Ubuntu is making that (trust thing) more likely in the future. Now if I could only trust the APPS... Maybe better not to trust too much, Googie likes my info...

---

