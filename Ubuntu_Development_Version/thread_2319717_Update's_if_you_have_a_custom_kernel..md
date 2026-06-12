---
title: "Update's if you have a custom kernel."
date: 2016-04-06
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-04-06
Will apt suggest or install "new" kernels if you currently run the newest stable one? 

ex: I am now on  4.6.0-040600rc2-generic, my latest kernel from repository is: 4.4.0-17-generic.

Will i get an update when 4.4.0-18-generic is released?

---

### Post by PaulW2U on 2016-04-06
> **izznogooood said:**
> Will i get an update when 4.4.0-18-generic is released?
One of the great mysteries abut this sub-forum is why some choose to use a version of the Linux kernel that is not part of the current development version of Ubuntu and its various flavours. Are we not here to discuss and test what actually **is** the current development version?

I mean no disrespect intended towards you izznogooood. May be we need an "experimental" sub-forum to discuss such matters?

I think that you will get the update but may be not a prompt to reboot.

---

### Post by izznogooood on 2016-04-06
I must say you make a valid point PawlW2U, an experimental sub-forum would be the correct place to ask such a question.

---

### Post by zika on 2016-04-06
> **izznogooood said:**
> Will apt suggest or install "new" kernels if you currently run the newest stable one? 
ex: I am now on  4.6.0-040600rc2-generic, my latest kernel from repository is: 4.4.0-17-generic.
Will i get an update when 4.4.0-18-generic is released?Yes, that is the main purpose of packages like linux-image-generic...
> **PaulW2U said:**
> One of the great mysteries abut this sub-forum is why some choose to use a version of the Linux kernel that is not part of the current development version of Ubuntu and its various flavors. Are we not here to discuss and test what actually **is** the current development version?
I mean no disrespect intended towards you izznogooood. May be we need an "experimental" sub-forum to discuss such matters?
I think that you will get the update but may be not a prompt to reboot.Having some other kernel does not mean that &#8222;proper&#8220; kernel is not installed and I'm yet to see two identical installations of any OS apart from those in classrooms/workspaces (and even there each of those is somewhow personalized) and such... Should we even dress the same while we are using/testing Ubuntu? ;)
It is easy to make a check while we do log-in if we have all required for testing forum so we could write, even read... ;) But, for some of us that venture only in this part of vast UF that will be like getting a ban... Maybe we deserved it because we ventured into some other pastures and smelled some other flowers... Shame on us... ;) This is not for the first time that we get scolded...

---

### Post by grahammechanical on 2016-04-06
Someone usually starts a thread on a specific release candidate kernel for those who want to install & test. I see nothing wrong with having those threads in this section of the forum. The section title is quiet specific but I do not think that we should be rigid about the definition of the section title. And it is not unknown for us to go off topic from time to time. A little freedom in these cases keeps the forum alive.

Regards

---

### Post by cariboo on 2016-04-06
> **PaulW2U said:**
> One of the great mysteries abut this sub-forum is why some choose to use a version of the Linux kernel that is not part of the current development version of Ubuntu and its various flavours. Are we not here to discuss and test what actually **is** the current development version?

I mean no disrespect intended towards you izznogooood. May be we need an "experimental" sub-forum to discuss such matters?

I think that you will get the update but may be not a prompt to reboot.

To answer your question, I have had to use a custom/newer kernel a couple of times. because my system wouldn't boot with the supplied kernel version. In both cases it was a system with an Intel Atom cpu. I created a bug report, and was asked to do a diff between a working kernel, and one that wouldn't boot, it took a couple of days, but in both cases the problem was solved fairly quickly. 

Note: This was several versions ago, before the focus was on quality.

---

### Post by MikeMecanic on 2016-04-06
@ izznogooood

It does not affect by any meaning incoming updates.  I have Proposed enable since 25 weeks now and I didn't have any issues related to Stock Kernel.  The only thing that you must be aware of, is that it may take up to a full day before things come back to normal.  Usually, after receiving the first updates the system runs normally.
 
 In rc-2, there is a bug in the boot sequence that disappear after receiving the first updates.

@ PaulW2U:

Your pushing a lot dear Paul.   
 
 Stock Kernel is what testing is all about and is closely linked to the development of Ubuntu   
 
 Keep in mind that If Ubuntu Xenial Xerus is on is way to be among the best O/S on the market. It has a lot to do with those who were testing Kernel 4.4 last year.  Those of us on stock Kernel will maintain Ubuntu on top of the list.  
 
 Regards,

---

### Post by izznogooood on 2016-04-07
> **MikeMecanic said:**
> 
 In rc-2, there is a bug in the boot sequence that disappear after receiving the first updates.


I'm pretty sure this kernel is not in the purposed repo, and i dont understand how running a custom kernel could delay updates? (I did not install this via any repo's).
Does apt take the kernel in to consideration when building its lists? (Not just repositories)

---

### Post by zika on 2016-04-07
> **izznogooood said:**
> I'm pretty sure this kernel is not in the purposed repo, and i dont understand how running a custom kernel could delay updates? (I did not install this via any repo's).
Does apt take the kernel in to consideration when building its lists? (Not just repositories)Notice the (strongly intentional) difference in names of such (actually all, for sake of clarity of course) packages (kernels, images and headers, in this case) and You'll start seeing the bigger picture of how apt/dpkg does its job with packages... Source of the package is very low (if any) on that tree...

---

### Post by izznogooood on 2016-04-07
It might be the language, but that made no sens to me :D

---

### Post by MikeMecanic on 2016-04-07
> **izznogooood said:**
> It might be the language, but that made no sens to me :D

  	 	 	 	   I’m always loading the latest Kernel at night and I shutdown the computer till the next morning.  Why updates are delayed?  It’s not a big deal.  _Just keep in mind that there is a delay_.  If your experiencing bugs, the solution rely all the time on related updates.
 
 
 I was given rc-2 as an example because it was the first major issue in the last 25 weeks.  I was not able to shutdown or reboot after loading it:  Abnormal and frozen splash screen.  It is rarely the case (minor issues only) and It’s never the same.
 
 
 PPA are available each Sunday night (EST), an hour or so after Linus Torvald announcement.

---

