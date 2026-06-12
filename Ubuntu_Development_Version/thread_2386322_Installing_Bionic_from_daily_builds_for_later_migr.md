---
title: "Installing Bionic from daily builds for later migration to stable LTS"
date: 2018-03-04
forum: Ubuntu Development Version
---

### Post by neuronaut on 2018-03-04
Hi there,
tomorrow I will start my new job, and they gave me the free choice of OS and a notebook which I have to setup now. So I deleted Windows and now want to install Ubuntu-server 18 from the daily builds ([http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)). 
I know it's not stable yet, but I don't mind and understand the risks, I know my way around - and I want to use the newest software and kernel without having to upgrade from 16 to 18 and cluttering my disk.
What I want to know: Will it be automatically upgraded to the LTS when it is released or will it stay on the dev branch? The name suggests that it already is LTS (18.04), so it should be fine, right?
What would you recommend me to do?

Thanks for your help!

---

### Post by howefield on 2018-03-04
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by kerry_s on 2018-03-04
i recommend you try it live to see if everything works.

personally, if its for work i'd go for stable. theres nothing like needing it & having to fix it.

i loaded that daily into a vm, for the most part seems okay. it did have 1 app crash but it was nothing important.

---

### Post by neuronaut on 2018-03-04
I tried it in a VM, too. It seems to work really well. I tried it with Gnome, KDE and LXDE and did not have any issues so far.
What's more important to me is the question if it will become stable when the LTS is released or if it will stay on the development branch.

The apt sources.list contains only references bionic, so it should be just fine as soon as 18.04 is released, right?

---

### Post by cruzer001 on 2018-03-04
> **neuronaut said:**
> What's more important to me is the question if it will become stable when the LTS is released or if it will stay on the development branch.

It will upgrade to the final (stable) release.

---

### Post by neuronaut on 2018-03-04
Cool. Thank you guys!
I will take the risk and install bionic beaver :-)

Let's find out if it works in production...
:popcorn:

---

### Post by oldfred on 2018-03-04
I typically do a new clean install after it is released.

Primarily as during development packages are regularly updated, so a lot of history & log files. While I normally clean those out anyway, I assume there may be other cruft and just like to have clean install.

---

### Post by mikewhatever on 2018-03-04
> **neuronaut said:**
> Hi there,
tomorrow I will start my new job, and they gave me the free choice of OS and a notebook which I have to setup now. So I deleted Windows and now want to install Ubuntu-server 18 from the daily builds ([http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)). 
I know it's not stable yet, but I don't mind and understand the risks, I know my way around - and I want to use the newest software and kernel without having to upgrade from 16 to 18 and cluttering my disk.
What I want to know: Will it be automatically upgraded to the LTS when it is released or will it stay on the dev branch? The name suggests that it already is LTS (18.04), so it should be fine, right?
What would you recommend me to do?

Thanks for your help!

I'd recommend aganst that plan. It will "cluttering my disk" with tonns of updates, things may break in the process, you may need to fix things or reinstall, while unable to work. Also, if you " want to use the newest software" Ubuntu is really not for you. It will becaome outdated in a few weeks.

---

### Post by SeijiSensei on 2018-03-04
Just a warning that support for the proprietary NVIDIA driver is currently broken.  I'm running with the open-source nouveau driver without problems, but I don't use the machine I'm running it on for things like video.

Otherwise there's only one niggling bug in the Kubuntu 18.04 release, a problem in KDE's plasma-desktop that requires you to enter your wifi passphrase twice.

---

### Post by exploder on 2018-03-04
I too have adopted 18.04 before it is released as final. 18.04 runs on both my desktop and laptop where earlier versions would not. There is some risk involved for sure but it is beter than the alternative. :D

---

### Post by VMC on 2018-03-04
> **SeijiSensei said:**
> Just a warning that support for the proprietary NVIDIA driver is currently broken.  I'm running with the open-source nouveau driver without problems, but I don't use the machine I'm running it on for things like video.

Otherwise there's only one niggling bug in the Kubuntu 18.04 release, a problem in KDE's plasma-desktop that requires you to enter your wifi passphrase twice.

Yes, nvidia-304xx is doomed. The last working install is 17.10, and of course 16.04.4. It has to do with the newer kernels 15- and above. Luckily nouveau works much better than in the past.

---

### Post by mikewhatever on 2018-03-10
> **VMC said:**
> Yes, nvidia-304xx is doomed. The last working install is 17.10, and of course 16.04.4. It has to do with the newer kernels 15- and above. Luckily nouveau works much better than in the past.

Indeed, nvidia 304 is not even in the repositories, and with nouveau, that does work much better then in the past, but still being light years behind, it is not really an option.

---

### Post by corradoventu on 2018-03-10
I'm using Bionic from 1st ISO, daily updated and I have no problems.

---

### Post by mikewhatever on 2018-03-10
> **corradoventu said:**
> I'm using Bionic from 1st ISO, daily updated and I have no problems.

I am sure you do, just don't know it. Lucky you. :popcorn:

---

### Post by VMC on 2018-03-10
> **mikewhatever said:**
> Indeed, nvidia 304 is not even in the repositories, and with nouveau, that does work much better then in the past, but still being light years behind, it is not really an option.
What's not working?

---

