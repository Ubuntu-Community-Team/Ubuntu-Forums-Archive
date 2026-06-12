---
title: "My first 2 weeks of using Ubuntu"
date: 2008-09-04
forum: Testimonials &amp; Experiences
---

### Post by Zerocxis on 2008-09-04
Well it all started with a conversation in one of the MMORPGs I play (Eve-Online) with a guy in my corp(guild) chat mentioning some nonsense about open source OS's. Well I started talking about how Vista was good and good for gaming, he rebutted with how Vista is bogged down (this I agree with... now) and that Vista will never take off and blah blah blah. During the course of this, he mentioned that he has XP on one box and Ubuntu on another. So I inquired about Ubuntu and Linux in general. He said that Ubuntu has pretty much the same things that Windows has, but it's free to use in anyway you want. 

So, the following day, I torrented a copy of 8.04 Hardy x86 to play around with inside of Vista with VirtualBox. About 2 hrs later, I began to install it. I was surprised by the way how it installed and the speed of the install (about 20 mins) and got the guest additions installed and immediately began to play around with some of the features. Along the way, I ran into a hurdle with the idea of command lines. Commands are not my forte so I had to find a community doc regarding the command line and some of the most common commands to use inside of the terminal. Well after I educated myself to some of the more easy to use commands, I played around with them. Next thing I knew, I had downloaded and installed the codecs necessary for listening to music and such. Also, I had installed the common plugins for Firefox as well. I installed Flash the hard way because I didn't know about the Medibuntu repositories or the finer aspects of apt-get and aptitude. 

Well, after about a week of using Ubuntu in a VM, I wanted to try it in a real environment. After doing some searching, I found out about Wubi and the way how it works. I had also, alongside the download of the x86 version of 8.04, also downloaded the x64 version so I thought, why not have Wubi install that version. Well after Wubi installed it and I rebooted Windows into the "partition" of Ubuntu, I found out that I had bitten more off than I could chew. I did not realize that the x64 version did not come with any 32 bit libraries and such for using 32 bit apps and plugins. Well I tried to cope with that by doing some of the fixs and such but to no avail. Another thing that I hated about running it in the real environment was that it did not natively support the X-Fi soundcard without doing some "h4x" in order to get it to work inside of Linux. I ended up uninstalling the "partition" and when back to using the VM of Ubuntu I still had setup. 

A few days later, I decided to give Ubuntu inside a real environment another shot, so I did a minor operation on my computer (I removed the X-Fi soundcard and enabled the onboard audio). I rebooted back into Windows to find that it booted quite considerably faster and I didn't have to do anything else to make sure that the sound worked. I then used the Wubi installer I had downloaded previously with the x86 version of Ubuntu and installed it to have another go at Ubuntu. I had also did the same on my mother's laptop as a test to see if her hard disk was really going, I found out that it was the way how Windows was seeing her hibernation of the system regarding the way it powered down the hard disk and caused it to generate errors in the Event Viewer regarding a bad sector and such. 

After configuring it on her computer to see how it ran, I was impressed and that is what led me to perform the minor operation on my computer to have another go at Ubuntu in a real environment. After it had gotten configured, I did some of the same stuff I did in my VM of Ubuntu and some other tweaks I had read about on various forums and blogs on tweaking Ubuntu to get it to run the way I wanted it to run. 

Well, after about 3 days of messing around with the Wubi of Ubuntu, I decided to pull the trigger and do a dual boot of Vista and Ubuntu. I burned the x86 version to a CD and did the live session to check for any possible errors and any stability issues. All went smoothly, so I double clicked on the install icon on the desktop and began the dual boot installation. The part where gparted came up to either delete the partition or resize it was the most interesting part because if I entered something wrong, I would have either deleted the entire Vista partition or would have messed it up in some form that I would have to reinstall it. Well after about an 45 mins of waiting for it to redo the partition, the installing commenced. It didn't even take 15 minutes and I was running Ubuntu off of my HD on the brand new partition that was set up. I booted into Vista to make sure that it still worked, and thank goodness it did. 

So after about a few days of setting up Ubuntu the way I want I started putting it to the test to really see what I can do with this OS. Needless to say, every task I have done, Ubuntu has met or exceeded expectations in regards to performance, stability (only crashes I had were GNOME related). The kernel itself is very stable as well. I am very impressed with this OS and it's capabilities. I really think that the developers of Ubuntu have introduced a nice bit of competition for Windows in regards to functionality and usability. I still am keeping my Vista partition for gaming and stuff that I cannot possibly do in Ubuntu. Anyways, I thank you for reading my long testimonial and how I discovered such a great OS such as Ubuntu. I really haven't had this fun with an OS in a very long time. Ubuntu is great!

Zerocxis

---

### Post by hyper_ch on 2008-09-04
as you are not afraid of the cli anymore you might find this quite useful:

[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

---

### Post by vikramaditya on 2008-09-04
Ahhh...self-sufficiency.  Most commendable, **Zerocxis**!  Thanks for that well written (and informative) testimonial.  :)

---

### Post by Crafty Kisses on 2008-09-05
Very nice read, nice to hear everything is working out so far. :)

---

### Post by Zerocxis on 2008-09-06
Thanks for the compliments for my very wordy testimonial (it almost was a nonstop textwall and I know that is a pita for some people). I also would like to thank hyper_cu for that guide to some of the more complex commands that can be used, thank you very much :D

Ubuntu has really surprised me these past 2 weeks in it's complexity and simplicity. It is a great tool for use in general computing as well as more complex computing and not to mention it is very fast and snappy when performing tasks like web-surfing and some office/schoolwork. I even am trying my hand at running a few games that seem to work well in Wine and Linux in general, I will let ya'll know how that goes. Will still be keeping the Vista partition for gaming and other multimedia stuff that cannot possibly be done in Linux even under the most ideal conditions. 

Thanks again for reading my testimonial and I hope to be here in the Linux and Ubuntu community for a good long while :) Ya'll have made a fan outta me!

Zero

---

### Post by wesley_of_course on 2008-09-06
Welcome and enjoy , here's another cli tool - this one for Ubuntu
[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

---

### Post by Zerocxis on 2008-09-26
Hey folks, haven't been talking much in this thread as of late. Anyways, my first month's experience with Ubuntu has been the most entertaining month I have ever had using an OS. The last time I had this much fun was with Win95/98 because of the new interface and such. 

Right now, I am running full on Ubuntu. I deleted my Vista partition because the gparted resizing didn't go as well as I thought it did (the event viewer had too many errors I wasn't sure of being reported). Along the way I decided to try some other distributions of Linux. My second favorite so far is Debian (the parent of Ubuntu) because of it's stability and speed. Another favorite is Sabayon but as a standard OS, it leaves much to be desired because of the kitchen sink approach it has. Anyways, my experiences with Ubuntu have pretty much been the same as they were as I previously stated in this thread. Just thought I'd give ya'll an update as to what has been happening on my end. 

Thanks to you all for providing me with this entertaining experience. I finally have control of my PC again through Linux and Ubuntu. :D

Zerocxis

P.S I will probably be putting Vista back on this PC and moving to Linux on my laptop because first and foremost I am a gamer and the PC I am running Ubuntu on currently was built as a gaming PC and gaming is so-so on Linux overall, but I do like some of the Linux based games I have played so far. So yeah, this was definitely worth it. :)

---

