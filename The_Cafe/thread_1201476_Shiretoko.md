---
title: "Shiretoko"
date: 2009-07-01
forum: The Cafe
---

### Post by 6205 on 2009-07-01
I am trying to install latest Firefox 3.5 in jaunty, but it seem that it's harder than i though. Every possiple <snip> PPA repository install some 'Shiretoko' browser and i am unable to find anywhere properly branded Firefox..

Is this so big problem for this distibution to have basic things done. Even damn openSUSE has One-Click install of proper Firefox 3.5 available from day One, but Ubuntu noooo, Ubuntu must simply piss off their users..

If somebody has link to 'normal' repository without all that shire-crap-toko i am waiting.

---

### Post by alphacrucis2 on 2009-07-01
> **6205 said:**
> I am trying to install latest Firefox 3.5 in jaunty, but it seem that it's harder than i though. Every possiple fu*king PPA repository install some 'Shiretoko' browser and i am unable to find anywhere properly branded Firefox..

Is this so big problem for this distibution to have basic things done. Even damn openSUSE has One-Click install of proper Firefox 3.5 available from day One, but Ubuntu noooo, Ubuntu must simply piss off their users..

If somebody has link to 'normal' repository without all that shire-crap-toko i am waiting.

You will have to wait until a backport is done.

---

### Post by KegHead on 2009-07-01
Hi!

I updated with sudo apt-get install firefox 3.5

No problems.

KegHead

---

### Post by colau on 2009-07-01
> **KegHead said:**
> Hi!

I updated with sudo apt-get install firefox 3.5

No problems.

KegHead
```

sudo apt-get install [COLOR="Red"]firefox-3.5[/COLOR]

```
[http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm](http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm)

---

### Post by VastOne on 2009-07-01
> **colau said:**
> ```

sudo apt-get install [COLOR="Red"]firefox-3.5[/COLOR]

```
[http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm](http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm)

All these are doing is putting Shiretoko on. As the OP said, these have suggested that the final of 3.5 would be installed, but both of your links and all how-tos I have tried is only and still loading Shiretoko

Edit: It is possible that because I am 64 bit, the backport does not have the 64 bit as of yet

---

### Post by 6205 on 2009-07-01
I have 32-bit Jaunty and it's the same. Shiretoko everywhere and i don't understand why.. This is simply a neverending problem with Ubuntu..

---

### Post by joemun on 2009-07-01
gksudo firefox

and upgrade from Help as in windows...so far no problems at all...

---

### Post by VastOne on 2009-07-01
> **joemun said:**
> gksudo firefox

and upgrade from Help as in windows...so far no problems at all...

Nope....

Says I am up to date and to check back periodically

I would guess you are 32 bit?

---

### Post by abhi_69 on 2009-07-01
i think ubuntu is a good distro, but, sometimes it really make us frustrated. i still using firefox 3.0.11 in ubuntu 9.04 becoz there is no update of firefox 3.5 in official repo still & even ubuntu-mozilla-daily build team repo. (it still installs minefield 3.5 browser, not firefox 3.5 final)...but, my frnds using other distros like openSUSE or Fedora already get latest firefox 3.5. 
this matter really making me unhappy. i want to use firefox 3.5 final version in ubuntu 9.04....i love ubuntu, but, it should concern about such kind of issues....its not a good exeperience for us to wait longer for a new version when other people already using new version.

---

### Post by LowSky on 2009-07-01
You could always download the source code and install it that way... so stop complaining if the officially labels verison is not in the repos, testing takes time!

Shiretoko is the code name for Firefox 3.5, so dont worry it works. Until a proper backport is completed your stuck with the Shiretoko name, which is nothing to worry about... heck I'm on Arch Linux and it never uses the Firefox name.

---

### Post by Synt4x_3rr0r on 2009-07-01
Mozilla's license is a little stupid. If a distro compiles it themselves they can't call it Firefox and they can't use they official logos either. So that's why it's called Shiretoko.
I don't know how Ubuntu got the permission to use the Firefox name with 3.0 but they did somehow. So just wait till they get it for 3.5 as well.

---

### Post by ShadowWraith on 2009-07-01
If you want to use firefox 3.5 before it's officially in the repositories, you can just go to [http://www.mozilla.com/en-US/firefox/upgrade.html](http://www.mozilla.com/en-US/firefox/upgrade.html) , download firefox, untar the package, and run the firefox bin inside. Just make sure that when it asks you to make firefox 3.5 your default browser you answer "no"; you should wait until you get the official package before making it default.

Anyway, cut the ubuntu guys some slack. They have to do a comprehensive quality check on Firefox 3.5 before they allow it into the official repository since it's such a crucial piece of software. Give them a couple more days or even a week, it'll get there.

---

### Post by t4thfavor on 2009-07-01
I compiled it from source, and I also got Shiretoko. Now I am having trouble getting rid of it as the sudo make uninstall seems broken or non-existent.

---

### Post by mcduck on 2009-07-01
> **abhi_69 said:**
> i think ubuntu is a good distro, but, sometimes it really make us frustrated. i still using firefox 3.0.11 in ubuntu 9.04 becoz there is no update of firefox 3.5 in official repo still & even ubuntu-mozilla-daily build team repo. (it still installs minefield 3.5 browser, not firefox 3.5 final)...but, my frnds using other distros like openSUSE or Fedora already get latest firefox 3.5. 
this matter really making me unhappy. i want to use firefox 3.5 final version in ubuntu 9.04....i love ubuntu, but, it should concern about such kind of issues....its not a good exeperience for us to wait longer for a new version when other people already using new version.

Actually the default policy is that you should not be getting Firefox 3.5 until the next Ubuntu release.

By default, packages are updated after release only to provide security updates and to fix serious bugs, never just to add new features.

If you want to always have the latest and greatest program versions you should be using some rolling-release distribution, not Ubuntu. Or be prepared to install the unsupported packages on your own.

---

### Post by abhi_69 on 2009-07-01
> **LowSky said:**
> You could always download the source code and install it that way... so stop complaining if the officially labels verison is not in the repos, testing takes time!

Shiretoko is the code name for Firefox 3.5, so dont worry it works. Until a proper backport is completed your stuck with the Shiretoko name, which is nothing to worry about... heck I'm on Arch Linux and it never uses the Firefox name.
but, i came to know from an internet article that, ubuntu 9.04 repo. will not update to firefox 3.5 & firefox 3.5 will be available only in next release of ubuntu (karmic koala/9.10). this make me afraid. is it true?
what about this issue?

---

### Post by t4thfavor on 2009-07-01
Thats how its intended to work, they don't introduce new apps between releases. You can however install it from source, or another repo (such as backports).

---

### Post by abhi_69 on 2009-07-01
> **mcduck said:**
> Actually the default policy is that you should not be getting Firefox 3.5 until the next Ubuntu release.

By default, packages are updated after release only to provide security updates and to fix serious bugs, never just to add new features.

If you want to always have the latest and greatest program versions you should be using some rolling-release distribution, not Ubuntu. Or be prepared to install the unsupported packages on your own.
yes, i see the same in that article. firefox 3.5 will be available in ubuntu 9.10 only. 
we hav to wait for ubuntu 9.10......
i enable jaunty-backport (unsupported) repo. in synaptic. will it help me to get firefox 3.5?
can anyone inform me?

---

### Post by Synt4x_3rr0r on 2009-07-01
> **t4thfavor said:**
> I compiled it from source, and I also got Shiretoko. Now I am having trouble getting rid of it as the sudo make uninstall seems broken or non-existent.

You can add the flag "ac_add_options --with-branding=browser/branding/official" in your mozconfig file and recompile it and it will be called Firefox. It's just if you are going to redistribute it that you can't call it Firefox.

Also, get checkinstall from the repos and use that instead of make install. Just type "sudo checkinstall" instead and it will make a .deb package that is easy to remove and upgrade.

---

### Post by moster on 2009-07-01
I am only not sure why someone do not make .deb file so less experienced users can install it problem free.

---

### Post by Chronon on 2009-07-01
> **mcduck said:**
> Actually the default policy is that you should not be getting Firefox 3.5 until the next Ubuntu release.

Could it be that's not being followed in this case?

[QUOTE=https://help.ubuntu.com/community/FirefoxNewVersion]
To install Firefox 3.5 on Jaunty or Karmic, install the following package: firefox-3.5. It normally takes a few hours or days for new versions of Firefox to be tested and packaged this package currently installs a recent beta version.[/QUOTE]

and

[QUOTE=http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html]
It’s definitely hot news today: firefox 3.5 was released – you can finally stop holding your breath!

Also checkout the release notes or get an overview on what is new in this great release.

So after all the partying, you might end up wondering: “Great, Where can I get it for ubuntu now?”

As usual, the answer depends on what Ubuntu version you are running:

Karmic and Jaunty users:

    * just install the currently available firefox-3.5 package from universe and wait. The final bits will be there really soon.
    * If you want to have them earlier, enable ubuntu-mozilla-security PPA where the bits will land first. Enabling this PPA also will help us test security updates before they get rolled to the masses in future; so if you don’t mind a slightly increased risk of breakage keep this enabled; in the unlikely event that you see a regression from this archive, instantly report them to the ubuntu mozillateam.
    * If the security PPA is still not bleeding edge enough for you, go for the daily PPA, a great service that is run by ubuntu mozillateam for quite some time now.
[/QUOTE]

So, it seems that the firefox-3.5 package in the Jaunty repositories will be updated to point to the final release version once everything is tested.  

I got impatient and downloaded it yesterday from the mozilla site.  It's noticeably faster (I hadn't tried any of the beta versions before now).

---

### Post by VastOne on 2009-07-01
> **LowSky said:**
> You could always download the source code and install it that way... so stop complaining if the officially labels verison is not in the repos, testing takes time!

Shiretoko is the code name for Firefox 3.5, so dont worry it works. Until a proper backport is completed your stuck with the Shiretoko name, which is nothing to worry about... heck I'm on Arch Linux and it never uses the Firefox name.

I agree with you completely, but even dloading the source has kept me at Shiretoko and again, it may be that there is no 64 bit version yet..I honestly do not know

---

### Post by wirelessmonkey on 2009-07-01
I'm using 64 bit Kubuntu Jaunty, with default repos, and aptitude install firefox-3.5 installed the proper version...

---

### Post by VastOne on 2009-07-01
> **wirelessmonkey said:**
> I'm using 64 bit Kubuntu Jaunty, with default repos, and aptitude install firefox-3.5 installed the proper version...

And it is branded Firefox 3.5 and not Shiretoko? Because that is exactly how I have done all 6 of my test machines and have only gotten Shiretoko each and every time

---

### Post by abhi_69 on 2009-07-01
@chronon, thanz to share this with us. this give me some kind of hope in my mind after lots of frustration about new version of firefox in jaunty. i hope soon we get firefox 3.5 final version in official ubuntu 9.04 repo. & we can easily install & use it in ubuntu 9.04 jaunty.
now, i am waiting for the day in which we get ubuntu build of firefox 3.5 from official repo.
.................

---

### Post by moster on 2009-07-01
> **Chronon said:**
> Could it be that's not being followed in this case?
So, it seems that the firefox-3.5 package in the Jaunty repositories will be updated to point to the final release version once everything is tested.  

I got impatient and downloaded it yesterday from the mozilla site.  It's noticeably faster (I hadn't tried any of the beta versions before now).

I got impatient too because firefox 3.0 very slow on my computer. What they need to test? Windows users just download and run damn installation and have firefox in no time. I spend hours running around forum because "shiroko" and some bug on top that confuse me.

This is no good way dealing with things...

edit:
until linux in general get a proper package management we will not be taken seriously. This is too stupid reason for frustration.

---

### Post by Chronon on 2009-07-01
> **wirelessmonkey said:**
> I'm using 64 bit Kubuntu Jaunty, with default repos, and aptitude install firefox-3.5 installed the proper version...

It's possible they were updated, but I just reloaded the package list in Synaptics and it shows as the beta version still.  Only an observation since the mirror I'm looking at may not have gotten the update yet.  If the package has been updated to the final version then all of the mirrors should start to show the change in the next hours.

---

### Post by abhi_69 on 2009-07-01
> **moster said:**
> I got impatient too because firefox 3.0 very slow on my computer. What they need to test? Windows users just download and run damn installation and have firefox in no time. I spend hours running around forum because "shiroko" and some bug on top that confuse me.

This is no good way dealing with things...
u hav to wait...u know every software launch in windows first (i.e. google chrome, still no stable version for linux) than linux...becoz, linux need more test than windows. so, perhaps ubuntu development team taking time for this purpose.
i am also impatient, but what can i do???? i try many method to get it now but ended up with either shiretoko or lots of bugs & errors.
so....wait...........wait.........wait

---

### Post by akakingess on 2009-07-01
> **moster said:**
> I got impatient too because firefox 3.0 very slow on my computer. What they need to test? Windows users just download and run damn installation and have firefox in no time. I spend hours running around forum because "shiroko" and some bug on top that confuse me.

This is no good way dealing with things...

edit:
until linux in general get a proper package management we will not be taken seriously. This is too stupid reason for frustration.
Those same Windows users spend the next six months downloading security/(insert problem here) patches that should have been addressed before release. That's just my opinion, I know almost everyone out there wants the newest fastest best right NOW, but I am one of the few that feel that the developers know what they are doing and am more than willing to wait and be patient. Heck, I have been nothing but happy with Ubuntu thus far, so why fix something that's not broke?

akakingess

---

### Post by VastOne on 2009-07-01
> **moster said:**
> I got impatient too because firefox 3.0 very slow on my computer. What they need to test? Windows users just download and run damn installation and have firefox in no time. I spend hours running around forum because "shiroko" and some bug on top that confuse me.

This is no good way dealing with things...

edit:
until linux in general get a proper package management we will not be taken seriously. This is too stupid reason for frustration.

Or too stupid of a reason to be frustrated...Looking at it from a half glass full, mind you...

I have no qualms with this "improper package management" I can be patient and find the way that finally fits or use the Shiretoko which is working flawlessly, it is just blue and not called FF 3.5

---

### Post by Chronon on 2009-07-01
> **VastOne said:**
> 
I have no qualms with this "improper package management" I can be patient and find the way that finally fits or use the Shiretoko which is working flawlessly, it is just blue and not called FF 3.5

I agree with you.  If I had known (at the time) that the beta package would be updated to the final version I would have just installed that.  I used IceWeasel on Debian and don't really think branding is so important.

---

### Post by GCFreak on 2009-07-01
To people who are complaining about how people here are not getting it the same time as Windows, Mac and other Linux distros, I thought it was logical to scrutinise and test programs before they went on the repos. Some people here obviously do not share my opinion, it seems. I haven't tried installing 3.5 on any of my Ubuntu installations yet, but for something to be put on the repos, it would be nice if it was assured to be stable on the distro in question...

---

### Post by moster on 2009-07-01
> **VastOne said:**
> Or too stupid of a reason to be frustrated...Looking at it from a half glass full, mind you...

I have no qualms with this "improper package management" I can be patient and find the way that finally fits or use the Shiretoko which is working flawlessly, it is just blue and not called FF 3.5

Sorry, I little overreacted. But, It would save me today lot of time that beside install.exe for windows there was install.deb (or whatever) was for linux.
Totally confuse me "shiroko 3.5.1. pre" and icon was blue. I was like WTF? That was name of final version firefox? I must be having wrong version.
I downloaded from mozilla too, but that version was crashing when full screen on youtube, that I connect with I do something wrong. After shiroko crash too I realise I have some other problem. Bug was in nvidia driver, I repair it now...

I have bad taste in my mouth from everything, you know.. how to say..

edit:
Firefox suppose to be at home in linux. So it was not suppose to be 3x harder to get it working then in stinkin vista.

---

### Post by akakingess on 2009-07-01
> **moster said:**
> Sorry, I little overreacted. But, It would save me today lot of time that beside install.exe for windows there was install.deb (or whatever) was for linux.
Totally confuse me "shiroko 3.5.1. pre" and icon was blue. I was like WTF? That was name of final version firefox? I must be having wrong version.
I downloaded from mozilla too, but that version was crashing when full screen on youtube, that I connect with I do something wrong. After shiroko crash too I realise I have some other problem. Bug was in nvidia driver, I repair it now...

I have bad taste in my mouth from everything, you know.. how to say..

edit:
Firefox suppose to be at home in linux. So it was not suppose to be 3x harder to get it working then in stinkin vista.
Glad to hear you found the root of the problem and are up and running. Hope all is well and stays that way for you.

akakingess

---

### Post by moster on 2009-07-01
> **akakingess said:**
> Glad to hear you found the root of the problem and are up and running. Hope all is well and stays that way for you.

akakingess

Thanks, I appreciate it. :)  I will not bloat this thread more, I said what was on my chest...

---

### Post by VastOne on 2009-07-01
> **akakingess said:**
> glad to hear you found the root of the problem and are up and running. Hope all is well and stays that way for you.

Akakingess

+1

---

### Post by VastOne on 2009-07-01
> **moster said:**
> Thanks, I appreciate it. :)  I will not bloat this thread more, I said what was on my chest...

It is never easy, these roads we travail, but the journey is fun and usually worth the walk!

---

### Post by xavierp94 on 2009-07-01
You can always try to use Ubuntuzilla. Its a script that downloads Mozilla Firefox 3.5 and replaces it with your version of Firefox and cleans up the installation. It also gives you an option to reinstall the old Firefox that you had. 
[www.ubuntuzilla.wiki.sourceforge.net](www.ubuntuzilla.wiki.sourceforge.net)

---

### Post by t4thfavor on 2009-07-01
Someone mentioned above that there is a configure directive that will let you compile the branding, and icons into firefox, so as not to get Shiretoko anymore. I made the mistake of not doing that, and am still having a hard time adjusting to the new icon :) Glad everything is figured out, and hope it stays that way.

---

### Post by moster on 2009-07-01
Thanks guys for caring. You just sometimes need help from someone :)

---

### Post by luigi_mb on 2009-07-01
You can download the Firefox v3.5 (binaries) directly from the Mozilla site:

[http://www.mozilla.com/en-US/firefox/firefox.html](http://www.mozilla.com/en-US/firefox/firefox.html)

Unpack the archive in your home folder

```

cd ~
mv /full-path-to-folder-where-Firefox-was-downloaded/firefox-3.5.tar.bz2 ./
tar xvf firefox-3.5.tar.bz2

```

Run it

```

firefox/firefox

```

Plugins can be copied directly (or simlinked, depending on the plugin) to firefox/plugins.

/luigi

---

### Post by steveneddy on 2009-07-01
Shiretoko IS Firefox 3.5

---

### Post by VastOne on 2009-07-01
> **steveneddy said:**
> Shiretoko IS Firefox 3.5

We know

---

### Post by VastOne on 2009-07-01
> **luigi_mb said:**
> You can download the Firefox v3.5 (binaries) directly from the Mozilla site:

[http://www.mozilla.com/en-US/firefox/firefox.html](http://www.mozilla.com/en-US/firefox/firefox.html)

Unpack the archive in your home folder

```

cd ~
mv /full-path-to-folder-where-Firefox-was-downloaded/firefox-3.5.tar.bz2 ./
tar xvf firefox-3.5.tar.bz2

```

Run it

```

firefox/firefox

```

Plugins can be copied directly (or simlinked, depending on the plugin) to firefox/plugins.

/luigi

Following this exactly (yet again) All it loads is 3.011, my old version

---

### Post by lovinglinux on 2009-07-01
> **VastOne said:**
> Following this exactly (yet again) All it loads is 3.011, my old version

Follow [this](http://www.psychocats.net/ubuntu/firefox) instead or try one of the other 2 methods described in the **Installing Other Versions** section of the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by VastOne on 2009-07-02
> **lovinglinux said:**
> Follow [this](http://www.psychocats.net/ubuntu/firefox) instead or try one of the other 2 methods described in the **Firefox Alternatives & Newer Versions** section of the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

I dloaded the script and it worked perfectly but....

I have no connection with 3.5

I am now in Shiretoko writing this but in 3.5 all I get is connection errors...

Any thoughts?

---

### Post by lovinglinux on 2009-07-02
> **VastOne said:**
> I dloaded the script and it worked perfectly but....

I have no connection with 3.5

I am now in Shiretoko writing this but in 3.5 all I get is connection errors...

Any thoughts?

Could be ipv6 or bad connection settings in Firefox (solution in the same tutorial)

Could be an addon messing with the connection. Try running it in safe mode:

```

firefox-3.5 -safe-mode
```

Could be something else...

---

### Post by abhi_69 on 2009-07-02
i have the same problem. this script download firefox 3.5 for me. everything seems ok on 1st look. but....i can't connect to any site using this. moreover, some of my plugins not working under it. so,............another method to get firefox 3.5 failed.
what can we do now? wait for official ubuntu build?

---

### Post by lovinglinux on 2009-07-02
> **abhi_69 said:**
> i have the same problem. this script download firefox 3.5 for me. everything seems ok on 1st look. but....i can't connect to any site using this. moreover, some of my plugins not working under it. so,............another method to get firefox 3.5 failed.
what can we do now? wait for official ubuntu build?

Better methods:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

They both worked for me pretty fine. Actually, I haven't tried the one you asked for.

---

### Post by VastOne on 2009-07-02
> **lovinglinux said:**
> Could be ipv6 or bad connection settings in Firefox (solution in the same tutorial)

Could be an addon messing with the connection. Try running it in safe mode:

```

firefox-3.5 -safe-mode
```

Could be something else...

It was the ipv6.....

Thanks I appreciate your help and the tutorial...It is well done

---

### Post by lovinglinux on 2009-07-02
> **VastOne said:**
> It was the ipv6.....

Thanks I appreciate your help and the tutorial...It is well done

You are welcome. I'm glad the tutorial is helping. :popcorn:

---

### Post by ronaldprettyman on 2009-07-02
> **6205 said:**
> I am trying to install latest Firefox 3.5 in jaunty, but it seem that it's harder than i though. Every possiple <snip> PPA repository install some 'Shiretoko' browser and i am unable to find anywhere properly branded Firefox..

Is this so big problem for this distibution to have basic things done. Even damn openSUSE has One-Click install of proper Firefox 3.5 available from day One, but Ubuntu noooo, Ubuntu must simply piss off their users..

If somebody has link to 'normal' repository without all that shire-crap-toko i am waiting.
Why not try going to Firefox's offical website and downloading the genric linux binaries. It use to be the only way to do it back in the days of Mozilla and Firefox 1.0

---

### Post by abhi_69 on 2009-07-02
> **lovinglinux said:**
> Better methods:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

They both worked for me pretty fine. Actually, I haven't tried the one you asked for.
better i will wait until it comes to official repo. thanz for reply......

---

### Post by lovinglinux on 2009-07-02
> **abhi_69 said:**
> better i will wait until it comes to official repo. thanz for reply......

Is it going to be there? I'm not sure it will.

---

### Post by abhi_69 on 2009-07-02
well........understand......
now i am using flock, seamonkey & opera 10 beta in ubuntu 9.04.
becoz, those 3 seems faster than firefox 3.0.11. hope opera 10 final version will release soon (beta version available now) & i can use it directly in ubuntu 9.04. i like opera's policy becoz they provide various distro specific package format (like- .deb, .rpm etc.) for their browser. so, its easy for any linux distro user to upgrade to latest one as soon as it released without any problem.

---

### Post by lovinglinux on 2009-07-02
> **abhi_69 said:**
> well........understand......
now i am using flock, seamonkey & opera 10 beta in ubuntu 9.04.
becoz, those 3 seems faster than firefox 3.0.11. hope opera 10 final version will release soon (beta version available now) & i can use it directly in ubuntu 9.04. i like opera's policy becoz they provide various distro specific package format (like- .deb, .rpm etc.) for their browser. so, its easy for any linux distro user to upgrade to latest one as soon as it released without any problem.

Well, Opera doesn't have all the extensions I like. Besides, after compiling Firefox 3.5 from source, with optimizations for my processor, it is running 24% faster than Opera 10. If I load a bunch of extensions, it runs with the same performance as Opera 10. Check my [benchmarks](http://service.futuremark.com/peacekeeper/index.action) below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=119664&stc=1&d=1246476466[/IMG]

---

### Post by abhi_69 on 2009-07-02
good.....
it looks well. but, what about plugins? mainly about totem-mozilla or vlc-plugins....r all these plugins working well with compiled firefox? which name u get under Applications->internet? firefox or Shiretoko? can it replace my ubuntu build firefox (version 3.0.11)?
how u compile from source without problem? how can i optimize it for my processor? is there any other problem with compiled version?
plz. give me details. i want to test this thing out. compile from source is the only method i still not tested to get new firefox 3.5......
can u help me?
thanz in advance.

---

### Post by lovinglinux on 2009-07-02
> **abhi_69 said:**
> it looks well. but, what about plugins? mainly about totem-mozilla or vlc-plugins....r all these plugins working well with compiled firefox?

I use gecko-mediaplayer plugin and works like a charm. So far the only problem I have experienced is with YouTube on fullscreen. It crashes Firefox. I have just noticed that, so I still don't know what's causing it. Besides, flash sucks on Jaunty.

> **abhi_69 said:**
> which name u get under Applications->internet? firefox or Shiretoko? 

Firefox 3.5 :)

> **abhi_69 said:**
> can it replace my ubuntu build firefox (version 3.0.11)

No. The compilation process installs a new version, but it uses the same profile directory and automatically update the symlinks used by launchers, so you don't even notice Firefox 3.0.11 after the compilation, but you are still able to open it if something goes wrong with the compiled version. 

> **abhi_69 said:**
> how u compile from source without problem? how can i optimize it for my processor? is there any other problem with compiled version?

Follow my tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Scroll down to "Compiling Firefox".

This is my first compiled Firefox. I didn't have any problems compiling it, on both times I did it (just for practice). The only problem I have so far is this issue on YouTube. 

> **abhi_69 said:**
> plz. give me details. i want to test this thing out. compile from source is the only method i still not tested to get new firefox 3.5......
can u help me?
thanz in advance.

Yes. The tutorial is pretty straight forward. The only part that you could need to some help is the creation of the mozconfig file. That requires some reading. Anyway, as I said, this was my first compilation and I did it in a couple of hours. The compiling process itself took 1 hour. Nothing went wrong. I'm amazed :) I tried to write the tutorial to be as simple as possible, following exactly what I did. So, give it a try and if you get stuck just ask and we try to figure it out.

---

### Post by moster on 2009-07-02
> **lovinglinux said:**
> I use gecko-mediaplayer plugin and works like a charm. So far the only problem I have experienced is with YouTube on fullscreen. It crashes Firefox. I have just noticed that, so I still don't know what's causing it. Besides, flash sucks on Jaunty.


That crash I had with every version of firefox 3.6. I solve it with this simple instructions in this thread. Is is connected with nvidia drivers somehow... here it goes..

[http://ubuntuforums.org/showthread.php?p=7487421]("http://ubuntuforums.org/showthread.php?p=7487421")

---

### Post by lovinglinux on 2009-07-02
> **moster said:**
> That crash I had with every version of firefox 3.6. I solve it with this simple instructions in this thread. Is is connected with nvidia drivers somehow... here it goes..

[http://ubuntuforums.org/showthread.php?p=7487421]("http://ubuntuforums.org/showthread.php?p=7487421")

Thanks a lot for the tip and link. Unfortunately, I don't have the file that should be edited :)  But I will ask for help there.

---

### Post by moster on 2009-07-02
> **lovinglinux said:**
> Thanks a lot for the tip and link. Unfortunately, I don't have the file that should be edited :)  But I will ask for help there.

I too have no "firefox.sh", I have "firefox-3.5" right in firefox directory.

I post bellow how look begining of my file. You should only add second line from top in yours. It must work :)

```

#!/bin/sh
export LD_PRELOAD=/usr/lib/libGL.so.1
# Firefox launcher containing a Profile migration helper for
# temporary profiles used during alpha and beta phases.

# Authors:
#  Alexander Sack <asac@jwsdot.com>
#  Fabien Tassin <fta@sofaraway.org>
#  Steve Langasek <steve.langasek@canonical.com>
# License: GPLv2 or later

## profile migration disabled for now, instead, resurrect the previous code

# If there's still no ~/mozilla/firefox-3.5 profile, try to find a previous
# firefox profile and initialize with that.
# If nothing is found, we'll go for a fresh run and let firefox create a
# default profile for us.

MOZDIR=$HOME/.mozilla
LIBDIR=/usr/lib/firefox-3.5.1pre
APPVER=3.5
META_NAME=
GDB=/usr/bin/gdb
DROPPED=abandoned

NAME="$0"
if [ "x$META_NAME" != "x" ] ; then
  NAME="${NAME%%-$APPVER}"
................
.........

```

---

### Post by lovinglinux on 2009-07-02
> **moster said:**
> I too have no "firefox.sh", I have "firefox-3.5" right in firefox directory.

I post bellow how look begining of my file. You should only add second line from top in yours. It must work :)

Nope. I don't have that file either. What I have is this:

/usr/lib/firefox - has only a plugin folder inside

/usr/lib/firefox-3.0.11 - has a firefox.sh similar to yours, but with paths to Firefox 3.0.11

/usr/local/lib/firefox-3.5 - has all firefox files, except firefox.sh

No other files, except for /usr/lib/firefox-3.0.11/firefox.sh, are similar to yours.

---

### Post by moster on 2009-07-02
hm... I do not know what to say, little confused. Where it can be then.

Ok, let me explain what I did... In two ways. (dont ask why :) )

1. I added mozilla repositories and installed firefox 3.5 called shiretoko. Shell script that I have to edit is in /usr/bin/ and it is called "firefox-3.5"

2. I downloaded firefox-3.5.tar.bz2 from mozilla home page, unpack it. After that I had to edit "firefox" file right in that unpacked directory.

Ok, this is all. Hope you will solve this silly bug :)

---

### Post by ethoxyethaan on 2009-07-02
Ubuntu brings changes to the firefox sourcecode (like changes the way the google search-bar works for precious money), i think firefox needs to approve before adding branding to the product, (sound like real GPL right there)

also ubuntu dev's decided to put some internet inside the browser:

[IMG]http://i40.tinypic.com/14sytl2.png[/IMG]
[IMG]http://i42.tinypic.com/1zlyzif.jpg[/IMG]

---

### Post by abhi_69 on 2009-07-02
@lovinglinux, thanz for ur help & tutorial. i follow it & install 3.5. but, no plugins (even flash works much slowly) mainly totem-mozilla, vlc-plugins, mozilla-mplayer etc. works. suddnly, firefox 3.5 stop working for a moment & then my system crash. so, i hav to restart my PC using CPU power switch. but, when i restore my old firefox files & use it, it working well. so, i decided to keep old one instead of new version. i hav PPA repo. of ubuntu-mozilla-daily build team enable & hope soon they will give us final version (it still minefield 3.5.1pre).....now, i hav no other way without this.
thanz for ur try to help me.

---

### Post by lovinglinux on 2009-07-02
> **abhi_69 said:**
>  i hav PPA repo. of ubuntu-mozilla-daily build team enable & hope soon they will give us final version (it still minefield 3.5.1pre).....now, i hav no other way without this.
thanz for ur try to help me.

They won't give you the final version, because they already passed by it. The ubuntu-mozilla-daily already has the 3.5.1pre, which will be the next Firefox version.

> [color=#CC0000]**Warning:**[/color] these repositories do not stop at the same release version that can be downloaded from Mozilla web site, so you will continue to get updates, including unstable Alpha releases. For example, the current version available at *ubuntu-mozilla-daily* is Firefox 3.5.1 Alpha. If you want the stable release 3.5.0, then follow one of the methods below.

---

### Post by lovinglinux on 2009-07-02
> **moster said:**
> hm... I do not know what to say, little confused. Where it can be then.

Ok, let me explain what I did... In two ways. (dont ask why :) )

1. I added mozilla repositories and installed firefox 3.5 called shiretoko. Shell script that I have to edit is in /usr/bin/ and it is called "firefox-3.5"

2. I downloaded firefox-3.5.tar.bz2 from mozilla home page, unpack it. After that I had to edit "firefox" file right in that unpacked directory.

Ok, this is all. Hope you will solve this silly bug :)

Problem solved with [this](http://ubuntuforums.org/showpost.php?p=7550250&postcount=21). Thank you very much.

---

### Post by abhi_69 on 2009-07-02
> **lovinglinux said:**
> They won't give you the final version, because they already passed by it. The ubuntu-mozilla-daily already has the 3.5.1pre, which will be the next Firefox version.

thanz for info. can u say how i can install latest stable release of firefox 3.5.0 from the PPA of ubuntu-mozilla-daily? is there any other PPA to get this latest version?
any help for me?

---

### Post by lovinglinux on 2009-07-02
> **abhi_69 said:**
> thanz for info. can u say how i can install latest stable release of firefox 3.5.0 from the PPA of ubuntu-mozilla-daily? is there any other PPA to get this latest version?
any help for me?

There is another PPA, from the maintainer of ubuntu-mozilla-daily. See quote below.

> **mencial said:**
> I found it in Fabien Tassin's personal repository. He seems to be the maintainer of ubuntu-mozilla-daily:

deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main

I do not know how long those packages will last there, I think someone should ask him...

---

### Post by abhi_69 on 2009-07-02
@lovinglinux, i enable this repo. as well. it contain almost same packages like ubuntu-mozilla-daily PPA. it has few new packages also like chromium browser. i install firefox-3.5 from it....but, it again installs minefield 3.5.1pre (not shiretoko that means firefox 3.5.0)...now trying to install chromium browser from this PPA, this may be an unstable build...but, i want to give it a try

---

### Post by moster on 2009-07-02
> **abhi_69 said:**
> @lovinglinux, i enable this repo. as well. it contain almost same packages like ubuntu-mozilla-daily PPA. it has few new packages also like chromium browser. i install firefox-3.5 from it....but, it again installs minefield 3.5.1pre (not shiretoko that means firefox 3.5.0)...now trying to install chromium browser from this PPA, this may be an unstable build...but, i want to give it a try

You probably see it wrong. It help about look same as mine, you have right version :) btw, minefield is 3.6 and shiretoko is 3.5.1

---

### Post by abhi_69 on 2009-07-02
thanz.....a lot. yes, i see it wrong...my web browser show exactly same like ur photo. i just check it. but, under Applications->Internet menu it show **minefield 3.5 web browser**, not shiretoko. what about it?
any ideas? BTW, my all plugins (including flash) works well :-) in this version unlike compiled & ubuntuzilla provided version.

---

### Post by moster on 2009-07-02
At my knowledge minefield if firefox 3.6 alpha version. It is next generation of firefox and they said it will be even more faster than google chrome.

---

### Post by t0p on 2009-07-02
> **luigi_mb said:**
> You can download the Firefox v3.5 (binaries) directly from the Mozilla site:

[http://www.mozilla.com/en-US/firefox/firefox.html](http://www.mozilla.com/en-US/firefox/firefox.html)

Unpack the archive in your home folder

```

cd ~
mv /full-path-to-folder-where-Firefox-was-downloaded/firefox-3.5.tar.bz2 ./
tar xvf firefox-3.5.tar.bz2

```

Run it

```

firefox/firefox

```

Plugins can be copied directly (or simlinked, depending on the plugin) to firefox/plugins.


I have got the Firefox 3.5 binary running from my home directory, and I have not needed to do anything to get my addons working. A few of them are not compatible with 3.5, but most just work, and I did not need to lift a finger. 

As for all the people complaining about the different name of the version they installed... Wtf is wrong with you all? Moaning about nothing, you remind me of my ex-gf. She was stupid too.

---

### Post by gweaver on 2009-07-03
Firefox 3.5 is now in the jaunty-proposed repositories.
All you need to do enable the jaunty-proposed repo in Synaptic and install firefox-3.5.
Once installed you can remove the jaunty-proposed again. I'm sure it will filter through to backports or wherever for those who don't want to risk using "proposed packages".

Enjoy

---

### Post by Soul-Sing on 2009-07-03
> Wtf is wrong with you all? Moaning about nothing, you remind me of my ex-gf. She was stupid too.

Nah,, , nothing wrong with me/us. I am (we are) curious sometimes.
Ubuntu is not a rolling release distro, so firefox 3.5 is form. not supported.....
(But indeed Curiosity Kills The Cat...);)
The only thing i could say about this is: install 3.5 next to the "real" one, site by site===> /opt. [COLOR="Red"]If[/COLOR] you want to try this new version.

---

### Post by Laibcoms on 2009-07-04
> **abhi_69 said:**
> well........understand......
now i am using flock, seamonkey & opera 10 beta in ubuntu 9.04.
becoz, those 3 seems faster than firefox 3.0.11. hope opera 10 final version will release soon (beta version available now) & i can use it directly in ubuntu 9.04. i like opera's policy becoz they provide various distro specific package format (like- .deb, .rpm etc.) for their browser. so, its easy for any linux distro user to upgrade to latest one as soon as it released without any problem.

Off-topic...
Where can you get Opera 10 repository??

I only have:
    deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
    deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) testing non-free

---

### Post by abhi_69 on 2009-07-04
> **Laibcoms said:**
> Off-topic...
Where can you get Opera 10 repository??

I only have:
    deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
    deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) testing non-free
well, u use opera repo. to install opera in ubuntu. via this repo. u will always get only stable (may be RC also) releases of opera. i also use this repo. to get stable opera version (current one is 9.64).
but, to test opera 10 Beta, u should download it directly from [www.opera.com](www.opera.com) in .deb format & install it from ur local hard disk. i think u know how to install a .deb format file from local hard disk.
BTW, when opera 10 final version is available, u can install it via this repo. as well.
cheers!

---

### Post by 6205 on 2009-07-04
Mmmm... looks like i'm not the only one who's pissed off. FF v3.5b4 was finally replaced with final v3.5 in universe, but it's still Shiretoko :( What a *uck it means anyway ? Shire-what-means-toko-that name? Why it is not properly branded? Also Shiretoko from repos is in english, they don't even bother to add other translations..

Is it so frakin' big problem to do normal official update and replace 3.0 with 3.5? I think they(whoever is responsible) simply don't want to do it.. 

Not to even mention badly rendered fonts on some websites.
[http://ubuntuforums.org/showthread.php?t=1093157](http://ubuntuforums.org/showthread.php?t=1093157)

I really dunno.. but openSUSE seems to me much better in so many ways..

---

### Post by elamericano on 2009-07-05
Are people having trouble using their browser because the icon's changed? Ubuntu **must** be attracting more Windows users. Take some responsibility people for doing an elective upgrade. Firefox 3.0 is recommended, secure, and functional.

However, I do think FF3.5 ought to be properly branded once it's reached "final" and is put in Universe (if you used a PPA, all bets are off, and more people should understand this.)

Getting "pissed off" and encouraging others to be pissed off is stupid. I won't recount the real errors I encountered using OpenSUSE last time, but it amounted to more than a visual theme. If getting 3.5 with icons this very minute means that much to you...

I won't say anything bad about ex-girlfriends at this point, because I'm not a cad :rolleyes:

---

### Post by lovinglinux on 2009-07-05
> **elamericano said:**
> Are people having trouble using their browser because the icon's changed? Ubuntu **must** be attracting more Windows users. Take some responsibility people for doing an elective upgrade. Firefox 3.0 is recommended, secure, and functional.

However, I do think FF3.5 ought to be properly branded once it's reached "final" and is put in Universe (if you used a PPA, all bets are off, and more people should understand this.)

Getting "pissed off" and encouraging others to be pissed off is stupid. I won't recount the real errors I encountered using OpenSUSE last time, but it amounted to more than a visual theme. If getting 3.5 with icons this very minute means that much to you...

I won't say anything bad about ex-girlfriends at this point, because I'm not a cad :rolleyes:

I agree. Besides, you can always compile it yourself with an option to enable branding, so it will be called Firefox and use the Firefox logo. ;)

---

### Post by Justin Trouble on 2009-07-05
> **6205 said:**
> Mmmm... looks like i'm not the only one who's pissed off. FF v3.5b4 was finally replaced with final v3.5 in universe, but it's still Shiretoko :(

I really dunno.. but openSUSE seems to me much better in so many ways..

It's been decided officially that Firefox 3.5 will never be branded as Firefox in Jaunty and will remain as Shiretoko, and should be considered *only a preview release*.

I must admit I want to upgrade to and use Firefox 3.5, but the currently Shiretoko branding makes the official package pretty useless as anything other than it's intended preview usage when browsing some web sites - especially banking.
I'm not an expert in this (especially in the branding licensing) but to be honest it all seems rather nonsensical to me.
Firefox is exempt from the [Stable Release Update]("https://wiki.ubuntu.com/StableReleaseUpdates") procedure: [https://wiki.ubuntu.com/StableReleaseUpdates/MicroReleaseExceptions](https://wiki.ubuntu.com/StableReleaseUpdates/MicroReleaseExceptions)

Read from the following line (timestamped 23:32) at [http://irclogs.ubuntu.com/2009/07/03/%23ubuntu-mozillateam.html]("http://irclogs.ubuntu.com/2009/07/03/%23ubuntu-mozillateam.html")

> 23:32   [COLOR=#818144]micahg   [/COLOR]ok, what do I tell people, wait for Jaunty release for branding?

---

### Post by scouser73 on 2009-07-05
> **6205 said:**
> I am trying to install latest Firefox 3.5 in jaunty, but it seem that it's harder than i though. Every possiple <snip> PPA repository install some 'Shiretoko' browser and i am unable to find anywhere properly branded Firefox..

Is this so big problem for this distibution to have basic things done. Even damn openSUSE has One-Click install of proper Firefox 3.5 available from day One, but Ubuntu noooo, Ubuntu must simply piss off their users..

If somebody has link to 'normal' repository without all that shire-crap-toko i am waiting.

Visit here for installing Firefox 3.5

[http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/]("http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/")

I installed it this morning, and it works a treat, plus it's not Shiretoko.


[[IMG]http://img7.imageshack.us/img7/3250/23423039.th.png[/IMG]](http://img7.imageshack.us/i/23423039.png/)

---

### Post by adam on 2009-07-05
> 
I must admit I want to upgrade to and use Firefox 3.5, but the currently Shiretoko branding makes the official package pretty useless as anything other than it's intended preview usage when browsing some web sites - especially banking.

If the browser is being rejected by sites as unsupported, you just have to change the useragent string.

Put "about:config" in the address bar. Enter "useragent" into the filter, and then change "Shiretoko/3.5" to "Firefox/3.5".

---

### Post by markharding557 on 2009-07-05
i have been using shiretoko without any problems including my bank site.
why are people so concerned about branding on my debian box it is called iceweasel same software different name and logo thats all.
on ubuntu you can opt to have abrowser,branding makes no difference

---

### Post by michaelpagz on 2009-07-05
> **scouser73 said:**
> Visit here for installing Firefox 3.5

[http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/]("http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/")


That method works. I did it this way a little while back when I got impatient. If branding is an issue for you, use those directions and you'll be good to go. This is the way to get a fully branded and functional 3.5 on Ubuntu. Actually, if you're really a stickler, it didn't change my icons from the old Firefox 3 icons so you may have to do that manually, I guess. They're pretty much the same though.

---

### Post by doorknob60 on 2009-07-05
Honestly, does it really matter what it's called? It's just a name, and it's the EXACT same software...it's like that in Arch and nobody complains. (although there is a firefox-branded PKGBUILD, which I use, but I don't mind the unbranded version).

---

### Post by jabrno on 2009-08-07
The name of the browser does matter to me because my bank will only let me use it's online banking service if I'm using IE, Safari, Opera or Firefox.

---

### Post by 243kof on 2009-08-07
Maybe this could help: [http://ubuntuforums.org/showthread.php?t=1225754]("http://ubuntuforums.org/showthread.php?t=1225754")

---

### Post by bobbob94 on 2009-08-07
> **jabrno said:**
> The name of the browser does matter to me because my bank will only let me use it's online banking service if I'm using IE, Safari, Opera or Firefox.

as adam pointed out a few posts above, "If the browser is being rejected by sites as unsupported, you just have to change the useragent string.

Put "about:config" in the address bar. Enter "useragent" into the filter, and then change "Shiretoko/3.5" to "Firefox/3.5"

Works fine for me with onine banking that previously complained about an unsupported browser...

---

### Post by TeoK on 2009-08-07
Can someone explain to me why is Ubuntu messing with Firefox?

as a result of this thoughtlessness, Firefox 3.5 is available to just about anybody (for about month now) but Ubuntu users...

this is becoming a big black eye for Canonical.

---

### Post by 3rdalbum on 2009-08-07
> **TeoK said:**
> as a result of this thoughtlessness, Firefox 3.5 is available to just about anybody (for about month now) but Ubuntu users...

What's stopping you from going to mozilla.com and downloading Firefox 3.5 that way? Or downloading it through the repositories and using User Agent Switcher to have it identify itself to websites as Firefox?

There's nothing stopping Ubuntu users from getting Firefox 3.5. Canonical just don't want to have to officially support two different major versions of some software. Unless you need Firefox 3.5 AND you take out an official support contract, what's the problem?

---

### Post by tkrisz on 2009-08-07
1. Please help me to localize Shiretoko!

[IMG]http://i230.photobucket.com/albums/ee224/tkrisz/Shiretoko-Add-ons.png[/IMG]

2. Please help me to autosyncronize FF 3 and 3.5 bookmarks without add-on.

---

### Post by virusiidx on 2009-08-07
I don't really see what the big deal is. If it's not updated in the repository, there are other methods of installing 3.5, both easy and hard. Ubuntuzilla being one of the easy methods. I've been running 3.5 since near release with the help of ubuntuzilla. 

There are some reasons Ubuntu doesn't update Firefox in the repositories right away. If I recall, it has something to do with the security, stability, testing and Ubuntu not being a rolling release distro.

---

### Post by northwestuntu on 2009-08-07
ive been using 3.5 since it came out and im not really impressed.  think i will go back to 3 until the next ubuntu version is out.  seems a little buggy to me.

---

### Post by HappyFeet on 2009-08-07
I installed firefox 3.5 from synaptic (jaunty). What is the big deal about installing it?

---

