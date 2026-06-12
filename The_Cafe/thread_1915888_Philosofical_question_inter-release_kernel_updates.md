---
title: "Philosofical question: inter-release kernel updates"
date: 2012-01-27
forum: The Cafe
---

### Post by lads on 2012-01-27
Hello everyone,

This is perhaps a philosophical question but bournes out of the increasing trouble I'm having with the kernel updates between releases, especially in the 64-bit version. We had another of these updates around Tuesday and once again a lot stuff went heywire: Evince, Rythmbox, Clementine, VirtualBox and Eclipse all experienced different levels of usability break down the following days. Evince was completelly irresponsive up to this morning, when a new batch of updates fixed something. The others I've more or less managed to get to run properly, apart from Rythmbox.

The issue is that I'm an intermediate user and already know my way around to look for solutions for this sort of problems, but what about new users? We are simply presented with the update dialog and click ok; the next day a bunch of stuff stops working.

So the question is: wouldn't it be more prudent to have kernel updates only with new releases? Why does the development team opt to have these inter-release kernel updates?

Thanks for reading and please share your thoughts.

---

### Post by TheNessus on 2012-01-27
> **lads said:**
> Hello everyone,

This is perhaps a philosofical question but bournes out of the increasing trouble I'm having with the kernel updates between releases, especially in the 64-bit version. We had another of these updates around Tuesday and once again a lot stuff went heywire: Evince, Rythmbox, Clementine, VirtualBox and Eclipse all experienced different levels of usability break down the following days. Evince was completelly irresponsive up to this morning, when a new batch of updates fixed something. The others I've more or less managed to get to run properly, apart from Rythmbox.

The issue is that I'm an intermediate user and already know my way around to look for solutions for this sort of problems, but what about new users? We are simply presented with the update dialog and click ok; the next day a bunch of stuff stops working.

So the question is: wouldn't it be more prudent to have kernel updates only with new releases? Why does the development team opt to have these inter-release kernel updates?

Thanks for reading and please share your thoughts.

impossible to get our thoughts into this without knowing which release you're talking about. I myself am in 10.04 and therefor can't use 3.2 kernel, which is probably what you upgraded.

---

### Post by coffeecat on 2012-01-27
> **lads said:**
> We had another of these updates around Tuesday and once again a lot stuff went heywire:

This is not common experience. A question: do you have the proposed repository enabled?

---

### Post by lads on 2012-01-27
> **coffeecat said:**
> A question: do you have the proposed repository enabled?

Thanks for answering. What repository exactly? All my colleagues get regular updates also, I thought this was the standard behaviour.

---

### Post by coffeecat on 2012-01-27
> **lads said:**
> I thought this was the standard behaviour.

What, everything breaking with an update? No, definitely not standard behaviour. :wink:

OK. Two issues here, one a technical one. The proposed repository is for updates to packages which need some QA testing before being put into the regular repositories. The reason I asked the question is that some people enable the proposed repository thinking that they are getting the latest and greatest. They may be getting the latest but they are also inviting system breakage. Not everything that goes into proposed survives testing. If you want to check to see whether you have the proposed repository enabled, look in Synaptic -> Settings -> Repositories if you are running 11.04 or earlier, or in Software Centre -> Edit -> Software Sources if 11.10.

But to turn to your philosophical question, "Why does the development team opt to have these inter-release kernel updates?" The answer is security patches and bugfixes primarily - necessary ones. Kernel updates are a good thing and do not commonly cause any breakage at all. I can only remember one really bad breakage with a kernel update and that was back in 2006.

---

### Post by lads on 2012-01-30
Thank you for your answer coffeecat. 

I'm working with a Lenovo Thinkpad T420 since September and every single kernel upgrade since then has broked stuff. The most problematic have been Lotus Notes and Virtual Box, but I've also experienced regular issues with media software like the eye of gnome, Rythmbox and Evince.

As you can see from the following, my system is yet to fully recover from last week's update:

```
$ sudo synaptic
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
```

Is there a way I can change the settings you suggest simply editing files?

The truth is that my colleagues using 32-bit versions do not have the same issues that I experience. Even if this is more of a technical issue, the amount of programmes affected would call for a more carefull update timing, IMHO.

Best.

---

### Post by coffeecat on 2012-01-30
I really don't believe this is anything to do with kernel updates. If it was, the forum would be flooded with help threads every time there was a kernel upgrade. Nor is it anything to do with the updates themselves - similar story. I'd guess there is a serious underlying issue in your particular system. I run 64-bit, by the way, and all my recent updates (and many there are) have been flawless.

Or possibly you are very unlucky and there is a hardware issue with your particular machine which is causing this.

If I was in your situation I would choose between spending hours investigating, or backing up personal files and re-installing and seeing if that helps.

---

### Post by grahammechanical on 2012-01-30
I do not speak with the same authority as coffecat but I think that the problems are unrelated to kernel updates. I do not think that I have ever had an update to just the kernel. Other stuff is updated as well.

You do not say which version of Ubuntu you are using. I am using 12.04 development branch and so I expect things to fail. I have taken several kernel updates over the last few weeks and I have had programs breaking but I do not blame the kernel update.

There was one update to Libreoffice that brought in a beta version but failed to download Libreoffice core. So, Libreoffice stopped working. Along with it there seemed to be a mix up with the links in the repositories because it was next to impossible to un-install Libreoffice and then re-install it. The package lists would not update correctly or completely. After a few days whatever was wrong was fixed. And I was able to re-install Libreoffice. I do not blame the kernel updates. That is my point.

At about the same time others who were not using 12.04 began to complain about update manager and software centre. So, I wonder if there was a problem with the links or paths to various packages in the repositories.

I also wonder if you what you were experiencing was due to the same issue.

Either way you can refuse a kernel update or only update the kernel and reject the other stuff being updated. A process of elimination.

Regards.

---

### Post by lads on 2012-01-30
Hello,

It's a pity this question is not being taken serious. For future reference a few issues that do not affect me alone:

[http://ubuntuforums.org/showthread.php?t=1885936](http://ubuntuforums.org/showthread.php?t=1885936)

[http://ubuntuforums.org/showthread.php?t=1864573](http://ubuntuforums.org/showthread.php?t=1864573)

[https://bugs.launchpad.net/ubuntu/+source/eog/+bug/880227](https://bugs.launchpad.net/ubuntu/+source/eog/+bug/880227)

Finally, I've tried to find out any setting on my profile that would prevent other users from viewing the system I use but I find none. Could someone please confirm that the Ubuntu version on my avatar/signature is not visible?

Thanks.

---

### Post by oldos2er on 2012-01-30
The ```
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
``` error has a solution here: [http://ubuntuforums.org/showthread.php?t=1854470](http://ubuntuforums.org/showthread.php?t=1854470)

---

### Post by lads on 2012-02-08
Another thing that suddenly stopped working:

[http://ubuntuforums.org/showthread.php?p=11672424](http://ubuntuforums.org/showthread.php?p=11672424)

Best.

---

