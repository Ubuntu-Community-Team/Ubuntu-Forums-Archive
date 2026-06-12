---
title: "Remastersys 3.0.4-1 for Ubuntu precise(12.04) and quantal(12.10) released"
date: 2013-01-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Fragadelic on 2013-01-06
From the changelog:


      * 3.0.4-1
      * iso is now also isohybrid so it can be dd'd to a usb key simply without having to use usb creator or unetbootin
      * fixed urandom issue
      * fixed ssh keys being leftover
      * fixed resolv.conf removal for 12.10 as if it is a link, it will not be removed
      * fixed issue with timezone for live system
      * fixed issue with too many tty's logged in on the live system

Also added .desktop files for remastersys-gui and remastersys-gtk for kde.  Fixed a missing dep in remastersys-gtk that didn't have remastersys as a dependency.

One thing I almost forgot to mention is that creation of the filesystem.squashfs is now completed in 1 run.

Info on adding the repository and installing the packages can be found at [http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

---

### Post by ray field on 2013-01-08
Hooray!!!!

thanks, Fragz

---

### Post by Fragadelic on 2013-01-08
I've been doing a lot of testing with the higher compression for mksquashfs and it works fine now.

If you want to have higher compression, add "-comp xz" to the end of the squashfsopts and it will have the highest compression possible.  This increases the time to create the squashfs file considerably but will allow smaller iso sizes.

---

### Post by Portaro on 2013-01-08
Thanks!:D

---

### Post by mörgæs on 2013-04-27
Are there any news about support for 13.04?

---

### Post by Fragadelic on 2013-04-27
The latest version 3.0.4-2 works with 13.04.

---

### Post by mörgæs on 2013-04-28
What... are you stopping development?
[http://www.remastersys.com/](http://www.remastersys.com/)

Please say it's a joke.

---

### Post by Fragadelic on 2013-04-28
It is no joke.  I have stopped development of remastersys altogether.  There is someone that might fork it and continue but not sure at this point.  I am completely done with it and remastersys is dead now.h

---

### Post by Karlchen on 2013-04-28
Hello, Fragadelic.

I knew  that you were serious about it. This is the second time that you drop your Remastersys project. The first time you dropped Remastersys at v2.18.1 way back in 2010. Then you revived it in 2011, just to stop it in 2013 a second time. And again, like in 2010, you seem to have been really quick in removing the repositories from the web.
Therefore your statement that you made only a day ago that Remastersys v3.04.2 worked on Ubuntu 13.04 is not really helpful, because as far as I can find out there is no way of downloading and hence installing Remastersys v3.04.2 anywhere.
Or have I missed a location?

Kind regards,
Karl

---

### Post by Gavin77 on 2013-04-28
If you already have Remastersys installed but want the deb to install on another system etc you can use dpkg-repack.

```
sudo dpkg-repack remastersys
```

There is also a program called Relinux to create a livecd backup.  I tested that out today and it worked nicely.

---

### Post by viordiasko on 2013-04-28
I hope this is a joke. Remastersys has always been my first choice of clone/backup software.

The download links are 404'ed and I've had to use 
[FONT=Courier New]remastersys_3.0.3-1_all.deb
 remastersys-gui_3.0.3-1_amd64.deb[/FONT]
from a copy of 12.10. I'll see how this goes..

Does anyone know where I can get remastersys 3.0.4-2?

---

### Post by Gavin77 on 2013-04-28
Edit: download links in post 20.

---

### Post by Fragadelic on 2013-04-28
3.0.4-2 has been out for many months now.  Yes this is the end of the road.  I have also stopped development help of another project that actually has the website so it isn't right for me to continue using the space without giving something back and I do not have the funds to host it myself nor the desire.

I got tired of arguing over things that, in the end, really mean nothing.  This all started out as a fun hobby and stopped being fun when folks started demanding things and weren't willing to do anything about it.

Lately, all this has provided me is stress and frustration at the lack of appreciation of my time and experience.  It was never accepted upstream either by ubuntu or debian and I received lots of negative comments about it so it was time for me to leave all of that behind.

There are other alternatives and in fact quite a few forks of it so you just have to search for them.

A select few folks will be receiving my final packages that work perfectly with Debian Wheezy and Ubuntu up to 13.04 but I won't be offering them up for anyone else.  What they do with them is of no concern to me other than the fact that they need to change the name if they want to continue it and provide it to folks.

I apologize to all the good folks I have met over the years but the number of those compared to the ones that just provided frustration meant it was a very negative experience lately and I have no desire to continue down this road.

I freely offered it up for almost 7 years with very little return on what I invested it in it over the years so I cut my losses and and putting it all behind me.

Those that run projects for anything longer than 3 years understand where I am coming from.  Those that don't and think I owe them or anyone else anything are the reason I have stopped.

Time for me to concentrate on family and my career - the 2 things that are positive in my life and actually provide me with joy.

---

### Post by SIW2 on 2013-04-28
Fragadelic, 

I registered to thank you for the work you have done with remastersys. 

As a newcomer to Linux, it has been great. Very useful to help introduce family and friends to linux also. 

I have been using it on 12.10. Now I have installed Ubuntu 13.04 amd64, I hope someone can keep up the development.

Best of luck and happiness for the future. :D

---

### Post by Karlchen on 2013-04-28
Hello, Fragadelic.

We are not entitled to question your decision to stop developing Remastersys. It is your life. You decide. If Remastersys development has turnt into a pure burden, it is certainly time to stop developing it.
I do wonder, however, whether the software packages might not have survived a few more months [on your sourceforge space](http://sourceforge.net/projects/remastersys/) without causing any costs or hassle. - Anyway, too late, they are gone.

Remastersys helped me migrate a fully configured Ubuntu system to a new machine twice thus sparing me the time of performing a new installation from the scratch twice. So I will be missing it sooner or later.

Kind regards,
Karl

---

### Post by Fragadelic on 2013-04-28
It looks like this will be the fork that I authorize - [http://system-imaging.blogspot.ca/](http://system-imaging.blogspot.ca/)

I am in the process of handing everything over to them.

---

### Post by pfeiffep on 2013-04-28
> **Fragadelic said:**
> 3.0.4-2 has been out for many months now.  Yes this is the end of the road.  I have also stopped development help of another project that actually has the website so it isn't right for me to continue using the space without giving something back and I do not have the funds to host it myself nor the desire.

I got tired of arguing over things that, in the end, really mean nothing.  This all started out as a fun hobby and stopped being fun when folks started demanding things and weren't willing to do anything about it.

Lately, all this has provided me is stress and frustration at the lack of appreciation of my time and experience.  It was never accepted upstream either by ubuntu or debian and I received lots of negative comments about it so it was time for me to leave all of that behind.

There are other alternatives and in fact quite a few forks of it so you just have to search for them.

A select few folks will be receiving my final packages that work perfectly with Debian Wheezy and Ubuntu up to 13.04 but I won't be offering them up for anyone else.  What they do with them is of no concern to me other than the fact that they need to change the name if they want to continue it and provide it to folks.

I apologize to all the good folks I have met over the years but the number of those compared to the ones that just provided frustration meant it was a very negative experience lately and I have no desire to continue down this road.

I freely offered it up for almost 7 years with very little return on what I invested it in it over the years so I cut my losses and and putting it all behind me.

Those that run projects for anything longer than 3 years understand where I am coming from.  Those that don't and think I owe them or anyone else anything are the reason I have stopped.

Time for me to concentrate on family and my career - the 2 things that are positive in my life and actually provide me with joy.

I am relatively new to Linux and Remastersys. I know that from a new comer this might not mean much to you, but I'm positive that **you **and Remastersys will be missed. 

I'm happy that I used your product and that I have the most recent release that works perfectly with Raring and Linux Mint 14!  [SIZE=4]Thank You[/SIZE]

---

### Post by Fragadelic on 2013-04-28
I will make final update packages with some recent fixes and provide them as a direct download from my website in the next few days.  After that, Robert Dohnert's fork of remastersys should be used as I will be passing on my sources to him and will be available from [http://system-imaging.blogspot.ca/](http://system-imaging.blogspot.ca/)

---

### Post by gobangos on 2013-04-28
sad!!
Thank you!!
latest production, thanks Remastersys!!
[http://gobangos.wordpress.com/](http://gobangos.wordpress.com/)

---

### Post by rjdohnert on 2013-04-29
We have provided the packages for Remastersys 3.0.4-2 on the System Imager website.  These are provided as a convenience for those of you that need them now.  As soon as we get the source files and final debs from Fragadelic we are very much anticipating getting started to work on the new versions.  We look forward to serving you guys and i thank you all for your ongoing support.
[URL="http://system-imaging.blogspot.com/"]
http://system-imaging.blogspot.com/[/URL]

---

### Post by Portaro on 2013-04-29
**Thanks for all years of good work with Remastersys**, with the end of Remastersys i also end my remaster projects with Ubuntu.

Greetings to Fragadelic.

---

### Post by C.S.Cameron on 2013-04-29
Thanks Fragadelic:
Your work has been significant to the progress of Linux.
I wish you all the best in your future endeavors.
Cork

---

### Post by Fragadelic on 2013-04-29
I have re-enabled the repositories for now but I don't know how long I can keep them up.

---

### Post by Karlchen on 2013-04-29
Hello, Fragadelic.

Thanks a ton for re-enabling the repositories, even if this may only be for a short while.
And thanks a ton, too, for handing over the project to RJDohnert.

Hello, RJDohnert, 
of course, thanks a ton to you for taking over. Hopefully we remastersys users will not cause you frustration too in the end.

Kind regards,
Karl

---

### Post by chinmay3 on 2013-08-11
[B]Thank You very much  _Fragadelic _for the great piece of software .. Remastersys.
[/B]This is the one of the best software in Linux world. It always helped me when i was in trouble & still helping me. I never said thanks this way ( from deep heart) to anybody (except you). 
Thank you very much.):P

---

### Post by Fragadelic on 2013-09-09
For those that are interested, I have the sources available for a donation.  You can check my website [http://www.remastersys.com](http://www.remastersys.com) for details on how to get them.

You will get the Ubuntu sources for 32 and 64 bit for the current version 3.0.4-2 and the current Debian versions for Squeeze and Wheezy.

Not sure how long the repo will be up as the webspace may not be available much longer since the project that hosts it has also stopped and I'm not sure if he will be keeping the hosting going much longer.

This is available to anyone.

---

### Post by leeper69 on 2014-02-13
thank you fragadelic for all that you have done for the linux community!
I have used your software for a few years and it always just worked.
your contribution will be missed and so will you!
why do the best programs always fade away?
Hopfully your fine work will be picked up by someone as talanted as you.

---

### Post by Fragadelic on 2014-02-13
Thanks for the kind words.

I'm renewing the domain for at least another year so the repo will still be there for at least another year.

You never know, I may change my mind and continue.  For now, the current versions work with the current versions of ubuntu and debian.

---

### Post by C.S.Cameron on 2014-02-14
Thank you.
Install to 12.04 went perfect.

---

