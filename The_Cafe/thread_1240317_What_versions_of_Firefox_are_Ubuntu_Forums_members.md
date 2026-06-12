---
title: "What versions of Firefox are Ubuntu Forums members using?"
date: 2009-08-14
forum: The Cafe
---

### Post by aysiu on 2009-08-14
I'm just curious, in light of Firefox 3.5's recent release and the whole Shiretoko labeling thing, what versions of Firefox the Community Cafe folks are using.

---

### Post by HappinessNow on 2009-08-14
> **aysiu said:**
> I'm just curious, in light of Firefox 3.5's recent release and the whole Shiretoko labeling thing, what versions of Firefox the Community Cafe folks are using.
Firefox/3.5.2

---

### Post by MaxIBoy on 2009-08-14
I use the minefield builds. I've also been trying to compile my own from mercurial, but with no success yet.

---

### Post by SuperSonic4 on 2009-08-14
Firefox from [extra] although I used the firebrand script to give it offical logo

---

### Post by FuturePilot on 2009-08-14
3.5 from the repositories. I don't see what the big deal is about the branding. I really don't care. It acts exactly the same as Firefox. Actually it *is* Firefox. Plus I can just let Ubuntu take care of the updates for me.

---

### Post by itreius on 2009-08-14
firefox-3.5 package from the official repositories, aka Shiretoko. I edited the useragent string through about:config so it shows up as Firefox/3.5.2, and I used perfectska's GNOME-colors [extra icon pack]("http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562") to add Firefox icons to it (just had to change the folder /usr/lib/firefox-3.0.12 to /usr/lib/firefox.3.5.2 before running the script).

---

### Post by venator260 on 2009-08-14
Ubuntu 9.04 using Minefield 3.6a2pre

---

### Post by RiceMonster on 2009-08-14
3.5.2

> **SuperSonic4 said:**
> Firefox from [extra] although I used the firebrand script to give it offical logo

I use firefox-branded from the AUR to get the branding.

---

### Post by Anxious Nut on 2009-08-14
using 3.5 from the repositories, having no problems, though im starting to use flock-browser ... but also use firefox(since it's da papa)

> **aysiu said:**
> I'm just curious
you know, curiosity killed a cat

---

### Post by Xbehave on 2009-08-14
firefox3.5 from fedora repos, used 3.0 and then 3.1/3.5 from /opt (with links from /usr/bin/ though)

Given firefox's poor security record (relative to chrome/etc not IE), i hope people running firefox in /home really know what they are doing OR start doing something less dangerous soon!

---

### Post by khelben1979 on 2009-08-14
[Mozilla Firefox 3.5]("http://en.wikipedia.org/wiki/Mozilla_firefox#Version_3.5").2.

---

### Post by sydbat on 2009-08-14
> **Xbehave said:**
> Given firefox's poor security record (relative to chrome/etc not IE), i hope people running firefox in /home really know what they are doing OR start doing something less dangerous soon!Source?

---

### Post by Tibuda on 2009-08-14
> **Xbehave said:**
> Given firefox's poor security record (relative to chrome/etc not IE), i hope people running firefox in /home really know what they are doing OR start doing something less dangerous soon!

How is that more dangerous than running from somewhere else? It runs with the same privileges.

EDIT: Voted 'I don't use Firefox regularly', Epiphany WebKit for me.

---

### Post by Firestem4 on 2009-08-14
Swiftweasel. PGO Compiled version of Firefox using a modified iceweasel branding/logo etc. (Lightweight and fast).

I was using Swiftfox for the same reason (PGO compiled) but it slowly started becomming unresponsive as i kept using it.

---

### Post by Xbehave on 2009-08-14
> **sydbat said:**
> Source?[URL="http://secunia.com/advisories/product/19089/?task=statistics"]secunia on firefox 3.0.x
[/URL]
[mozillas own page on 3.5.x]("http://www.mozilla.org/security/known-vulnerabilities/firefox35.html")

The idea of running a binary in such a way that it can modify itself thus leaving you permanently owned is shocking from a security point of view anyway.

edit:
> How is that more dangerous than running from somewhere else? It runs with the same privileges.
Because if your firefox gets compromised the attacker can easily modify firefox to run various forms of malware/never patch itself/report all your browsing habits/passwords/bank details/etc

---

### Post by Tibuda on 2009-08-14
> **Xbehave said:**
> The idea of running a binary in such a way that it can modify itself thus leaving you permanently owned is shocking from a security point of view anyway.

Understood. Thanks!

---

### Post by Xbehave on 2009-08-14
> **Firestem4 said:**
> Swiftweasel. PGO Compiled version of Firefox using a modified iceweasel branding/logo etc. (Lightweight and fast).

I was using Swiftfox for the same reason (PGO compiled) but it slowly started becomming unresponsive as i kept using it.
I thought the only difference between swiftfox and swiftweasel was the branding :confused:, do you know if the swiftfox guys are helping with the mozilla bug stopping mozilla from using PGO on linux?

> Understood. Thanks! 
glad to help, tbh its not bad but i think its worth the effort to install firefox the "right way", even if it means using gtksu/kdesu when you want to update.

---

### Post by Dobbie03 on 2009-08-14
version 3.5.3pre (what ever the pre means)

I am confused, I dual boot both Ubuntu 9.04 and Crunchbang 9.04, Ubuntu installed Firefox 3.5 no worries, Crunchbang has installed Shiretoko and it won't run the same add-ons the Firefox does.  Weird, anyone know how to get rid of this Shiretoko crap and replace it with official Firefox?

I know Shiretoko is meant to ne official but it doesn't run the same, it feels different.

---

### Post by FuturePilot on 2009-08-14
> **Xbehave said:**
> [URL="http://secunia.com/advisories/product/19089/?task=statistics"]secunia on firefox 3.0.x
[/URL]
[mozillas own page on 3.5.x]("http://www.mozilla.org/security/known-vulnerabilities/firefox35.html")

The idea of running a binary in such a way that it can modify itself thus leaving you permanently owned is shocking from a security point of view anyway.

edit:

Because if your firefox gets compromised the attacker can easily modify firefox to run various forms of malware/never patch itself/report all your browsing habits/passwords/bank details/etc

All of those could be done whether or not you run Firefox from your /home or not. The only way to be really safe is to sandbox Firefox with something like AppArmor

---

### Post by Tibuda on 2009-08-14
> **MattDobson said:**
> I know Shiretoko is meant to ne official but it doesn't run the same, it feels different.

No. If you are using Jaunty, 3.0 is official, not Shiretoko.

---

### Post by aysiu on 2009-08-14
> **FuturePilot said:**
> All of those could be done whether or not you run Firefox from your /home or not. The only way to be really safe is to sandbox Firefox with something like AppArmor
AppArmor sounds great, but right now it seems a bit too complicated for point-and-click folks like me.

I just use NoScript.

---

### Post by Viva on 2009-08-14
Shiretoko, but I haven't updated it on a few noobs' systems I've installed ubuntu on.

---

### Post by t0p on 2009-08-14
I'm using  3.52 - the one you get from [getfirefox.com]("http://ubuntuforums.org/http//:getfirefox.com").  The one that runs from my home directory.  Contrary to popular belief, there is no problem *viz* automated updates.  Firefox checks Mozilla for updates every day.

---

### Post by j.bell730 on 2009-08-14
Firefox 3.5 installed for me -- branding and all -- along with Karmic.

---

### Post by t0p on 2009-08-14
I'm using  3.52 - the one you get from [getfirefox.com]("http://ubuntuforums.org/http//:getfirefox.com").  The one that runs from my home directory.  Contrary to popular belief, there is no problem *viz* automated updates.  Firefox checks Mozilla for updates every day.

> **Xbehave said:**
> 
Given firefox's poor security record (relative to chrome/etc not IE), i hope people running firefox in /home really know what they are doing OR start doing something less dangerous soon!

Can you please give me some examples of firefox's "poor security record"?  I was under the impression that firefox has a robust security model.

Also, can you enlighten me as to what is the danger of running firefox from my home directory?

---

### Post by running_rabbit07 on 2009-08-14
I am using the 3.5 release on Karmic. (Not suggested)

---

### Post by doorknob60 on 2009-08-14
Whoa a lot of options there, and none of them apply to Arch Users :-P Anyways I'm using Firefox 3.5.2 with profile guided optimization and some other optimizations enabled (firefox-pgo package in AUR). It also has the official branding enabled (not Shiretoko, I don't know why that bugs people so much though, jeez it's the same thing...)

---

### Post by gnomeuser on 2009-08-14
I use Chromium, it has completely replaced Firefox and Gecko based browsers for me.

---

### Post by Xbehave on 2009-08-14
> **FuturePilot said:**
> All of those could be done whether or not you run Firefox from your /home or not. The only way to be really safe is to sandbox Firefox with something like AppArmor
That's simply not true, if you put firefox in /opt and own it by root, an attacker would have to comprise you while you are running as root to modify it (at that points its game over anyway). The chance of being exploited while viewing about:blank,the update notification page or running update firefox now, to be a lot less than that of everyday browsing.

AppArmor is nice and simple by comparison to selinux/etc but is not needed for something as simple as protecting your binaries!

> Can you please give me some examples of firefox's "poor security record"? 
I have already provided various sources for the claim that firefox is not 100% safe and you should not do stupid things with it (e.g run it as root or run it in a way it can update itself). That is not to say it has a bad security record it's just worse than your average linux program.
> I was under the impression that firefox has a robust security model.you were mistaken, if anything is holding firefox back its the lack of a robust security model for the threats of today! It's security model is far worse than chrome/IE7+, the quality of code makes up for this in parts, but generally firefox's security model is very good in 2009.

> Also, can you enlighten me as to what is the danger of running firefox from my home directory? 
As ive stated before, the danger of running any binary in somewhere it can modify itself is that if it is owned once, it can be modified to allow the attacker all the info firefox gets and to not protect itself when future updates fix the problem.

---

### Post by Starlight on 2009-08-14
> **itreius said:**
> I edited the useragent string through about:config so it shows up as Firefox/3.5.2

Cool! I've just done that, and it works :) I didn't know that the user agent could be changed without a special add-on. 

I'm using Shiretoko 3.5.2 from the repositories.

---

### Post by SuperSonic4 on 2009-08-14
> **doorknob60 said:**
> Whoa a lot of options there, and none of them apply to Arch Users :-P Anyways I'm using Firefox 3.5.2 with profile guided optimization and some other optimizations enabled (firefox-pgo package in AUR). It also has the official branding enabled (not Shiretoko, I don't know why that bugs people so much though, jeez it's the same thing...)

```
[22:39:52] sonic /mnt/Music $  pacman -Ss firefox
extra/firefox 3.5.2-1 [1.00 MB]
    Standalone web browser from mozilla.org
extra/firefox-i18n 3.5.2-1 [9.18 MB]
    Language packs for Firefox
extra/totem-plugin 2.26.3-1 [0.13 MB]
    Totem mozilla/firefox plugin
community/arch-firefox-search 0.7-5 [0.00 MB]
    Firefox Arch search engines (AUR, Pkgs, BBS, Wiki, etc.)
community/firefox-spell-pt-br 3.0.8-1 [1.25 MB]
    Portuguese (Brazil) dictionary for Firefox
community/firefox-spell-ru 0.4.2-3 [0.50 MB]
    Russian spellchecker dictionary for Firefox
community/mozplugger 1.12.1-1 [0.04 MB]
    A Mozilla & Firefox multimedia plugin.
archlinuxfr/firebrand 3.5-1 [0.34 MB]
    A script to brand Firefox without recompiling.
archlinuxfr/firefox-fr 3.5.1-1 [0.12 MB]
    French pack for Firefox
[22:39:57] sonic /mnt/Music $
```

[extra] is a repository ;)

---

### Post by lovinglinux on 2009-08-14
I'm using 3.5.1 compiled from source with processor optimization flags and PGO. I have Swiftweasel 3.5.2 as main browser on a notebook, mainly because I was lazy to compile FF 3.5 for another processor. Sometimes I also use 3.0.13 official Ubuntu version for extension development.

I've tried to compile 3.5.2 but it gives me an error every time, so I will wait for 3.5.3 final release. I also tested Namoroka 3.6a1 compiled from source without PGO, but I was afraid to use an alpha version and some extensions were messed up, while forcing them by disabling version check. 

I have also tested Ubuntuzilla, Shiretoko 3.5 from universe, 3.5.whatever from ubuntu-mozilla-daily, Firefox 3.5.0 from Mozilla using Psychocats method, Swiftfox 3.5.rc1, <put version here> <put source here>... :)

---

### Post by DougieFresh4U on 2009-08-14
I use the '3.6pre' version. Trying to get the '3.7 pre' version to install but it keeps crashing

---

### Post by steveneddy on 2009-08-14
Launchpad ppa

---

### Post by ratcheer on 2009-08-14
3.5.2 downloaded from Mozilla and extracted to a subdirectory of Desktop.

Tim

---

### Post by Artemis3 on 2009-08-14
I'm running Shiretoko 3.5 from a launchpad repo which i added before Ubuntu had it. The same repo has 3.6...: [https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)

Launchpad repos are like a gold mine, i have added at least 10, so my favorite apps remain updated.

---

### Post by Arup on 2009-08-14
3.52 Shiretoko from repo with branding fix so its the default FF instead of FF 3.12

---

### Post by gOLdenHaWK3D on 2009-08-16
Just use what ever is there in the repos! :P

---

### Post by NCLI on 2009-08-16
> **Xbehave said:**
> [URL="http://secunia.com/advisories/product/19089/?task=statistics"]secunia on firefox 3.0.x
[/URL]
[mozillas own page on 3.5.x]("http://www.mozilla.org/security/known-vulnerabilities/firefox35.html")
1. Mozilla's page on 3.5 shows FIXED vulnerabilities, so they aren't relevant anymore.
2. This image comes from Secunia, the site you linked to, showing that all known vulnerabilities have been fixed by Mozilla for Firefox 3.0.X
[IMG]http://secunia.com/advisories/graph/?type=sol&period=all&prod=19089[/IMG]

---

### Post by Frak on 2009-08-16
Firefox 3.5 for PowerPC Mac OS X

---

### Post by Bachstelze on 2009-08-16
Firefox 3.5 on Windows and Mac OS. I'm not using a Linux desktop anymore (but I have a Debian server with VNC for when I need to run GUI stuff, it runs Epiphany as a web browser though).

---

### Post by mamamia88 on 2009-08-16
chrome

---

### Post by meborc on 2009-08-16
3.7 minefield, too bad it is not in the poll ;)

---

### Post by TheNessus on 2009-08-16
Swiftfox, but my main browser is Opera 10

---

### Post by wojox on 2009-08-16
Swiftfox 3.5.2

---

### Post by grizzler on 2009-08-16
Mozilla's Firefox 3.5.2, installed manually in /opt, mainly because I couldn't find a translated version anywhere else. Could have used Ubuntuzilla I suppose...

---

### Post by imlinux on 2009-08-16
> **meborc said:**
> 3.7 minefield, too bad it is not in the poll ;)

edit:can you please post the link from where did you download it ,i am unable to find


oh sorry to bother i [found it]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/")

---

### Post by spoons on 2009-08-16
Namoroka 3.6 Alpha 1 :)

---

### Post by aktiwers on 2009-08-16
Firefox 3.5.2 and Firefox 3.6a from PPA

---

### Post by JillSwift on 2009-08-16
3.5.2 self compiled to try and squeeze a little more performance out of it.

A process that was a far greater pain in the neck than I'd expected it to be. Worth it, though. It's pretty perky compared to the pre-compiled tarball.

---

### Post by Warpnow on 2009-08-16
Installed version is 3.0.13 but I hardly ever use firefox. Just had to apt-get it so I could browse to the opera download.

---

### Post by MasterNetra on 2009-08-16
Using 3.5.2 for windows, sense I'm trying out Windows 7. Can't bash it until you try it first. ^.^

---

### Post by sports fan Matt on 2009-08-16
I hardly fire up firefox either..trying opera these days

---

### Post by koleoptero on 2009-08-16
> **aysiu said:**
> I'm just curious, in light of Firefox 3.5's recent release and the whole Shiretoko labeling thing, what versions of Firefox the Community Cafe folks are using.

"Just curious" HA! I am sure there's something conspiratorial going on here. :-k

---

### Post by samjh on 2009-08-16
> **NCLI said:**
> 1. Mozilla's page on 3.5 shows FIXED vulnerabilities, so they aren't relevant anymore.
2. This image comes from Secunia, the site you linked to, showing that all known vulnerabilities have been fixed by Mozilla for Firefox 3.0.X
[IMG]http://secunia.com/advisories/graph/?type=sol&period=all&prod=19089[/IMG]

Yeah, that's what I saw too.

I took a look at IE 7, IE 8, and Opera.  They have surprisingly few vulnerabilities on Secunia.  It makes Firefox look very buggy.

---

### Post by Bölvaður on 2009-08-16
> **venator260 said:**
> Ubuntu 9.04 using Minefield 3.6a2pre
that's what I got

---

### Post by wojox on 2009-10-11
Just compiled Minefield/3.7a1pre

---

### Post by coldReactive on 2009-10-11
Other version: Windows Mozilla Firefox 3.5.3 due to me being on Windows.

---

### Post by Redundant Username on 2009-10-11
When was it released? I've been running the extracted executable in my home folder to get 3.5.

---

### Post by NCLI on 2009-10-11
> **samjh said:**
> Yeah, that's what I saw too.

I took a look at IE 7, IE 8, and Opera.  They have surprisingly few vulnerabilities on Secunia.  It makes Firefox look very buggy.
Chrome has only received one Secunia advisory, and Opera none. Rather than being a sign of being safer, I think it's more likely to be because of how relatively unknown they are compared to Firefox & IE., and how few businesses(Secunias main customers)are using them.

Now, Firefox and IE. Firefox has received 4 advisories for 3.5, 3 of those have been fixed according to Secunia. IE 8 has received also received 4 advisories, and 2 of those have been fixed. All in all, I'd say they're pretty equal, but since Firefox is updated faster and more often, I think we'll see Firefox pull ahead of IE in security soon enough.

Off-topic but... :D
[[IMG]http://xs344.xs.to/xs344/09410/vista_vs_xp_vs_ubuntu_8.04_vs_ubuntu_9.04356.png.xs.jpg[/IMG]]("http://xs344.xs.to/xs344/09410/vista_vs_xp_vs_ubuntu_8.04_vs_ubuntu_9.04356.png")

---

### Post by Regenweald on 2009-10-11
I started using Ubuntu last year, and only enjoyed FF's ridiculous startup time and ok rendering. Since starting with chromium I have had no reason to try FF again, even though i hear it's new performance is great. I stick to webkit from now on.

On a side note, FF 3.5 caused serious HD thrashing in XP for me, it's since been fixed but my confidence is mozilla is very low. Opera is my XP browser on the occasions that require me to boot XP.

---

### Post by speedwell68 on 2009-10-11
Firefox 3.5.3

---

### Post by lovinglinux on 2009-10-11
> **lovinglinux said:**
> I'm using 3.5.1 compiled from source with processor optimization flags and PGO. I have Swiftweasel 3.5.2 as main browser on a notebook, mainly because I was lazy to compile FF 3.5 for another processor. Sometimes I also use 3.0.13 official Ubuntu version for extension development.

Now I'm using the vanilla version shipped with Karmic. Still working great and Karmic is awesome ;)

---

### Post by oxf on 2009-10-14
OK forgive me for being dense but please could someone explain. 

What exactly is Shiretoko? Is this essentially like a beta version of FF3.5?

It's in Synaptic as FF3.5 and if I add it it shows up as Shiretoko and not FF. Why is this?

Finally someone talked about changing things so that it does show as FF. SPECIFICALLY how to I do this? Do I change certain lines in about:config? or is there more to it?

And what exactly is meant by "branding", "dummy packages" etc?

Sorry if these seem like silly questions!

Thanks :)

---

### Post by lovinglinux on 2009-10-14
> **oxf said:**
> What exactly is Shiretoko? Is this essentially like a beta version of FF3.5?

Not necessarily beta. It's a development version, that can be alpha, beta or even the final release.

Today, Shiretoko is the final release of Firefox 3.5.

> **oxf said:**
> It's in Synaptic as FF3.5 and if I add it it shows up as Shiretoko and not FF. Why is this?

It has a different name and logo to avoid confusion, since it is installed side-by-side with the default version. In Karmic Koala, Firefox 3.5 is already the default. The development one, which is 3.6, is called Namoroka.

> **oxf said:**
> Finally someone talked about changing things so that it does show as FF. SPECIFICALLY how to I do this? Do I change certain lines in about:config? or is there more to it?

Don't bother. Ubuntu Karmic Koala will be released this month and will be shipped with Firefox 3.5.

If you want to always have the most recent version of Firefox, with name and logo, then I recommend Ubuntuzilla. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **oxf said:**
> And what exactly is meant by "branding", "dummy packages" etc?

Firefox is released as open source, so you can compile yourself and distribute it, but you can't use their brand (logo and name). That's the case of Swiftfox, Siftweasel, Iceweasel, Wizo and other browsers based on Firefox. They essentially have the same core code, but cannot have the branding. Mozilla enforces trademark policies to protect the image of their brand.

So if you want to compile Firefox and get the real name and logo, you need to enable branding in the compilation configuration. But then you cannot distribute it. 

Ubuntu developers take a different approach. They distribute the branding as a separate package. If you remove it, you will end up with an unbranded browser.

Dummy packages are usually (as far as I know) packages that simply points to another package. For example, when the developers change the name of a package, for whatever reasons, they keep a dummy package pointing to the new one to avoid dependency issues. Let's say application **A** depends on **B**, but **B** has been renamed to **BCool** in the new Ubuntu release. So they keep a dummy **B** package that depends on **BCool**. So when someone installs a package that depends on **B**, then **BCool** will also be installed, even if it's not in the dependency list of the application installed by the user.

---

### Post by anonymous_user on 2009-10-14
Swiftfox 3.5.3 using their installer (extracts to /opt).

---

### Post by SomeGuyDude on 2009-10-14
Arch's AUR has a PGO-enabled version. I'm using that.

---

### Post by DougieFresh4U on 2009-10-14
I have been playing around with **3.7a1pre**

---

### Post by RATM_Owns on 2009-10-14
3.6a1

---

### Post by niccholaspage on 2009-10-14
I'm using Karmic with Firefox 3.5 from repos, Plus I have 3.7 nightly build in my home folder for testing :P.

---

### Post by oxf on 2009-10-14
> **lovinglinux said:**
> Not necessarily beta. It's a development version, that can be alpha, beta or even the final release.

ntu developers take a different approach. They distribute the branding as a separate package. If you remove it, you will end up with an unbranded browser.

Dummy packages are usually (as far as I know) packages that simply points to another package. For example, when the developers change the name of a package, for whatever reasons, they keep a dummy package pointing to the new one to avoid dependency issues. Let's say application **A** depends on **B**, but **B** has been renamed to **BCool** in the new Ubuntu release. So they keep a dummy **B** package that depends on **BCool**. So when someone installs a package that depends on **B**, then **BCool** will also be installed, even if it's not in the dependency list of the application installed by the user.

Thanks :)

---

### Post by taavi on 2009-10-20
> **DougieFresh4U said:**
> I have been playing around with **3.7a1pre**

Hahaha, totally ugly : D or comic sans is sex now?

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.3) Gecko/20090920 Firefox/3.5.3 (Swiftfox)

---

### Post by hellion0 on 2009-10-20
3.5.3 on Hardy via UbuntuZilla.

---

