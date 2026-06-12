---
title: "'apt-get install' not working on fresh copy of Ubuntu 17.04"
date: 2018-09-09
forum: Server Platforms
---

### Post by sporek on 2018-09-09
So I have installed a fresh copy of Ubuntu Server 17.04, and its running smoothly. However, I cannot use the command 'apt-get' to install packages.

I tried typing 'sudo apt-get install xinit,' however I got an error 'Unable to locate package xinit.'

I tried the command for other packages but was greeted with the exact same error. I am able to ping other websites, so I must have an internet connection. I've also tried updating, rebooting and checking sources.list and haven't found any obvious problems.

What can I try?

---

### Post by howefield on 2018-09-09
The error is telling you what the problem is, it cannot locate the package. Most likely because you are using an end of life unsupported version of Ubuntu and the repositories for 17.04 have been moved, you can either amend your sources.list file to point to the correct location or better, use a currently supported version of Ubuntu.

---

### Post by deadflowr on 2018-09-09
It won't work because 17.04 is no longer supported and the package archives have been removed.
Best to grab a clean fresh copy of a supported release such as 16.04 or 18.04.

ninja'd by howefield

---

### Post by sporek on 2018-09-09
I have tried to update, but ran into the same problem.

What should be in my sources.list file?

---

### Post by sporek on 2018-09-09
I wasn't able to find a version of 18.04 which doesn't use AMD. I could try 16.04, but I didn't think that would be more supported than 17. :-?

---

### Post by jeremy31 on 2018-09-09
What does AMD have to do with it?  Can you only use 32 bit?  AMD64 just means it is a 64 bit install

---

### Post by howefield on 2018-09-09
> **sporek said:**
> I wasn't able to find a version of 18.04 which doesn't use AMD. I could try 16.04, but I didn't think that would be more supported than 17. :-?

16.04 is a Long Term Support release meaning it gets 5 years of updates, as 14.04 before it did and 18.04 does now, ie, even numbered years (April releases). All the rest get nine months updates/support.

---

### Post by sporek on 2018-09-09
Im on 18.04 now and it seems to be working (for now at least). Thanks for the clarification!

---

### Post by deadflowr on 2018-09-09
> it seems to be working (for now at least).

It should keep on keeping on for the foreseeable future.
if you feel you've found the solution works, please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").
so others with the same problem might easily find it.

---

