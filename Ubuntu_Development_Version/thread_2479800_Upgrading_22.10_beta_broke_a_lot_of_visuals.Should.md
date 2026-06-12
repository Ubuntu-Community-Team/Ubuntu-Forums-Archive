---
title: "Upgrading 22.10 beta broke a lot of visuals.Should I expect this with the final too?"
date: 2022-10-07
forum: Ubuntu Development Version
---

### Post by mikber18 on 2022-10-07
I have been loving my ubuntu for the last few months. Made it look just right including custom icons etc. 

I'm no Linux expert, but over the last few months TimeShift has saved my butt a number of times including a whole 22.10 Beta install and revert to 22.04 LTS - Thank you Timeshift! 

My question is, when it comes to the full release of 22.10, when its finally out of beta in a few months, should I expect things to break like they did when I installed beta. The things that I have in mind are: custom icons, themes, extensions or is it likely that with the full release it will be a like-for-like install with the added 22.10 goodness? 

Just wondering, not too familiar with Ubuntu/Linux, but have been learning a lot over the last 6months of daily use... Again, Thank you Timeshift for saving me from disaster. 

Thank you.

---

### Post by TheFu on 2022-10-07
22.10 isn't an LTS.  The purpose of non-LTS releases is to try new technologies and to fix bugs that require a new kernel to fix.  I would never recommend any beginner or someone who just wants their computer to work us any non-LTS release, unless they have bleeding edge hardware and the current LTS will not run on that hardware.

BTW, anything related to non-released versions belongs in a special "development release" subform, not in this general Install subforum.

---

### Post by MAFoElffen on 2022-10-08
To discuss and report anything about a development version: [Ubuntu Development Version]("https://ubuntuforums.org/forumdisplay.php?f=427")

Does a development version change from day-to-day? Yes. Do thinks break? Yes. That is why it is called a development release.

Daily's come out every night, with different things in testing on every day... What matches something one day is differnt the next... I admit that sometimes it seemed if it was like "what if we do this? Then they take the comments, what happened, what broke and was fixed, and how worked well, and roll it into the rolling release. Which doesn't exactly look like it was in the weeks before that release, because of the decisiosn process collecting all the testing data and making decisions from that into what it should be.

When it is released, 22.10 is a rolling interim release, which only gets support for a very limited time, where the user is forced to upgrade the release more often than an LTS release. I beieve the new timeline is 8 months. Whereas LTS releases is 5 years of support...

If what you want is stabiltity, and where changes and tweaks for personalized UI and such will stay, at least choose a released version. Preferably an LTS version.

---

### Post by coffeecat on 2022-10-08
*Thread moved to the **Ubuntu Development Version** sub-forum*.

---

### Post by grahammechanical on 2022-10-10
> when it comes to the full release of 22.10, when its finally out of beta in a few months,

Not months. Just days. Ubuntu 22.10 will be released October 20 2022.

> The things that I have in mind are: custom icons, themes, extensions

The responsibility for making sure custom code complies with each release of Ubuntu rests with the developers of those custom icons, themes, and extensions. To me it would make sense for developers of icons, themes and extensions to focus their efforts on the Ubuntu Long Term Support versions (LTS) and not interim versions that only have nine months life support. You should also take into account that Ubuntu's desktop environment is actually Gnome 3 desktop environment and that is under continual development and often breaks extensions even those written by Gnome developers.

My advice is to revert to using 22.04. Then dual boot with Ubuntu 24.04 development version when it is released and use it to experiment with your customizations before you upgrade 22.04 to 24.04.

Regards

---

### Post by zebra2 on 2022-10-13
Currently getting a smoother ride with the 5.19.0-20 kernel and dependency updates.

---

### Post by mikber18 on 2022-10-23
I'm following-up on this, because it was a thread that I have opened. 

Now that 22.10 is out when I try to upgrade I get the following error during update: 

```
W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., W:GPG error: https://dl.winehq.org/wine-builds/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F, E:The repository 'https://dl.winehq.org/wine-builds/ubuntu jammy InRelease' is not signed.
```

How can I fix this? Its something to do with Wine-Builds but not sure?

---

### Post by zika on 2022-10-24
[https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)
Also take a look of that word &#8222;jammy&#8220; in error... ;) Correct accordingly and check if repo has appropriate sub-folder...

---

