---
title: "Compiled My Own Kernel"
date: 2010-09-28
forum: The Cafe
---

### Post by NightwishFan on 2010-09-28
I decided to learn a bit more about low level stuff so I decided to compile my own kernel set up to my machine. Although it is based on the Ubuntu source (for practical reasons among other things) I am testing my own workstation focused kernel configuration.

Some Changes I Made:

Disabled CGroups
Enabled Intel Core Optimization
Disabled Hyperthreading (my machine does not use it)
Set HZ=1000 + Config No_HZ
Voluntary Preemption (not config_preempt)
Disabled Kernel Debugging

My rationale is that I do not need hard real time and the overhead it brings, so I enabled no forced preemption. Multimedia seems to work much better with 1000hz so I configured to that. I disabled a few options such as cgroups which allows grouping of tasks.

It seems to work great I plan on running some benchmarks to see if it boots faster.

Overall it was a lot of fun, though I had to look up a Lucid specific workaround to enable the initrd to boot my kernel, as the old method did not work precisely. I followed the guide here using the old fashioned Debian way. If you follow that part of the tutorial ensure you read the section below as well if you want to try yourself.
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I will edit in a sec with a diff file.

---

### Post by amitabhishek on 2010-09-28
> **NightwishFan said:**
> I decided to learn a bit more about low level stuff so I decided to compile my own kernel set up to my machine. Although it is based on the Ubuntu source (for practical reasons among other things) I am testing my own workstation focused kernel configuration.

Some Changes I Made:

Disabled CGroups
Enabled Intel Core Optimization
Disabled Hyperthreading (my machine does not use it)
Set HZ=1000 + Config No_HZ
Voluntary Preemption (not config_preempt)
Disabled Kernel Debugging

My rationale is that I do not need hard real time and the overhead it brings, so I enabled no forced preemption. Multimedia seems to work much better with 1000hz so I configured to that. I disabled a few options such as cgroups which allows grouping of tasks.

It seems to work great I plan on running some benchmarks to see if it boots faster.

Overall it was a lot of fun, though I had to look up a Lucid specific workaround to enable the initrd to boot my kernel, as the old method did not work precisely. I followed the guide here using the old fashioned Debian way. If you follow that part of the tutorial ensure you read the section below as well if you want to try yourself.
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I will edit in a sec with a diff file.

Congrats! 

I did mine sometime back but then I used an existing .config file. Make menuconfig was too geeky for me :).

---

### Post by NightwishFan on 2010-09-28
> **amitabhishek said:**
> Congrats! 

I did mine sometime back but then I used an existing .config file. Make menuconfig was too geeky for me :).

It was quite nice, I was wary I would have to edit by hand. I did base my configuration off the Ubuntu generic one though, I was not going to fix what wasn't broken. I did some minimal changes that made it more specific to my hardware.

---

### Post by matthew.ball on 2010-09-28
Well done dude. Massive geek props.

---

### Post by KdotJ on 2010-09-28
Congrats! I did this too a few weeks back on my netbook which runs Arch Linux. Purely as a learning experience mainly. Among some of the things you mentioned, I also disabled support for CD-ROM (as my netbook doesn't have one) and disabled support for all file systems I know that I won't use. It's great fun to play around with

---

