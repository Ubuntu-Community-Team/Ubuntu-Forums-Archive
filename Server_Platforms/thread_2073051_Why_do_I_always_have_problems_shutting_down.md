---
title: "Why do I always have problems shutting down?"
date: 2012-10-18
forum: Server Platforms
---

### Post by mattlach on 2012-10-18
When I go to shut down my Ubuntu server, across multiple releases,a and multiple machines, I always have this shutdown problem.

[img]http://farm9.staticflickr.com/8189/8101483071_d4166aec61_o.jpg[/img]

This has been plaguing me with every release since probably 08.04 LTS, across three different servers I have had in that time.

1.) AMD Athlon X2 e3250
2.) AMD Zacate E350
3.) AMD FX-8120

Fresh installs every time, always the same issue shutting down.  Failing to kill some process, and kicking me out to single user mode.

I can try again from single user mode, and the same thing will just happen over and over.

Worth noting, if I issue the reboot command, rather than the shutdown command, it works just fine, and I never see a failure message.

I've been putting up with this for a long time, as I can always just issue a reboot, and then quickly reach for the power button once it is done, but this isn't ideal.

Has anyone else been having issues like these?

---

### Post by lisati on 2012-10-18
What happens if you allow the e2fsck run to completion?

---

### Post by mattlach on 2012-10-18
> **lisati said:**
> What happens if you allow the e2fsck run to completion?

Thanks for the thought.

Unrelated though.

The drive that it was running on is external, and it happens with or without it connected.

---

### Post by lykwydchykyn on 2012-10-19
If killing all processes is failing, it follows that the problematic process is still running, and you might be able to find which one it is by running "ps -e".

---

### Post by mattlach on 2012-10-19
> **lykwydchykyn said:**
> If killing all processes is failing, it follows that the problematic process is still running, and you might be able to find which one it is by running "ps -e".

Good point.

I'll check that.

Still doesn't make sense to me that it would fail to kill all processes during shutdown operations, but not during reboot operations...

Is there a significant difference in how those two commands handle the killing of processes?

---

### Post by cariboo on 2012-10-20
Although it probably has nothing to do with your problem, you don't need sudo if you are running as root.

---

### Post by mattlach on 2012-10-21
> **cariboo907 said:**
> Although it probably has nothing to do with your problem, you don't need sudo if you are running as root.

Thank you.   Just a force of habit, I don't usually use the root account directly.  I usually manage everything from my user account.

---

### Post by koenn on 2012-10-22
you're not issuing the correct command for a "shutdown" if by shutdown you mean "turn the machine off":

the shutdown command expects an option 
  -r                          reboot 
  -h                          halt or power off 
  -H                          halt
  -P                          power off

without one of those, it (apparently) does "go to maintenance mode" a.k.a. single user mode; It says as much in your screenshot.

try ```
shutdown -h now
```

---

### Post by mattlach on 2012-10-22
> **koenn said:**
> you're not issuing the correct command for a "shutdown" if by shutdown you mean "turn the machine off":

the shutdown command expects an option 
  -r                          reboot 
  -h                          halt or power off 
  -H                          halt
  -P                          power off

without one of those, it (apparently) does "go to maintenance mode" a.k.a. single user mode; It says as much in your screenshot.

try ```
shutdown -h now
```

Doh  :oops:

That was silly of me.

I'll try this and see if it works, but chances are you are right.   I've been issuing the wrong command all these years.

---

