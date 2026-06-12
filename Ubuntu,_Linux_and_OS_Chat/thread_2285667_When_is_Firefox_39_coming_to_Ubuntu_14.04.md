---
title: "When is Firefox 39 coming to Ubuntu 14.04?"
date: 2015-07-07
forum: Ubuntu, Linux and OS Chat
---

### Post by orange2k on 2015-07-07
Firefox 39 was released a couple of days ago, but when is it coming to Ubuntu 14.04?

---

### Post by PaulW2U on 2015-07-07
> **orange2k said:**
> Firefox 39 was released a couple of days ago, but when is it coming to Ubuntu 14.04?

I can't give you a definite answer but Firefox 39 is currently in the proposed repository of Ubuntu 15.10, the current development version. I saw in the minutes of the recent Security Team's meeting that there was a problem with one of the 12.04 builds crashing shortly after starting up.

So, I'm sure Firefox 39 will be released as soon those responsible for its release say it's ready for all of the current Ubuntu versions.

---

### Post by ajgreeny on 2015-07-07
If you really need that version for some reason or another you can download the tar.gz archive direct from mozilla, extract it, and run the firefox binary by double clicking it in the extracted folder.

I tried it a little while ago today to see what all the fuss is about pocket.
Having now seen what pocket is I don't think I need it, but version 39 ran fine on Ubuntu 15.10.

---

### Post by Mike_Walsh on 2015-07-07
> **ajgreeny said:**
> If you really need that version for some reason or another you can download the tar.gz archive direct from mozilla, extract it, and run the firefox binary by double clicking it in the extracted folder.

Agreed. The Firefox downloads are completely self-contained. If you go to [this page]("http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/"), you can find every Firefox release since 0.8.....released on the 11th February, 2004.

I install FF like this in 'Puppy' Linux all the time......and the advantage is that it comes with a built-in updater. Just go to Help>About Firefox, and FF will check for, and install available updates. As AJ says, it should work without any problems.

I believe the Ubuntu version in the repositories has the updater mechanism removed by default.


Regards,

Mike. :)

---

### Post by Dennis N on 2015-07-07
Firefox 39! We don't have 38.0.5 (the previous release) yet in our Ubuntu updates. At least for me it has not shown up (as of Jul 7).

---

### Post by QDR06VV9 on 2015-07-07
Just to clarify.
It is always best to stay within the stock Repos's(To be clear Factory Repos That come installed with the OS)
If was a security flaw it would already be in The Stock Factory Repo's 
But if you don't mind testing or even curious to see the latest. You can add this PPA 
>  Official PPA for Firefox Beta
PPA description

This PPA contains releases of Firefox from the beta channel

All users of this PPA are encouraged to report any bugs they find. Instructions for reporting bugs can be found at [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs). Please have a read of this before reporting a bug, as it may help save time.

Please don't email the package uploader to report bugs. Not only is email not a good tool for tracking bugs, it also excludes anybody else from tracking or working on the issue.

If publishing is disabled for this PPA, there is no need to email the team or any of its members to tell them this. Publishing will be reneabled by a team member when it is appropriate to do so.

For questions and bugs with software in this PPA please *don't* contact mozillateam.
Adding this PPA to your system

You can update your system with unsupported packages from this untrusted PPA by adding ppa:mozillateam/firefox-next to your system's Software Sources. (Read about installing) 

To install the "beta" version
```
sudo add-apt-repository ppa:mozillateam/firefox-next
sudo apt-get update
sudo apt-get upgrade
```
Current build shows 39.0~b7+build1-0ubuntu, It currently supports Ubuntu 12.04 to Development 15.10(Wily)


I have been using this PPA for years now with No Ill effects to my OS but have from time to time found Bugs with Firefox No Show Stopper's Though. [B]And your mileage may vary.
[/B]
To revert back to your old firefox
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:mozillateam/firefox-next
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
```

I would also agree with ajgreeny about Pocket Not Sure I need it!
> Pocket meanwhile is a service for managing a reading list of online  articles (it allows you to save stories, videos, and websites to check  out later). While Pocket is already offered as a Firefox add-on, including  it directly in Firefox means the browser&#8217;s users can save all the pages  they want to read or watch later without signing up separately for the  service. Pocket is available in Firefox Accounts in U.S. English,  German, Japanese, Russian, and Spanish.


Kind Regards

---

### Post by vasa1 on 2015-07-07
> **runrickus said:**
> Just to clarify.
It is always best to stay within the stock Repos's
...
While that's mostly true, I've read of exceptions. Owncloud was a recent case.

Re. Firefox, it would be interesting to know how many security fixes have been provided by the repo team after being missed by the people at Mozilla.

And staying with the repo version may be useful for those dependent on "integration" with certain DEs such as Unity.

---

### Post by VMC on 2015-07-07
> **ajgreeny said:**
> If you really need that version for some reason or another you can download the tar.gz archive direct from mozilla, extract it, and run the firefox binary by double clicking it in the extracted folder.

I tried it a little while ago today to see what all the fuss is about pocket.
Having now seen what pocket is I don't think I need it, but version 39 ran fine on Ubuntu 15.10.

I just upgraded my lubuntu wily install to 40 beta the tar.gz. There was no instructions inside the compressed file, so I found this "[5-easy-steps]("http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint#a_install_firefox")" to install. Very simple.

Edit: I just installed it for no other reason than curiosity.

---

### Post by Yellow Pasque on 2015-07-08
> **runrickus said:**
> If was a security flaw it would already be in those Repo's 

[https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/#firefox39](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/#firefox39)

---

### Post by coffeecat on 2015-07-08
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by QDR06VV9 on 2015-07-08
> **vasa1 said:**
> While that's mostly true, I've read of exceptions. Owncloud was a recent case.

Re. Firefox, it would be interesting to know how many security fixes have been provided by the repo team after being missed by the people at Mozilla.

And staying with the repo version may be _useful for those dependent on "integration" with certain DEs such as Unity_.
Yes that alone is the only reason I posted. And this was not meant to be used as a daily browser for the reasons you state. 

> **Temüjin said:**
> [https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/#firefox39](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/#firefox39)
Perhaps you you misunderstood when I said in those Repo's I was referring to Factory(installed with the OS) not PPA's.  Specially when the PPA shows "BETA"
So I amended my first post to clear up my vague text. Thanks for bringing that to my attention. And the the Link you posted should be read by all even the ones just using tar.gz
Downloads.
Again this is not to be used as a daily browser but more as a sneak peak, or testing and bug finding(witch is how I use it) to ensure a Quality Release to be enjoyed by all.
Regards

---

### Post by Yellow Pasque on 2015-07-08
My point with the link had nothing to do with PPA's. You said that FF39 would be in the repos if it fixed security issues. My point was that it does fix security flaws, but it's not in the standard (or "Factory" as you call them) repos.

EDIT: Sorry if it was vague just posting a link, but I'm a lazy typist.

---

### Post by bcschmerker on 2015-07-08
> **PaulW2U said:**
> ...I can't give you a definite answer but Firefox 39 is currently in the proposed repository of Ubuntu 15.10, the current development version. I saw in the minutes of the recent Security Team's meeting that there was a problem with one of the 12.04 builds crashing shortly after starting up.

So, I'm sure Firefox 39 will be released as soon those responsible for its release say it's ready for all of the current Ubuntu versions.
Thanks for a clarification on the delay in getting Mozilla® Firefox® 39.0+build?-0ubuntu0.12.04.1 to Ubuntu® 12.04.6-LTS, which I currently run.  As of 8 July 2015 I'm having some difficulty finding where to submit a crash to Mozilla Add-Ons concerning Tab Utilities, which triggered a runaway condition on my installation; I'm running Tab Mix Plus, which is stable, on 38.0+build3-0ubuntu0.12.04.1.

---

### Post by night_sky2 on 2015-07-08
> **Dennis N said:**
> Firefox 39! We don't have 38.0.5 (the previous release) yet in our Ubuntu updates. At least for me it has not shown up (as of Jul 7).

Point releases are often introduced to adress bugs affecting Windows OSes and therefore don't necesserely bring anything meaningful to Ubuntu.

Firefox 39 will be packaged and pushed to the Ubuntu official repo soon enough I assume.

---

### Post by vasa1 on 2015-07-08
> **night_sky2 said:**
> Point releases are often introduced to adress bugs affecting Windows OSes and therefore don't necesserely bring anything meaningful to Ubuntu.
...
I don't know about Firefox, but Google doesn't issue a point release for Linux, for example, if there's nothing related to Linux. Anyway, this can be nailed by looking at the [release notes for 38.05]("https://www.mozilla.org/en-US/firefox/38.0.5/releasenotes/") which was released by Mozilla over a month ago.

```

What’s New

    Reference: Release notes for Firefox 38.0.1
    New

    Keep track of articles and videos with Pocket
    New

    Clean formatting for articles and blog posts with Reader View
    New

    Share the active tab or window in a Hello conversation
    Fixed

    A race condition that would cause Firefox to stop painting when switching tabs (bug 1067470)
    Fixed

    Fixed graphics performance when using the built-in VGA driver on Windows 7 (Bug 1165732)


```

Neither of the fixes relate to Linux whereas the "new" features aren't really core to the browser. So it's possible Canonical decided to give 38.05 a miss.

Then there's also the information provided by Paul2Wu that building (?) Canonical's version for 12.04 was running into difficulties.

---

### Post by fyfe54 on 2015-07-09
Updated laptop a few minutes ago and Firefox is now version 39.0

---

### Post by kansasnoob on 2015-07-09
> **fyfe54 said:**
> Updated laptop a few minutes ago and Firefox is now version 39.0

+1 ............................. I fired up two of my PC's this AM and was notified of updates available before the coffee was done - Firefox as well as flash and some other security related updates.

SABDFL is still looking out for us :guitar:

---

### Post by ajgreeny on 2015-07-09
> **kansasnoob said:**
> +1 ............................. I fired up two of my PC's this AM and was notified of updates available before the coffee was done - Firefox as well as flash and some other security related updates.

SABDFL is still looking out for us :guitar:
And are those FF-39 versions running fine for you; I have just done it on my Xubuntu 14.04 64bit system and if I use a flash plugin, which in my case is the freshplayerplugin, ie pepperflash, the same version of flash as in chromium FF-39 seems to crash.

I have disabled pocket and reader in FF-39 as they annoy me when they keep popping up, and I wonder if that might help; if not I shall downgrade to FF38 again as I have the .deb for 38 from my apt/cache still available.

---

### Post by SantaFe on 2015-07-09
While you slowpokes are on 39, I'm already on Firefox 40 (Beta). ;)

---

### Post by night_sky2 on 2015-07-09
> **ajgreeny said:**
> And are those FF-39 versions running fine for you; I have just done it on my Xubuntu 14.04 64bit system and if I use a flash plugin, which in my case is the freshplayerplugin, ie pepperflash, the same version of flash as in chromium FF-39 seems to crash.

The NPAPI plugin architecture is often the cause of hangs and crashes. There's not much that can be done about it and it's the reason why both Google
and Mozilla wants to get rid of it altogether. In my case, I use the FlashDisable addon and default to HTML5 wherever possible. I enable flash only when required.

> **ajgreeny said:**
> I have disabled pocket and reader in FF-39 as they annoy me when they keep popping up, and I wonder if that might help; if not I shall downgrade to FF38 again as I have the .deb for 38 from my apt/cache still available.

Firefox Hello, Pocket, Reader View are all turned off in my Firefox install. I don't need these particular built-in features and they increase RAM cumsomption.

---

### Post by monkeybrain20122 on 2015-07-10
> **ajgreeny said:**
> 
I have disabled pocket and reader in FF-39 as they annoy me when they keep popping up, and I wonder if that might help; if not I shall downgrade to FF38 again as I have the .deb for 38 from my apt/cache still available.

Actually I have not noticed any difference between 38 and 39. The pocket may have popped up once otherwise it just sits on the toolbar. Didn't notice any change in ram or cpu usage.

---

### Post by ajgreeny on 2015-07-10
> **monkeybrain20122 said:**
> Actually I have not noticed any difference between 38 and 39. The pocket may have popped up once otherwise it just sits on the toolbar. Didn't notice any change in ram or cpu usage.
Then you have been very lucky, I think.  That and the reader pop-up kept appearing on mine, so I've added the new add-on from [https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming](https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming) to get rid of them.

I have also had to remove the freshplayerplugin and reinstall flashplugin-installer as that was causing continuous crashes on any flash page, and though I don't use it much there are some sites where there is no alternative.

---

### Post by Dennis N on 2015-07-10
> Then you have been very lucky, I think. That and the reader pop-up kept appearing on mine

I think the reader pop up message stops appearing after you try it once. At least that seems to be the case for me. Now there is just an icon in the address bar (next to reload) in situations where it can be used. In fact, I like it, as it strips the ads off the article page. I also found that you need to leave reader mode after using it or other pages lose their style. All based on my limited observations over a brief period!

---

### Post by monkeybrain20122 on 2015-07-10
> **ajgreeny said:**
> Then you have been very lucky, I think.  That and the reader pop-up kept appearing on mine, so I've added the new add-on from [https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming](https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming) to get rid of them.

I have also had to remove the freshplayerplugin and reinstall flashplugin-installer as that was causing continuous crashes on any flash page, and though I don't use it much there are some sites where there is no alternative.

The pocket has actually been introduced in Firefox 38.05, which has not been packaged for Ubuntu. But Fedora is on 38.05 (hasn't upgraded to 39 yet for bugs which I don't see in Ubuntu,-- e.g tabs don't open) and there it is. I have not even noticed it before.

I think the freshplayer thing probably has to do with the ppa build. I suggest you try to build it yourself once and if it still crashes Firefox file a bug. 
[https://github.com/i-rinat/freshplayerplugin](https://github.com/i-rinat/freshplayerplugin)

---

### Post by kansasnoob on 2015-07-10
> **monkeybrain20122 said:**
> Actually I have not noticed any difference between 38 and 39. The pocket may have popped up once otherwise it just sits on the toolbar. Didn't notice any change in ram or cpu usage.

+1 .................. I went one step further - right-clicked pocket and selected to move it to menu because I'll never use it. Otherwise no noticeable change.

---

### Post by night_sky2 on 2015-07-10
> **ajgreeny said:**
> Then you have been very lucky, I think.  That and the reader pop-up kept appearing on mine, so I've added the new add-on from [https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming](https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming) to get rid of them.

You can disable them yourself once and for all, you don't need an addon for that.

about:config

browser.pocket.enabled -> false

loop.enabled -> false

reader.parse-on-load.enabled -> false

Et voilà. ;)

---

### Post by ajgreeny on 2015-07-11
> **night_sky2 said:**
> You can disable them yourself once and for all, you don't need an addon for that.

about:config

browser.pocket.enabled -> false

loop.enabled -> false

reader.parse-on-load.enabled -> false

Et voilà. ;)
So I had found after installing the add-on, but it is a very small add-on so I will keep it for now.

I am still playing around with freshplayer configuration and disabling vdpau and vaapi to see if I can make use of it without the continual crashing after viewing flash, but too soon to tell so far.
Watch this space!

---

### Post by Karlchen on 2015-07-11
> **PaulW2U said:**
> I saw in the minutes of the recent Security Team's meeting that there was a problem with one of the 12.04 builds crashing shortly after starting up. Could this be my report perhaps? [Mint 13: Firefox 39.0 crashes right on startup]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1471565")
The reported phenomenon seems to affect all 32-bit versions of Mint 13, which is based on Ubuntu 12.04 32-bit.

[Added]
No, it was not my report. Mine turned out to be a duplicate of this Launchpad bug report:
[**Firefox 39 crashes on startup or within a few seconds on Precise/x86**](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1471949)

Karl

---

### Post by night_sky2 on 2015-07-12
> **ajgreeny said:**
> I am still playing around with freshplayer configuration and disabling vdpau and vaapi to see if I can make use of it without the continual crashing after viewing flash, but too soon to tell so far. Watch this space!

I've made a clean install of Xubuntu and downloaded Flash 11.2 (Disabled but one click away with the FlashDisable addon)
 from the Ubuntu Software Center instead of installing pepperflash and the Fresh Player Plugin that just is a bit too messy for me as of late. 

Everything is good now. All things considered, my needs of the flash player are very limited so I don't necesserely require the latest version.

---

### Post by ajgreeny on 2015-07-12
> I am still playing around with freshplayer configuration and disabling vdpau and vaapi to see if I can make use of it without the continual crashing after viewing flash, but too soon to tell so far.
Watch this space! As I said above in post #27, I have been trying this for a while now.

I thought previously that I had disabled both vdpau and vaapi in the freshwrapper.conf file, but stupidly I had made the changes but left the edited file open and unsaved, so was still having crashes.  Having now disabled both vdpau and vaapi properly I haven't had a crash when using flash.

So I am now very hopeful that this was, indeed, the only problem and it is now solved and I can continue to use freshplayerplugin.

---

### Post by bcschmerker on 2015-07-13
> **Karlchen said:**
> 
[Mint 13: Firefox 39.0 crashes right on startup]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1471565"):...

Mine turned out to be a duplicate of this Launchpad bug report:
[**Firefox 39 crashes on startup or within a few seconds on Precise/x86**](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1471949)

Karl
Thanks for the link to the actual Launchpad thread(s) your reply.  Mozilla traced the issue for Firefox 39.0-build2-0ubuntu0-0.12.04.1 to a mis-compile of the i386 version, meaning an unforeseen issue with the GNU Compiler Collection on 12.04-LTS.  Hopefully they can fix the GCC bug(s) and get 39.0-build6-0ubuntu0.12.04.1 out to us.

**Addendum:**  Don't know whether the GCC issue is a zero-day bug as of 13 July 2015, but no mis-compiles have been reported on other Releases.

---

### Post by bcschmerker on 2015-07-16
**Update:**  The Ubuntu browser team has apparently solved the mis-compile problem for 12.04.6-LTS; Mozilla® Firefox® 39.0+build5-0ubuntu0.12.04.2 is now available for download.

---

