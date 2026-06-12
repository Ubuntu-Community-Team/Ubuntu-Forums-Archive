---
title: "Backport of kdepim/kmail ?"
date: 2016-10-31
forum: Repositories &amp; Backports
---

### Post by oygle on 2016-10-31
Having significant problems with KMail, and the forums at [http://kde.org](http://kde.org) have asked if I can enquire about a backport of kdepim/kmail. I'm on Kubuntu 16.04.1, however it seems the KMail version is not current.

---

### Post by T.J. on 2016-10-31
As a disclaimer - this is just my opinion.  I believe that Kubuntu rushed into a KDE Frameworks 5 release.  The quality of code just isn't there yet.   It's been my experience that any version of KDE Frameworks 5 is still buggy, and will be for some time. I realize that doesn't help you.  I could theoretically help you backport the lastest KDE Apps to Kubuntu 16.04 - but I can't promise stability or that it would even compile at all.  You're better off asking Kubuntu for a patch for the existing Kmail rather than backporting an upstream version with new problems. 

Still, it could be interesting to try.

---

### Post by oygle on 2016-10-31
> **T.J. said:**
> I believe that Kubuntu rushed into a KDE Frameworks 5 release.  The quality of code just isn't there yet.   It's been my experience that any version of KDE Frameworks 5 is still buggy, and that It has been for some time. I personally would not expect completely stable behaviour from it or any KDE application compiled against v5 for at least another year.

Okay thanks. Interesting to know that; I will keep it in mind. KMail crashes many times each day, so the workaround is to restart akonadi server, which has been using 25% of the CPU.

> **T.J. said:**
> The latest release of KDE Applications has support for KDE 4.14.25 for those who need the latest applications and stability both.

I'm running Kubuntu 16.04.1 - KMail version info has "Version 5.1.3 - Using:
KDE Frameworks 5.18.0
Qt 5.5.1 (built against 5.5.1)
The xcb windowing system

In synaptic KMail and Kontact have both got this version info - 4:15.12.3-0ubuntu1

I'd probably change from KMail if I knew some other mail client had all the features I use. Pegasus Mail was amazing.  lol

> **T.J. said:**
> 
If you want a stable KDE desktop, I recommend Debian 8.

Pardon my ignorance, but what is Debian 8 ? Isn't Ubuntu and all it's flavours, based on Debian ?

---

### Post by T.J. on 2016-11-01
> **oygle said:**
> Okay thanks. Interesting to know that; I will keep it in mind. KMail crashes many times each day, so the workaround is to restart akonadi server, which has been using 25% of the CPU.  As I said, that was an opinion.   Others have had better luck, but my tests have yielded less than ideal results.  You should probably decide for yourself.    > The xcb windowing system  The windowing system is called X11.  XCB is a programming library for X11.  =) > I'd probably change from KMail if I knew some other mail client had all the features I use. Pegasus Mail was amazing.  lol  You can try Thunderbird.    > Pardon my ignorance, but what is Debian 8 ? Isn't Ubuntu and all it's flavours, based on Debian ?  Ubuntu is a derivative of Debian, specifically Debian Unstable.  Debian 8 is the most recent version of Debian.  I mentioned it because Debian 8 supports KDE 4. KDE 4 is older, but Debian's KDE is much more stable than Kubuntu.  If you really prefer Kmail, this makes it a viable option, in my opinion.

---

### Post by oygle on 2016-11-01
> **T.J. said:**
> You can try Thunderbird.

Yes, see how it goes. I don't use Kontact or the other "K"s from the kdepim suite, so maybe Thunderbird will suffice. It would remove my reliance on KMail.

> **T.J. said:**
> Ubuntu is a derivative of Debian, specifically Debian Unstable.  Debian 8 is the most recent version of Debian.  I mentioned it because Debian 8 supports KDE 4. KDE 4 is older, but Debian's KDE is much more stable than Kubuntu.  If you really prefer Kmail, this makes it a viable option, in my opinion.

Have been looking through packages from Debian 8. Noticed some versions were like 2014 (youtube-dl). However, I do have a spare HDD that I can install Debian 8 to, boot to it, and see how it goes. Thanks for all your help.  :)

---

### Post by acheronuk on 2016-11-01
> **oygle said:**
> Having significant problems with KMail, and the forums at [http://kde.org](http://kde.org) have asked if I can enquire about a backport of kdepim/kmail. I'm on Kubuntu 16.04.1, however it seems the KMail version is not current.

We will hopefully have an updated version of kmail in the kubuntu backports ppa in the next few weeks. 

Packaging and testing of backports got a little sidelined with work on the release of Yakkety, but I hope things can now catch up somewhat.

---

### Post by T.J. on 2016-11-01
> **acheronuk said:**
> We will hopefully have an updated version of kmail in the kubuntu backports ppa in the next few weeks.   Packaging and testing of backports got a little sidelined with work on the release of Yakkety, but I hope things can now catch up somewhat.  I have a great respect for all of your work as I do for KDE itself, so please do not take anything I have said as any form of disparagement.  It has been my experience that the raw KDE Applications bundle from upstream occasionally inherits new bugs and sometimes doesn't even produce a working binary.  I find that very odd; it must make your job difficult.      The last time with upstream code for me was with Bloglio - everything compiled, but it constantly crashed when configuring it.  I believe it was patched finally.  The longstanding annoyance for me has been Basket.  I'm about ready to patch it myself - there are many issues with drag and drop that have been there for a long time.  I do not think the original author maintains it anymore.

---

### Post by T.J. on 2016-11-01
In this case, you may find that Debian 8 fits your particular needs better. It's worth testing; and if it doesn't work out - no big deal.  Ubuntu and Debian often help each other out. The Debian Project and Ubuntu are friends; with developers often working in both projects. The reason that Debian and Ubuntu do things differently is just a difference of opinion. There is room in world for both. Don't be discouraged if you run up against a few hardcore people, there are a few on both sides. For myself, I need the best stability I can get, but I love the energy and friendliness of the Ubuntu community, which is why I stop by often.

 > **oygle said:**
> Have been looking through packages from Debian 8. Noticed some versions were like 2014 (youtube-dl). However, I do have a spare HDD that I can install Debian 8 to, boot to it, and see how it goes. Thanks for all your help.  :)    That is because Debian values stability over new features.  Debian 8 was released in 2015. It is released approximately every two to three years like an Ubuntu LTS.  The difference in age is because Debian does not allow new software to be added once the testing freeze has begun - which takes 6 months to a year.If new versions are a concern, Debian maintains a special repository for Debian Stable with updated software called Backports. So that may interest you.

  You can also use software directly from Debian Testing or Unstable by pinning or backporting. Debian provides instructions on how to do it.  It should also be said that you can install Ubuntu software in Debian (and vice versa) using a chroot with debootstrap.

---

### Post by oygle on 2016-11-01
> **acheronuk said:**
> We will hopefully have an updated version of kmail in the kubuntu backports ppa in the next few weeks. 

Packaging and testing of backports got a little sidelined with work on the release of Yakkety, but I hope things can now catch up somewhat.

Oh thanks, great news.  :)

> **T.J. said:**
> In this case, you may find that Debian 8 fits your particular needs better. It's worth testing; and if it doesn't work out - no big deal. 

Yes, if I installed it on a secondary HDD, and then just boot when testing. I did spend a hour or so looking at Debian yesterday. For me, because I have found so much helpful support in the Ubuntu forums, the first port of call was Debian forums. Checking posts on comparing Debian/Ubuntu and posts about the applications I use. Good comments there, and helpful. Just noticed a few things..

1. Installing/trying doesn't seem so easy. With Kubuntu, just d/load an ISO, put it on USB and go. But there were 3 huge DVD's or the other d/load options were a small iso and then update. What concerned me also was the many links to using peering for downloading. I prefer downloading from the one site, not bits and pieces from many sources.

2. Finding "how to's" and other documentation was no way near as clear and easy as the Ubuntu 'help' sites. It was not as structured and set out as I have become used to with Ubuntu. I assume having a background in structured programming makes me aware of things that do not strictly pertain to structure.  lol

For now, I will wait for the backport of KMail. There is a general 'resource' problem with this desktop, but given it's age (8 yrs), it may well be time to update.  :)

Thanks for all your help.

---

### Post by T.J. on 2016-11-01
> **oygle said:**
> I did spend a hour or so looking at Debian yesterday. For me, because I have found so much helpful support in the Ubuntu forums, the first port of call was Debian forums. Checking posts on comparing Debian/Ubuntu and posts about the applications I use. Good comments there, and helpful. Just noticed a few things..


I agree with your feelings about the forums. Debian's forums are not as good as Ubuntu's are.  Each community has strengths and weaknesses.




> 
1. Installing/trying doesn't seem so easy. With Kubuntu, just d/load an ISO, put it on USB and go.





In order to install Debian you need only the disc 1 ISO.  The rest are entirely optional. I haven't downloaded them in years.  There is also a minimal disc &#8211; which fits on one CD or USB stick.  






> 
 But there were 3 huge DVD's or the other d/load options were a small iso and then update. What concerned me also was the many links to using peering for downloading. I prefer downloading from the one site, not bits and pieces from many sources.





That's a common assumption, and no harm done.  Even when you are using the Ubuntu website, you are downloading from a bunch of different mirrors &#8211; same as Debian.  Debian just does not bother to hide that fact from you.  The reason Debian and Ubuntu use multiple mirrors (and offers torrent or jigdo) is reliability and speed.




> 
2. Finding "how to's" and other documentation was no way near as clear and easy as the Ubuntu 'help' sites. It was not as structured and set out as I have become used to with Ubuntu. I assume having a background in structured programming makes me aware of things that do not strictly pertain to structure.  Lol



That's very strange to me.  I've always felt the reverse &#8211; that Ubuntu's documentation was terrible and Debian's was far more helpful. I've always found answers to my problems elsewhere, that is why I come to the Ubuntu forums to share what I have learned.


You may find this helpful in the future. Much applies to Ubuntu as well, since Ubuntu is made from Debian: [https://debian-handbook.info/browse/stable/](https://debian-handbook.info/browse/stable/)




> 
For now, I will wait for the backport of KMail. There is a general 'resource' problem with this desktop, but given it's age (8 yrs), it may well be time to update.  :)



That's okay.  It is best to stick with what you feel is best for you. After much frustration, I settled with XFCE.  Who knows?  You may find Xubuntu is right for you.


> 




Thanks for all your help.


You're very welcome.  I do have one thought, if you feel willing to try it.  It may not work well.  You could try reconfiguring Akonadi to use SQLite to see if that has an effect on your resource problem.  I did not suggest it sooner because KDE used to classify it as experimental.It may be problematic for you, since KDE only supports MySQL/MariaDB out of the box.  I've always felt that was a bad policy, and a black mark on KDE's reputation for configurability..

---

### Post by oygle on 2016-11-05
> **T.J. said:**
> In order to install Debian you need only the disc 1 ISO.  The rest are entirely optional. I haven't downloaded them in years.  There is also a minimal disc – which fits on one CD or USB stick.

Oh, okay. Thanks  :)

> **T.J. said:**
> That's very strange to me.  I've always felt the reverse – that Ubuntu's documentation was terrible and Debian's was far more helpful. I've always found answers to my problems elsewhere, that is why I come to the Ubuntu forums to share what I have learned.

It was probably just what I was used to, so something different (Debian docs) seemed so different.  :D

> **T.J. said:**
> You could try reconfiguring Akonadi to use SQLite to see if that has an effect on your resource problem.  I did not suggest it sooner because KDE used to classify it as experimental.It may be problematic for you, since KDE only supports MySQL/MariaDB out of the box.  I've always felt that was a bad policy, and a black mark on KDE's reputation for configurability..

I don't think I would be comfortable with Akonadi reconfig. Even in the last few days, KMail is displaying entries in folders, but there is actually no mails there, not even visible by Dolphin. So Akonadi 'thinks" there are emails in folders. Why it can't just use the folder and file as the 'real' basis to emails, I don't know. It seems a huge overload and a big mess.  lol

---

### Post by T.J. on 2016-11-05
I use Thunderbird presently.  I suppose I am "old school" and prefer longer release cycles with better QA.

> **oygle said:**
> 

I don't think I would be comfortable with Akonadi reconfig. Even in the last few days, KMail is displaying entries in folders, but there is actually no mails there, not even visible by Dolphin. So Akonadi 'thinks" there are emails in folders. Why it can't just use the folder and file as the 'real' basis to emails, I don't know. It seems a huge overload and a big mess.  lol

Speaking as one who has had some lengthy experience with email servers - plain flat files are the traditional default. Parsing extremely large text files or folders filled to the brim with individual files can be problematic.  A database offers a reasonable compromise between speed and ease of implementing search/spam algorithms.   The problem - as with most of Linux, Windows or Mac - is that the documentation of the software and format is - well it is CRAP.   Programmers are slovenly documenters. I should know.  I am one.  If it weren't, you would be able to configure a different backend without difficulty.

I'd gather that you have run across one of Kmail's many bugs.  At that point, I either restart each account individually and then reset Kmail or recreate them.  I stopped using Kmail because longstanding bugs never seem to get any attention, and to be quite honest, I saw no point in trying to fix them.  KDE completely switches base libraries and frameworks every few years. The last time I downloaded and compiled the release versions of their apps from source - some of them crashed outright and were entirely unusable.  By the time the latest version of KDE becomes usable, the KDE Project has moved on to  creating an entirely new mess.  

I have a similar opinion of Gnome's antics. Rather than run the hamster wheel, I washed my hands of it and went over to XFCE.    If I dabble with KDE again, it will only be from Debian Stable.  The last time I tried installing KDE on Ubuntu - kaccounts dependencies trashed the package consistency.

---

### Post by oygle on 2016-11-05
> **T.J. said:**
> Programmers are slovenly documenters. I should know.  I am one. 

I so totally agree with you there. Having spent about 40 years writing software, it was always more important to get it up and running. Function before form. In reality, whilst the function part/s usually worked well, the form (how it looked) and especially the documentation was very sadly lacking. 

Sorry to hear your experiences with the KDE side of things (and hard work) have not been too favourable. I may still try Thunderbird if the KMail backport doesn't address all the 'annoying' bugs. 

I hadn't heard of XFCE The last release was Feb 2015.

The other day I 'finally' said my last good-bye to Windows, by reformatting a Win XP pro partition. The off grid power data only comes for Windows though, so we make the decision to not have that data. Not everything that runs under win is also flavoured in *nix somewhere, unfortunately. The best email client I ever used was pegasus Mail, and it's a shame the author never ported to Unix flavours at all.

---

### Post by T.J. on 2016-11-05
> I hadn't heard of XFCE The last release was Feb 2015.

That's the point.  They do not release until it is tested, unlike some others.  While XFCE is not perfect and I have encountered the annoying bug or two, it very stable; and generally sane and consistent.   I highly recommend it if you are "old school" as I am.  It can interop between KDE and Gnome by spawning their services in session.


> 
The off grid power data only comes for Windows though, so we make the decision to not have that data. Not everything that runs under win is also flavoured in *nix somewhere, unfortunately. 

I solved that problem by using KVM.  I run Windows 7 under virtualization.  XP can be made to function by the same process.  In this way, you can run whatever version of Windows indefinitely regardless of your hardware upgrades, while isolating it so security holes do not take down the whole system.  Since you are backing up an image file of the hard disk, restores are a breeze.  Believe me, I have never been so happy coding as the day I decided that Windows was nothing more than legacy middleware.


> The best email client I ever used was pegasus Mail, and it's a shame the author never ported to Unix flavours at all.

Pegasus was good.  Thunderbird buried it, because the authors did not adapt to open source.  Terrible shame that.  It is still alive though - if significantly diminished ([http://www.pmail.com/](http://www.pmail.com/)). I do not expect it to survive much longer.  Older versions of Windows are going to disappear now that Microsoft no longer sells 7 or 8 to vendors, and will no longer certify drivers for new processors for anything other than Windows 10.  Once the existing stockpiles of Windows 7 and 8 are gone, that's all done.  The fact that Pegasus still has not made the jump toward 64 bit is not a good sign either. There has been considerable talk even in the world of dropping support for the 32 bit code base among application developers (except for embedded).[URL="http://www.pmail.com/"]

[/URL]

---

### Post by oygle on 2016-11-05
> **T.J. said:**
> That's the point.  They do not release until it is tested, unlike some others.  While XFCE is not perfect and I have encountered the annoying bug or two, it very stable; and generally sane and consistent.   I highly recommend it if you are "old school" as I am.  It can interop between KDE and Gnome by spawning their services in session.

Yes I'm old school. Started IT in 1972 when we used paper tape, punch cards, magnetic tape reels for master files, and it took 2 Honeywell engineers to carry in 32 Mb of memory.  lol

Stable is better than buggy and unstable, so XFCE would be good for that reason. 

> **T.J. said:**
> I solved that problem by using KVM.  I run Windows 7 under virtualization.  XP can be made to function by the same process.  In this way, you can run whatever version of Windows indefinitely regardless of your hardware upgrades, while isolating it so security holes do not take down the whole system.  Since you are backing up an image file of the hard disk, restores are a breeze.  Believe me, I have never been so happy coding as the day I decided that Windows was nothing more than legacy middleware.

I do have windows 8 or 9 somewhere on a CD; it came with the laptop. Have hesitated to run that laptop as dual boot (Kubuntu - primary and Win as secondary) because I saw so many posts where a Windows install wants to 'take over' and be primary partition. But you are talking KVM. I have no experience with that, but if it can completely 'isolate' the Windows OS, that would be great. We don't _really_ need the stats from the inverter, but it would be great to match watts produced to watts used, etc. The people who supply the software don't want to make it available in Linux.  :(

Regards Pegasus. This doc is over 11 years old now - [http://www.pmail.com/sundry/pmlinux.htm](http://www.pmail.com/sundry/pmlinux.htm)

Thanks  :)

---

### Post by T.J. on 2016-11-06
> **oygle said:**
> 

I do have windows 8 or 9 somewhere on a CD; it came with the laptop. Have hesitated to run that laptop as dual boot (Kubuntu - primary and Win as secondary) because I saw so many posts where a Windows install wants to 'take over' and be primary partition. But you are talking KVM. I have no experience with that, but if it can completely 'isolate' the Windows OS, that would be great. We don't _really_ need the stats from the inverter, but it would be great to match watts produced to watts used, etc. The people who supply the software don't want to make it available in Linux.  :(
  
  
A copy of Windows sold with a computer is normally OEM licensed, and can't be used for virtualization without breach of contract.   That said, it is very helpful.  The hardware itself has been capable of running multiple OS's since the late 80's.  It creates a virtual computer where the OS can be installed.  It cannot touch data on the host system unless you allow it.  Since the guest OS is actually running on virtual hardware, you can change the actual physical hardware and it will not know the difference.  So Windows will work indefinitely.

---

### Post by oygle on 2016-12-05
> **acheronuk said:**
> We will hopefully have an updated version of kmail in the kubuntu backports ppa in the next few weeks. 

Packaging and testing of backports got a little sidelined with work on the release of Yakkety, but I hope things can now catch up somewhat.

Can you please advise the status of the KMail backport ?

> **T.J. said:**
> A copy of Windows sold with a computer is normally OEM licensed, and can't be used for virtualization without breach of contract.   That said, it is very helpful.  The hardware itself has been capable of running multiple OS's since the late 80's.  It creates a virtual computer where the OS can be installed.  It cannot touch data on the host system unless you allow it.  Since the guest OS is actually running on virtual hardware, you can change the actual physical hardware and it will not know the difference.  So Windows will work indefinitely.

I didn't receive any media with the laptop, just Win 8 preloaded. So, I later purchased from Dell - "Windows 8.1 OEM - Deployment Solution Media Kit - OM Kit-DVD". Does that still indicate I can't use that Win 8.1 for KVM ?

---

### Post by acheronuk on 2016-12-06
> **oygle said:**
> Can you please advise the status of the KMail backport ?

For Xenial 16.04 LTS, a backport of kmail from 15.12.3 to 16.04.3 (5.2.3) is currently in our landing ppa for testing.

This is part of a backport of all the KDE applications, plus an updated Qt (5.6.1) and Plasma (5.8.4); so with all that being updated we are just being a bit cautious with testing before we let that go to the [backports ppa]("https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports") itself.

---

### Post by oygle on 2016-12-07
> **acheronuk said:**
> For Xenial 16.04 LTS, a backport of kmail from 15.12.3 to 16.04.3 (5.2.3) is currently in our landing ppa for testing.

This is part of a backport of all the KDE applications, plus an updated Qt (5.6.1) and Plasma (5.8.4); so with all that being updated we are just being a bit cautious with testing before we let that go to the [backports ppa]("https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports") itself.

Okay thanks for the update. Does that mean when it is released I will have to update my sources to get KMail from the backport ppa, or will the backport eventually flow back into the official updates for Xenial 16.04 ?

Interesting that there is a Plasma update also. Plasma crashes many times each day on this 16.04.1

---

### Post by oygle on 2016-12-07
> **T.J. said:**
> A copy of Windows sold with a computer is normally OEM licensed, and can't be used for virtualization without breach of contract.

Can you please view [my post]("https://ubuntuforums.org/showthread.php?t=2345585&p=13579633#post13579633") and provide some clarification and feedback ?

---

### Post by acheronuk on 2016-12-07
> **oygle said:**
> Okay thanks for the update. Does that mean when it is released I will have to update my sources to get KMail from the backport ppa, or will the backport eventually flow back into the official updates for Xenial 16.04 ?

Interesting that there is a Plasma update also. Plasma crashes many times each day on this 16.04.1

It will be in the kubuntu backports ppa

[https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports](https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports)

Update to Plasma 5.8.4 are also likely to land with it. Hopefully.

---

### Post by oygle on 2016-12-07
> **acheronuk said:**
> It will be in the kubuntu backports ppa

[https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports](https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports)

Update to Plasma 5.8.4 are also likely to land with it. Hopefully.

Thanks, I have included that backports repository in my updates.  :)

Now, nearly 300 updates !!  Hope it's 'safe' to proceed.  :)

---

### Post by oygle on 2016-12-08
Regarding the backports ppa ...

> You can update your system with _unsupported_ packages from this _untrusted_ PPA by adding **ppa:kubuntu-ppa/backports** to your system's Software Sources.

Can someone please explain the "unsupported" and "untrusted" aspects ? Is it safe to install the updates from the ppa ?  Will these updates eventually flow back into the official updates ?

---

### Post by acheronuk on 2016-12-08
Please see the info on kubuntu PPAs here:

[https://community.kde.org/Kubuntu/PPAs](https://community.kde.org/Kubuntu/PPAs)

---

### Post by oygle on 2016-12-09
> **acheronuk said:**
> Please see the info on kubuntu PPAs here:

[https://community.kde.org/Kubuntu/PPAs](https://community.kde.org/Kubuntu/PPAs)

Thanks for that. I guess the worst thing that can happen is that I apply the updates and then my Kubuntu may break.  lol

I see that Kubuntu 16.10 (Yakkety Yak) is released. Possibly a lot of the Kubuntu backports re KMail, Plasma, etc are contained within that release ?

---

### Post by acheronuk on 2016-12-10
> **oygle said:**
> I see that Kubuntu 16.10 (Yakkety Yak) is released. Possibly a lot of the Kubuntu backports re KMail, Plasma, etc are contained within that release ?

The KDE applications are, yes.

16.10 also has Plasma 5.7.5 vs Xenial's 5.5.5 (or 5.6.5) in the backports ppa.

However, as said if /when we move our testing packages into the backports ppa, that will be plasma 5.8.4 for both 16.10 and 16.04.

So if you can have a little more patience while we test, there should be no reason to jump ship from whatever version you currently have. Unless of course you want something else non-kubuntu that is only in 16.10 etc

---

### Post by oygle on 2017-01-08
Plasma crashes at least 30 times a day and KMail at least that many times. I assume if I don't want to add the Kubuntu backports or ppa, then I should go to vers 16.10 , is that correct ?

---

### Post by T.J. on 2017-01-09
> **oygle said:**
> Plasma crashes at least 30 times a day and KMail at least that many times. I assume if I don't want to add the Kubuntu backports or ppa, then I should go to vers 16.10 , is that correct ?



Well, if you want my advice - which you are free to absolutely ignore - if you want a stable KDE, you should use Debian 8, instead of Kubuntu.  I'm not criticizing Kubuntu, rather I am simply acknowledging that Plasma 5 is still under development by the KDE developers upstream, and in spite of Kubuntu's best efforts, it still has a number of bugs to work out, especially with Kwin's compositor.

Debian 8 maintains KDE 4, which is probably the most stable version of KDE available at present.

If you want to stick with Kubuntu I recommend 16.04 LTS, and perhaps disabling the compositor.  Either way, Kmail has a few longstanding bugs - which you can usually work around.

---

### Post by oygle on 2017-01-09
> **T.J. said:**
> Well, if you want my advice - which you are free to absolutely ignore - if you want a stable KDE, you should use Debian 8, instead of Kubuntu. 

As time goes on, Debian 8 is becoming more attractive. Will it run KMyMoney, LibreOffice, Dolphin. VLC, KMail, Keepassx, Filezilla,etc ?

I assume I would be going backwards, in terms of versions though.

> **T.J. said:**
> If you want to stick with Kubuntu I recommend 16.04 LTS, and perhaps disabling the compositor.  Either way, Kmail has a few longstanding bugs - which you can usually work around.

If Thunderbird or some other email client can do all that KMail can do, then I'd change over. To me, KMail is pretty much 'broken' in Kubuntu 16.04.1

* Constantly hangs or resource problems. ONLY workaround is exit KMail, then **akonadictl restart**, then back into KMail and hope it works. But many times it doesn't, so exit KMail, restart ......

* Searching does **NOT** work at all

* There are ghost emails in a number of folders ?

* Folders are often not updated

That's seems like 'broken' to me.  :(

---

### Post by oygle on 2017-04-25
Having major problems with KMail/akonadi , and need to contact akonadi support. Have tried the KDE forums to no avail.

Does anyone know who I can contact in regards to akonadi support please ? The issue mainly is to get the akonadi db data in synch with the file system.

---

### Post by oygle on 2017-04-29
Whilst the problems with KMail/akonadi are not fixed, there is finally a workaround solution - [https://ubuntuforums.org/showthread.php?t=2359701&p=13639546#post13639546](https://ubuntuforums.org/showthread.php?t=2359701&p=13639546#post13639546)

Also, this thread as a reference to the major problems - [https://ubuntuforums.org/showthread.php?t=2349281](https://ubuntuforums.org/showthread.php?t=2349281)

---

