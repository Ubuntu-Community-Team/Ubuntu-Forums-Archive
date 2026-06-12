---
title: "Just Curious"
date: 2013-01-01
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-01-01
Has anyone taken a look at the daily builds lately of ubuntu 13.04?
I was just wondering if they were using the 3.8 kernel as of yet?

Just wondering, as i read it had quite a few improvements on it...

---

### Post by kansasnoob on 2013-01-01
It's still linux-generic 3.7.0.7 :)

---

### Post by JMB74 on 2013-01-01
The raring git repo is still based on 3.7

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-r.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-r.git;a=summary)

Until they rebase to 3.8, then do some package uploads based on that, the daily iso builds will stay with kernel 3.7.

---

### Post by Cheesemill on 2013-01-01
You can always check available package versions at [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

For your query you'd just search for the linux package to see this page:
[http://packages.ubuntu.com/search?keywords=linux&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=linux&searchon=names&exact=1&suite=all&section=all)

---

### Post by offgridguy on 2013-01-01
Does it really make all that much difference to the overall performance of the OS ?
 Just curious.

---

### Post by JMB74 on 2013-01-01
Or you can check what packages/version went into the latest build by checking the contents of the ** .manifest** files at:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

> lightdm-remote-session-freerdp    1.0-0ubuntu2 
lightdm-remote-session-uccsconfigure    1.1-0ubuntu2 
lintian    2.5.10.2ubuntu3 
linux-firmware    1.98 
linux-generic    3.7.0.7.11 
linux-headers-3.7.0-7    3.7.0-7.15 
linux-headers-3.7.0-7-generic    3.7.0-7.15 
linux-headers-generic    3.7.0.7.11 
[COLOR=DarkOrange]**linux-image-3.7.0-7-generic    3.7.0-7.15 **[/COLOR]
linux-image-extra-3.7.0-7-generic    3.7.0-7.15 
linux-image-generic    3.7.0.7.11 
linux-libc-dev:amd64    3.7.0-7.15 
linux-signed-generic    3.7.0.7.11 
linux-signed-image-3.7.0-7-generic    3.7.0-7.15 
linux-signed-image-generic    3.7.0.7.11 
linux-sound-base    1.0.25+dfsg-0ubuntu3 
localechooser-data    2.49ubuntu1 
locales    2.13+git20120306-3 
lockfile-progs    0.1.17 login    1:4.1.4.2+svn3283-3ubuntu7 
logrotate    3.8.3-3ubuntu2 
lsb-base    4.0-0ubuntu27 
lsb-release    4.0-0ubuntu27

---

### Post by JMB74 on 2013-01-01
> **offgridguy said:**
> Does it really make all that much difference to the overall performance of the OS ?
 Just curious.

There are significant improvement for some hardware and in some areas.

[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MDg](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MDg)

For example, the graphics on this laptop is much smoother as a result of the changes that went into the DRM etc drivers for 3.8.

---

### Post by cariboo on 2013-01-01
> **offgridguy said:**
> Does it really make all that much difference to the overall performance of the OS ?
 Just curious.

There are several of us, that can't successfully boot from any version of the 3.7 kernel.

---

### Post by offgridguy on 2013-01-01
> **cariboo907 said:**
> There are several of us, that can't successfully boot from any version of the 3.7 kernel.
Interesting,  i was wondering as i remember reading some info regarding the
history of the GNU Project. They downplayed the importance of the kernel
to about 3% of the total system.  I am trying to find the article.

---

### Post by Cheesemill on 2013-01-01
> **offgridguy said:**
> Interesting,  i was wondering as i remember reading some info regarding the
history of the GNU Project. They downplayed the importance of the kernel
to about 3% of the total system.  I am trying to find the article.
I know the article you're talking about.

It's true that it may only be 3% of the system, but its the 3% at the bottom of the pile. Remove it and everything else falls over :)

Edit - Is this it?
[http://www.gnu.org/gnu/linux-and-gnu.html](http://www.gnu.org/gnu/linux-and-gnu.html)

---

### Post by craig10x on 2013-01-01
Thanks for all the feedback...i read the article about it and noticed it mentioned improvement for acpi power management and also lower ram usage in certain situations...so i was anxious to check it out...

When i tried a recent daily build with the 3.7 kernel i already noticed some improvements regarding power management, and it sounds like that will be refined even further with 3.8

Perhaps one of you 13.04 testers can make an announcement in this section when you get 3.8 in your updates...that way i will know to download a daily build and check it out :D

---

### Post by dino99 on 2013-01-01
by the way you can download and install the latest vanilla kernel:

inside an empty folder, download the 2 headers & the 2 images (32 or 64 depending of your actual ubuntu), then:

sudo dpkg -i *

---

### Post by offgridguy on 2013-01-01
> **Cheesemill said:**
> I know the article you're talking about.

It's true that it may only be 3% of the system, but its the 3% at the bottom of the pile. Remove it and everything else falls over :)

Edit - Is this it?
[http://www.gnu.org/gnu/linux-and-gnu.html](http://www.gnu.org/gnu/linux-and-gnu.html)
This is it, thank you.  The whole tenure of the article sounded a little "sour grapes" that the linux name has become synoymous with
everything the gnu project pioneered.
I like your explanation about the bottom of the pile.

---

### Post by grahammechanical on 2013-01-01
> **offgridguy said:**
> This is it, thank you.  The whole tenure of the article sounded a little "sour grapes" that the linux name has become synoymous with
everything the gnu project pioneered.
I like your explanation about the bottom of the pile.

I read that article myself just the other day. I noticed this:

> By the early 90s we had put together the whole system aside from the kernel. We had also started a kernel, the GNU Hurd, which runs on top of Mach. Developing this kernel has been a lot harder than we expected; the GNU Hurd started working reliably in 2001, but it is a long way from being ready for people to use in general.

and then this:

> Fortunately, we didn't have to wait for the Hurd, because of Linux. 

We would still be waiting. And it took more than fortune. A work of hard work by Linux developers.

Regards.

P.S. January 10th is marked as kernel freeze with another kernel freeze for 11th April. So, if the devs are going to bring this in for testing, then they have to do so in the next few weeks.

---

