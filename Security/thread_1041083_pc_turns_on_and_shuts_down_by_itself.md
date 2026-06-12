---
title: "pc turns on and shuts down by itself"
date: 2009-01-16
forum: Security
---

### Post by skullomaniac on 2009-01-16
isn't that weird?
i sit infront of the pc and it wants to shut down
then when i turn it off, it switches back on by itself...
im starting to think that something is wrong
although i dind't execute any funny script and didn't change my sources and stff like that... what is happening and how can i get rid of this problem??

---

### Post by Tubes6al4v on 2009-01-16
You'll have to be more specific about the problem. When you say it wants to shut down, what does it do? Display a box, give you the little blue recycling-like logo?

And when it turns back on, is it imediately after it shuts down? Do the fans and hard drive stop spinning?

Is your system up to date? What are you running?

---

### Post by skullomaniac on 2009-01-16
when it sais it wants to shut down it gives me the box with all the options (restart, hybernate ecc.) without my clicking anywhere... 
and the computer turns back on as soon as i shut it down and the fans are working...
it seems weird coz i have another older pc running 8.04 that works just fine and doesn't give me these problems... 
and my system is up to date...

---

### Post by Tubes6al4v on 2009-01-16
Sounds like your computer is stuck in some reboot cycle. I am afraid I don't know how to help you there. I wouldn't think it was a security issue. Have you installed anything lately? Can you remember what you did before it started? You may get better responses in one of the other forum catagories. I am impatient, so I would probably just see what installing Intrepid over it would do. It is a good OS, not as much of a difference as Hardy had over Gutsy, as far as I can see.

---

### Post by skullomaniac on 2009-01-16
ok thanks fot your time anyways...
then i guess this is the wrong section.. i'll just fighure it out some other way
p.s intrepid does the same thing...

---

### Post by cariboo on 2009-01-16
I wouldn't reinstall just yet, have you check dmesg and /var/log/messages to see if there is any sort of error message. If you have done clean installs of two different versions and it still does the same thing, I would suggest it is a hardware problem of some sort. I would start by disconnecting things one at a time to see if the problem stops, for example remove any addin cards one at a time, unhook any peripherals, until all that is left hooked up is the keyboard, mouse and monitor. If none of that stops the problem, hook everything back up again and run memtest. If that runs with no errors, find someone that has a good quality power supply tester.

In cases like this it is a process of elimination, to find the problem.

Jim

---

