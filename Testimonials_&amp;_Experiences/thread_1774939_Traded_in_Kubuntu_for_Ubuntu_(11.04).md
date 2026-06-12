---
title: "Traded in Kubuntu for Ubuntu (11.04)"
date: 2011-06-04
forum: Testimonials &amp; Experiences
---

### Post by marl30 on 2011-06-04
I must say that I absolutely love Kubuntu 11.04. KDE has grown to become my favourite desktop environment without a doubt. however, lately I've been needing to use Skype more often than before, so I needed my microphone working, which I have never gotten to work under KDE for my 5.1 surround sound card.

 I haven't really made a support thread here or on the Kubuntu forum. I didn't bother after seeing countless threads both here and there with no solution. I hate having to launch virtualbox just to make calls. I hope that this issue will be rectified in KDE 4.7.  Until then I've decided to give Unity a spin. 

I wasn't a big fan of Unity and that's the reason I migrated to KDE. I'm still not a big fan but I must say it has improved a bit and is not as awkward as I found it when I tried it before, well, that might be because I filled the launcher with all my most used apps. I still think it's incomplete and slow though. It even uses more memory than KDE and slower at starting up too. My mic works though, that is why I am forced to use it.

I could really get use to Unity, but if there was a solution to to my problem I would be back to Kubuntu in a heartbeat. 

The next thing, I haven't had any issues with bugs in Unity so far. I have been using it for more than 24 hours now too. Only that Nautilus is a bit slow, and Unity takes about the same amount of time to start up as Windows. Perhaps these issues are because I had used that Psychocat command to remove KDE and get back to pure Gnome. 

Overall Unity is not that bad. It just needs some additional features before it can make classic Gnome a distant memory. I'm not a keyboard shortcut person so I was worried if Unity would work out fine, so far it has. But I still would give anything to have Kubuntu working how I want it to.

---

### Post by lovinglinux on 2011-06-04
I have experienced several issues with KDE Phonon on Kubuntu 11.04. 

The root of the problem is that Phonon is not saving settings properly. See the following bug report for more info: 

[https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274](https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274)

I was able to make my mic work with Skype, using pavucontrol.

```
sudo apt-get install pavucontrol
```

I am not sure which options are best for you, but my mic worked selecting *Analog Stereo Output* in the *Internal Audio* device, in the *Configuration* tab of pavucontrol. I have a USB mic. You may need to play with pavuncontrol a little bit to find the best configuration for you. 

To make it work with Skype you need to start pavucontrol, start Skype and initiate a dummy call to their testing service. Once the call is accepted, click the *Recording* tab of pavucontrol. You will see a Skype entry, with a drop-down menu. Click it and select your microphone device.

---

### Post by marl30 on 2011-06-04
> **lovinglinux said:**
> I have experienced several issues with KDE Phonon on Kubuntu 11.04. 

The root of the problem is that Phonon is not saving settings properly. See the following bug report for more info: 

[https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274](https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274)

I was able to make my mic work with Skype, using pavucontrol.

```
sudo apt-get install pavucontrol
```I am not sure which options are best for you, but my mic worked selecting *Analog Stereo Output* in the *Internal Audio* device, in the *Configuration* tab of pavucontrol. I have a USB mic. You may need to play with pavuncontrol a little bit to find the best configuration for you. 

To make it work with Skype you need to start pavucontrol, start Skype and initiate a dummy call to their testing service. Once the call is accepted, click the *Recording* tab of pavucontrol. You will see a Skype entry, with a drop-down menu. Click it and select your microphone device.

Thanks for the suggestion. I'm reinstalling Kubuntu desktop just to try this.

---

### Post by lovinglinux on 2011-06-04
> **marl30 said:**
> Thanks for the suggestion. I'm reinstalling Kubuntu desktop just to try this.

Let me know if it works or not.

---

### Post by marl30 on 2011-06-04
> **lovinglinux said:**
> Let me know if it works or not.

The funny thing is, when I went to install that thing it turned out I had it installed already. I've been fooling around with it before and haven't seen my mic work until now.:D I'm going to completely remove Ubuntu-desktop by running the get back to pure KDE command and then try this again, just to make sure it's not working because I have Ubuntu and Kubuntu installed on top of one another. 

I'll give it a go with pure Kubuntu when I get back later in the day and let you know.

---

### Post by SeijiSensei on 2011-06-04
I *strongly* recommend using Kubuntu 10.10 instead of 11.04.  It's been much more stable for me and others on this forum.  If you want to upgrade the desktop to KDE 4.6, add the [backports]("https://launchpad.net/~kubuntu-ppa/+archive/backports") repository.

I had the same problem with Phonon not saving settings in 11.04.  In 10.10 it works flawlessly.

---

### Post by lovinglinux on 2011-06-04
> **SeijiSensei said:**
> I *strongly* recommend using Kubuntu 10.10 instead of 11.04.  It's been much more stable for me and others on this forum.  If you want to upgrade the desktop to KDE 4.6, add the [backports]("https://launchpad.net/~kubuntu-ppa/+archive/backports") repository.

I had the same problem with Phonon not saving settings in 11.04.  In 10.10 it works flawlessly.

I have no problems on 11.04, except for this Phonon issue.

---

### Post by marl30 on 2011-06-04
> **SeijiSensei said:**
> I *strongly* recommend using Kubuntu 10.10 instead of 11.04.  It's been much more stable for me and others on this forum.  If you want to upgrade the desktop to KDE 4.6, add the [backports]("https://launchpad.net/%7Ekubuntu-ppa/+archive/backports") repository.

I had the same problem with Phonon not saving settings in 11.04.  In 10.10 it works flawlessly.

> **lovinglinux said:**
> I have no problems on 11.04, except for this Phonon issue.

Relax, Lovinglinux's suggestion works. I have my mic working with Skype now. With that Unity is gone. I'm back to my beloved Kubuntu :D

---

### Post by lovinglinux on 2011-06-04
> **marl30 said:**
> Relax, Lovinglinux's suggestion works. I have my mic working with Skype now. With that Unity is gone. I'm back to my beloved Kubuntu :D

Glad to read that. Have fun.

---

### Post by SeijiSensei on 2011-06-05
> **lovinglinux said:**
> I have no problems on 11.04, except for this Phonon issue.

My problems can be traced more to the kernel and drivers than KDE itself.  My RT2500USB wifi became flaky once again after working flawlessly in 10.10.  I also had a strange video problem with my NVIDIA 9500GT; moving a window would sometimes cause the entire screen to be covered in what TV viewers used to call "snow" and required a reboot to fix. This problem might have something to do with KDE's screen drawing functions, but it could just as easily be a kernel/driver compatibility issue.

I'm glad everything is working for the OP, but not all of us have had the same good experiences with 11.04, and not just because of the change to Unity.

---

### Post by marl30 on 2011-06-05
> **SeijiSensei said:**
> My problems can be traced more to the kernel and drivers than KDE itself.  My RT2500USB wifi became flaky once again after working flawlessly in 10.10.  I also had a strange video problem with my NVIDIA 9500GT; moving a window would sometimes cause the entire screen to be covered in what TV viewers used to call "snow" and required a reboot to fix. This problem might have something to do with KDE's screen drawing functions, but it could just as easily be a kernel/driver compatibility issue.

I'm glad everything is working for the OP, but not all of us have had the same good experiences with 11.04, and not just because of the change to Unity.
If you happen to try 11.04 again, maybe you could try it with the latest released kernel:                                 2.6.39. 

For Unity I don't think most of the problems people are having is because of the kernel. For me I haven't had any of those problems with Unity.  My only two issue was that it was too slow starting up, and Nautilus was very slow, otherwise it gave me no issue. As for Kubuntu 11.04, it has been working perfectly ever since I tried the beta until now, I only had the mic issue. Now that that is solved it is running perfectly for me.

---

### Post by el_koraco on 2011-06-05
> **SeijiSensei said:**
> My problems can be traced more to the kernel and drivers than KDE itself.  My RT2500USB wifi became flaky once again after working flawlessly in 10.10.  I also had a strange video problem with my NVIDIA 9500GT; moving a window would sometimes cause the entire screen to be covered in what TV viewers used to call "snow" and required a reboot to fix. This problem might have something to do with KDE's screen drawing functions, but it could just as easily be a kernel/driver compatibility issue.



The wifi issue is definitely kernel related, because I've heard people having trouble with the same chip on Unity. The nvidia thing could have to do with the new version of X, which just isn't cutting it for me either. 

I do think that the wifi is resolved in 2.6.39, but don't take my words for granted.

---

