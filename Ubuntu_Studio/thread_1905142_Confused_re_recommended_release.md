---
title: "Confused re recommended release"
date: 2012-01-06
forum: Ubuntu Studio
---

### Post by nickdc on 2012-01-06
Having just lost best part of two days trying to get Kdenlive working on Ubuntu 11.10, I'm considering installing Ubuntu Studio, but not sure which version. Home page for Ubuntu Studio says 11.10 is not a recommended release, while Ubuntu wiki says it is! On the downloads page 8.04 is commented as the recommended release for production critical machines. Mine's not that, I'm not a pro, just an enthusiast fed up with Windows, familiar enough with Ubuntu now to realise it's not the panacea I'd first thought, and just wanting something that *works* for dv video capture and editing. Please would someone recommend the best release for me to install for video work. Cheers!

---

### Post by jejeman on 2012-01-06
I have succesfully use kdenlive on 11.04 for two projects.
You can also install 10.04, it works there too, but I didn't made my projects on it. 10.04 is great for audio for which I use it.

---

### Post by nickdc on 2012-01-08
After many hours spent trying to install 10.04 (burned 3 dvds before I could get one to boot, trying 2 different cd/dvd drives, then, when one did finally boot, various errors caused failure on three separate install attempts) I gave up and tried 8.04 instead. Compared to the 10.04 process, this went relatively smoothly and I now have a working Ubuntu Studio 8.04 on a separate hard drive. 

However, when I go to software to install Kdenlive, it seems not to be available for 8.04, so what should I upgrade to, and how? When I run the update manager, I'm offered 10.04 as a new release upgrade, but it appears to be standard ubuntu, rather than studio that's offered. What's the recommended process for updating and upgrading an Ubuntu Studio installation, and which version of Studio is likely to give me the best combination of stability and up-to-dateness?

PS  And why when you go to download Studio is the iso labelled as the *alternate* install dvd??? That implies there's a standard one. I wish there was - it might have saved me hours of hassle!

---

### Post by khelben1979 on 2012-01-08
First off I think that you need to think about if you really need Ubuntu Studio or not, because a standard release of Ubuntu contains all the software an Ubuntu Studio release does, but... you would need to install applications and configure things which isn't there from the start. 

If I were you, I would go for a more fresh release of Ubuntu studio or just a standard release. Choosing a LTS release is the best choice if you're looking for stability and less software bugs.

It all comes down to what software you intend to use and your skills with Linux determines what would suit you best. The latest version of Ubuntu Studio would be the best choice for fresh software and if you got the time to fix things, it might be worth it, otherwise stick with what you got and avoid the software which ain't supported.

---

### Post by jejeman on 2012-01-08
If you are intrested in dv production you don't need ubuntu studio. I used Xubuntu 11.04 for my projects.

---

### Post by nickdc on 2012-01-08
Thanks for the advice, but as you'll see from my original post, I already have the latest version of vanilla Ubuntu, which seems to have problems with legacy firewire support, which is why I've installed an earlier Studio as well. I really want to upgrade 8.04 to 10.04, as I said in my previous post, but I'm asking advice re the best way to do that.

---

### Post by jejeman on 2012-01-08
> I really want to upgrade 8.04 to 10.04, as I said in my previous post, but I'm asking advice re the best way to do that. There is no best way for that, there is just one and only way. Use update manager and upgrade it.
Maybe you should resolve the firewire problems in 11.10.
> which seems to have problems with legacy firewire supportwhat legacy support? You don't need old firewire stack for camera to be working.

---

### Post by nickdc on 2012-01-08
> **jejeman said:**
> There is no best way for that, there is just one and only way. Use update manager and upgrade it.
Maybe you should resolve the firewire problems in 11.10.
what legacy support? You don't need old firewire stack for camera to be working.

OK, so although when I hover over the upgrade button of the update manager in Studio it says "upgrade to the latest version of Ubuntu", it actually means "... Ubuntu Studio", and will upgrade all the specific Studio relevant parts of the OS as well as the parts they have in common? Are you absolutely sure about that? 

Re firewire, I spent the best part of an evening and a day trying to resolve firewire issue in 11.10. I came to the conclusion after a lot of reading on the forums that a) for my camcorder I do need the legacy firewire stack and b) I can't load it because, as one poster put it, someone screwed up with firewire in the latest version and left out a crucial part of the necessary code. See for example this thread:
 
[http://ubuntuforums.org/archive/index.php/t-1742787.html](http://ubuntuforums.org/archive/index.php/t-1742787.html)

I'm getting exactly the same problem with the absence of raw1394 and as far as I can see people far more savvy than me have eventually had to give up. :(

---

### Post by snowpine on 2012-01-08
Here are the official instructions to upgrade 8.04 to 10.04:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by jejeman on 2012-01-08
Okay, I never tried 11.10, maybe something is broken there with firewire, but in 11.04 camera works with the new stack.

Well having 8.04 do you no good. So, just upgrade. Ubuntu studio and Ubuntu are the same distro. All differences can fit on one wikki page
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
Ubuntu studio is ubuntu. So no need to wory on that part. But as it knows to be, upgrade itself has always been risky. You can end up with unusable system.
> a) for my camcorder I do need the legacy firewire stackI don't think that there is more than one way camcoders works with firewire. If mine woked with the new stack, all of them should.

---

### Post by nickdc on 2012-01-08
Thanks for the links, folks.

Snowpine - yes, I've looked at that, but no mention of Studio. In fact it's reading docs like that, which says you can directly upgrade from 8.04 to 10.04 in Ubuntu but not in Kubuntu, which makes me wary of going ahead until someone who fully understands the upgrade process relating to Studio assures me it's ok.

Jejeman - they surely can't be the same or Studio wouldn't have received the blessing of Canonical as a separate entity. I take your point that they may not be very different, but as you say, upgrades can be tricky and you can end up with an unusable system. Having had so much trouble getting Studio 8.04 installed, I want to be absolutely sure what I'm doing before I upgrade to 10.04. Hence my post.
Re firewire, you're probably right, all the cameras are much the same. I think the problem is more likely to be with the firewire card in my pc. It all works fine on my partner's pc.

---

### Post by snowpine on 2012-01-08
> **nickdc said:**
> Snowpine - yes, I've looked at that, but no mention of Studio. In fact it's reading docs like that, which says you can directly upgrade from 8.04 to 10.04 in Ubuntu but not in Kubuntu, which makes me wary of going ahead until someone who fully understands the upgrade process relating to Studio assures me it's ok.

Ubuntu Studio **is** Ubuntu.

I have no idea why you installed the April 2008 release (that would not have been my recommendation at all) but hopefully the official instructions from ubuntu.com will assist with your upgrade.

---

### Post by nickdc on 2012-01-08
> **snowpine said:**
> Ubuntu Studio **is** Ubuntu.

I have no idea why you installed the April 2008 release (that would not have been my recommendation at all) but hopefully the official instructions from ubuntu.com will assist with your upgrade.

We're maybe getting into semantics here! As I understand it, Ubuntu Studio is Ubuntu in a similar way that a Ford Focus is a Ford, but if I wanted new parts for my Ford Focus I would want to be sure I was getting parts for that particular model, not just any Ford parts.

I installed 8.04 because all the more recent ones I tried failed to install. That was the first one I succeeded with. It is actually still the officially recommended release for "work-critical machines". Not that I would put myself in that category, but such a description does indicate that the people who actually develop the code recognise that all is not as they'd like it to be in the later releases.

Thanks anyway for your input. Every bit of advice is valuable.

---

### Post by snowpine on 2012-01-08
> **nickdc said:**
> We're maybe getting into semantics here! As I understand it, Ubuntu Studio is Ubuntu in a similar way that a Ford Focus is a Ford, but if I wanted new parts for my Ford Focus I would want to be sure I was getting parts for that particular model, not just any Ford parts.

Your understanding is incorrect; Ubuntu Studio uses the same "parts" as Ubuntu.

8.04 reached "end of life" back in May (except for the Server version supported through 2013) and is no longer supported: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I don't see any compelling reason why you need Ubuntu Studio; "regular" Ubuntu with kdenlive should meet your needs just fine. :) (sorry I don't have an answer for your firewire problem)

---

### Post by khelben1979 on 2012-01-08
Hmm.. about your firewire support. You say it works with the older release of Ubuntu Studio, but when you go for a newer version of Ubuntu it doesn't work. So I clearly understand the reason why choosing the old version of Ubuntu studio.

I'm curious, what does ```
lspci
``` report?

I'm very sure that you can have functional firewire support in the newer version of Ubuntu as well, but in that case, a kernel module haveto get initialized to get the firewire support you're after.

Usually the needed hardware support is there in the Linux kernel and get initialized by automatic, but if it's not there, it haveto get initialized manually, and in some cases, compiling your own Linux kernel can solve this problem. It's definitely not to recommend to a Linux newbie, but if you really want the hardware support and it isn't there, you can fix that either way, but it isn't easy. So if it's worth your time, then maybe.. :)

---

### Post by nickdc on 2012-01-09
Thanks for further ideas.

Snowpine, with respect, I think you may be wrong. In the end I took a risk and upgraded from the update manager. The upgrade completed and I have a Studio desktop with Ubuntu 10.04, but the terminal readout showed a very different set of details to those which happen with a vanilla Ubuntu update, so clearly Studio *is* a different beast and clearly too (to answer my own previous question) the upgrade manager knows this and installs the relevant parts. However, during the upgrade there were many error details, and I now can't access the internet via Studio (even though it downloaded all the packages during the installation process) and I'm no further forward with the firewire: after all this effort it still doesn't work! Anyway, thanks again for your help, but I'm giving up for the time being - other things need attending to.

Khelben1979, I *believed and hoped* it would work on an earlier version, based on what I'd learned in the forums, but now I've actually got 10.04, it still doesn't work! See my remarks to snowpine, above. I now have the added problem of not knowing whether the problem is still just the same firewire issue, or more due to the upgrade having introduced other problems. I'll run the lspci command when I next boot into Studio and post the result, though it won't be for a while as I have other things to do now. But if you have any further advice meanwhile I'd welcome it.

---

### Post by nickdc on 2012-01-09
> **khelben1979 said:**
> 
I'm very sure that you can have functional firewire support in the newer version of Ubuntu as well, but in that case, a kernel module haveto get initialized to get the firewire support you're after.

Usually the needed hardware support is there in the Linux kernel and get initialized by automatic, but if it's not there, it haveto get initialized manually, and in some cases, compiling your own Linux kernel can solve this problem. It's definitely not to recommend to a Linux newbie, but if you really want the hardware support and it isn't there, you can fix that either way, but it isn't easy. So if it's worth your time, then maybe.. :)

Thanks for this suggestion too. I'm still too much of a novice to attempt compiling my own kernel, though even that might not work: see this :-

[LIST=1]
[*]     [Ubuntu]("https://launchpad.net/ubuntu")
[*]     [“dvgrab” package]("https://launchpad.net/ubuntu/+source/dvgrab")
[*]     [Bugs]("https://bugs.launchpad.net/ubuntu/+source/dvgrab")
[*]     Bug #779680
[/LIST]
You'll understand what's being discussed much better than me, but for me it reads: "**more hassle**", and for the moment I've run out of time!

---

### Post by sgx on 2012-01-09
> **nickdc said:**
> Thanks for further ideas.

Snowpine, with respect, I think you may be wrong. In the end I took a risk and upgraded from the update manager. The upgrade completed and I have a Studio desktop with Ubuntu 10.04, but the terminal readout showed a very different set of details to those which happen with a vanilla Ubuntu update, so clearly Studio *is* a different beast and clearly too (to answer my own previous question) the upgrade manager knows this and installs the relevant parts. However, during the upgrade there were many error details, and I now can't access the internet via Studio (even though it downloaded all the packages during the installation process) and I'm no further forward with the firewire: after all this effort it still doesn't work! Anyway, thanks again for your help, but I'm giving up for the time being - other things need attending to.

Khelben1979, I *believed and hoped* it would work on an earlier version, based on what I'd learned in the forums, but now I've actually got 10.04, it still doesn't work! See my remarks to snowpine, above. I now have the added problem of not knowing whether the problem is still just the same firewire issue, or more due to the upgrade having introduced other problems. I'll run the lspci command when I next boot into Studio and post the result, though it won't be for a while as I have other things to do now. But if you have any further advice meanwhile I'd welcome it.
You will be better off in the end, with separate full installs of 
the ubuntu versions you try. Updates are often flawed, especially when skipping over releases, as with the leap from 8.04, to 10.04,
two of the better ubuntu releases.

You can add just the needed parts of a studio release, to a
ubuntu with a lightweight gui, that has few dependencies, thus potentially increasing performance, and minimizing conflicts.

Import and export of video formats/codecs will likely be the thorniest
issue, and I would plan on also getting basic familiarity with
blender, openshot, avidemoux, kino, cinellera, as well as mencoder,
and the ffmpeg command line options. The nature of free software,
usually means that none of the offered ones will be fully self-suffiecient, but a workable solution can often be pieced together.


Upgrading 8.04 will often lead to unsolvable dependencies, so experimenting may be necessary, hopefully revealing a couple of video apps that will run nicely in its RT environment.
Cheers

---

### Post by nickdc on 2012-01-11
> **sgx said:**
> You will be better off in the end, with separate full installs of 
the ubuntu versions you try. Updates are often flawed, especially when skipping over releases, as with the leap from 8.04, to 10.04,
two of the better ubuntu releases.

You can add just the needed parts of a studio release, to a
ubuntu with a lightweight gui, that has few dependencies, thus potentially increasing performance, and minimizing conflicts.

Import and export of video formats/codecs will likely be the thorniest
issue, and I would plan on also getting basic familiarity with
blender, openshot, avidemoux, kino, cinellera, as well as mencoder,
and the ffmpeg command line options. The nature of free software,
usually means that none of the offered ones will be fully self-suffiecient, but a workable solution can often be pieced together.


Upgrading 8.04 will often lead to unsolvable dependencies, so experimenting may be necessary, hopefully revealing a couple of video apps that will run nicely in its RT environment.
Cheers

Thanks, sgx. I was coming to the decision to do another fresh install, this time using Ubuntu 10.04, and your advice has helped confirm that decision. I don't know if it's coincidence or not, but since installing Studio on a separate drive, and finding that it couldn't find/make an internet connection (I was so hacked off by then I didn't even attempt any troubleshooting) I've now got connectivity problems (ie web pages taking forever to load) in my main Ubuntu on my "system" drive. More troubleshooting ahead! It's beginning to feel like the bad old Windoze days!:(

---

### Post by khelben1979 on 2012-01-11
> **nickdc said:**
> More troubleshooting ahead! It's beginning to feel like the bad old Windoze days!:(

Then maybe Ubuntu isn't what you're looking for.. It's not easy to say which Linux distribution is the best one for you, but you should know that it's a lot of alternatives available, and each Linux distribution has it's own Linux kernel, configured and compiled in the sense that the pc hardware which is supported depends on what you choose.

[Distrowatch.com]("http://distrowatch.com/").

---

