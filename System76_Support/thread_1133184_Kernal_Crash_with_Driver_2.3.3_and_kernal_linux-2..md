---
title: "Kernal Crash with Driver 2.3.3 and kernal linux-2.6.27-14"
date: 2009-04-22
forum: System76 Support
---

### Post by rehan.iftikhar on 2009-04-22
Hi All

Just updated my System 76 driver. Did a "restore" and rebooted. Much to my surprise my system has crashed 3 times.

What should i look for in my logs to report more info?

Thanks in advance.

-Rehan

---

### Post by thomasaaron on 2009-04-22
Please provide more detail on your system. Which System76 model is it? etc...

Also, please go to System > Administration > System76 Driver > Support > Create. It will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

---

### Post by rehan.iftikhar on 2009-04-22
Thanks, Here are my logs.

My system is SERP3 running 8.10 (from upgrade).

---

### Post by thomasaaron on 2009-04-23
I don't think the problem has anything to do with the System76 Driver. The errors in your logs look exactly like the ones in this bug report...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275227](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275227)

A few clarification questions:

1. Are you running Ubuntu, Kubuntu, etc...?
2. 32-bit or 64-bit?
3. Are you using proposed updates (See System > Administration > Software Sources > Updates (i.e. is the third checkbox down selected)?
4. What do you mean by 'Crash'? Is it shutting down? Locking up?
5. If you boot into the previous kernel, does the problem happen?

---

### Post by rehan.iftikhar on 2009-04-23
> 1. Are you running Ubuntu, Kubuntu, etc...?

I am using Ubuntu 8.10

> 2. 32-bit or 64-bit?

64-bit

> 3. Are you using proposed updates (See System > Administration > Software Sources > Updates (i.e. is the third checkbox down selected)?

I am using proposed updates

> 4. What do you mean by 'Crash'? Is it shutting down? Locking up?

The system locks up and is unresponsive. The wifi LED on front flashes.

> 5. If you boot into the previous kernel, does the problem happen?

I am trying 2.6.27-13 now, will report if anything changes.

---

### Post by thomasaaron on 2009-04-23
Thank you. If running a previous kernel (and you might want to go back a little further for testing purposes) doesn't fix it, try running this command...

sudo apt-get install linux-restricted-modules-intrepid

It sounds like a kernel panic caused by the wireless driver.

---

