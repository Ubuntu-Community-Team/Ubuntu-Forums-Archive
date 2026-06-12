---
title: "Will Xubuntu 14.04 LTS Receive Security Support for 5 Years?"
date: 2015-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by perknh on 2015-06-07
Hello Xubuntu lovers,

I recently installed Xubuntu 14.04.2 on a friend's aging, 11-year-old, computer.  Now this computer is so old that I even had to downgrade Flash for both YouTube and the New York Times to render correctly!

I told the owner of this old computer that 14.04.2 will have security updates until April of 2019 --even if there will be no other support after April of 2017.

I believe I'm correct about this --that security support comes through the LTS versions for 5 years, even if bug patching ends a couple of years earlier.  

So now that I stated this, I thought I better check from the Xubuntu folks themselves!  Am I correct in telling the owner of this old computer that security support --and security support only-- is the exception to the LTS support rule.  Security support has go through all LTS releases for 5 years, even if bug patching stops.

Thank you,

perknh 

P.S.

I tried several versions of Ubuntu on this old computer --Ubuntu Unity, Lubuntu, Ubuntu MATE, and Xubuntu.  And, Xubuntu, hands down, was the fastest distribution there was for this 11-year-old computer. ;)

---

### Post by Copper Bezel on 2015-06-07
The core system from Ubuntu is all supported for five years, and I think that includes bugs along with security. Xubuntu themselves are only supporting the LTS for three years. So you'd be reasonably safe running it for five, the security updates that don't relate to Xubuntu-specific packages will keep coming, and you'll have access to the repos and whatever XFCE software you can install from them for the entirety of the five-year cycle, but Xubuntu themselves won't have anything to do with it after 2017.

---

### Post by grahammechanical on 2015-06-07
Actually the support clock started ticking 13 months ago. It would be best to advise the owner to upgrade to Xubuntu 16.04 when it is released at the end of April 2016.

The kernel in Ubuntu 14.04.2 is only supported for 18 months until April 2016. Ubuntu will be getting a 14.04.3 and a 14.04.4 and the kernels in boths will only be supported up to April 2016. When 14.04.5 comes out kernel support is extended until into 2019. But I am not sure if there will be a Xubuntu 14.04.3 or 14.04.4 or 14.04.5.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by Copper Bezel on 2015-06-07
So, wait, you're locked into the cycle if you get Xubuntu, but if you get the Ubuntu LTS and install XFCE on top, you get all the updates through to 2019?

---

### Post by kurt18947 on 2015-06-08
> **Copper Bezel said:**
> So, wait, you're locked into the cycle if you get Xubuntu, but if you get the Ubuntu LTS and install XFCE on top, you get all the updates through to 2019?

If I have it right, the 'underpinnings' of Xubuntu (the Ubuntu bits) will be kept up to date 'til 2019, the 'pretty bits' (XFCE4 desktop) will not.

---

### Post by perknh on 2015-06-08
Hello Copper Bezel and grahamechanical,

Thank you, both.  I can see I hit the jackpot when you two answered my question! 

I got this idea for using Xubuntu knowing that Peppermint Linux OS is expecting to receive Ubuntu's 14.04's security support until April of 2019, and also why Peppermint 6 decided to build off of Ubuntu's 14.04.2 instead of 14.10 or 15.04 --for longer lasting security support as well as improvements. But Peppermint, being a smaller distribution, has the benefit of small team of aficionados watching what happens to Peppermint OS like hawks.  I wasn't exactly sure what would happen here with Xubuntu.  I hope, in this case, that the 14.04.2 kernel will remain strong and secure for the remainder of the LTS cycle.  If strange things begin happening to this Xubuntu installation after Ubuntu implements 14.04.3, I have to try playing with the LTS Enablement Stack.  But, right now, if it ain't broke; I don't want try fixing it.

Believe me, if this old computer could have a full 5 years of support I would have kept Ubuntu MATE on it -- that is if MATE hadn't been moving like mud.  How delicate is this old computer?  Well, Linux Mint won't even install on it.  MX-14 comes across completely illegible.  And, nothing built off of Chromium will work either --including Maxthon for Linux which has to be a least 7 to 10 versions behind Chrome browser now.  This is also why Peppermint 3, 5, and 6 were no-goes too. :(

I mean this old computer seems to run only on Xubuntu 14.04 --and that is it.  I'm afraid that when 16.04 comes around, we'll just have to throw in the towel.  But, until then, I know the owner of this old computer will just be happy to enjoy Xubuntu 14.04 LTS's ride!

Thank you both so much for your excellent answers.:)

perknh

  

 
[URL="http://ubuntuforums.org/member.php?u=1228996"]
[/URL]

---

### Post by Yellow Pasque on 2015-06-08
Yeah, you'll still get non-xfce security updates.

>  Now this computer is so old that I even had to downgrade Flash for both YouTube and the New York Times to render correctly!
Is this one of those old CPU's that doesn't support SSE2 and can only run Flash 11.1.xxx? That, by far, is probably going to be the biggest security concern. Hopefully, you have Flashblock installed on the system.
(BTW, I thought Youtube uses html5 by default now?)

---

### Post by Bucky Ball on 2015-06-08
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by night_sky2 on 2015-06-08
I wish it was supported for a full-blown 5 years, because 14.04 is the best Xubuntu release I ever used.

I guess I'll have to wait and see what Xubuntu 16.04 LTS will look like but I am *very* reluctant to move away from the current LTS. *If ain't broke, don't fix it*!

> **perknh said:**
> Hello Xubuntu lovers,I told the owner of this old  computer that 14.04.2 will have security updates until April of 2019  --even if there will be no other support after April of 2017.

I believe I'm correct about this --that security support comes through  the LTS versions for 5 years, even if bug support ends a couple of years  earlier.  

You also need to take into consideration the kernel version. Since you installed 14.04.2, you have kernel v.3.16 which is only supported for 18 months.

That's is why I am sticking with Xubuntu 14.04.1 on my media installation. Because this will install kernel v3.13 which is supported for the *full* *5 years span*. My system will still update to 14.04.2 and 14.04.3 eventually but I retain the 3.13 kernel nonetheless which is exactly what I want to enjoy long-term support at this level. For more details: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by night_sky2 on 2015-06-08
> **Temüjin said:**
> Is this one of those old CPU's that doesn't   support SSE2 and can only run Flash 11.1.xxx? That, by far, is probably   going to be the biggest security concern. Hopefully, you have  Flashblock  installed on the system.
(BTW, I thought Youtube uses html5 by default now?)

You can also play all Youtube and Dailymotion videos in VLC Media PLayer  or SMPlayer. I think it would be safer to use that method instead of  compromising security with an outdated release of Flash player. Sure,  you can set flash to ''Ask to Activate'' in Firefox or use Flashblock but it  doesn't guarantee that the outdated plugin cannot be use for malicious attacks. You're running the risks.

---

### Post by mörgæs on 2015-06-08
A chain is only as strong as its weakest link. Though the parts which are in common with Ubuntu have five years support (from april 2014) the Xubuntu-specific parts have only three years, that is a little less than two years from now. Thus, the system as a whole is not secure after april 2017 - and one could argue that the old Flash plugin is a security breach as of today, as mentioned above.

I would go for a fresh install of 16.04 when that time comes and don't try to push the limits of 14.04.

---

### Post by verymadpip on 2015-06-08
> **mörgæs said:**
> Thus, the system as a whole is not secure after april 2016 - 

Sorry if I've misunderstood this, but that appears to say, effectively, we only get 2 years support.
I was under the impression Xubuntu LTS releases had 3 years support.
I thought I could safely & securely use **a *vanilla Xubuntu 14.04*** install until I had to replace it, for common sense reasons, in 2017, with either 16.04, 16.10 or 17.04. (16.10 seems pointless because I'd only have 3 months support).
Please clarify.

---

### Post by Copper Bezel on 2015-06-08
It does have three years of support, yes, you're guaranteed that much. But the LTS updates come out every two years, so you can't really skip one, either; whether you upgrade in 2016 or 2017, *that *release only takes you to the end of 16.04's cycle, obviously. Stating the obvious, but running vanilla Ubuntu with XFCE, you're guaranteed five years, and it's the same repos, so ... yeah, you can probably feel reasonably safe taking it to 2019, too.

---

### Post by monkeybrain20122 on 2015-06-09
The computer is so old that it probably won't survive until 2019. I wouldn't worry about it.

---

### Post by mörgæs on 2015-06-09
> **Copper Bezel said:**
> Stating the obvious, but running vanilla Ubuntu with XFCE, you're guaranteed five years

No, the XFCE packages are not maintained beyond three years, no matter if they are alone or accompanied by Ubuntu. 

I don't see why people would use an operative system older than three years anyway (unless forced to, but that's another matter). There are so many improvements in both kernel and applications that it pays to be updated.

---

### Post by Bucky Ball on 2015-06-09
Here's a conundrum. I install Ubuntu mini.iso 14.04 LTS. Just the base Ubuntu 14.04 kernel, no desktop environment, no 'machine profile' chosen at the beginning, so on reboot I have a CLI.

I install xfce4 and Synaptics and start installing other stuff, not specific to Xubuntu. I'm using the Ubuntu archives.

Now, the kernel is Ubuntu LTS so supported for five years. I am using the Ubuntu archives so even though xfce4 is the desktop environment used in Xubuntu, I am installing it from the 14.04 LTS repos so they are supported until 2019. xfce4 is, after all, just another piece of software in the repos, not specific to Xubuntu installs only. 

I'm guessing that as I've installed a spin of Ubuntu 14.04 LTS whatever I install from its repos should be supported for five years, whether that be Ubuntu specific software or lxterminal and pcmanfm from Lubuntu or xfce4 or gnome apps.

---

### Post by perknh on 2015-06-09
> **monkeybrain20122 said:**
> The computer is so old that it probably won't survive until 2019. I wouldn't worry about it.

That is very distinct possibility! 

> [COLOR=#000000]I would go for a fresh install of 16.04 when that time comes and don't try to push the limits of 14.04. --[/COLOR][COLOR=#000000]mörgæs[/COLOR]

First, let's see if we can get there with it. Funny thing is, the 1404.2 version of Xubuntu is even faster the Xubuntu 14.04  version was.  Now, I'll have to keep my eyes open for when Xubuntu moves into 14.03. I'll have to go to the LTSEnablementStack so I can run the command for a kernel upgrade.

I can see now that Flash is this computer's weakest link.  I've never seen or experienced what bad things an unsupported Flash installation can do to a computer with a Linux installation.  I suspect, although I'm taking some risk here,  the risk isn't so great.  Also, since I'm always game for new ideas, I'm wondering if I had installed Ubuntu Unity 14.04 (which moved as slowly on this computer as a Pink Floyd light show) and then added Xubuntu on top of it, would this computer still moving as quickly as it does now?  Right now, for an old aging clunker, this computer with its new Xubuntu 14.04.2 installation is dancing right along. \\:D/

> [COLOR=#000000]I wish it was supported for a full-blown 5 years, because 14.04 is the best Xubuntu release I ever used.[/COLOR]

[COLOR=#000000]I guess I'll have to wait and see what Xubuntu 16.04 LTS will look like but I am [/COLOR]*very reluctant to move away from the current LTS. [I]If ain't broke, don't fix it! --*[/I]*[I]night_sky2*[/I]

That's how I'm feeling about Xubuntu 14.04.2 right now. 

I thank everyone who has posted here for all the good ideas and insights. [IMG]http://ubuntuforums.org/images/icons/icon14.png[/IMG]

perknh

---

### Post by Copper Bezel on 2015-06-09
> **Bucky Ball said:**
> Now, the kernel is Ubuntu LTS so supported for five years. I am using the Ubuntu archives so even though xfce4 is the desktop environment used in Xubuntu, I am installing it from the 14.04 LTS repos so they are supported until 2019. xfce4 is, after all, just another piece of software in the repos, not specific to Xubuntu installs only.
Yeah, but there's no actual guarantee of support for any particular piece of software in the repositories, either. I mean, Ubuntu versions shipping with broken versions of software frozen in the repos are not unheard of. That becomes a question of who's maintaining it. I suppose that, like mörgæs [COLOR=#000000]says, xfce4 is being maintained in the Ubuntu repos by the Xubuntu folks, or LXDE by the Lubuntu folks? But there's also the question of how necessary or consequential that support is, too. I mean, you know there won't be any new features or software versions, bug fixes are likely until the next LTS rolls out, and security fixes, if you expect to see a critical security fix for pcmanfm anytime soon, should be offered through the support cycle ... but if upstream *and *the flavors have moved on from the software version supplied and aren't maintaining them anymore, and Ubuntu as a project itself doesn't have any priority on maintaining those packages, who's actually going to *make* any updates? This isn't Firefox we're talking about here.[/COLOR]

---

### Post by mörgæs on 2015-06-09
> **verymadpip said:**
> Sorry if I've misunderstood this, but that appears to say, effectively, we only get 2 years support.
I was under the impression Xubuntu LTS releases had 3 years support.

You are correct. 2014 + three years was a bit too complicated for me. 
Support runs through april 2017.

---

### Post by mörgæs on 2015-06-09
> **Bucky Ball said:**
> I'm using the Ubuntu archives.


All Buntus share the same main, universe, multiverse and restricted repositories so I prefer the name 'Buntu archives'.

All software (not counting PPA's now) for the Buntu family is stored here, regardless of the support length. The fact that some packages have five years of support does not indicate that this applies to all packages.

There is a command which shows the distribution of packages on end-of-support date. I can't find it right now, does anybody remember?

---

### Post by monkeybrain20122 on 2015-06-09
> **mörgæs said:**
> 

I don't see why people would use an operative system older than three years anyway (unless forced to, but that's another matter). There are so many improvements in both kernel and applications that it pays to be updated.

+1 to that. I can't imagine still using 12.04 at this point. :) Though from time to time you still have people showing up asking questions about 10.04. :o

---

### Post by Bucky Ball on 2015-06-09
> **mörgæs said:**
> 
There is a command which shows the distribution of packages on end-of-support date. I can't find it right now, does anybody remember?

Love to get my eyes and fingers on that. Would be very handy. :)

---

### Post by Yellow Pasque on 2015-06-09
> **perknh said:**
> I can see now that Flash is this computer's weakest link.  I suspect, although I'm taking some risk here,  the risk isn't so great.

Think again. Flash is a popular attack method. I'd be far, far, far (I'd type more far's if I wasn't lazy) more worried about the outdated Flash plugin than xfce packages only getting 3 years of security updates as opposed to 5. As others have pointed out, there are ways around using Flash, at least for video playback.

---

### Post by verymadpip on 2015-06-09
> **mörgæs said:**
> You are correct. 2014 + three years was a bit too complicated for me. 
Support runs through april 2017.
haha, no worries.
Adding 3 to something is about my mathematical limit.

I think I'm probably not supposed to mention this, but:
If you use minitube for youtube playback a file gets stored in /tmp which can be played back with mplayer/smplayer.
Smtube may be a viable option too, probably preferable to the minitube hoop jumping.

---

### Post by deadflowr on 2015-06-09
> **Bucky Ball said:**
> Love to get my eyes and fingers on that. Would be very handy. :)

ubuntu-support-status --show-all

I forget if it is part of a certain package or not...

---

### Post by mörgæs on 2015-06-09
Yes, that's the one. 
It gives a long output, so adding a ```
| more
``` helps.

---

### Post by monkeybrain20122 on 2015-06-09
> **verymadpip said:**
> 
If you use minitube for youtube playback a file gets stored in /tmp which can be played back with mplayer/smplayer.
Smtube may be a viable option too, probably preferable to the minitube hoop jumping.

These work only for Youtube and Smtube is definitely better than minitube (but need the newest version from rvm's ppa) But Youtube is the least of the problem when it comes to flash so I don't know why the fixation on it. Most  Youtube videos have html5 version  anyway and you don't even need flash to  watch them. There is definitely no need to use the clumsy method of streaming through minitube then retrieve the file form /tmp. 

If you have the newest Smplayer you can also play Youtube and many other sites by copying the url into Smplayer if you configure Smplayer to use mpv and youtube-dl instead of mplayer as the backend.

But the best, most direct and easiest way is to use this [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)  Then you can just watch videos from Firefox. It  works on many  streaming sites and not just flash but also other formats like quicktime, html5 etc,--html5 is not exactly easy on old systems and you would need gecko-mediaplayer for other formats otherwise,--because mpv supports a lot of formats and youtube-dl works on lot of popular sites. There is no need for special configuration, it just works.But of course you need mpv and youtube-dl in the system.

Get mpv from [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
and youtube-dl from [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

**@OP**

Instead of risking security and suffering poor performance by installing unsupported flash I would not install flash at all on that machine if I were you. Use the mpv addon.

---

### Post by mikodo on 2015-06-09
> **Copper Bezel said:**
> Yeah, but there's no actual guarantee of support for any particular piece of software in the repositories, either. I mean, Ubuntu versions shipping with broken versions of software frozen in the repos are not unheard of.

> **mörgæs said:**
>  The fact that some packages have five years of support does not indicate that this applies to all packages.

Yep. I as a noob was using the then, newer DejaDup GUI backup app in 10.04 LTS, for all my /home. I found out through testing it, that it had "stuffed itself". I found a bug for it, that had a fix for newer Ubuntu releases, but it couldn't be back-ported to 10.04. (The Canonical employee who maintains it, tried with me and eventually indicated he couldn't do it). It was a duplicity package problem, that was left unresolved. That could have been a serious problem.

Then, I found rsync.  :)

---

### Post by Bucky Ball on 2015-06-10
Thanks for that. Fascinatin' indeed!

```
You have 17 packages (0.9%) supported until March 2016 (9m)
You have 1540 packages (78.0%) supported until May 2019 (5y)
You have 116 packages (5.9%) supported until February 2015 (9m)
You have 151 packages (7.6%) supported until May 2017 (3y)
```

Remembering that this is a 'hybrid' not an install of a 'standard' Ubuntu flavour but the mini install with xfce4 and the apps I want/need thrown on.

It appears I already have a heap of unsupported software according to the output. Can't figure that out as I'm using 14.04.2 LTS!

---

### Post by Copper Bezel on 2015-06-10
Same for me, also on 14.04: 
> You have 231 packages (7.5%) supported until February 2015 (9m)
So I assume that has to be normal, and it does make the concerns about running an unsupported version of xfce4 seem slightly less pressing.

Obviously, it also lists packages from PPA as unsupported as well, separately.

---

### Post by mikodo on 2015-06-10
Upon closer review, what I had said was just, not accurate. I thought it best to delete.

---

### Post by deadflowr on 2015-06-10
Unsupported means indeterminate.
Meaning the developers for which packages listed as unsupported never filled in the support length for those packages.
Meaning they can be either dead packages or packages that those maintainers will actually be supporting forever...

---

### Post by monkeybrain20122 on 2015-06-10
> **deadflowr said:**
> ubuntu-support-status --show-all

I forget if it is part of a certain package or not...

I don't know, it shows that I have a whole bunch of "unsupported packages" including things I have installed straight out of the repo like compiz, ccsm, apache etc. It seems either I misunderstand the meaning of supported packages or that this is broken in 15.04.

---

### Post by Bucky Ball on 2015-06-10
> **monkeybrain20122 said:**
> I don't know, it shows that I have a whole bunch of "unsupported packages" including things I have installed straight out of the repo like compiz, ccsm, apache etc.

Same.

---

### Post by monkeybrain20122 on 2015-06-10
Just saw deadflower's post above mine. :) That explains it.

---

### Post by perknh on 2015-06-10
> **deadflowr said:**
> ubuntu-support-status --show-all

I forget if it is part of a certain package or not...

Hello deadflowr,

Now that's a gem of a command --thank you!

[B]@night_sky2

[/B]> [COLOR=#000000]You also need to take into consideration the kernel version. Since you installed 14.04.2, you have kernel v.3.16 which is only supported for 18 months. --night_sky2[/COLOR]

This is will definitely keep in mind, thank you. That computer, running the 14.04.2 version of Xubuntu, is running pretty much like new.  Xubuntu has transformed that old computer.  It now runs as though it has found the fountain of youth!

> [COLOR=#000000]...in Firefox or use Flashblock but it doesn't guarantee that the outdated plugin cannot be use for malicious attacks --[/COLOR][COLOR=#000000]night_sky2[/COLOR]

I'm sure this is not a perfect solution but it is the most realistic solution I can find to help minimize risks in the environment where that old, but revived, computer dwells. I have now installed Flashblock, and have made sure that security updates are now downloaded and installed automatically.

Thank you, everyone, for all of the help and ideas I have found here,

perknh

---

