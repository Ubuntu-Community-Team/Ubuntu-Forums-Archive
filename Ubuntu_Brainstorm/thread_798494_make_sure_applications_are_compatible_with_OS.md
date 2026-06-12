---
title: "make sure applications are compatible with O/S"
date: 2008-05-18
forum: Ubuntu Brainstorm
---

### Post by wpshooter on 2008-05-18
IMO, it would be nice if BEFORE they write and release this new O/S that they check and make sure that **ALL** of the application programs that are listed in the Synpatic package manager will install and run properly on this new version of the O/S, unlike Hardy, which currently does not have this capability.

What good is a drop dead O/S if the applications can not be installed and ran on it !!!

Thanks.

---

### Post by qamelian on 2008-05-18
> **wpshooter said:**
> IMO, it would be nice if BEFORE they write and release this new O/S that they check and make sure that **ALL** of the application programs that are listed in the Synpatic package manager will install and run properly on this new version of the O/S, unlike Hardy, which currently does not have this capability.

What good is a drop dead O/S if the applications can not be installed and ran on it !!!

Thanks.
Can you provide specific examples? I have several Hardy installs using vastly different arrays of software for different purposes and haven't encountered anything that won't install or run properly.

---

### Post by wpshooter on 2008-05-18
Well for example, 2 are **xsensors** and **glipper**.

Thanks.

---

### Post by qamelian on 2008-05-18
> **wpshooter said:**
> Well for example, 2 are **xsensors** and **glipper**.

Thanks.
Well, I can't comment on xsensors, but what is wrong with glipper? It seems to be working fine here.

---

### Post by Steveway on 2008-05-18
Just installed xsensors and it works. My Hardware is not supported by it but it works.
I'm not gonna install glipper but I assume that it works, too.
Are you sure that isn't only a faulty install on your side?

---

### Post by wpshooter on 2008-05-18
> **Steveway said:**
> Just installed xsensors and it works. My Hardware is not supported by it but it works.
I'm not gonna install glipper but I assume that it works, too.
Are you sure that isn't only a faulty install on your side?

NO, there is nothing wrong with my installation(s).  I have installed the Hardy (final release) a goodly number of times and there is nothing wrong with my installation other than the bugs in it that have not been addressed !!!

Are you SURE that you did not have to do some tweaking to get the xsensors program to work ?

The thing that is wrong with glipper in Hardy is that it does not work like it did (perfectly) under Gutsy and that the name for the program is one thing in Synaptic and then all of a sudden it is named something else when it is found hidden in the add to panel functions.  And until you reboot the machine it is not found in the add panel at all and there is NO warning during the installation of glipper from Synaptic that the machine needs to be restarted for the program to be available.

These are examples of bad or at a minimum, incomplete programming.

Thanks.

---

### Post by olskar on 2008-05-19
I agree with wpshooter. There is more programs in synaptic that does not work. One examle is gnome-voice-control. Install it and try to add it to the gnomepanel. Good luck.

---

### Post by smartboyathome on 2008-05-19
These need bug reports filed on them. There are 25000+ packages in the repos, so it is common for packages to be missed and then found by someone else. This goes right down to the trying to make Ubuntu "bug free", which isn't possible.

---

### Post by wpshooter on 2008-05-19
> **smartboyathome said:**
> These need bug reports filed on them. There are 25000+ packages in the repos, so it is common for packages to be missed and then found by someone else. This goes right down to the trying to make Ubuntu "bug free", which isn't possible.

How could they be "MISSED" ?

All you would have to do is go down the/a listing of the applications in Synaptic and check them off after you had installed and tested them **BEFORE** you released the final version of each release of Ubuntu.

You are probably going to say this is going to be a monumental task BUT I think taking the time to do that would be better than the embarrasement to Ubuntu when new users come along to use the O/S and the applications won't install and/or run correctly and then they wind up dropping Ubuntu as their choice of O/Ss.  And I know that there a users out there that really don't care if that happens or not but I predict that Ubuntu is not going to last LONG-TERM if they don't come up with a more **STRUCTURED** developement strategy for Ubuntu.

Thanks.

---

### Post by shad0w_walker on 2008-05-19
Ok, well if it's worth the time, here's a suggestion, you do it.

Seriously, learn the concept of time and multiplication. It's a ridiculous and completely impractical task to check 25,000 programs individually to make sure they all work. Whilst you're at this though, why don't you go phone up Microsoft and complain as well? I mean you PAY for that so surely they should check everything completely as well.

---

### Post by christianxxx on 2008-05-19
While I can understand OPs concerns, I must say its nothing short of unfair and silly.
Canonical do an increadible effort to test and verify the software before it's included, but diverse hardware configurations, and great diversity in installed libraries and other software make this more than impossible. You could easily calculate testing scenarios to 25000*25000*[number of hardware configurations].

Furthermore, Linux is based on a community effort, so if you find something wrong, report it. Only reporting it will result in a fix. Complaining in the supportforums will only give you workarounds, or if you are lucky, a solution.

And finally, not all 25000 programs are intended for you. You as a responsible user have to make sure you meet the hardware requirements and possibly other requirements.
That is no different from any other OS. Where it actually do differ from Windows is that Linux usually will help you out with software requirements.

---

### Post by wpshooter on 2008-05-19
> **christianxxx said:**
>  
Canonical do an increadible effort to test and verify the software before it's included, but diverse hardware configurations, and great diversity in installed libraries and other software make this more than impossible. You could easily calculate testing scenarios to 25000*25000*[number of hardware configurations].



When an included application WILL work with Dapper and WILL work with Edgy and WILL work with Feisty and WILL work with Gutsy but will NOT work with Hardy that tells me that there is something not exactly correct in these testing processes.

And yes I have reported (and will continue to report) these bug NUMEROUS times thru out the entire development phase of Hardy and they are yet to be fixed.  And I know that this is probably an overwhelming task, which leads me to think that they are just trying to accomplish TOO MUCH in too short a time frame with too little resources and this may wind up hurt them in the long run (although I hope not).

Thanks.

---

### Post by smartboyathome on 2008-05-19
Sounds like you want Debian. It would be either Ubuntu makes everything absolutely stable so that there are no bugs whatsoever, but the programs are terribly obsolete (this is debian stable), or it includes some of the latest stable software, but risks there being bugs. It could be that the app was upgraded and a bug was introduced to the code because of that. If it were able to work from dapper to gutsy, check to see what versions they were in each.

Also, even though you file bugs,they may not get fixed right away. This can take a little time, especially if the program upstream has not had it fixed yet.

---

### Post by DrMega on 2008-05-19
> **wpshooter said:**
> How could they be "MISSED" ?

In my experience, the problem is often that some dependancy is missing. As a developer, I can see that this would be easy to overlook.

You have all sorts installed on your machine. You test an app, it works, great. You package it up and give info about all the dependancies (if you can remember them all). You miss one or two but it works on your machine, and it works on the testers machines (because they've already got everything installed), it goes to the user and kaboom!

I've installed apps from the repos that haven't worked. Quite often a bit of digging about (and some guess work) points me in the direction of some library which I install, and hey presto, fixed.

It's not ideal but this approach has solved stuff for me before.

(EDIT: I should point out, so as not to mislead anybody, when I pointed out I am a developer, I meant on Windows - I'm not an Ubuntu developer so can't comment about specifics).

---

### Post by 23meg on 2008-05-19
[QUOTE=wpshooter]And yes I have reported (and will continue to report) these bug NUMEROUS times thru out the entire development phase of Hardy and they are yet to be fixed.[/QUOTE]

Could you point to some examples? 

There's no other way to fix this kind of thing other than having a large, responsive and responsible group of testers who run the development versions and file good bug reports. Just saying "Please make all programs run, thanks" would be both stating the obvious, and demanding that others do the work that you as a tester are equally responsible from.

---

