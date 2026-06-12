---
title: "setup vs installation?"
date: 2023-07-12
forum: Ubuntu Development Version
---

### Post by Claus7 on 2023-07-12
Hello,

I tried to install ubuntu 23.10 from daily iso under virtualbox. While doing so I was greeted with a setup wizard right away which, among others, asked me about my keyboard. I was really glad, since by choosing a non latin one, right away english became available as well, in case it was needed.

After a couple of options I came across the desktop screen. From there I had the ability to install ubuntu. No matter how many times I clicked on the installation desktop icon, nothing happened. What puzzled me was that I had many different disk icons under ubuntu dock. 

So I took the decision to reboot and check what will happen. This time no setup was required. The installation procedure started, yet right after choosing keyboard (english this time) the installation did not proceed.

Has anyone faced anything similar?

Regards!

---

### Post by Paddy Landau on 2023-07-16
As this is the development version, still very much in active development and not ready for distribution, it might just be a bug in the installer. Wait 24 hours and try with a new download. If it persists, raise a bug report for it.

---

### Post by Claus7 on 2023-07-17
Hello,

> **Paddy Landau said:**
> As this is the development version, still very much in active development and not ready for distribution, it might just be a bug in the installer. Wait 24 hours and try with a new download. If it persists, raise a bug report for it.

thank you for your response. I will wait until the daily iso is updated (last one 12th of July till the time of writing), and report back.

Regards!

---

### Post by Claus7 on 2023-07-18
Hello,

no luck with vb. I tried to use gnome boxes to test it as well. It had a bug, it was fixed and a new bug emerged. Even this:
[https://bugs.launchpad.net/ubuntu/+source/gnome-boxes/+bug/2019254](https://bugs.launchpad.net/ubuntu/+source/gnome-boxes/+bug/2019254)
didn't solve the issue for me. 

Regards!

---

### Post by Paddy Landau on 2023-07-19
I've just downloaded and installed 23.10 in VirtualBox. The only problem that I had was some temporary screen glitches during the first minute or so of the installation. I even successfully installed Guest Additions.

In case it makes a difference, here are relevant details:

[LIST]
[*]The [ISO's SHA256]("https://cdimage.ubuntu.com/daily-live/pending/SHA256SUMS"), which might have changed by the time you read this:
```
46a8ee32711e136f4369f10c4b5dd109d08e43fae9131d72547621978daaeff6
```
[/LIST]

[LIST]
[*]Host: Ubuntu 22.04
[*]VirtualBox version 7.0.10 r158379
[*]Guest allocation:
[LIST]
[*]5,120 Gb RAM
[*]6 cores
[*]128 Mb video
[*]Enable 3D acceleration
[*]Enable EFI and Secure Boot
[/LIST]

[*]Keyboard: English UK
[/LIST]
I haven't used Gnome Boxes, so I haven't tried it.

---

### Post by guiverc on 2023-07-19
I'll respond, though I'll likely not offer much additional details.

To look at what *daily* ISOs are available, I'd always check the ISO QA tracker, ie. [http://iso.qa.ubuntu.com/qatracker/milestones/446/builds](http://iso.qa.ubuntu.com/qatracker/milestones/446/builds) for *mantic*.

That page gives the ISO dates rather visibly (*at that level especially*).  If you go down to a specific test too, you'll be greeted with some bug reports filed in QA tests of that ISO & testcase (Note: it won't show all; just a few randomly selected).  If you're not familiar with that page, I'll suggest you give it a try, and if you encounter problems, I suggest you file bugs normally & add the bug ID to the QA *test report* on that site as it allows for easier tracking (*bug appears on more reports*).

The only ISO I've zsync'd & used today is Lubuntu's, but I've used the Ubuntu Desktop ISO for *amd64* twice in the last week without issue on real hardware.

---

### Post by Claus7 on 2023-07-19
Hello,

> **Paddy Landau said:**
> I've just downloaded and installed 23.10 in VirtualBox. The only problem that I had was some temporary screen glitches during the first minute or so of the installation. I even successfully installed Guest Additions.

In case it makes a difference, here are relevant details:

[LIST]
[*]The [ISO's SHA256]("https://cdimage.ubuntu.com/daily-live/pending/SHA256SUMS"), which might have changed by the time you read this:
```
46a8ee32711e136f4369f10c4b5dd109d08e43fae9131d72547621978daaeff6
```
[/LIST]

[LIST]
[*]Host: Ubuntu 22.04
[*]VirtualBox version 7.0.10 r158379
[*]Guest allocation:
[LIST]
[*]5,120 Gb RAM
[*]6 cores
[*]128 Mb video
[*]Enable 3D acceleration
[*]Enable EFI and Secure Boot
[/LIST]

[*]Keyboard: English UK
[/LIST]
I haven't used Gnome Boxes, so I haven't tried it.

thank you for your response. I tried just now to install it anew, yet to no avail. The only difference with your case is the host OS. I'm using 23.04. The process is slow. For example when typing my credentials e.g. mantis, I often get a result like mntias or something similar. The setup is compulsory. I cannot avoid it, which I think that it will be the new procedure for installing ubuntu. 

Checking your configuration I decided to bypass the default installation of vb and set parameters similar to yours: e.g. video memory 80 Mb, 4 GB ram, 4 cores, enabling 3D acceleration. This time only the (1) below didn't show up.

1) have you gone through setup process? 
2) by "screen glitches" do you mean just some screen distortions? No slowing down? You allocate more resources than in my case, yet this does not explain why the installation process I'm facing is much slower. 
3) the version of virtual box I'm using is 7.0.6 ubuntu. It might be different, yet both are >7, so I do not suppose that this is the problem.
4) in order to verify that we used the same iso from the code you provided I guess that I click on the SHA256SUMS from here:
[https://cdimage.ubuntu.com/daily-live/pending/](https://cdimage.ubuntu.com/daily-live/pending/)
where I get the same code as yours, so I suppose we tested the same iso.

The last time I tried to install mantic I faced reports like:
ubuntu_subiquity_event.4517[4517]:subiquity/Error/apply_autoinstall_config
with the last report 
ubuntu_subiquity_event.4517[4517]:subiquity/Ad/has_support_GET

Regards!

---

### Post by Claus7 on 2023-07-19
Hello,

> **guiverc said:**
> I'll respond, though I'll likely not offer much additional details.

To look at what *daily* ISOs are available, I'd always check the ISO QA tracker, ie. [http://iso.qa.ubuntu.com/qatracker/milestones/446/builds](http://iso.qa.ubuntu.com/qatracker/milestones/446/builds) for *mantic*.

That page gives the ISO dates rather visibly (*at that level especially*).  If you go down to a specific test too, you'll be greeted with some bug reports filed in QA tests of that ISO & testcase (Note: it won't show all; just a few randomly selected).  If you're not familiar with that page, I'll suggest you give it a try, and if you encounter problems, I suggest you file bugs normally & add the bug ID to the QA *test report* on that site as it allows for easier tracking (*bug appears on more reports*).

The only ISO I've zsync'd & used today is Lubuntu's, but I've used the Ubuntu Desktop ISO for *amd64* twice in the last week without issue on real hardware.

thank you for your response. It has been a while, till I had paid a visit to that webpage. The thing is that you can install mantic, whereas I cannot. So there is something else that causes that issue. Fresh installation is not an option at the time being for my systems. I will check from time to time to see if it is possible to install it.

Regards!

---

### Post by guiverc on 2023-07-19
I just found [https://bugs.launchpad.net/ubuntu/+source/subiquity/+bug/2018943](https://bugs.launchpad.net/ubuntu/+source/subiquity/+bug/2018943) so thank you for your testing @Claus7

That issue is tracked as reported on ISO QA tracker by Nio/sudodus.

Whilst here, thanks also to Paddy for support & QA.

---

### Post by Claus7 on 2023-07-19
Hello,

> **guiverc said:**
> I just found [https://bugs.launchpad.net/ubuntu/+source/subiquity/+bug/2018943](https://bugs.launchpad.net/ubuntu/+source/subiquity/+bug/2018943) so thank you for your testing @Claus7

That issue is tracked as reported on ISO QA tracker by Nio/sudodus.

Whilst here, thanks also to Paddy for support & QA.

at least that time you mention I had the ability to install ubuntu with one way or the other. Now I can't. You will ask: why do you have to install it anew? The answer is that after some time, I couldn't boot this specific virtual machine, so I removed it and tried with a new iso. I hope that it will help someone else facing the same.

Regards!

---

### Post by Paddy Landau on 2023-07-19
Thanks, @guiverc.

@Claus7, it seems that it's specifically to do with the keyboard, so it appears that your bug is the blocking point.

Unfortunately, I don't have time now to test this with a non-Latin keyboard myself.

---

### Post by Paddy Landau on 2023-07-19
To answer your questions, though I don't think that they will matter:
> **Claus7 said:**
> 1) have you gone through setup process? 
2) by "screen glitches" do you mean just some screen distortions? No slowing down? You allocate more resources than in my case, yet this does not explain why the installation process I'm facing is much slower. 
3) the version of virtual box I'm using is 7.0.6 ubuntu. It might be different, yet both are >7, so I do not suppose that this is the problem.
4) in order to verify that we used the same iso from the code you provided I guess that I click on the SHA256SUMS from here:
[https://cdimage.ubuntu.com/daily-live/pending/](https://cdimage.ubuntu.com/daily-live/pending/)
where I get the same code as yours, so I suppose we tested the same iso.
1) I installed manually. I didn't use VirtualBox's unattended installation.
2) No slowing down. Just severe screen distortion on the installation window for a minute or thereabouts.
3) I use the latest VirtualBox directly from the [VB Linux downloads]("https://www.virtualbox.org/wiki/Linux_Downloads") page.
4) Yes, that's the same. That page also has a link to the SHA256 sums, which you should always check before using the ISO.
> **Claus7 said:**
> [COLOR=#000000]video memory 80 Mb[/COLOR][COLOR=#000000]
I would suggest the full 128 Mb, in order to reduce the chance of screen glitches.[/COLOR]

---

### Post by Claus7 on 2023-07-19
Hello,

> **Paddy Landau said:**
> Thanks, @guiverc.

@Claus7, it seems that it's specifically to do with the keyboard, so it appears that your bug is the blocking point.

Unfortunately, I don't have time now to test this with a non-Latin keyboard myself.

you shouldn't. I mean that in the recent installations I haven't used non-Latin keyboard, yet just English one. This was another issue that I faced during installation of mantic iso.

> **Paddy Landau said:**
> To answer your questions, though I don't think that they will matter:

1) I installed manually. I didn't use VirtualBox's unattended installation.
2) No slowing down. Just severe screen distortion on the installation window for a minute or thereabouts.
3) I use the latest VirtualBox directly from the [VB Linux downloads]("https://www.virtualbox.org/wiki/Linux_Downloads") page.
4) Yes, that's the same. That page also has a link to the SHA256 sums, which you should always check before using the ISO.
[COLOR=#000000]
I would suggest the full 128 Mb, in order to reduce the chance of screen glitches.[/COLOR]

thank you for your answers. As I mentioned I cannot bypass the messages of subiquity. I will try the latest vb in case this was the issue.

Regards!

---

### Post by Claus7 on 2023-07-19
Hello,

even with the latest vb the same.

Regards!

---

### Post by Paddy Landau on 2023-07-19
> **Claus7 said:**
> even with the latest vb the same.
Have you checked the ISO's SHA256? If you have a corrupt ISO, it could give these problems. Even if you download again, you still need to check the SHA256 sum (I once had a mirror that was corrupted, so downloading again didn't help).

I'm trying to think what else could be at fault.
> **Claus7 said:**
> No matter how many times I clicked on the installation desktop icon…
I bypassed that by choosing to install when booting the VM, instead of going via the desktop icon. Does that make a difference for you?

Another thing might be that your computer is a bit slow, and so when you click the icon, it takes a while to start up. Once you've double-clicked the icon (just once, otherwise you're going to create multiple processes), open a terminal and use [FONT=courier new]top[/FONT] to see what, if anything, is happening.

---

### Post by guiverc on 2023-07-19
> **Claus7 said:**
> 
at least that time you mention I had the ability to install ubuntu with one way or the other. Now I can't. You will ask: why do you have to install it anew? The answer is that after some time, I couldn't boot this specific virtual machine, so I removed it and tried with a new iso. I hope that it will help someone else facing the same.

**All your testing is extremely valuable**.

I'm an aussie (*I normally write that as dumb aussie*), and like many aussies, can *barely speak* english.

Due to *lacking time*, my QA testing is currently a fraction of what I did many *cycles* before... but even if I had time for more, I can only QA in *english*, my keyboards are all US default, and I've never used anything else (*thus have no understanding of any other languages & complexities you're more familiar with*).

My heavy involvement with the Lubuntu team has me very much focus on Lubuntu ISOs  (*which uses `calamares` installer thus differs greatly in this area*), next I tend to *gravitate* to Xubuntu (*`ubiquity`*).. Ubuntu Desktop is further down my list (`ubuntu-desktop-installer`)  with 20230705 media the last I did; so wasn't actually* that recent* anyway (*probably back when you said it was working*)

**All our testing is valuable**... my only purpose for posting was to try and *encourage* recording tests on the ISO QA tracker, to make the time/testing as valuable as possible.  Thank you for reporting your results here on UF !

---

### Post by Claus7 on 2023-07-19
Hello,

> **Paddy Landau said:**
> Have you checked the ISO's SHA256? If you have a corrupt ISO, it could give these problems. Even if you download again, you still need to check the SHA256 sum (I once had a mirror that was corrupted, so downloading again didn't help).

I'm trying to think what else could be at fault.

I bypassed that by choosing to install when booting the VM, instead of going via the desktop icon. Does that make a difference for you?

Another thing might be that your computer is a bit slow, and so when you click the icon, it takes a while to start up. Once you've double-clicked the icon (just once, otherwise you're going to create multiple processes), open a terminal and use [FONT=courier new]top[/FONT] to see what, if anything, is happening.

If all isos I download are corrupted and this happens only for mantic, then its great luck! 

It is slow, the thing is that I see first setup (most of the times) and then I cannot do anything. If I reboot and wait installation might start on its  own. Yet the result is the same: no installation.

> **guiverc said:**
> **All your testing is extremely valuable**.

I'm an aussie (*I normally write that as dumb aussie*), and like many aussies, can *barely speak* english.

Due to *lacking time*, my QA testing is currently a fraction of what I did many *cycles* before... but even if I had time for more, I can only QA in *english*, my keyboards are all US default, and I've never used anything else (*thus have no understanding of any other languages & complexities you're more familiar with*).

My heavy involvement with the Lubuntu team has me very much focus on Lubuntu ISOs  (*which uses `calamares` installer thus differs greatly in this area*), next I tend to *gravitate* to Xubuntu (*`ubiquity`*).. Ubuntu Desktop is further down my list (`ubuntu-desktop-installer`)  with 20230705 media the last I did; so wasn't actually* that recent* anyway (*probably back when you said it was working*)

**All our testing is valuable**... my only purpose for posting was to try and *encourage* recording tests on the ISO QA tracker, to make the time/testing as valuable as possible.  Thank you for reporting your results here on UF !

I can understand you very clearly and I get your point. In the late versions of Files, it is extremely annoying either to press super+space under wayland to change languages or try to write a portion of a file in english and then change language, right click it anew, choose rename and fill the rest of the name.

One last thing: when mantic prompts you for erasing disk, I can see no information about the disk size that is about to get erased. Just empty boxes. This is happening all the time. Do you remember seeing such a display?

Regards!

---

### Post by Paddy Landau on 2023-07-19
> **Claus7 said:**
> If all isos I download are corrupted and this happens only for mantic, then its great luck!
It might not be all downloads; just 23.10. You never know. That's why it's recommended to *always* check the SHA256 sum. It's not hard; you can do it from the file manager (right-click the file > Properties > Digests > select SHA26 > Hash). I have had a corrupted ISO more than once.

---

### Post by Claus7 on 2023-07-19
Hello,

I opened synaptic package manager and found the file gtkhash. I installed it (no nautilus/Files version was available at the time) and opened it. At the same time I downloaded the latest amd iso of ubuntu 23.10 development. Under gtkhash this iso was selected. Also, next to Check option, I added the SHA256SUMS code of the iso and hit hash. It took a couple of seconds and verification showed up. So the iso was ok. 

I tried virtualbox once again, to no avail. In case my virtualbox had an issue, I downloaded a 10.10 amd iso which worked like a charm. I tried once again by removing the old installations of mantic changing the name of the virtual machine and see what I will get. I wasn't greeted with the setup screen I mentioned before. After choosing to install ubuntu I waited for a little while and installation screen appeared. Once again, I do not see any information when choosing to erase the disk. Usually at this place it mentions the partitions and disk size that are about to get erased.

The end result is no installation. The graphics during installation are displayed as presentation, the system monitor shows that installation is almost inactive and the bottom installation bar does not move at all. My outcome is that I cannot install 23.10 development under 23.04 using virtualbox at the time being.

edit: I have to mention that I reverted back to the default version of virtualbox under 23.04.

Regards!

---

### Post by guiverc on 2023-07-19
I'm *days* (*if not further*) behind you two with regards this issue.. I've not experienced any such issue. I've the current Ubuntu Desktop *mantic daily* writing to thumb-drive now, but I'm not expecting issues on my install.. but I'll see.

I just noted (*alas again*) [https://bugs.launchpad.net/subiquity/+bug/2025535](https://bugs.launchpad.net/subiquity/+bug/2025535) and thus wonder if its related to the discussion?

---

### Post by Claus7 on 2023-07-19
Hello,

> **guiverc said:**
> I'm *days* (*if not further*) behind you two with regards this issue.. I've not experienced any such issue. I've the current Ubuntu Desktop *mantic daily* writing to thumb-drive now, but I'm not expecting issues on my install.. but I'll see.

I just noted (*alas again*) [https://bugs.launchpad.net/subiquity/+bug/2025535](https://bugs.launchpad.net/subiquity/+bug/2025535) and thus wonder if its related to the discussion?

nice catch! The difference with my case is that I face no freezing. Other than that, as you posted before, this is related with subiquity, since these are the messages I'm getting. It seems that it is under great revamp. Now things are fitting together. I will add info to the bug report you sent me.

Good luck with your installations!

Regards!

---

### Post by Paddy Landau on 2023-07-20
It's quite bizarre that we're getting such different results for the same ISO.

I'm trying to think of what might be different, and from what I can see, it seems to be the host. I'm remembering that there was once a problem with VirtualBox on the short-term releases of Ubuntu. Oracle supports VirtualBox only on the long-term releases, and so it's possible that having 23.04 as the host is causing a problem.

I can't say if that's actually the case, as I don't have a machine with 23.04 to test (I have 22.04 LTS, and I can install 23.10 successfully).

---

### Post by Claus7 on 2023-07-20
Hello,

> **Paddy Landau said:**
> It's quite bizarre that we're getting such different results for the same ISO.

I'm trying to think of what might be different, and from what I can see, it seems to be the host. I'm remembering that there was once a problem with VirtualBox on the short-term releases of Ubuntu. Oracle supports VirtualBox only on the long-term releases, and so it's possible that having 23.04 as the host is causing a problem.

I can't say if that's actually the case, as I don't have a machine with 23.04 to test (I have 22.04 LTS, and I can install 23.10 successfully).

my original messages never made it. So my recap: it crossed my mind as well, since this was the most notable difference between our systems. While writing these lines, I went to launchpad and saw that fixes were landed for this issue. I will try in a couple of days and report back.

Thank you very much for your time!

Regards!

---

### Post by Claus7 on 2023-07-22
Hello,

testing today's iso (22nd of July), problem solved. Thank you for your responses!

Regards!

---

