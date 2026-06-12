---
title: "Study on the configuration of the Linux kernel"
date: 2011-08-18
forum: The Cafe
---

### Post by ahubaux on 2011-08-18
Dear Ubuntu users, 

we are a team of researchers from the GSD Lab of the University of Waterloo (ON, Canada). We do research on configuration methods and algorithms and are conducting a study on the problems faced by users during the configuration of the Linux kernel.  We would greatly appreciate it if you could answer this questionnaire: [https://docs.google.com/spreadsheet/viewform?formkey=dHJrQ1B6OXVCRTRmbGJ2ZlFQTmdpQVE6MA](https://docs.google.com/spreadsheet/viewform?formkey=dHJrQ1B6OXVCRTRmbGJ2ZlFQTmdpQVE6MA)
It should not take you more than 15 minutes to complete. 

Thank you very much for your contribution.

---

### Post by An Sanct on 2011-08-18
This should go into the community caffe ... administrators notified 

(I think more people, who will answer the study, will see it there)

---

### Post by ahubaux on 2011-08-18
Thanks for letting me know! Should I post it again or will the admin move it there?

---

### Post by sffvba[e0rt on 2011-08-18
Already moved :p


404

---

### Post by Copper Bezel on 2011-08-18
Is this for typical desktop users?

Because, I mean, I can't imagine a bunch of Never, 0, 0, 0, 0, N/A answers are going to be very useful to the study. (What's an xconfig again?)

---

### Post by sffvba[e0rt on 2011-08-19
> **Copper Bezel said:**
> Is this for typical desktop users?

Because, I mean, I can't imagine a bunch of Never, 0, 0, 0, 0, N/A answers are going to be very useful to the study. (What's an xconfig again?)

I call hax! (Or how else did you know my answers...?)


404

---

### Post by An Sanct on 2011-08-19
> **Copper Bezel said:**
> Is this for typical desktop users?

Because, I mean, I can't imagine a bunch of Never, 0, 0, 0, 0, N/A answers are going to be very useful to the study. (What's an xconfig again?)

Well, my guess was, that in the community cafe one would find more people, that know what a kernel is in the first place ;)

Besides, if one is not interested, one will not go and answer, so the probability of answers like "I don't know" and "what is that?" is slim.

---

### Post by ahubaux on 2011-08-19
Thanks for moving the post to the right place :D.

The questionnaire is for any user who has ever fought with the Linux kernel. Our problem is that modern distributions like Ubuntu have made Linux so "affordable and easy" that less and less people get their hands dirty in the kernel ;-). We hope that those who still do will spare 15 minutes of their time to help us figure how to improve the kernel configurators. 

xconfig is a graphical alternative to menuconfig.

---

### Post by Bandit on 2011-08-19
I am pretty fluent at building my own kernels from source, so I did the survey for you. 

Menuconfig can be run without a xwindows sub system, while xconfig requires QT and xfree86 or xorg to be installed IIRC.

---

### Post by ahubaux on 2011-08-19
Thank you very much Bandit, both for filling out the questionnaire and clarifying the difference between menuconfig and xconfig.

---

### Post by Bandit on 2011-08-19
> **ahubaux said:**
> Thank you very much Bandit, both for filling out the questionnaire and clarifying the difference between menuconfig and xconfig.

Not a problem. I wished I could have answered more it the questionnaire but currently the default kernel shipped with Ubuntu for example really doesnt need any reconfiguring unless someone has older equipment and is trying to lighten up the kernel by removing lots of built in drivers and such, or adjusting the kernel timing. But like I mentioned currently the basic kernel with Ubuntu is fine and sometimes best to stick with for compatibility reasons. Now when there is a hardware transition cycle going on like a few years back going from 32bit to 64bit, you will see a lot of users building custom kernels to make better use of hardware. But right now everything is just going to touch screen devices that work fine with the basic kernel config. So you want see many custom kernels. Now one sector of the market you will see many custom kernels is the the robotics industry for example or manufacturing industry for automated equipment. 

Hope this helps.

Joe

---

