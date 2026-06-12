---
title: "Disappointed with pulseaudio bugs"
date: 2008-07-24
forum: Testimonials &amp; Experiences
---

### Post by MeatIsMurder on 2008-07-24
Hi all,

WARNING: Rant alert!!!! Read last sentence only if you wish to skip.

I have been using 8.04 since a few days after release.  It was good timing because my motherboard had just died and after reinstalling Windows XP the activation didn't work any more.  Calling Microsoft they said that as my version of XP Pro was OEM it could no longer be used and had died along with my motherboard.  So how fortunate I thought I was when I discovered a LTS Linux had been released, I imagined an OS that was stable like Windows XP and was transferable to another system when my current computer takes its final walk to the great computer graveyard.

Sure I had teething problems getting everything to work but I was expecting that and after so many years of using XP I knew it would not be easy to change.  I had about 20 or so apps that I needed to get working, most of which I learnt how to get working on these forums and a few with the help of Google. It took me most of first two months to get everything installed and working.  This I would have hoped to be a happy ending... except for the couple of issues I have which as far as I can tell all surround pulseaudio.  Current issues with sound include but are not limited too: 

*No Sound in Flash until I installed libflashsupport
*Firefox constantly crashes on flash pages after libflashsupport is installed but at least there is sound
*Wine has no sound most of the time.
*If you do manage to get sound working in Wine forget trying to make it work in anything else at the same time.
*Skype has no sound now after my last attempt to repair the above.

I have been though more fixes for these problems than I can remember.  Edited files, installed packages, endless commands... thats what it feels like.  I was also saddened to learn that the above issues were known in the beta but the release went ahead anyway.  This was one of the main reasons we purchased redhat at work instead of Ubuntu when my boss asked me to recommend a Linux distro that was supported by VMware ESX server 3.5.

So instead of the happy ending and a new shiny distro I can recommend to my friends.... I am starting to feel a little sour. I am still a fan of Ubuntu and won't change to an ebayed retail version of XP or another distro any time soon but my life is not as great as it should be because when I look at my computer I feel a little disappointed.  

Does anyone have some kind words to keep me going until the bugs in pulseaudio are sorted?

---

### Post by Vivaldi Gloria on 2008-07-24
Other than an occasional firefox crash, the following guide fixed all my sound problems:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

In particular, I choose OSS in wine settings and I start wine apps with padsp in front of them:

```
padsp wine app.exe
```

---

### Post by bapoumba on 2008-07-24
Moved to "Ubuntu Testimonials & Experiences".

---

### Post by Methuselah on 2008-07-24
Yeah, the PA issues can be a bit of a pain.
I had initial problems with skype but never had issues with flash.

However the bright side is that PA has good goals and inclusion in a popular distro like Ubuntu can only be a good thing for it.
All that exposure and use means that bugs will more likely to be found and fixed.

---

### Post by MeatIsMurder on 2008-07-24
Thanks Methuselah that did make me feel a bit better. Cheers. Vivaldi Gloria I am glad that that post helped you, sadly not so for me.

---

### Post by olskar on 2008-07-24
This is a quote from the main PulseAudio developer, Lennart Pöttering:

> Some distributions did a better job adopting PulseAudio than others. On the good side I certainly have to list Mandriva, Debian, and Fedora. OTOH Ubuntu didn't exactly do a stellar job. They didn't do their homework. Adopting PA in a distribution is a fair amount of work, given that it interfaces with so many different things at so many different places. The integration with other systems is crucial. The information was all out there, communicated on the wiki, the mailing lists and on the PA IRC channel. But if you join and hang around on neither, then you won't get the memo. To my surprise when Ubuntu adopted PulseAudio they moved into one of their 'LTS' releases rightaway. Which I guess can be called gutsy -- on the background that I work for Red Hat and PulseAudio is not part of RHEL at this time. I get a lot of flak from Ubuntu users, and I am pretty sure the vast amount of it is undeserving and not my fault.


Perhaps you can fix some things with this guide:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

