---
title: "Clarification on Debian kernel, hardware support with brand new hardware, etc."
date: 2015-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Roasted on 2015-01-07
Hello friends. I run OpenMediaVault on my home server, which is basically a Linux based FreeNAS oriented NAS specific distro. It's based on Debian Stable. You can either install the OMV ISO, or install Debian and then pull in the OMV repo.

I learned that the OMV ISO contains a specific kernel, 3.2.X of some sort, which is expected given that OMV is based on Debian and that's what Debian is on. It's often recommended for people having issues with installing OMV on brand spankin new hardware to try installing Debian first, then pull in OMV from their repo. The regular OMV ISO works nearly every time, but as mentioned, brand new hardware may pose an issue. That made me curious about something.

A while back I had run in to an issue where a system flat out would not successfully complete its boot with Ubuntu unless it was on the 3.8 kernel or above. If it was on 3.7 or below, no dice. (I forget what Ubuntu versions this coincides this, I just remember 3.7 vs 3.8 was the turning point). This had me wondering about Debian in particular in case I ever buy some brand new hardware and slap together an OMV box that redefines the definition of amazing. What if that new hardware refuses to boot? What if I need a newer kernel to get everything moving?

With that story on the table, here's my questions.

1) Does Debian update their ISOs with newer kernels? I.e. if a Debian ISO is built in June for Wheezy, is that the same Wheezy ISO in December? Or would December's ISO contain a newer branch of 3.2.X kernel?
2) If #1 is a no go, is there a custom spin of Debian somewhere with the backports kernel already bundled in?
3) Do those updates contain drivers that might cause a system to operate normally? Or are they typically just bug fixes?

In short, I'm just trying to be aware of an alternative plan in case Debian's epic stability, thanks to not being bleeding edge, ends up biting me because of potentially buying bleeding edge hardware in the future.

---

### Post by ian-weisser on 2015-01-07
> **Roasted said:**
> Does Debian update their ISOs with newer kernels?

The ISOs don't usually include backported software, and never a backported kernel (that would break the 'stable' concept).
However, after install it's trivial to enable backports and pull in the latest. 

Here are the current kernels in Debian, including backports:
```
$ rmadison -u debian linux
 linux | 3.2.57-3+deb7u2~bpo60+1 | squeeze-backports | source
 linux | 3.2.63-2                | wheezy            | source
 linux | 3.2.63-2+deb7u1~bpo60+1 | squeeze-backports | source
 linux | 3.2.63-2+deb7u2~bpo60+1 | squeeze-backports | source
 linux | 3.2.63-2+deb7u2         | wheezy-security   | source
 linux | 3.2.65-1                | wheezy-p-u        | source
 linux | 3.12.9-1~bpo70+1        | wheezy-backports  | source
 linux | 3.13.10-1~bpo70+1       | wheezy-backports  | source
 linux | 3.14.12-1~bpo70+1       | wheezy-backports  | source
 linux | 3.14.15-2~bpo70+1       | wheezy-backports  | source
 linux | 3.16.7-ckt2-1~bpo70+1   | wheezy-backports  | source
 linux | 3.16.7-ckt2-1           | jessie            | source
 linux | 3.16.7-ckt2-1           | sid               | source
 linux | 3.18-1~exp1             | experimental      | source
```

You can see that original Wheezy is still on 3.2, and that Wheezy-security is patching that same 3.2. That patched 3.2 is on the ISO.
But Wheezy-backports has a much more recent 3.16 available.

---

### Post by Roasted on 2015-01-07
> **ian-weisser said:**
> The ISOs don't usually include backported software, and never a backported kernel (that would break the 'stable' concept).
However, after install it's trivial to enable backports and pull in the latest. 

Here are the current kernels in Debian, including backports:
```
$ rmadison -u debian linux
 linux | 3.2.57-3+deb7u2~bpo60+1 | squeeze-backports | source
 linux | 3.2.63-2                | wheezy            | source
 linux | 3.2.63-2+deb7u1~bpo60+1 | squeeze-backports | source
 linux | 3.2.63-2+deb7u2~bpo60+1 | squeeze-backports | source
 linux | 3.2.63-2+deb7u2         | wheezy-security   | source
 linux | 3.2.65-1                | wheezy-p-u        | source
 linux | 3.12.9-1~bpo70+1        | wheezy-backports  | source
 linux | 3.13.10-1~bpo70+1       | wheezy-backports  | source
 linux | 3.14.12-1~bpo70+1       | wheezy-backports  | source
 linux | 3.14.15-2~bpo70+1       | wheezy-backports  | source
 linux | 3.16.7-ckt2-1~bpo70+1   | wheezy-backports  | source
 linux | 3.16.7-ckt2-1           | jessie            | source
 linux | 3.16.7-ckt2-1           | sid               | source
 linux | 3.18-1~exp1             | experimental      | source
```

You can see that original Wheezy is still on 3.2, and that Wheezy-security is patching that same 3.2. That patched 3.2 is on the ISO.
But Wheezy-backports has a much more recent 3.16 available.

Very nice. Sounds like a great alternative. Here's the catch that I'm somewhat struggling with... what if (this may be a big 'if', but what IF...) your computer simply will not boot on Debian with 3.2 and requires a much newer kernel to even boot, let alone install?

That's what part I was questioning. I never ran into a system like this except that one system, which was a laptop where 3.7 and below was a bust, 3.8 and above, worked fine. I just question if I hit that again *but* Debian is my target... am I stuck?

(this is specifically looking at stable, not testing, sid, etc)

---

### Post by ian-weisser on 2015-01-07
If you insist on sticking with Stable (one of my servers runs Debian Stable, too),
and _if_ the hardware won't boot off the Stable kernel,
then you would be stuck.

But the former seems a matter of choice.
And the latter hasn't been tested yet.

Laptops may not be the best guide for this situation. Lots of laptop-specific and occasionally desktop-specific needs - power managerment, video cards, GPUs, PAE - that require later kernels should not apply to simpler NAS hardware.

---

### Post by Roasted on 2015-01-07
> **ian-weisser said:**
> If you insist on sticking with Stable (one of my servers runs Debian Stable, too),
and _if_ the hardware won't boot off the Stable kernel,
then you would be stuck.

But the former seems a matter of choice.
And the latter hasn't been tested yet.

Laptops may not be the best guide for this situation. Lots of laptop-specific and occasionally desktop-specific needs - power managerment, video cards, GPUs, PAE - that require later kernels should not apply to simpler NAS hardware.

Oh certainly. I knew asking this question it would be a rarity, and also that laptops are almost always the ones "needing" newer kernels to function. And uh, yeah I'm definitely not running a server, NAS, or anything like that off of a laptop. ;) But that didn't curb my curiosity enough to keep from asking!  Thanks for your input. It's appreciated. :D

---

### Post by grahammechanical on 2015-01-07
If I was running Debian and not Ubuntu and thinking of buying newer hardware my concerns would be whether this newer hardware required a proprietary video driver. My understanding of Debian philosophy is that proprietary is not allowed. I know that proprietary software can be installed on Debian but newer hardware might need a newer kernel with a matching proprietary video driver. I would not have such concerns with Ubuntu.

Regards.

---

### Post by Roasted on 2015-01-07
> **grahammechanical said:**
> If I was running Debian and not Ubuntu and thinking of buying newer hardware my concerns would be whether this newer hardware required a proprietary video driver. My understanding of Debian philosophy is that proprietary is not allowed. I know that proprietary software can be installed on Debian but newer hardware might need a newer kernel with a matching proprietary video driver. I would not have such concerns with Ubuntu.

Regards.

If I recall there are unofficial builds hosted on the Debian site that actually include a lot of those bits. It's not that Debian doesn't allow it, it's just that Debian doesn't ship with any proprietary bits by default.

---

### Post by mastablasta on 2015-01-08
you talk about how you want stable and then you go on about unofficial builds:

> **Roasted said:**
> If I recall there are unofficial builds hosted on the Debian site that actually include a lot of those bits. It's not that Debian doesn't allow it, it's just that Debian doesn't ship with any proprietary bits by default.

as well as using backports. you are not on stable anymore if you use backports and new kernel. but you are basically on your own version of Debian that was "created" from stable version.

also stable doesn't necessarily mean bugs free or anything like that. it just means there are no changes made. you are using OMV and if you check you logs there should be some silly errors constantly logging. this is due to a bug in Debian and has something to do with disk uuid or whatever they are. anyway they immediately notified Debian team about the bug and reply was - won't fix. they might fix it in next Debian stable but it doesn't look good so far. anyway you can fix that bug but another one will show up only it won't write so many messages. funny how Ubuntu doesn't have this bug. I guess they are more interested in actually having less bugs rather than having an OS frozen in time.

since I had it all setup for the 5th time I decided not to do another reinstall and I removed OMV but stayed on Debian. I am waiting if they will fix the bug or not and there were some other minor issue I had with OMV. just didn't do what I wanted it to do. I still owe them a write up of what went wrong. but in any case I am waiting for things to get fixed so I can reinstall OMV. until then I make do with Ajenti. not perfect but certainly no unnecessary errors reported.

the errors are probably not much of an issue if server is LAN but if you open it online then it is hard to see the real errors when they pop up. furthermore it was constantly spinning disks up and down for no good reason. while many people don't see a problem with that, I do. If Debian will start failing me I will replace it with Ubuntu LTS. but so far it seems to be doing OK. system updates itself. all is quiet any errors are reported by email. for now I closed port 22 from outside. got sick of constant attacks from the Chinese (I might reopen it but first blocking all that comes from NK or China). just the way I like it.

edit: bleeding edge hardware usually doesn't go well with Linux anyway. if it does it might need bleeding edge kernel. those are usually beta, testing, unstable and so on.

---

### Post by Roasted on 2015-01-08
> **mastablasta said:**
> 
also stable doesn't necessarily mean bugs free or anything like that. it just means there are no changes made. you are using OMV and if you check you logs there should be some silly errors constantly logging. this is due to a bug in Debian and has something to do with disk uuid or whatever they are. anyway they immediately notified Debian team about the bug and reply was - won't fix. they might fix it in next Debian stable but it doesn't look good so far. anyway you can fix that bug but another one will show up only it won't write so many messages. funny how Ubuntu doesn't have this bug. I guess they are more interested in actually having less bugs rather than having an OS frozen in time.

That's kind of a loaded statement to make... I have personally submitted a multitude of bug reports to Ubuntu that affected many users... and have yet to get addressed. Some even being 3+ years old. I love Ubuntu, but it too is far from being bug free. ;)

---

### Post by mastablasta on 2015-01-09
well form my experience in ubuntu more things just work. sure it has bugs, but usually if there is a solution they would patch the bug. debian stable (!) won't necessarily do that. Debian testing will though.

---

### Post by monkeybrain20122 on 2015-01-09
> **mastablasta said:**
> 
also stable doesn't necessarily mean bugs free or anything like that. it just means there are no changes made. 

Great point. In Debian speak 'stability' simply means consistency. So if something is consistently and predictably broken it is 'stable' in Debian sense. :)

---

