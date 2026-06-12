---
title: "Do I need to change the kernel ?"
date: 2011-03-27
forum: Security
---

### Post by Scunnered on 2011-03-27
In the latest Linux Format mag there is an article **"Ubuntu machines may need a fix"** in which they state that researchers discovered 40 separate holes in a recent kernel which effect the LTS version.

They state that by upgrading to kernel version 2.6.35-25 should cure the problem.

As far as I can see I am using 10.04.2 and kernel 2.6.32-30. I accepted the usual update offered yesterday and would hope that everything should be ok.

Is it the case that the magazine is bolting the stable door after the horse has bolted or need I do anything more to ensure that I am protected.

---

### Post by handy on 2011-03-27
11.04 will be released next month with the .38 kernel amongst many other enhancements to the system.

Personally I use Arch, & have been using the most recent dev' versions of the .38 kernel since they first started to be released. They have been stable as usual.

If you do feel the need to upgrade your kernel, there is a how-to positioned in the "Ubuntu Stuff:" section of the first post in this thread:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129) 

You can read about some of the changes coming in 11.04 here:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1)

***[edit:]** Just to be more specific, the kernel that I'm currently using is the **2.6.38-rc8-44191-g38f1cff-dirty***

---

### Post by dacoolio on 2011-03-27
I would say you could probably wait for 11.04, but if you're up for an adventure you can try compiling your own. [This tutorial]("https://help.ubuntu.com/community/Kernel/Compile") shows how you can do it.

While it might not be the most quick fix, you'll learn a lot about how the system behind a GUI works. And in the end, you could just copy your current kernel configuration and not really have to worry about configuring it yourself.

---

### Post by BkkBonanza on 2011-03-27
The current kernel in 10.10 is 2.6.35-28 (at least that's what I have and I always update). I'm not sure why you wouldn't just upgrade to 10.10 as the simplest choice.

I also think you may be able to just manually upgrade the kernel (with apt-get by choosing the correct package) but I haven't done that recently. I did do that with 10.4 because I needed the SSD enhancements before they came out in 10.10. That doesn't cause such a big disruption but also makes you kind of an in-betweener with possible issues I'd expect.

---

### Post by cariboo on 2011-03-27
You can keep an eye on the [Ubuntu Security Notice]("http://www.ubuntu.com/usn") page, to see if there are any security updates.

---

### Post by BkkBonanza on 2011-03-27
> **cariboo907 said:**
> You can keep an eye on the [Ubuntu Security Notice]("http://www.ubuntu.com/usn") page, to see if there are any security updates.

Now that's scary. 
Reading thru some of the list-archives gives me the willies :)

---

### Post by cariboo on 2011-03-27
I have my Lucid (10.04) server set to automatically download, but not install updates, I check them against the USN before installing. even though I have no intention of ever letting the server be accessed from the internet.

---

### Post by ptn107 on 2011-03-27
All Ubuntu kernels that are still supported will get the same security patches.  The latest lucid kernel (2.6.32.31.60 [2.6.32.32]) has the same *security* patches as the latest maverick kernel (2.6.35.28.50 [2.6.35.11]).  What you miss by not upgrading is additional hardware support and upstream bug fixes.  The Ubuntu devs will patch both.  Refer to the change logs on launchpad.

---

### Post by Scunnered on 2011-03-28
My thanks to everyone for their contributions.

If **BkkBonanza**as a forums staff member can get the willies by reading the link provided by **cariboo907** then what hope do I have as someone who is still finding his way through the mysteries of Ubuntu.

Most everything that I know and understand has been through this medium so I think that I will put my trust in Ubuntu and assume that as I am fully up to date with the Updates that I should be secure.

As to the suggestion of upgrading to 10.10 or 11.04 I have been attempting to see if I can wean my partner off windows and thought that by sticking to the LTS that it would be easier for her rather than the 6 monthly upgrades.

I will mark this as solved as no doubt someone who is braver than I may adopt the suggestions.

Again my sincere thanks for your kind responses.

---

