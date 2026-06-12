---
title: "Better Power Managment"
date: 2010-11-07
forum: Server Platforms
---

### Post by Vegan on 2010-11-07
After battling defective software and seeking replacements I think I have figure out how to get a server running on far less power. 

The advantage for a lower electric bill is material to any IT manager. Got to earn their keep somehow.

Anyway cpufrequtils is useless and it left my machine in performance mode constantly so it was not correct.

So I figured, maybe notebook management software could be of help.

So I installed notebook power related packages.

```
sudo apt-get install acpi-support
```

```
sudo apt-get install laptop-mode-tools
```

This package seems to be the ticket.

Now the power LED on my server is not longer solid green all the time. Now it flashes green or even turns yellow. This tells me the machine is now in low power state which is what I want.

I opened a browser to the machine, it served immediately.

I noticed the power LED remained yellow even when the backup script was working as its set daily. This suggests the disk was the load not the CPU.

I did change the ACPI in the BIOS to support S1 and S3 but the CPU itself uses C states.

So now I seem to have achieved my goal of better power management and get around the bug ridden packages I first tried.

I thought I would share my solution with the swarm, I am sure power management is a worthy topic.

---

### Post by Vegan on 2010-11-08
I also think one of the problems with the kernel Ubuntu ships is that its not compiled to support cpufreq so as a result its impossible to use that tool to manage power.

I suggest it might be an idea to add that so that those who are sensitive to energy costs can take advantage.

---

### Post by arrrghhh on 2010-11-08
Never really thought much about it, but I would like to figure out a way to have the server spool itself down when not in use, but be available on a whim.

I just kinda assumed it was built in.  I'll see what my UPS has to say when I try these things thanks!  ;)

---

### Post by Vegan on 2010-11-12
I took some philosophy in school and they show the hazard of an assumption.

So I decided to look at the situation and I noticed the cpufreq tool actually was hostile to my intent leaving the CPU maxed out all the time. So that means my box wastes power like mad.

So removing that program and using the ones above seem to cure the problem.

Turns out the kernel used by 10.10 lacks the support for various power modes. Not what I wanted to see.

It would be nice if Canonical would recognize that server power management is fashionable.

---

