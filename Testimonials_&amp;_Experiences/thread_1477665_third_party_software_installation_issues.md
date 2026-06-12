---
title: "third party software installation issues"
date: 2010-05-09
forum: Testimonials &amp; Experiences
---

### Post by Ronnie_ovms on 2010-05-09
Hi everyone,
 

 I am sort of newish to Linux – Ubuntu in my case, I have to admit – I love it, there are so many advantages to using it over the Windows environment, it is much more stable, faster, much improved L AF and many more compliments can be given....
 

 I have installed Ubuntu for the third time, and now the new V10.04.
 I have played around with it, installed additional packets, software and was pretty impressed and got to know the system better,  and It is not difficult to get use to it after using Windows for 17 years.
 

 However: when I started using the Internet, I have come across some issues that where a bit time consuming to resolve, and make things operate and render properly, one of the easier issues was the Adobe Flash Player installation, but when it got to some sites that have Java, Ajax and other software requirement do make things display correctly it started getting really time consuming.
 

 So after a few of hours trying to download and install Java, I have given up.
 

 I think that if the Linux community developers where thinking of how to make certain programs install in a more simple way there would have definitely been more users diverting to Linux, as not every one is computer savvy, and not many people these days have the time to sit there for hours getting their computer software to work.
 

 To conclude: I will probably return and use Linux one day when all other issues have been addressed, as I previously said, it is very good and I like it, but as much as I like it and would have liked all my office computers changed to Linux environment I don't think it is quite practical for us yet.
 

 Would love to know that some of these issues have been addressed and return to using Ubuntu one day.
 

 Ronnie_ovms

---

### Post by Sealbhach on 2010-05-09
Hi,
Just follow the guide here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Don't be put off by the commands, just copy and paste them into the terminal. This will solve 99.9999% of your multimedia problems.

Also, ubuntu doesn't include all this third party stuff purely for legal reasons. There is a distro called Linux Mint that is based off Ubuntu but they go ahead and include all this stuff already.
.

---

### Post by 3rdalbum on 2010-05-09
> **Ronnie_ovms said:**
> So after a few of hours trying to download and install Java, I have given up.

Please don't give up yet. Java is easy to install - you just need to get out of the Windows mindset.

> I think that if the Linux community developers where thinking of how to make certain programs install in a more simple way

That's why we use the repositories. If something is in a repository, it becomes very easy to install.

Java is in a repository. In Ubuntu 10.04 that repository is known as Partner, and it's not activated by default. It's easy to activate; just go to System > Administration > Software Sources, click on Other Software, and then put a tick alongside "http://archive.canonical.com/ubuntu lucid partner".

Click Close and you'll be asked if you want to reload the package list. Click OK.

Now you can go to Synaptic or Ubuntu Software Center and install the "sun-java6-plugin" package.

See? You can't get much easier than that.

Most of the software you'll ever need will be in repositories. You can easily add third-party repositories to your system to gain access to a lot of new software, and it's increasingly common for programs to install via a Deb package and automatically add a repository to your system too, to keep things up-to-date.

---

### Post by Ms_Angel_D on 2010-05-09
Ronnie_ovms, Thank you for sharing your experience. If you need support please see the support sections of the forums.

Thanks,
Angel

---

