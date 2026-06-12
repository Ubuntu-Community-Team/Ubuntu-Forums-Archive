---
title: "Failed Mainline and Development Kernel Builds at kernel.ubuntu.com"
date: 2020-12-12
forum: Ubuntu Development Version
---

### Post by 64bitguy2 on 2020-12-12
Good Afternoon

I've noticed that the latest Kernel builds are corrupted... Not sure why; but it has been happening only with whatever the latest build its.  The last good build of an Ubuntu kernel was from **December 2, 2020**.

For example:  

[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9.14/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9.14/) - **Latest Mainline Kernel **- Failed Build from December 11, 2020
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9.13/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9.13/) - Previous Mainline Kernel - Failed Build from December 8, 2020
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10-rc7/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10-rc7/) - RC - Failed Build from December 6, 2020

Can someone with the power to do so please rebuild these?

I'm arm deep in testing of BTRFS 5.9 functions.

While it is possible to work with 5.9.12 (the last good mainline build on December 2nd) or if I really were desperate, 5.10-RC6; it doesn't make "apples-to-apples" sense for me _not_ to be working with Mainline Kernel 5.9.14 like everyone else.

In keeping with the standards defined in the Wiki: [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Download_upstream_kernel_files_from_the_Ubuntu_archive](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Download_upstream_kernel_files_from_the_Ubuntu_archive)
> 
**Note:** If you are testing to isolate a bug or  regression, please do not use the daily folder. Instead, use the latest  mainline kernel at the top from the link above. 

I looked around for the best place to post this and this seemed like the "logical" choice; however, if an admin feels that it is misplaced, please feel free to move it to the most suitable location.

Thanks for your prompt help and attention in this matter... The weekend is the only time I ever get to debug, so it is very much appreciated.

---

### Post by Doug S on 2020-12-12
> **64bitguy2 said:**
> Good Afternoon

I've noticed that the latest Kernel builds are corrupted... Not sure why; but it has been happening only with whatever the latest build its.  The last good build of an Ubuntu kernel was from **December 2, 2020**.

Can someone with the power to do so please rebuild these?

I looked around for the best place to post this and this seemed like the "logical" choice; however, if an admin feels that it is misplaced, please feel free to move it to the most suitable location.

Thanks for your prompt help and attention in this matter... The weekend is the only time I ever get to debug, so it is very much appreciated.

hi, and welcome to Ubuntu forums.

we always have a development kernel release candidate thread going herein, this issue has been noted [there]("https://ubuntuforums.org/showthread.php?t=2452692&page=2&p=14006133#post14006133").

mainline kernel build failures are occurring much more often than in previous years.
Surprisingly often, the kernel team seems to have no idea the builds are failing until someone tells them via IRC or their e-mail list.
Typically, I review several days of [IRC logs]("https://irclogs.ubuntu.com/2020/12/12/%23ubuntu-kernel.html") to see if someone mentioned it already. (hmmm ... interesting, is that you there already?)
In the past, the kernel team has responded quickly to the issue when raised on IRC.

In general, we here do not have the power to re-build the Ubuntu mainline PPA.

I compile the mainline kernel myself, and notes on my method, using the git master source, are [here]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662").

---

### Post by 64bitguy2 on 2020-12-12
> **Doug S said:**
> hi, and welcome to Ubuntu forums.

we always have a development kernel release candidate thread going herein, this issue has been noted [there]("https://ubuntuforums.org/showthread.php?t=2452692&page=2&p=14006133#post14006133").

mainline kernel build failures are occurring much more often than in previous years.
Surprisingly often, the kernel team seems to have no idea the builds are failing until someone tells them via IRC or their e-mail list.
Typically, I review several days of [IRC logs]("https://irclogs.ubuntu.com/2020/12/12/%23ubuntu-kernel.html") to see if someone mentioned it already. (hmmm ... interesting, is that you there already?)
In the past, the kernel team has responded quickly to the issue when raised on IRC.

In general, we here do not have the power to re-build the Ubuntu mainline PPA.

I compile the mainline kernel myself, and notes on my method, using the git master source, are [here]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662").

Hi Doug... Yeah I had actually used your method on my "daily use" laptop before... like...OMG.. I'd have to think about how many years ago.  It's been a while since I had to worry about it.

The reason I rely on the Ubuntu Mainline (instead of building it myself) is because I have a bank of 23 laptops for Ubuntu builds that are pre-set to rely on automated procedures that grab the kernel via the mainline link and update through an automated bash pull.

Sadly, that results in the all too predictable:```
 Abort, the amd64 build has not succeeded
``` error message.

For my part, to interfere with the automated solution is to break "standard scripted testing compliance" because the rest of the file system functions proceed automatically after that kernel pull.  Each system is setup with set variables for building its file system and defining its specific options.  After each runs through all testing, it reboots and alters all of those variables and begins again, reporting statistics back to the Server in the lab after each test.  It took days to setup all of the automated procedures with all of the various variables for each make and model of CPU, chipset, bus, drive type, etc... trust me.... it's not something I would want to mess with now that it all FINALLY runs correctly.

I've generally kept to myself and ignored these kinds of "distro specific" issues as they typically work themselves out without any intervention and  I only mention it all here and now in the hopes that someone from the kernel team sees it (Mainly because the primary kernel POC doesn't even appear to be in the Chatroom anymore and that's never a good sign).  After 11-days, I figured it was time to post a comment given that every day that passes where I can't get the official kernel through official (formal) channel is another day of lost debugging and stress testing which is kind of annoying given that I'm paying the electrical bill out of my own pocket and I can't shut those systems down when I'm on the road (mainly because if the updates become available again, I need to actually go there to power them all back up again and that's not always feasible thousands of miles away).

I guess I should mention this isn't my primary Ubuntu ID...  I'm on a remote system today and my personal computer with all of my passwords is back in my hotel room, so I was forced to ... well... "find a way" to communicate my frustration because when remoting into my lab again today, I found the test Server logs filed with errors about none of the systems being able to update their kernels for like the 11th day in a row and well.... "I got annoyed"... hence my investigations and comments.

Thanks for the feedback... I guess I'll just have to hope someone decides to rebuild mainline sometime soon... I just hate falling this far behind and throwing all of that electricity money away.  I started working on rewriting Ericsson manuals today... I have to be in a really bad mood to find myself re-writing technical manuals.  Maybe I will start drinking... I haven't done that in a while.  :)

---

### Post by Doug S on 2020-12-13
thank you for the back story.

>  It took days to setup all of the automated procedures with all ... trust me.... it's not something I would want to mess with now that it all FINALLY runs correctly.Oh, I trust you. I just finished something similar myself. However, I don't want to mess with my setup because it is such a hurried hack job. It might fall apart if I tug at a loose thread (pun intended).

> reporting statistics back to the Server in the lab after each test.I am envious. I have no experience with sending test data to another computer, but it would be a useful ability. I guess I a little now via PuTTY session logs, but such is manual, not automated.

---

### Post by 64bitguy2 on 2020-12-14
> **Doug S said:**
> 

I am envious. I have no experience with sending test data to another computer, but it would be a useful ability. I guess I a little now via PuTTY session logs, but such is manual, not automated.

That's actually the easiest part of the setup.  Each system has a unique User ID and the scripts for the tests are coded to simply save testname-datestamp.txt in their corresponding Server data folder.  The beauty of this is I can tell they are all working correctly by Server data (I leave a console screen open browsing the /user directory so I can see the last datestamp of each account... if one is old, I can then remote into it or if it won't respond, force the Server to reboot it and then remote into after that).

I generally don't intervene if they are running, unless something hokey is going on with SSD's because that's my money.... hard disks I have to burn, SSDs not so much.

---

### Post by corradoventu on 2020-12-28
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11-rc1/) failed build

---

### Post by Doug S on 2020-12-28
> **corradoventu said:**
> [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11-rc1/) failed buildseems to be missing the kmod package (the amd64 build, at least):

```
Warning: 'make modules_install' requires depmod. Please install it.
This is probably in the kmod package.
```

---

