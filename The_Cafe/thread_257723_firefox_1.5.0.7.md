---
title: "firefox 1.5.0.7"
date: 2006-09-14
forum: The Cafe
---

### Post by TheRingmaster on 2006-09-14
just another security release. when will this hit ubuntu (or was it already)?

---

### Post by chaosgeisterchen on 2006-09-15
Wait for some time.. it may arrive today.

---

### Post by padre999 on 2006-09-15
> **chaosgeisterchen said:**
> Wait for some time.. it may arrive today.
Good joke. I am still waiting for 1.5.0.6...

**EDIT**
But after reading other threads I learned that the 1.5.0.5 to 1.5.0.6 update affected mostly the windows version. So there was no update neccessary. So lets hope that 1.5.0.7 will arrive some time soon.

---

### Post by greggh on 2006-09-15
> **padre999 said:**
> Good joke. I am still waiting for 1.5.0.6...

Wow! I didn't realize until you said that, that the FF in the Ubuntu repos is still 1.5.0.5. That's a little crazy for such an important and universally used app not to have the latest release, particulary when security problems are involved.

---

### Post by blitzer on 2006-09-15
> **greggh said:**
> Wow! I didn't realize until you said that, that the FF in the Ubuntu repos is still 1.5.0.5. That's a little crazy for such an important and universally used app not to have the latest release, particulary when security problems are involved.

My guess would be "Windows Security Problems"  :-\"   Linux Ubuntu may not have needed that update :lol:

---

### Post by Rhapsody on 2006-09-16
I just use the Linux download from Mozilla. Works well enough, and it can update itself. Great browser.

---

### Post by Polygon on 2006-09-16
1.5.0.6 never came out for ubuntu because ubuntu's customized version of firefox already fixed in 1.5.0.5 the bug that was suppost to be fixed in 1.5.0.6, so there was no reason to release a new version

with time, the repositories will be udpated. patience.

---

### Post by jetpeach on 2006-09-16
i don't mind a few days lag or so on getting an updated version, but sometimes i do wonder why it takes even that much time?  what are they doing, just testing to make sure their aren't unexpected regressions?  with so few changes between the versions, i would think this would take hours not days...

but like i said, a few days no big deal.  if weeks go by though, then i start to get annoyed.  with the exception of the 1.5.0.5->1.5.0.6, since we linux users didn't need that patch...

---

### Post by DC@DR on 2006-09-16
Firstly, I got annoyed when found out that they disable the auto-update feature in FF, but then I thought that there should be a reason for Ubuntu developers to do so, then I started to learn being patient to wait for updates and upgrades in Linux world. Everything will get just fine, it's just a matter of time :)

---

### Post by sultanoswing on 2006-09-16
Do a Google for 'Switftfox'...I use it, and it lives up to its name!

---

### Post by BWF89 on 2006-09-16
> **sultanoswing said:**
> Do a Google for 'Switftfox'...I use it, and it lives up to its name!
Isn't Swiftfox just Firefox with a couple of modifications you could make by going to about:config in the address bar?

---

### Post by Lord Illidan on 2006-09-16
> **BWF89 said:**
> Isn't Swiftfox just Firefox with a couple of modifications you could make by going to about:config in the address bar?

No, it is also optimized for your cpu..

---

### Post by Rhapsody on 2006-09-16
> **sultanoswing said:**
> Do a Google for 'Switftfox'...I use it, and it lives up to its name!
The performance comes with a price though. CPU optimization is only a small speed-up, most of it comes from disabling [Pango](http://en.wikipedia.org/wiki/Pango), which means some characters don't display correctly in Swiftfox. It began to get irritating for me, so I switched back to Firefox.

---

### Post by towsonu2003 on 2006-09-16
> **Polygon said:**
> 1.5.0.6 never came out for ubuntu because ubuntu's customized version of firefox already fixed in 1.5.0.5 the bug that was suppost to be fixed in 1.5.0.6, so there was no reason to release a new version
I'd like to see a reference for this.

---

### Post by Polygon on 2006-09-16
the reason it takes a while for a new version of firefox or whatever to come out for ubuntu (or any distro that has a customized version id imagine) is because ive read that the developers check the code and maybe add some stuff to it (like gnome intergration ) so they are sure its not some massive virus that will kill everyones computer.... or something.. i dunno

and to towson. , here is another post confirming what i stated:

[http://ubuntuforums.org/showpost.php?p=1424681&postcount=6](http://ubuntuforums.org/showpost.php?p=1424681&postcount=6)

---

### Post by aysiu on 2006-09-16
> **towsonu2003 said:**
> I'd like to see a reference for this.
Does [this](http://changelogs.ubuntu.com/changelogs/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1/changelog) help? > firefox (1.5.dfsg+1.5.0.5-0ubuntu6.06.1) dapper-security; urgency=low

  * Fix to non-HTTP loading of <object ...>'s (eg, streaming media
    files).  Mozilla Bugzilla #346167.  Expected to be the sole
    change in Firefox upstream 1.5.0.6.

 -- Ian Jackson <iwj@ubuntu.com>  Mon, 31 Jul 2006 13:55:56 +0100

---

### Post by jason.b.c on 2006-09-17
> **DC@DR said:**
> Firstly, I got annoyed when found out that they disable the auto-update feature in FF, but then I thought that there should be a reason for Ubuntu developers to do so, then I started to learn being patient to wait for updates and upgrades in Linux world. Everything will get just fine, it's just a matter of time :)

I wonder how that could be re-enabled..???

I mean , firefox is opensource software right..?

---

### Post by aysiu on 2006-09-17
> **jason.b.c said:**
> I wonder how that could be re-enabled..???

I mean , firefox is opensource software right..?
Are you going to read the source, modify it, and then create a new .deb for it?

If the auto-update feature is important to you, just use the Mozilla version of Firefox.

---

### Post by jason.b.c on 2006-09-17
> **aysiu said:**
> Are you going to read the source, modify it, and then create a new .deb for it?

If the auto-update feature is important to you, just use the Mozilla version of Firefox.

REEEERRRR

What was that all about..?

NO i'm not going to do all that , I wondered if it could be done from "Within" firefox itself...:-\"

---

### Post by argie on 2006-09-17
Then what's that "Firefox is Open Source" statement supposed to mean?

And, usually you should be able to modify that in Edit>Preference>Advanced>Update

However Ubuntu has disabled that. Even about:config says that app.update.enabled is locked. I think you will need to fiddle with the source. (or download the version available on the Firefox site)

---

### Post by NESFreak on 2006-09-17
> **argie said:**
> Then what's that "Firefox is Open Source" statement supposed to mean?

And, usually you should be able to modify that in Edit>Preference>Advanced>Update

However Ubuntu has disabled that. Even about:config says that app.update.enabled is locked. I think you will need to fiddle with the source. (or download the version available on the Firefox site)

why the hell did they lock it? normal users wont ever look in about:config, or even have heared of it. So if the normal user wont accedentaly screw it up, why can't we screw it just because we want to do it?.
(ow and on a dutch forum some sled users where making fun of ubuntu for they DO already have the latest firefox.)

NESFreak.

---

### Post by sailor2001 on 2006-09-17
new firefox is available  [http://www.wildgardenseed.com/Taj/autopackage](http://www.wildgardenseed.com/Taj/autopackage)

---

### Post by jason.b.c on 2006-09-17
> **argie said:**
> Then what's that "Firefox is Open Source" statement supposed to mean?

And, usually you should be able to modify that in Edit>Preference>Advanced>Update

However Ubuntu has disabled that. Even about:config says that app.update.enabled is locked. I think you will need to fiddle with the source. (or download the version available on the Firefox site)

No No No , What is your comment supposed to mean...???  :confused: 

Prove me wrong if i am , But i've alway's been under the impression that firefox "WAS" in fact "Opensource" ... , So why can't "WE" mess with it if we want to..? #-o 

And why is the auto-update feature locked out to begin with..? , That dosen't make any sence...:confused:

---

### Post by Lord Illidan on 2006-09-17
Even in Fedora, Firefox 1.5.0.7 is already here..

---

### Post by givré on 2006-09-17
Why the hell is it so important that a fox update come in the hour after the release. Sorry guys but your reactions are totally stupid.
We all know that it will go in the repo. What would change if it came now or in few hours or even few days.

---

### Post by chaosgeisterchen on 2006-09-17
It's still not there.. so I have to correct my words..

```
naithian@sequentia:~$ sudo apt-cache policy mozilla-firefox
Password:
mozilla-firefox:
  Installiert:1.5.dfsg+1.5.0.5-0ubuntu6.06.1
  Mögliche Pakete:1.5.dfsg+1.5.0.5-0ubuntu6.06.1
  Versions-Tabelle:
 *** 1.5.dfsg+1.5.0.5-0ubuntu6.06.1 0
        500 http://security.ubuntu.com dapper-security/main Packages
        100 /var/lib/dpkg/status
     1.5.dfsg+1.5.0.3-0ubuntu3 0
        500 http://de.archive.ubuntu.com dapper/main Packages
naithian@sequentia:~$
```

---

### Post by givré on 2006-09-17
> **chaosgeisterchen said:**
> It's still not there.. so I have to correct my words..

Why correct your words, even if it didn't come yesterday, it will come.

---

### Post by jason.b.c on 2006-09-17
> **givré said:**
> Why the hell is it so important that a fox update come in the hour after the release. Sorry guys but your reactions are totally stupid.
We all know that it will go in the repo. What would change if it came now or in few hours or even few days.

Because some of us have a hard time ( **or can't** ) do it that way.., I for one would prefer that firefox auto-updated.., But i guess if it don't then it don't...:rolleyes: 

It's just that i personnely don't enjoy fighting with things to get them installed correctly..

---

### Post by givré on 2006-09-17
> **jason.b.c said:**
> Because some of us have a hard time ( **or can't** ) do it that way..
What do you mean. It will come in dapper-security, so it will be a simple update. I don't know anything easier.

---

### Post by Lord Illidan on 2006-09-17
> **givré said:**
> Why the hell is it so important that a fox update come in the hour after the release. Sorry guys but your reactions are totally stupid.
We all know that it will go in the repo. What would change if it came now or in few hours or even few days.

An hour?? More like a day or two... or a few days...

It matters, yes. People who are not using the latest version of firefox are more vulnerable...and there is more chance of them being compromised, linux users or not.

---

### Post by jason.b.c on 2006-09-17
> **givré said:**
> What do you mean. It will come in dapper-security, so it will be a simple update. I don't know anything easier.

Not for me , One thing is i'm not using dapper ( don't know if that matters ), two - everytime i've tried something like that it **"ALWAY"S"** Fails to do it correctly , 3 - The only way i can do it is to use the script that asyiu told me about ...( but it takes a while )...

If I =>

```
sudo apt-get update
``` 
the newest version of firefox "Isn't" found.! , So how is that easy..?

Synaptic dosen't have it listed , How is that easy if it's not in the list...?

---

### Post by givré on 2006-09-17
The vulnerabilities are discover & publish days before each release of firefox, so i don't know what a few days will change.

---

### Post by givré on 2006-09-17
> **jason.b.c said:**
> Not for me , One thing is i'm not using dapper ( don't know if that matters )
Yes that matter, what are you using. We are speaking about dapper update now. Breezy use 1.0.* & edgy use 2.0

---

### Post by jason.b.c on 2006-09-17
> **givré said:**
> Yes that matter, what are you using. We are speaking about dapper update now. Breezy use 1.0.* & edgy use 2.0

Yea but , Why does it matter if it's dapper or not...???

I use breezy , So then it's the same firefox as the one in dapper i'm sure...:confused:

---

### Post by givré on 2006-09-17
> **jason.b.c said:**
> Yea but , Why does it matter if it's dapper or not...???

I use breezy , So then it's the same firefox as the one in dapper i'm sure...:confused:
Hum, not really. If you have firefox 1.5.0.*, you probably install it by yourself, and so you should be able to do the automatic update. If not, that's probably because it is install in /usr and so you have to be root to do the update. Launch firefox as root :
```
sudo firefox
```
Do the update, 
close & restart as a normal user, 
and you should have the new firefox.

---

### Post by jason.b.c on 2006-09-17
> **givré said:**
> Hum, not really. If you have firefox 1.5.0.*, you probably install it by yourself, and so you should be able to do the automatic update. If not, that's probably because it is install in /usr and so you have to be root to do the update. [B]Launch firefox as root :
```
sudo firefox
```
Do the update, 
close & restart as a normal user, 
and you should have the new firefox.[/B]
  :o 
WOAH Dude , I thought you weren't supposed to do it that way...??

---

### Post by givré on 2006-09-17
> **jason.b.c said:**
> :o 
WOAH Dude , I thought you weren't supposed to do it that way...??
The thing is you can't really do it in an other way if it is install as root :-\"
But if you do it for the update, and **just** for the update, there shouldn't be any problem. :cool:

---

### Post by jason.b.c on 2006-09-17
Well thats a bunch of crap..! , I updated and now my ubuntu forums extention is gone..](*,)

---

### Post by towsonu2003 on 2006-09-18
> **aysiu said:**
> Does [this](http://changelogs.ubuntu.com/changelogs/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1/changelog) help?

certainly does :) thanks. you've always been a good researcher.  :)

as for the locked up update featurein firefox, it's most probably in order not to introduce a bug by letting both apt-get and firefox deal with firefox updates. 

also, starting firefox with "sudo firefox" will / may cause file ownership changes of the profile of the current user (and it is dangerous). if <user> starts firefox with sudo, some files in <user>'s firefox profile will change ownership and be rott's files. to fix that after the fact, do $ sudo chown -r user:user ~/.mozilla/firefox  --"sudo firefox" is dangerous even if you do not visit any web pages because there is the risk of a well-buried bug in firefox causing bad things with root's privileges. 

finally, you might wanna give some time to the extensions so they can get their compatibility issues fixed (and contact the author).

---

### Post by bruce89 on 2006-09-18
> **padre999 said:**
> Good joke. I am still waiting for 1.5.0.6...

Ubuntu ChangeLog:
> firefox (1.5.dfsg+1.5.0.5-0ubuntu6.06.1) dapper-security; urgency=low

  * Fix to non-HTTP loading of <object ...>'s (eg, streaming media
    files).  Mozilla Bugzilla #346167.  Expected to be the sole
    change in Firefox upstream 1.5.0.6.

 -- Ian Jackson <iwj@ubuntu.com>   Mon, 31 Jul 2006 13:55:56 +0100 

I don't see the fuss about 1.5.0.7, it's only a security release.

Just to show off, I am using Firefox's 2.0b2 Gecko at the moment in Epiphany 2.16.0.

---

### Post by jetpeach on 2006-09-18
"I don't see the fuss about 1.5.0.7, it's only a security release."

Well, for many of us that IS why we run linux.  We like having more security.  And in fact, I think that is all the more reason for the patch to be quick and why it is an urgent matter.  If it's only a security release, then is little chance of breakage so patch it in a day or two and send out the update!

So on the issue, I posted a few days ago saying I'm fine with being patient for a little while, but now I am getting annoyed.  Is this the way things will always work?  Somewhere gets updated and we sit around chatting on forums for weeks wondering when we'll get to see the updates?  Or we attempt to download it ourselves/run firefox as root/cause all sorts of potential breakage?

But rather than just complain, maybe I should get on launchpad and make sure their is a bug filed to get this patch out soon.  And then, maybe I should build a deb from source, set the version so when the official update comes it will be updated, and install the newer version of firefox that way and then post it on the forums for everyone else...  Maybe after I go to work.

---

### Post by aysiu on 2006-09-18
They'll patch it. It usually takes them anywhere between a day and two weeks to patch it, but they always do.

If you're itching to get it patched right away, then use Mozilla's Firefox, not Ubuntu's Firefox. Then, you'll always get every update immediately, and you can calm down.

---

### Post by towsonu2003 on 2006-09-18
> **aysiu said:**
> If you're itching to get it patched right away, [then use Mozilla's Firefox, not Ubuntu's Firefox]("https://help.ubuntu.com/community/FirefoxNewVersion").

:)

---

### Post by edisav on 2006-09-18
> **aysiu said:**
> They'll patch it. It usually takes them anywhere between a day and two weeks to patch it, but they always do.

One day is pretty good, a few days is reasonable, but two weeks is unacceptable by all means!!! Matter as well turn back the clock and go back to microsoft, whose philosophy is we'll get there when we get there!!!!

As someone posted before, security is a top priority.

---

### Post by aysiu on 2006-09-18
> **edisav said:**
> One day is pretty good, a few days is reasonable, but two weeks is unacceptable by all means!!! Matter as well turn back the clock and go back to microsoft, whose philosophy is we'll get there when we get there!!!!

As someone posted before, security is a top priority.
If you feel that way, then get the Mozilla version of Firefox.

I thought I said that before...

---

### Post by edisav on 2006-09-18
> **aysiu said:**
> If you feel that way, then get the Mozilla version of Firefox.
I thought I said that before...

aysiu, I don't want to get here into a heated argument here so i won't post anything else. I'm not addressing here a concern about firefox only but rather in general. If ubuntu takes all its sweet time to fix something and I follow your apporach, then I would end up reinstalling everything from source. Then what is the point of using ubuntu?

Without getting defensive, look at the broader approach and perhaps you will see that you may not be completely right. That's it!

---

### Post by bruce89 on 2006-09-18
> **edisav said:**
> aysiu, I don't want to get here into a heated argument here so i won't post anything else. I'm not addressing here a concern about firefox only but rather in general. If ubuntu takes all its sweet time to fix something and I follow your apporach, then I would end up reinstalling everything from source. Then what is the point of using ubuntu?

It takes MS a month to fix things as they only release security updates on the second tuesday every month.  Ubuntu does it within a few days.

> **jetpeach said:**
> Somewhere gets updated and we sit around chatting on forums for weeks wondering when we'll get to see the updates?

The longest I have ever seen a Firefox upgrade take is a week.

> **jetpeach said:**
> But rather than just complain, maybe I should get on launchpad and make sure their is a bug filed to get this patch out soon.
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/60806](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/60806)

---

### Post by aysiu on 2006-09-18
The thing is, it mainly applies to Mozilla software--Thunderbird and Firefox, and those are the ones that also are more likely to be exploited, since they are internet applications. Yes, it's possible for GIMP to have some exploit that gives escalation of privileges, but who has access to GIMP except you (most of the time anyway)?

Internet applications (web browsers, email clients) are the ones with the most worrisome security holes. So when a slightly newer version of Inkscape or AmaroK comes out, it usually has nothing to do with security. New versions of Firefox come out every few weeks or so... and new releases are almost always security releases.

So, no, you do not have to recompile every application you have. Have a Mozilla Thunderbird and a Mozilla Firefox and self-update those. The rest of the applications will be fine for the six months until the following Ubuntu release (or one month right now until Edgy).

---

### Post by towsonu2003 on 2006-09-18
another reason firefox updates may come delayed is that the whole system is alittle bit too dependent on firefox. this is a side of ubuntu I don't like much, but it's still ok :)

I mean, they have to test a new update extensively to make sure it doesn't break anything (such as yelp / help browser etc). so we have to put up with such delay as long as we don't wanna see the latest issues we experienced with ubuntu (an X update breaking X, a kernel update breaking X and so on). 

I for one am all about later-release-of-fixes as long as they are _sure_ the fix won't break anything. 

A fast release is always prone to break things, especially if it's a package that the distro is too dependent on.

PS. I have Mozilla's firefox, and it's nice if you want the latest firefox as soon as possible. I gave the wiki page on how to do that above (quoting aysiu's text).

---

### Post by bruce89 on 2006-09-18
> **towsonu2003 said:**
> another reason firefox updates may come delayed is that the whole system is alittle bit too dependent on firefox. this is a side of ubuntu I don't like much, but it's still ok :)
Indeed:
```
bruce@Scooby-Doo:~$ apt-cache rdepends firefox
firefox
Reverse Depends:
 |mozilla-mplayer
  j2re1.4-mozilla-plugin
 |xfig-doc
 |xdg-utils
  wysihtml-el
 |wmnetselect
  totem-xine-firefox-plugin
  totem-gstreamer-firefox-plugin
  peercast-handlers
 |openoffice.org-experimental
 |nvu
 |nip2
 |mozplugger
 |mozilla-venkman
 |mozilla-tabextensions
  mozilla-stumbleupon
 |mozilla-nukeimage
  mozilla-mozgest
 |mozilla-livehttpheaders
 |mozilla-imagezoom
  mozilla-firefox-locale-tr
  mozilla-firefox-locale-tr
 |mozilla-firefox-locale-tr
  mozilla-firefox-gnome-support
  mozilla-firefox-gnome-support
  mozilla-firefox
  mozilla-firefox
 |mozilla-diggler
 |mozilla-ctxextensions
 |mozilla-checky
 |mozilla-bookmarksftp
 |mozilla-bonobo
 |mozilla-biofox
  monodevelop
  liferea-mozilla
  libgecko-cil
 |lastfm
  junior-internet
  gxine
 |gcjwebplugin-4.2
 |gcjwebplugin-4.1
  galeon
  firefox-webdeveloper
  firefox-webdeveloper
  firefox-greasemonkey
  firefox-dom-inspector
  firefox-dom-inspector
 |fibusql
 |endeavour2
  education-standalone
  yelp
  xubuntu-desktop
  ubuntu-desktop
 |openoffice.org
  mozilla-firefox-locale-zu
  mozilla-firefox-locale-zu
 |mozilla-firefox-locale-zu
  mozilla-firefox-locale-zh-tw
  mozilla-firefox-locale-zh-tw
 |mozilla-firefox-locale-zh-tw
  mozilla-firefox-locale-zh-cn
  mozilla-firefox-locale-zh-cn
 |mozilla-firefox-locale-zh-cn
  mozilla-firefox-locale-xh
  mozilla-firefox-locale-xh
 |mozilla-firefox-locale-xh
  mozilla-firefox-locale-tr-tr
  mozilla-firefox-locale-tr-tr
 |mozilla-firefox-locale-tr-tr
  mozilla-firefox-locale-sv-se
  mozilla-firefox-locale-sv-se
 |mozilla-firefox-locale-sv-se
  mozilla-firefox-locale-sl-si
  mozilla-firefox-locale-sl-si
 |mozilla-firefox-locale-sl-si
  mozilla-firefox-locale-sk
  mozilla-firefox-locale-sk
 |mozilla-firefox-locale-sk
  mozilla-firefox-locale-ru-ru
  mozilla-firefox-locale-ru-ru
 |mozilla-firefox-locale-ru-ru
  mozilla-firefox-locale-pt-pt
  mozilla-firefox-locale-pt-pt
 |mozilla-firefox-locale-pt-pt
  mozilla-firefox-locale-pl-pl
  mozilla-firefox-locale-pl-pl
 |mozilla-firefox-locale-pl-pl
  mozilla-firefox-locale-pa-in
  mozilla-firefox-locale-pa-in
 |mozilla-firefox-locale-pa-in
  mozilla-firefox-locale-nso
  mozilla-firefox-locale-nso
 |mozilla-firefox-locale-nso
  mozilla-firefox-locale-nn-no
  mozilla-firefox-locale-nn-no
 |mozilla-firefox-locale-nn-no
  mozilla-firefox-locale-nl-nl
  mozilla-firefox-locale-nl-nl
 |mozilla-firefox-locale-nl-nl
  mozilla-firefox-locale-nb-no
  mozilla-firefox-locale-nb-no
 |mozilla-firefox-locale-nb-no
  mozilla-firefox-locale-mn
  mozilla-firefox-locale-mn
 |mozilla-firefox-locale-mn
  mozilla-firefox-locale-mk-mk
  mozilla-firefox-locale-mk-mk
 |mozilla-firefox-locale-mk-mk
  mozilla-firefox-locale-lt
  mozilla-firefox-locale-lt
 |mozilla-firefox-locale-lt
  mozilla-firefox-locale-ko
  mozilla-firefox-locale-ko
 |mozilla-firefox-locale-ko
  mozilla-firefox-locale-ja-jp
  mozilla-firefox-locale-ja-jp
 |mozilla-firefox-locale-ja-jp
  mozilla-firefox-locale-it-it
  mozilla-firefox-locale-it-it
 |mozilla-firefox-locale-it-it
  mozilla-firefox-locale-hu-hu
  mozilla-firefox-locale-hu-hu
 |mozilla-firefox-locale-hu-hu
  mozilla-firefox-locale-gu-in
  mozilla-firefox-locale-gu-in
 |mozilla-firefox-locale-gu-in
  mozilla-firefox-locale-fy-nl
  mozilla-firefox-locale-fy-nl
 |mozilla-firefox-locale-fy-nl
  mozilla-firefox-locale-fr-fr
  mozilla-firefox-locale-fr-fr
 |mozilla-firefox-locale-fr-fr
  mozilla-firefox-locale-fi-fi
  mozilla-firefox-locale-fi-fi
 |mozilla-firefox-locale-fi-fi
  mozilla-firefox-locale-eu
  mozilla-firefox-locale-eu
 |mozilla-firefox-locale-eu
  mozilla-firefox-locale-es-es
  mozilla-firefox-locale-es-es
 |mozilla-firefox-locale-es-es
  mozilla-firefox-locale-es-ar
  mozilla-firefox-locale-es-ar
 |mozilla-firefox-locale-es-ar
  mozilla-firefox-locale-en-gb
  mozilla-firefox-locale-en-gb
 |mozilla-firefox-locale-en-gb
  mozilla-firefox-locale-el
  mozilla-firefox-locale-el
 |mozilla-firefox-locale-el
  mozilla-firefox-locale-de-de
  mozilla-firefox-locale-de-de
 |mozilla-firefox-locale-de-de
  mozilla-firefox-locale-da-dk
  mozilla-firefox-locale-da-dk
 |mozilla-firefox-locale-da-dk
  mozilla-firefox-locale-cs-cz
  mozilla-firefox-locale-cs-cz
 |mozilla-firefox-locale-cs-cz
  mozilla-firefox-locale-ca
  mozilla-firefox-locale-ca
 |mozilla-firefox-locale-ca
  mozilla-firefox-locale-bg-bg
  mozilla-firefox-locale-bg-bg
 |mozilla-firefox-locale-bg-bg
  mozilla-firefox-locale-ar
  mozilla-firefox-locale-ar
 |mozilla-firefox-locale-ar
  mozilla-firefox-locale-af
  mozilla-firefox-locale-af
 |mozilla-firefox-locale-af
  libnss3
  libgecko2.0-cil
  libdevhelp-1-0
  gnome-app-install
  firefox-themes-ubuntu
  firefox-gnome-support
  firefox-dev
  firefox-dbg
  epiphany-browser
  edubuntu-desktop

```

I hope that Ubuntu follows Debian's lead and use xulrunner for all this.

---

### Post by nu2this on 2006-09-19
Just my 2 cents here, but I can think that,the .xorg update a little while back made the Ubuntu guys a little gun shy. They want to be sure this time. I can certainly understand that,I'd rather have, & I'm sure they to want to have it work right the 1st time out,for everybody.
Besides, if one wants this is linux the alternatives have been listed in this thread one can do them **it's your choice!**

---

### Post by karamba_kid on 2006-09-19
> **givré said:**
> Hum, not really. If you have firefox 1.5.0.*, you probably install it by yourself, and so you should be able to do the automatic update. If not, that's probably because it is install in /usr and so you have to be root to do the update. Launch firefox as root :
```
sudo firefox
```
Do the update, 
close & restart as a normal user, 
and you should have the new firefox.

I believe your supposed to use gksudo or kdesu to open applications with root privileges, but this is still not recommended.  If your worried I would just disable java and javascript and wait for the new version in the repos.

---

### Post by aysiu on 2006-09-19
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by n2diy on 2006-09-21
> **karamba_kid said:**
> I believe your supposed to use gksudo or kdesu to open applications with root privileges, but this is still not recommended.  If your worried I would just disable java and javascript and wait for the new version in the repos.
I tried that, and check for updates was ghosted out. :/

Darryl

---

### Post by towsonu2003 on 2006-09-21
> **n2diy said:**
> I tried that, and check for updates was ghosted out. :/

Darryl

as long as you have the ubuntu-preinstalled firefox, you won't be able to use firefox's own update feature. you can check out how to install the newest firefox from the wiki at [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by givré on 2006-09-22
> **karamba_kid said:**
> I believe your supposed to use gksudo or kdesu to open applications with root privileges, but this is still not recommended.  If your worried I would just disable java and javascript and wait for the new version in the repos.
Sorry for the sudo instead of the gksudo :cool: 
The tip i gave to the other guy is not recommanded for sure, but you didn't really followed the conversation. This guy run breezy and installed FF 1.5 on it manually, so the only way to update it is to install the new version or to run it as root.

---

### Post by towsonu2003 on 2006-09-22
> **givré said:**
> Sorry for the sudo instead of the gksudo :cool: 
The tip i gave to the other guy is not recommanded for sure, but you didn't really followed the conversation. This guy run breezy and installed FF 1.5 on it manually, so the only way to update it is to install the new version or to run it as root.

the better way to update is:
```

cp -r ~/.mozilla ~/.mozilla-backup # backup profile
sudo chown -R username:username /opt/firefox  # change ownership
firefox  # launch firefox !!only to update it!! !!do not browse internet!!
sudo chown -R root:root /opt/firefox # change ownership back after update
```

[Reference here]("https://help.ubuntu.com/community/FirefoxNewVersion#head-989f6d047637b584e6af702799965c7570a81f6b")

---

### Post by DC@DR on 2006-09-23
I just updated my FF to v1.5.0.7 via apt-get today, it's already available in repositories, just come and check it out :)

---

### Post by bluenova on 2006-09-23
Hi all,

So at the moment I am running 2.0b2. It's installed systemwide, if I run 'firefox' from cli I get 2.0b2.

Synaptic seems to think I have 1.5.0.5 installed so of cause wants to upgrade to 1.5.0.7.

Is there a way to tell synaptic which version I have installed or do I just have to hold back the update?

---

### Post by jetpeach on 2006-09-23
wherever your 2.0b2 is stored, it's not in the same directory as the synaptic 1.5.0.5 version.  the only way to have synaptic know which version is installed is to compile from source and probably isn't worth it.  it almost certainly won't matter though if you let synaptic upgrade the 1.5.0.5 version to 1.5.0.7 (because 2.0b2 is stored in a separate directory than 1.5.0.x), but if you want to be sure i would just tell it to hold the update.
there are a few things i can think that could be affected by upgraded (maybe your firefox shortcut, or how you've configured firefox to be your default), but they all seem unlikely to happen but ultimately depend on how you installed 2.0b2...

---

### Post by towsonu2003 on 2006-09-23
> **bluenova said:**
> Hi all,

So at the moment I am running 2.0b2. It's installed systemwide, if I run 'firefox' from cli I get 2.0b2.

Synaptic seems to think I have 1.5.0.5 installed so of cause wants to upgrade to 1.5.0.7.

Is there a way to tell synaptic which version I have installed or do I just have to hold back the update?

you could check which firefox that is. if that's just a symlink, you can understand what's going on. For example, in my install:
```

~$ which firefox
/usr/bin/firefox
~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 22 2006-09-22 13:25 /usr/bin/firefox -> ../**lib**/firefox/firefox

```

in your install, this could very well be:
[code]
~$ which firefox
/usr/bin/firefox
~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 22 2006-09-22 13:25 /usr/bin/firefox -> ../**opt**/firefox/firefox

lib is where synaptic puts it. opt is where you would put it following the FirefoxNewVersion wiki page (check that for yourself). if you let synaptic upgrade to 1.5.0.7 and find that it changed symlinks, you could just change them back. 

you could also tell synaptic to "lock version" (under Package menu after selecting firefox package). that way, it won' ask you to upgrade firefox.

---

### Post by bluenova on 2006-09-25
Well I upgraded it and $firefox still gives me 2.0b2, so all is ok.

---

### Post by nocturn on 2006-09-25
> **jason.b.c said:**
> No No No , What is your comment supposed to mean...???  :confused: 

Prove me wrong if i am , But i've alway's been under the impression that firefox "WAS" in fact "Opensource" ... , So why can't "WE" mess with it if we want to..? #-o 

And why is the auto-update feature locked out to begin with..? , That dosen't make any sence...:confused:

It wasn't locked, just disabled.  It makes no sense to have a seperate update mech in each app when you have a system like apt that manages your software.  The two of them would clash.

---

### Post by nocturn on 2006-09-25
> **bruce89 said:**
> It takes MS a month to fix things as they only release security updates on the second tuesday every month.  Ubuntu does it within a few days.


Oh MS can patch pretty quickly, when the hole is in their DRM system (out of cycle patch).

---

