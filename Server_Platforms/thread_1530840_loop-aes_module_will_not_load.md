---
title: "loop-aes module will not load"
date: 2010-07-14
forum: Server Platforms
---

### Post by boba23 on 2010-07-14
Hey,

I installed Lucid Server AMD64 yesterday to replace my aging Debian Etch Box.
Install went fine including LUKS FDE encryption for the sys drive.
Now here is the problem .... I got a 7 disk software-raid5 array that is encrypted with loop-aes. So I depend upon loop-aes working on Lucid.
Well, I thought there are packages for loop-aes in the repos, so they should probably work out of the box. Well ... it doesn't :(
I can compile loop-aes modules just fine with module assistant but after that loop.ko fails to load with "invalid module format".
Now I took a look at the default kernel config options and the problem seems to be that the kernel loop driver is built into the kernel and not set as module.
I am really surprised that nobody else ran into this problem before.
I know, I could compile a custom kernel but well, that's not the way I wanna go. I want a modular kernel, which is updated regularly and I do NOT wanna compile my own kernel.
Question is, is there any other easy solution for this problem? 
At least there should be a note in the loop-aes-source in Lucid, telling the user, that the built module will not work with the default lucid kernel ...

thanks

boba

---

