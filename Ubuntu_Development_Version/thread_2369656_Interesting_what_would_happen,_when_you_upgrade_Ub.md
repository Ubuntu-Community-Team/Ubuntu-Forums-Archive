---
title: "Interesting what would happen, when you upgrade Ubuntu 17.04 to 17.10 normally"
date: 2017-08-25
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-08-25
Interesting what would happen, when you upgrade Ubuntu 17.04 to 17.10 normally, that is, from the Software Updater. Or, even by changing the repo name. Both have Ubuntu Session, one pointing to Unity and the other pointing to Gnome.

---

### Post by dino99 on 2017-08-25
you will get some goodies (newer kernel, gtk, gcc, ...), some changes( wayland as default, unity/mir kicked out, ...), and some not yet fixed gui's apps (pkexec need to be replaced by polkit) under wayland (synaptic, ubiquity, ...) and the usual troubles with rolling installation (system often not cleaned by user, old settings conflicting on dirty install, ...)  :P

---

### Post by Chanath on 2017-08-25
> **dino99 said:**
> , some changes( wayland as default, unity/mir kicked out, ...) :P

And, that is considered as a good thing?

---

### Post by ventrical on 2017-08-25
> **Chanath said:**
> And, that is considered as a good thing?

In between non LTS cycles it will most often break  the desktop and some other depends... but with work and dilligence you can recover. The time it takes to do a fresh install  takes extremely less time than it would to do a manual fix. So, in the way ComSci works .. you have to avoid the downtime and do whats most efficient. One can learn a lot from a manual recovery.

Regards..

---

### Post by dino99 on 2017-08-25
> **Chanath said:**
> And, that is considered as a good thing?

well, colors & tastes, ....
my own feeling is better close to upstream than un-proof custom tweaks  ):P

---

### Post by Chanath on 2017-08-25
> **ventrical said:**
> In between non LTS cycles it will most often break  the desktop and some other depends... but with work and dilligence you can recover. The time it takes to do a fresh install  takes extremely less time than it would to do a manual fix. So, in the way ComSci works .. you have to avoid the downtime and do whats most efficient. One can learn a lot from a manual recovery.

Regards..

I suppose so. Unity session can be installed, so something can be done with it. Yes, one can learn a lot from manual recovery.

---

### Post by ventrical on 2017-08-25
> **Chanath said:**
> I suppose so. Unity session can be installed, so something can be done with it. Yes, one can learn a lot from manual recovery.

Well... a lot of it is here :)

[https://ubuntuforums.org/showthread.php?t=1970289](https://ubuntuforums.org/showthread.php?t=1970289)

---

### Post by Chanath on 2017-08-25
> **ventrical said:**
> Well... a lot of it is here :)

[https://ubuntuforums.org/showthread.php?t=1970289](https://ubuntuforums.org/showthread.php?t=1970289)

I know that thread!:)

---

### Post by Cavsfan on 2017-08-25
> **Chanath said:**
> Interesting what would happen, when you upgrade Ubuntu 17.04 to 17.10 normally, that is, from the Software Updater. Or, even by changing the repo name. Both have Ubuntu Session, one pointing to Unity and the other pointing to Gnome.

That is exactly what I did initially: installed 17.04 and then changed the sources, did a dist-upgrade, etc. and had 17.10. However, nothing broke and everything was working perfectly well. I even had Compiz et. al working well so I knew it wasn't right. 

So, I've installed the daily ISO 2 or 3 times so far and it is a whole different experience completely. Starting out with 17.04 and upgrading it to 17.10 is like starting out with a fairly new car and painting it a different color but, that's about it.

Installing from a 17.10 daily ISO is really starting from scratch.

---

### Post by Chanath on 2017-08-26
> **Cavsfan said:**
> That is exactly what I did initially: installed 17.04 and then changed the sources, did a dist-upgrade, etc. and had 17.10. However, nothing broke and everything was working perfectly well. I even had Compiz et. al working well so I knew it wasn't right. 

At the beginning, Ubuntu 17.10 had Unity as its DE, but after a while (~8th June) it moved to Gnome-shell and GDM. The session was/is Ubuntu, but after the move to Gnome-shell, the Ubuntu session points to Gnome-shell, not Unity, even if Unity is still there. To point to Unity, you need to install unity-session. So, did you have Unity session automatically installed? Is the Unity greeter still there?

---

### Post by Cavsfan on 2017-08-26
> **Chanath said:**
> At the beginning, Ubuntu 17.10 had Unity as its DE, but after a while (~8th June) it moved to Gnome-shell and GDM. The session was/is Ubuntu, but after the move to Gnome-shell, the Ubuntu session points to Gnome-shell, not Unity, even if Unity is still there. To point to Unity, you need to install unity-session. So, did you have Unity session automatically installed? Is the Unity greeter still there?
I had Xubuntu 17.04 installed which became  Xubuntu  17.10, no Unity involved.

---

### Post by Chanath on 2017-08-26
> **Cavsfan said:**
> I had Xubuntu 17.04 installed which became  Xubuntu  17.10, no Unity involved.

Oh, I am talking about Ubuntu 17.04 upgrading to 17.10.

I know that Xubuntu would upgrade  without any trouble. Ubuntu+Openbox too. I have both of them, and they were upgraded to 17.10 by changing  the repos.

---

### Post by wgarcia on 2017-08-27
I always prefer a dist-upgrade than a clean reinstall. I have a lot of configurations and moving them to a clean install usually takes me more time than fixing the glitches of upgrading over an existing installation. I've been doing this since my first Ubuntu installation (of course over different systems where I had to start with a clean installation the first time) since Ubuntu Edgy (7.10, if I remember correctly). I learnt a lot by fixing the problems that I found, and (I hope to keep lucky) I never had to reinstall after an upgrade.

Usually Ubuntu provides an upgrade path, for instance when we moved from Gnome 2 to Unity (11.04) the upgrade was quite smooth, apart from the issues that the first versions of Unity had. So I expect that there will be an upgrade path from Unity to Gnome in 17.10. This is also needed for 18.04, where a lot of users will upgrade from 16.04. I don't think you can ask all these users to start with a clean installation, which requires having set up a separate home partition for instance, reinstall all non-standard applications, recovering customizations, and so on.

---

### Post by sp40140 on 2017-08-27
> **wgarcia said:**
> I always prefer a dist-upgrade than a clean reinstall. I have a lot of configurations and moving them to a clean install usually takes me more time than fixing the glitches of upgrading over an existing installation. I've been doing this since my first Ubuntu installation (of course over different systems where I had to start with a clean installation the first time) since Ubuntu Edgy (7.10, if I remember correctly). I learnt a lot by fixing the problems that I found, and (I hope to keep lucky) I never had to reinstall after an upgrade.

Usually Ubuntu provides an upgrade path, for instance when we moved from Gnome 2 to Unity (11.04) the upgrade was quite smooth, apart from the issues that the first versions of Unity had. So I expect that there will be an upgrade path from Unity to Gnome in 17.10. This is also needed for 18.04, where a lot of users will upgrade from 16.04. I don't think you can ask all these users to start with a clean installation, which requires having set up a separate home partition for instance, reinstall all non-standard applications, recovering customization, and so on.

I agree with you completely. I have been doing in-place upgrades instead of fresh installs as my machine does lots tasks and it takes me lots of time and googling along with this forum to get it to the point I like. 
So, even though the install time is almost same for the fresh install over upgrade it's still a waste of lots of time for me.
And luckily enough, I haven't run into any problem due to upgrade which I can recall and I have upgraded to every version of Ubuntu (not only LTS).

---

### Post by Cavsfan on 2017-08-27
> **Chanath said:**
> Oh, I am talking about Ubuntu 17.04 upgrading to 17.10.

I know that Xubuntu would upgrade  without any trouble. Ubuntu+Openbox too. I have both of them, and they were upgraded to 17.10 by changing  the repos.

I was just making the comparison with Xubuntu because that is what I had and it is not available yet as a daily ISO. But, I'm fairly sure the comparisons I made would still hold true with Xubuntu as it does with Ubuntu.
When you upgrade from one version to another, you're not getting the full effects of the totally new operating system, but are adding to the old one.

> **sp40140 said:**
> I agree with you completely. I have been doing in-place upgrades instead of fresh installs as my machine does lots tasks and it takes me lots of time and googling along with this forum to get it to the point I like. 
So, even though the install time is almost same for the fresh install over upgrade it's still a waste of lots of time for me.
And luckily enough, I haven't run into any problem due to upgrade which I can recall and I have upgraded to every version of Ubuntu (not only LTS).

I always did this too. Just upgrade from one version to the next and had very little difficulty doing it that way. Then when the final release came out I would do a clean install and found that many things were different afterwards.
Things appeared that were not on the upgraded version; that would seem to be a lame statement but, things are different as far as I've experienced.
But, when it was an LTS, I waited until the 1st point release to clean install.

I believe a clean install gets rid of the cruft that piles up.

---

### Post by ken78724 on 2017-08-27
thx for sharing. cheers!

---

