---
title: "Firefox 61"
date: 2018-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by treb0r on 2018-06-28
Will Firefox 61 land in 16.04 by default or should I add the PPA?

---

### Post by monkeybrain20122 on 2018-06-28
It will come. Firefox always gets updated, no need for ppa.

---

### Post by treb0r on 2018-06-28
Great, thanks!

---

### Post by treb0r on 2018-06-28
I was even toying with the idea of giving the snap a road test...

---

### Post by ajgreeny on 2018-06-28
If you really want to try a newer version than is in the repos you can simply download the Mozilla website's archive version from [https://www.mozilla.org/en-GB/firefox/download/thanks/](https://www.mozilla.org/en-GB/firefox/download/thanks/) then extract it and run the firefox executable file contained therein.

However, there is little point doing so as in a few days the repos will update to contain that version.

---

### Post by mikewhatever on 2018-06-29
Actually, this time, the new FF is not in the PPA, and it is unclear why it isn't, and when we'll get it.

---

### Post by treb0r on 2018-07-02
Hmm. Still not updated. I wonder what's up?

---

### Post by menneskelighet on 2018-07-02
Any news on this?

---

### Post by poorguy on 2018-07-02
Reminds me of a day back on ***April 26, 2018 ***when ***Bionic Beaver*** had not been released. ;)

---

### Post by treb0r on 2018-07-03
Well according to this article "If you&#8217;re running Ubuntu 18.04 LTS or another supported version you will get the Firefox 61 update automatically through the built-in Software Updater tool at some point in the next few days." 

[https://www.omgubuntu.co.uk/2018/06/firefox-61-released-with-faster-tab-switching-on-linux](https://www.omgubuntu.co.uk/2018/06/firefox-61-released-with-faster-tab-switching-on-linux)

---

### Post by poorguy on 2018-07-03
I figure we will get it when it's ready and until then*** FF 60.0.2 ***is working fine imo. :)

---

### Post by PaulW2U on 2018-07-03
> **treb0r said:**
> Well according to this article "If you’re running Ubuntu 18.04 LTS or another supported version you will get the Firefox 61 update automatically through the built-in Software Updater tool at some point in the next few days."
The author of that blog, Joey Sneddon, is just an Ubuntu user like you and me. Most of Joey's articles link to official sources but he also posts opinion and conjecture. Many of his articles are written and posted a little too soon.

I'm not going to provide links but this morning I noticed that pre-release builds of both Firefox **62** and **63** have appeared in one of the official Ubuntu PPAs that is used for development. Further builds are building as I type this. I'm sure Ubuntu's developers have a very good reason for Firefox 61's non-appearance (so far?).

---

### Post by spvkgn on 2018-07-03
The FF61 packages are building now in [Ubuntu Mozilla Security Team PPA]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+packages?field.name_filter=firefox&field.status_filter=published&field.series_filter=")

---

### Post by treb0r on 2018-07-03
> **spvkgn said:**
> The FF61 packages are building now in [Ubuntu Mozilla Security Team PPA]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+packages?field.name_filter=firefox&field.status_filter=published&field.series_filter=")

Good news. There a couple of new features in this release that I'm looking forward to taking for spin..

---

### Post by thenailedone on 2018-07-03
What do we want? **Everything!**
When do we want it? **Yesterday!**

---

### Post by walts48 on 2018-07-04
> **spvkgn said:**
> The FF61 packages are building now in [Ubuntu Mozilla Security Team PPA]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+packages?field.name_filter=firefox&field.status_filter=published&field.series_filter=")

Seems there is a 61.0.1 in the works from Mozilla and updates are throttled at 25% for other OS's, and those that install manually on Linux.

> 
[LIST]
[*] Planning desktop 61.0.1 dot release. Waiting on bug 1472137 to land and be uplifted before starting the builds.
[LIST]
[*] Desktop remains throttled at 25% in the mean time. 
[/LIST]
   
[/LIST]


REF:[ https://wiki.mozilla.org/Firefox/Channels/Meetings/2018-07-03#Schedule_Update]("https://wiki.mozilla.org/Firefox/Channels/Meetings/2018-07-03#Schedule_Update")

---

### Post by treb0r on 2018-07-04
Thanks for that, good to know what's happening. I'll keep on running apt update until it lands..

---

### Post by la.khan on 2018-07-05
What I noticed is that Canonical takes 2-3 days to test a new version of FF. If everything is good, the new FF version is built into a package and released to Ubuntu users. This may take 3-5 days. However, for FF 61, I see that Canonical hasn't released FF 61 yet, even though Joe Sneddon reviewed FF 61 more than a week back. From the links provided here in this thread, I see that it is in the process of testing/building.

I consider FF to be a very good browser (it serves my need well) and would like upgrade/install the latest version; however, I will wait for Canonical to package and release it. I am tempted to install the latest using snapd but it is 200+ MB (ugh! :rolleyes:) while the Canonical package comes to 50+ MB. Till Canonical officially releases it, I will use FF 60.0.2 :D

---

### Post by treb0r on 2018-07-05
> **la.khan said:**
> I am tempted to install the latest using snapd but it is 200+ MB (ugh! :rolleyes:) while the Canonical package comes to 50+ MB. Till Canonical officially releases it, I will use FF 60.0.2 :D

Last night I decided to try the snap. Version 61.0-3 installed really quickly, but global menu support is missing for Unity. It's not a huge deal but I like the global menu as it saves on screen space. Does anyone know a way to get the global menu working for the snap version of Firefox?

I've decided to stick with it for now. It's about time I tried out this snap thing. If using the Firefox snap means I get the latest versions faster then I'm happy. I can access all of the old menu items through the new chrome style 'burger' menu anyway.

Also, I don't mind if the size of the snap is much larger than the .deb as I have more than enough storage available.

---

### Post by walts48 on 2018-07-05
Just got the update to Firefox 61.0 along with a kernel update and other stuff through the Software Updater.

Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:61.0) Gecko/20100101 Firefox/61.0 ID:20180703192103

---

### Post by la.khan on 2018-07-05
Canonical has packaged Firefox 61 for install. Downloaded & installed it, just now :D

---

### Post by poorguy on 2018-07-05
I also got my update of ***Firefox 61*** along with the ***kernel update*** and ***other updates ***and all installed and is working great. :)

---

### Post by pauljw on 2018-07-05
> **poorguy said:**
> I also got my update of ***Firefox 61*** along with the ***kernel update*** and ***other updates ***and all installed and is working great. :)

Hmmm... I see that Mozilla just released Firefox 61.1B, is it in the repos yet, huh, is it?   Just kidding...  ;)

---

### Post by PaulW2U on 2018-07-05
> **pauljw said:**
> Hmmm... I see that Mozilla just released Firefox 61.1B, is it in the repos yet, huh, is it?   Just kidding...  ;)
You might be kidding but in the last couple of hours some builds for Firefox 61.0.1 have appeared in one of the official Ubuntu development PPAs. The build process is still in its early stages. According to the Mozilla changelog the new version fixes seven bugs, one of which is the possible loss of bookmarks when upgrading from Firefox 60.

No doubt we'll all be upgrading again in three or four days time.

---

### Post by pauljw on 2018-07-05
> **PaulW2U said:**
> You might be kidding but in the last couple of hours some builds for Firefox 61.0.1 have appeared in one of the official Ubuntu development PPAs. The build process is still in its early stages. According to the Mozilla changelog the new version fixes seven bugs, one of which is the possible loss of bookmarks when upgrading from Firefox 60.

No doubt we'll all be upgrading again in three or four days time.

Oh great, yeah, I was kidding.  Thanks for the heads up.  :)

---

### Post by treb0r on 2018-07-06
So I discovered that I can keep both versions of Firefox installed, the snap version and traditional .deb. It's not possible to run both at the same time but I don't need that anyway. So far the snap version has been great, it even plays Netflix. The problem with the lack of Global menu support is the only issue I have encountered. It will be interesting to see the difference in update frequency between the two versions.

---

### Post by monkeybrain20122 on 2018-07-07
> **treb0r said:**
> So I discovered that I can keep both versions of Firefox installed, the snap version and traditional .deb. It's not possible to run both at the same time but I don't need that anyway. So far the snap version has been great, it even plays Netflix. The problem with the lack of Global menu support is the only issue I have encountered. It will be interesting to see the difference in update frequency between the two versions.

I don't know what is the point of having two Firefox, and on top of it why would anyone need a snap version of Firefox? You can download a tarball from Mozilla and run it off your $HOME by just clicking the binary anyway and it is easy to upgrade just as you do in other OSes. :)

---

### Post by PaulW2U on 2018-07-07
> **treb0r said:**
> The problem with the lack of Global menu support is the only issue I have encountered. It will be interesting to see the difference in update frequency between the two versions.
I've read elsewhere that such issues are common when running (unofficial) snaps. I'm sure you'll get the Mozilla snap much sooner than the Ubuntu .deb. I don't know if you'll get any extra updates by keeping the snap installed though as I've never bothered to track Firefox point releases making their way into Ubuntu.

---

### Post by treb0r on 2018-07-07
> **monkeybrain20122 said:**
> I don't know what is the point of having two Firefox, and on top of it why would anyone need a snap version of Firefox? You can download a tarball from Mozilla and run it off your $HOME by just clicking the binary anyway and it is easy to upgrade just as you do in other OSes. :)

Well I really just wanted to see how well the snap works and if it gets updated faster than the deb.

I just prefer to use a package manager than deal with tarballs. I did use the tarball of the developer edition for a while.

---

### Post by alanianross on 2018-07-09
Yeah: it's landed. Precisely, in Kubuntu 16.04.4: Firefox 61.0 (64-bit) {canonical-1.0}.

And I wonder what's happened in the transition between the previous 60.x releases, and this one.

This version of Firefox is **EXACTLY THE SAME** I run also in Fedora 28: included the extensions, which I carry along from system to system, by transferring my personal profile in block (say, along such guidelines as those found at <[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)>, and similar). Business as usual.

Now, however, after the most recent system upgrades, in Firefox 61 "vanilla" under Fedora 28 I keep on being able to log into my Google account, and to remain connected to Google until I decide to log out. In Firefox 61 "canonical-1.0" under Kubuntu 16.04, on the contrary, I keep on being thrown out ANY open session (Google, Amazon, whatever), after just a bunch of seconds (I haven't made any measurement: but, I'd say they ALL last for no more than a minute).

I repeat: **SAME EXTENSIONS, SAME SETUP** of the browser.

If somebody can explain how this could happen, I would be happy :(

---

### Post by treb0r on 2018-07-10
So Firefox 61.0.1 was released a few days ago and neither the .deb or snap versions have been updated yet.

There is an open issue on bugzilla about automating the snap release process here:

[https://bugzilla.mozilla.org/show_bug.cgi?id=1297513](https://bugzilla.mozilla.org/show_bug.cgi?id=1297513)

Looks like the tarball is the only way to get the very latest version on release, for now anyway.

---

### Post by PaulW2U on 2018-07-10
> **treb0r said:**
> So Firefox 61.0.1 was released a few days ago and neither the .deb or snap versions have been updated yet.
Try updating again. I updated my Xubuntu 18.04 installation with Firefox 61.0.1 less than five minutes ago.

Edit: Xubuntu 17.10 also now updated.

---

### Post by treb0r on 2018-07-10
> **PaulW2U said:**
> Try updating again. I updated my Xubuntu 18.04 installation with Firefox 61.0.1 less than five minutes ago.

Edit: Xubuntu 17.10 also now updated.

Boom. Snap not updated yet though. Interesting experiment.

---

### Post by la.khan on 2018-07-12
I recd FF 61.0.1 yesterday (11th July) from Canonical, using Software Update.

---

### Post by treb0r on 2018-07-13
> **la.khan said:**
> I recd FF 61.0.1 yesterday (11th July) from Canonical, using Software Update.

Yes, me too.

Strange that the snap has still not updated. I was beginning to think that I had a problem with my system, but when I checked [https://snapcraft.io/firefox](https://snapcraft.io/firefox) it still shows Version: 61.0-3 in the stable channel.

I guess Mozilla are still working to get their snap releases in line with the main tarball releases.

---

### Post by treb0r on 2018-07-18
For anyone who might be interested, the snap has still not updated. I'm going to keep it installed just to see what happens.

The only reason I'm so interested in getting the most up-to-date version of Firefox possible is that I work as web developer and they keep adding cool new stuff to the dev tools.

---

### Post by pauljw on 2018-07-18
> **treb0r said:**
> For anyone who might be interested, the snap has still not updated. I'm going to keep it installed just to see what happens.

The only reason I'm so interested in getting the most up-to-date version of Firefox possible is that I work as web developer and they keep adding cool new stuff to the dev tools.

Have you considered the dev version?  [https://www.mozilla.org/en-US/firefox/channel/desktop/](https://www.mozilla.org/en-US/firefox/channel/desktop/)

Seems that would be a better way to go for a developer.

---

