---
title: "Kernel Updates on LemU4, PanP9, and GazP7 Laptops"
date: 2012-07-02
forum: System76 Support
---

### Post by isantop on 2012-07-02
**NOTE: The new, updated kernel is now available in the normal update channels, and this method is no longer necessary.**

Hi all!

The last few weeks has been a turbulent time for these laptops. There were a couple of issues regarding crashing and freezing that were introduced with the new kernel in Ubuntu 12.04.

There is a new kernel update being readied for release. It will be available very soon. We will notify users experiencing these issues on how to update to the new kernel once it is available. This will solve the problem completely. In order to receive notifications regarding these steps, please open a support case on our website by logging into your account. 

The kernel is the core program of an Operating System. It's a very vital part of the system, and any errors in it can show up in many different places. Ubuntu uses the Linux kernel, and by default uses version 3.2 in Ubuntu 12.04 LTS. 

We currently advise against manually installing future kernel versions (3.3 and higher), as these are not official Ubuntu kernels and may cause other issues with the system. The fix for this issue in kernel version 3.4 has been backported into the new update to be made available soon, so installing a newer kernel is not needed.

---

### Post by brdmn on 2012-07-02
Point of clarification: is this new kernel part of official Ubuntu, or is it something separately released by S76?

I'm experiencing no issues on my lemu4, and so I'd rather not install something from outside the distro if it is not necessary.  My current kernel is:
3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64

---

### Post by isantop on 2012-07-03
> **brdmn said:**
> Point of clarification: is this new kernel part of official Ubuntu, or is it something separately released by S76?

I'm experiencing no issues on my lemu4, and so I'd rather not install something from outside the distro if it is not necessary.  My current kernel is:
3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64

It's an official Ubuntu kernel. It will be coming via a regular update in a week or two. Our instructions will aid in installing it early.

---

### Post by isantop on 2012-07-09
The new Kernel is now available to install!

The root cause is a bug in the Intel graphics driver included in the Ubuntu kernel. The bug has been resolved and Ubuntu developers have released a new Ubuntu kernel that includes the fix. Please follow the below instructions to install the new kernel.

1.) Click the Ubuntu icon in your launcher and type "Update". Open Update Manager.
2.) Click "Settings..." on the bottom left of the Update Manager window
3.) Check the checkbox next to "Pre-released updates (precise-prosed)", enter your password and click "Close".
4.) On the Update Manager window click the "Check" button. Then click "Install Updates".
5.) After the updates are installed, reboot your laptop

Now that the new kernel is installed, we want to turn off Proposed Updates. Open Update Manager again, click Settings..., and uncheck the check box next to "Pre-released updates (precise-prosed)". You're all set!

---

### Post by kend650 on 2012-07-09
Any idea when this update will be available to the rest of the System 76 users running 12.04?

I'm on a Bonobo, and having a problem with the 'suspend' function.

---

### Post by Carborundum on 2012-07-09
> **kend650 said:**
> Any idea when this update will be available to the rest of the System 76 users running 12.04?

I'm on a Bonobo, and having a problem with the 'suspend' function.
This update has nothing to do with suspend. It's only a fix for freezing on Ivy Bridge graphics.

---

### Post by brdmn on 2012-07-11
> **kend650 said:**
> Any idea when this update will be available to the rest of the System 76 users running 12.04?

I'm on a Bonobo, and having a problem with the 'suspend' function.

As Carborundum says, this update isn't designed to fix the problem you mentioned.  However, I don't see anything here that says you can't install it on any system.  The update comes from Ubuntu, so you should be able to follow isantop's instructions on your Bonobo as long as you are running Precise Pangolin (12.04).

---

### Post by isantop on 2012-07-11
> **brdmn said:**
> As Carborundum says, this update isn't designed to fix the problem you mentioned.  However, I don't see anything here that says you can't install it on any system.  The update comes from Ubuntu, so you should be able to follow isantop's instructions on your Bonobo as long as you are running Precise Pangolin (12.04).

This is true; however, I would advise against it. There is nothing in the new updates that fix problems on other systems, and we haven't tested the updates on any Nvidia systems, so there could be some negative effect we could not account for. I would recommend waiting until the update gets pushed through the normal software channels.

---

### Post by philbert on 2012-07-12
> **isantop said:**
> The new Kernel is now available to install!

The root cause is a bug in the Intel graphics driver included in the Ubuntu kernel. The bug has been resolved and Ubuntu developers have released a new Ubuntu kernel that includes the fix. Please follow the below instructions to install the new kernel.

1.) Click the Ubuntu icon in your launcher and type "Update". Open Update Manager.
2.) Click "Settings..." on the bottom left of the Update Manager window
3.) Check the checkbox next to "Pre-released updates (precise-prosed)", enter your password and click "Close".
4.) On the Update Manager window click the "Check" button. Then click "Install Updates".
5.) After the updates are installed, reboot your laptop
Now that the new kernel is installed, we want to turn off Proposed Updates. Open Update Manager again, click Settings..., and uncheck the check box next to "Pre-released updates (precise-prosed)". You're all set!

Thanks for the update. I put in an order for a GazP7 yesterday.I take it that you will run the Update Manager as part of the build process to apply the kernel update?
Also, do you know which 3.2 .x kernel level will have the update?

---

### Post by isantop on 2012-07-12
> **philbert said:**
> Thanks for the update. I put in an order for a GazP7 yesterday.I take it that you will run the Update Manager as part of the build process to apply the kernel update?
Also, do you know which 3.2 .x kernel level will have the update?

We recently updated our Ubuntu images for Intel Graphics to include the fixed kernel, so your system will not need to have proposed updates installed when you receive it.

---

### Post by b7j0c on 2012-07-14
thanks for the clear instructions! I've applied the update and so far no issues. 

> **isantop said:**
> The new Kernel is now available to install!


---

### Post by Shaun_Yute on 2012-07-20
> **isantop said:**
> We recently updated our Ubuntu images for Intel Graphics to include the fixed kernel, so your system will not need to have proposed updates installed when you receive it.


Do you know what the name of the update is under update manager. I have 136 updates available since I selected pre-released updates. I would much rather only install the kernel update. Below is my current kernel version just in case the update was already pushed out.

Linux shaun-Pangolin-Performance 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Thank you.

---

### Post by Medeo on 2012-07-26
I was about to post a big message about my PanP9 freezing up all the time, and then I saw this. :) Let's see if it works!

Actually, quick question. Should I use the "proposed update" kernel from Ubuntu, or just upgrade to the new stable 3.4.6 that came out a few days ago? Or are they the same thing?

---

### Post by isantop on 2012-07-27
> **Medeo said:**
> I was about to post a big message about my PanP9 freezing up all the time, and then I saw this. :) Let's see if it works!

Actually, quick question. Should I use the "proposed update" kernel from Ubuntu, or just upgrade to the new stable 3.4.6 that came out a few days ago? Or are they the same thing?

You should definitely use the Ubuntu kernel. It contains all of the Ubuntu-specific patches that the mainline 3.4 Kernel doesn't We only test each version of Ubuntu with its official Kernel.

---

### Post by Medeo on 2012-07-27
Got it, thanks!

---

### Post by HDave on 2012-07-30
I have a brand new gazp7 and have experienced a hard freeze twice today when I found this thread.  However, I have already been running with all Ubuntu updates.

```
uname -a
Linux 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Is 3.2.0-27 the kernel that has the patches in it?

---

### Post by isantop on 2012-07-31
> **HDave said:**
> I have a brand new gazp7 and have experienced a hard freeze twice today when I found this thread.  However, I have already been running with all Ubuntu updates.

```
uname -a
Linux 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Is 3.2.0-27 the kernel that has the patches in it?

Are you doing anything funky in terms of usage? What is the system doing immediately before the freeze? Is it the same thing each time?

---

### Post by HDave on 2012-07-31
> **isantop said:**
> Are you doing anything funky in terms of usage? What is the system doing immediately before the freeze? Is it the same thing each time?

Something different every time.  The last time I was sitting there watching a software compile scroll past.

I did go to System76 support who put me on a kernel version 3.3.6 late yesterday....since then, no lockups.  Keeping fingers crossed....

Edit: I did run a memtest for about 15 minutes to ensure it wasn't that.  I have 16GB ram and wanted to check it anyway...

---

### Post by maxvon91 on 2012-08-03
Hello.  I just wanted to point out that this method is a little bit dangerous to your system.  You are in effect installing more than just the proposed kernel update.  This can lead to instability in the packages since proposed is not exactly stable.

Wouldn't it be more prudent to only select the kernel for installation instead of allowing all proposed packages to be installed?  Then after reboot uncheck the proposed updates as stated in the steps below?



> **isantop said:**
> The new Kernel is now available to install!

The root cause is a bug in the Intel graphics driver included in the Ubuntu kernel. The bug has been resolved and Ubuntu developers have released a new Ubuntu kernel that includes the fix. Please follow the below instructions to install the new kernel.

1.) Click the Ubuntu icon in your launcher and type "Update". Open Update Manager.
2.) Click "Settings..." on the bottom left of the Update Manager window
3.) Check the checkbox next to "Pre-released updates (precise-prosed)", enter your password and click "Close".
4.) On the Update Manager window click the "Check" button. Then click "Install Updates".
5.) After the updates are installed, reboot your laptop

Now that the new kernel is installed, we want to turn off Proposed Updates. Open Update Manager again, click Settings..., and uncheck the check box next to "Pre-released updates (precise-prosed)". You're all set!

---

### Post by isantop on 2012-08-03
> **maxvon91 said:**
> Hello.  I just wanted to point out that this method is a little bit dangerous to your system.  You are in effect installing more than just the proposed kernel update.  This can lead to instability in the packages since proposed is not exactly stable.

Wouldn't it be more prudent to only select the kernel for installation instead of allowing all proposed packages to be installed?  Then after reboot uncheck the proposed updates as stated in the steps below?

The updated kernel is now available through the normal update channels, so this process isn't necessary. But at the time, we tested installing all of the updates to ensure that nothing was unstable. In theory, you would be right, but in order to avoid confusion, we tested them all anyway.

---

