---
title: "Issue with Unity/ Compiz"
date: 2013-10-03
forum: Ubuntu Development Version
---

### Post by Hungry Man on 2013-10-03
I installed the beta compiz in 13.04, and that broke Unity. So I then installed 13.10 and I was able to install unity. Unity is still broken. I can run 'unity' and it seems to say that it's working etc, but it isn't.

Thoughts/ information I should be providing?

Compiz runs, but I can't reinstall it."Reinstallation of compiz is not possible, it cannot be downloaded."

---

### Post by grahammechanical on 2013-10-03
I do not understand what you are talking about. When we install Ubuntu, then Compiz and Unity are installed by default. I have been using 13.10 since its development started. It has always had Compiz and Unity. What do you mean "Unity is broken?" How? You need to describe what happens when you boot Ubuntu. Saying something is broken is no help to anyone.

I am going to guess. That is all I can do. At the Grub menu select Advance Options for Ubuntu and select Recovery mode in the Advanced options sub-menu. At the Recovery menu select Resume and if that loads to a working desktop then open System Settings>Software and Updates>Additional Drivers tab and apply another video driver.

Alternatively, re-install 13.10 but this time do not tick to install third party software. When we install third party software during the installation of Ubuntu we get a proprietary video driver and it may be the proprietary video driver that is causing this problem. I never install third party software during installation and I always get a working Ubuntu and I frequently install Ubuntu during its development cycle.

Regards.

---

### Post by Hungry Man on 2013-10-03
To break it down...

I installed the beta compiz (staging) to fix an issue with 13.04. That broke a dependency that Unity had on the old compiz, unity was removed. I moved to 13.10, and then I was able to install Unity again. Unity is still installed, but it won't load (I can load graphic programs, etc, but Unity itself will not work).

Compiz is still staging. I want to try reinstalling Compiz but when I try I get that it can not be downloaded.

When I say that Unity is broken I mean that it won't run.

---

### Post by ventrical on 2013-10-03
> **Hungry Man said:**
> To break it down...

I installed the beta compiz (staging) to fix an issue with 13.04. That broke a dependency that Unity had on the old compiz, unity was removed. I moved to 13.10, and then I was able to install Unity again. Unity is still installed, but it won't load (I can load graphic programs, etc, but Unity itself will not work).

Compiz is still staging. I want to try reinstalling Compiz but when I try I get that it can not be downloaded.

When I say that Unity is broken I mean that it won't run.

What desktop are you using then?? How are you running these "graphic programs"?

---

### Post by monkeybrain20122 on 2013-10-03
What Compiz staging? I did a google search there is a compiz staging ppa but it is old (0.9.8) and is for Precise and Quantal only. There is a Compiz experimental ppa 
[https://launchpad.net/~smspillaz/+archive/compiz-experimental](https://launchpad.net/~smspillaz/+archive/compiz-experimental) 

I use it in 13.04 and has been working great (cut down cpu usage by half for graphic intensive tasks). However, once in a while it would break Unity because the Unity packages are out of sync, as a result I have disabled the ppa after hitting a sweet spot a few months ago. I am not sure what is the status of the Unity package right now but it looks like it is quite old comparing to the Compiz package (Compiz built yesterday whereas Unity is 5 months old) , so I would recommend caution if you want to use it at this point or email the maintainer first. Also, it may be an obvious point, that you should avoid other Unity ppas (like the scopes) if you use this one.

---

### Post by Hungry Man on 2013-10-04
There is no DM. I have a wallpaper and that's it. I can launch terminals with ctrl + alt + T, and then I can launch programs from them.

Monkeybrain, perhaps I installed an old experimental version. That would explain a lot. Unfortunately I have no idea how to just remove it and install the one that I should be using.

---

### Post by Alan F on 2013-10-04
> **Hungry Man said:**
> Unfortunately I have no idea how to just remove it and install the one that I should be using.

Download a new .iso for Ubuntu 13.04. Create a new install CD/DVD. Install new Ubuntu to computer ensuring that you instruct the installer to format the existing Ubuntu partition.

---

### Post by xc3RnbFO8P on 2013-10-04
In terminal do:
> ccsm
and see if Unity plugin is active

---

### Post by deadflowr on 2013-10-04
> **Ringi said:**
> In terminal do:

and see if Unity plugin is active

or in existence.

---

### Post by Hungry Man on 2013-10-04
Unity was not installed. Either way, I decided to just reformat. Easiest way to fix this. Thanks.

---

### Post by uval2 on 2014-01-28
I've just upgraded from 13.04 to 13.10 and had exactly the same problem.
After trying numerous different things (apt-get clean, synaptic->fix broken packages etc...)
I've found out that *aptitude install unity* could solve the pblm.

Regards,
val

---

