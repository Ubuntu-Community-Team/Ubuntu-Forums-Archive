---
title: "I've given Desktop Linux another shot, after 8 hours I've given up and reverted to W7"
date: 2012-09-30
forum: Testimonials &amp; Experiences
---

### Post by byb3 on 2012-09-30
I like Linux and I want to use it as my Desktop environment, but everytime I begin to use it I find something trivial doesn't work. 

Ok maybe running 3 monitors on two graphics card isn't exactly trivial, but under Windows it is.  I have spent the best part of a day trying to get my head around the myriad of processes that have to go together to give you a desktop.  Xorg, xrandr, nouveau/nvidia and Xinerama are the main culprits here.  The different window managers all seemed to have the same problems, whether it was lightdm, gdm or kdm.

It appears on the forums that randr does not work with multiple GPUs.  Even in the proposed future versions Multiple GPUs are not supported, the only thing that can be used in Xinerama which has huge drawbacks and is not exactly what I would call a solution.

Some of the problems I faced:

1. When using the 'nvidia' driver, everytime I logged out all monitors would go dead and my computer would die.  Ie it wouldn't take me to a login screen.  Something wrong with the window manager?  This didn't happen with the 'nouveua' driver.  I had to manually reboot my PC everytime I logged out.

2. It is impossible at this time in Linux to have a single desktop with multiple GPUs (with Nvidia at least) as you would in Windows.  You have to use Xinerama which isn't ideal, and you have to use two X sessions which means you can't drag your windows over from one screen to the next.  This is due to lack of support in Randr and there seems to be no major motivation to support this in the near future.

3. When you have two monitors on one screen, the desktop would stretch over both monitors.  So if you maximised Firefox it would end up being a 3840x1080 monstrosity.   All popup boxes would be in the middle of the screen and thus split over both monitors.  Bizarrely if you had just two monitors this worked fine as it does in Windows, but as soon as you added a 3rd it decided that the other two would be one huge desktop.  I couldn't find a solution to this anywhere.

4. Xorg.conf is a complete and utter nightmare.  At one point I installed the Nvidia driver after giving up on the nouveau driver, to find I was unable to boot.  Even after using the recovery console, after about 20 seconds my console was interrupted with another console which then completely froze.  If I used the 'drop to root' under recovery console it was only read only so I couldn't even modify my xorg.conf file.  In the end I had to log in quickly, and remove the /etc/X11/xorg.conf under 20 seconds in order to make the computer usable.

This isn't exactly the fault of Linux, more so to do with the stubborn nature of Nvidia.  I hear on the forums that ATI devices are working much better than the Nvidia ones.  Unfortunately as Nvidia has such market penetration this ends up being a problem for Linux.  Things seem to be improving, but very slowly.

I would advise anyone who is looking to use Multiple Monitors with Linux to avoid Nvidia.  If you are running a simple Dual Display then this will work with the TwinView option from Nvidia (proprietary), but as soon as you add a 3rd this sends Xorg totally crazy.  If you go the ATI route you will have far more success, or using one of the Eyefinity branded cards looks to be a solution.

The hardest thing to accept is the hardware is fully capable of doing what I want, the driver and software support simply isn't there at the moment.

---

### Post by overdrank on 2012-09-30
moved to Ubuntu Testimonials & Experiences

---

### Post by rai4shu2 on 2012-09-30
> **byb3 said:**
> I hear on the forums that ATI devices are working much better than the Nvidia ones.

Not from me, you won't. And yes, I do have both. ATI drivers are about five years behind in terms of features and stability, from where I'm sitting.

---

### Post by Chdslv on 2012-10-01
> I like Linux and I want to use it as my Desktop environment, but  everytime I begin to use it I find something trivial doesn't work. 

Trivial, eh? Poor you!
The world is full of trivial things...

> I would advise anyone who is looking to use Multiple Monitors with Linux to avoid Nvidia.

You have gone back to W7, right? Why the advise...?

---

### Post by Arthur_D on 2012-10-01
Why the aggressive attitude against the OP? He gave a honest reason for why Ubuntu doesn't work out for him. I can certainly understand that he wants to utilize the hardware he's got, and he did not whine about it either, just stated facts.

Why people get all aggressive-defensive on people who are merely honest and not deragotatory in their writing is beyond me.

---

### Post by Chdslv on 2012-10-01
> **Arthur_D said:**
> Why the aggressive attitude against the OP? He gave a honest reason for why Ubuntu doesn't work out for him. I can certainly understand that he wants to utilize the hardware he's got, and he did not whine about it either, just stated facts.

Why people get all aggressive-defensive on people who are merely honest and not deragotatory in their writing is beyond me.

The guy had been a member of these forums since  Jul 2010 and all of a sudden in October 2012, he had gone back to Win 7 **after** 8 hours, just because of Nvidia! Does that smell of something, Arthur_D?

Time to time, when there is a new release around, some Win 7 fanbois come around attacking Linux in many forums. It is like **all **the Linux users with NVidia drivers have problems. Read his opinion carefully, and you'd notice the feeling he/she wanted to convey! Windows is everything, and Linux distros are nothing...

Joined in June 2010 and** in 8 hours**, he/she is advising us against Nvidia, or Linux?  He/she **went** (?) back to Win 7? He/she never came out of MS Windows. Period!

---

### Post by Elfy on 2012-10-01
Round and round we go. Closed.

---

