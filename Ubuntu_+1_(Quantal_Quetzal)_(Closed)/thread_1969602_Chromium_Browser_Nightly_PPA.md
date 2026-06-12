---
title: "Chromium Browser Nightly PPA"
date: 2012-04-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-04-30
I've tried searching (as you do).

I have the Chromium Nightly builds PPA added but this hasn't seen any changes for the last three weeks (same as Dev and Beta PPA). The Stable PPA, however, had a build 12 days ago.

Does anyone know what is happening with these PPAs? I'm having problems running a stable version...

[https://launchpad.net/~chromium-daily]("https://launchpad.net/%7Echromium-daily")

---

### Post by jerrylamos on 2012-04-30
Choices.  That's what it's all about.

First items on a new lubuntu install is synaptic complete removal of chromium which automatically installs firefox. 

Now one of my quantals updates to firefox 12, the other is at firefox 11.  Go figure.  They both work fine, quantal's not broken for me yet...

Jerry

p.s. just updated quantal, Firefox 12 installed fine.

---

### Post by Mathor on 2012-04-30
Sometimes the people uploading to the ppa's get lazy. Keep a lookout for new builds.

---

### Post by CaptainMark on 2012-05-01
yes its the ppa maintainers either being lazy or for whatever reason not updating it, i noticed about 2 months ago its been like that for ages now,
the nightly ppa only updated to version 18 about a week before the stable release, whats more according to the timeline the last update before that was over a year ago

---

### Post by vasa1 on 2012-05-01
[http://askubuntu.com/questions/105102/does-someone-know-why-the-chromium-daily-package-isnt-build-anymore](http://askubuntu.com/questions/105102/does-someone-know-why-the-chromium-daily-package-isnt-build-anymore)

---

### Post by ronacc on 2012-05-01
you can grab the latest unstable (dev) direct from google [ http://www.chromium.org/getting-involved/dev-channel ]( http://www.chromium.org/getting-involved/dev-channel ) it is at 20.1115.1 

it runs fine on amd64 + nvidia sys  .

---

### Post by jfernyhough on 2012-05-01
> **vasa1 said:**
> [http://askubuntu.com/questions/105102/does-someone-know-why-the-chromium-daily-package-isnt-build-anymore](http://askubuntu.com/questions/105102/does-someone-know-why-the-chromium-daily-package-isnt-build-anymore)Thanks! That explains the reason why, glad it's not just because they forgot about it.

> **ronacc said:**
> you can grab the latest unstable (dev) direct from google [ http://www.chromium.org/getting-involved/dev-channel ]("http://www.chromium.org/getting-involved/dev-channel") it is at 20.1115.1 

it runs fine on amd64 + nvidia sys  .That looks promising though it's Chrome and not Chromium. This could have changed but it used to be the case that Chrome sent a lot of information back to Google but Chromium did not. I've noticed that there's a "[COLOR=#303942][FONT=Droid Sans]Automatically send usage statistics and crash reports to Google"[/FONT][/COLOR] checkbox in Chrome settings now, though, so maybe this has changed.

---

### Post by vasa1 on 2012-05-01
> **jfernyhough said:**
> Thanks! That explains the reason why, glad it's not just because they forgot about it.

That looks promising though it's Chrome and not Chromium. This could have changed but it used to be the case that **Chrome sent a lot of information back to Google** but Chromium did not. I've noticed that there's a "[COLOR=#303942][FONT=Droid Sans]Automatically send usage statistics and crash reports to Google"[/FONT][/COLOR] checkbox in Chrome settings now, though, so maybe this has changed.
True but I figure I'd rather have the convenience of having an updated browser (Chrome) with an updated Flash player and an updated PDF reader all in one. "Privacy" is definitely a concern to some people, but I'm taking a chance, that given the numbers involved, Google may not have time to focus on me ;)

---

### Post by ronacc on 2012-05-01
this may help explain the differences between chrome and chromium [ http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome ]( http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome )

edit:  you can turn off reporting ( and also install the extension ghostery to kill off web bugs)

---

### Post by Krause on 2012-05-05
I dunno I think something is up with the Chromium Builds PPA's.

Their Dev and Daily builds havent been updated in 4 weeks and are both on 18.0.1025.151~r130497

Stable and Beta were last updated 4 days ago and are on a slightly newer 18.0.1025.168~r134367

Weird.

---

### Post by Mathor on 2012-05-05
> **jfernyhough said:**
> Thanks! That explains the reason why, glad it's not just because they forgot about it.

That looks promising though it's Chrome and not Chromium. This could have changed but it used to be the case that Chrome sent a lot of information back to Google but Chromium did not. I've noticed that there's a "[COLOR=#303942][FONT=Droid Sans]Automatically send usage statistics and crash reports to Google"[/FONT][/COLOR] checkbox in Chrome settings now, though, so maybe this has changed.

Also, Chrome is based on Chromium, not the other way around. So, if you want the most bleeding-edge, they would be in the Chromium Nightly builds, not the Chrome..

Chromium is Google's testing browser.  Open source testing and closed source release.  That way they can depend on the community to come out with new features, and then use the code for  the next Chrome release.

---

### Post by cimdrap on 2012-05-20
try this [https://launchpad.net/~towolf/+archive/crack](https://launchpad.net/~towolf/+archive/crack)

---

### Post by jfernyhough on 2012-05-20
> **cimdrap said:**
> try this [https://launchpad.net/~towolf/+archive/crack]("https://launchpad.net/%7Etowolf/+archive/crack")Nice. Only one version behind now. :D

---

### Post by VinDSL on 2012-05-20
Nice crack!

Good job, there...  ;)

---

### Post by Gaygerbil on 2012-05-26
> **cimdrap said:**
> try this [https://launchpad.net/~towolf/+archive/crack](https://launchpad.net/~towolf/+archive/crack)

Thanks so much! I was looking for the latest version of Chromium for a while!

---

### Post by w3rt on 2012-05-31
Is there any update on this? would love to have a daily build again.

---

### Post by jfernyhough on 2012-07-10
Ack, Tobias has removed Chromium from his PPA. Probably just as well, it would better to get the "official" PPA back...

---

### Post by balloons on 2012-07-10
> **jfernyhough said:**
> Ack, Tobias has removed Chromium from his PPA. Probably just as well, it would better to get the "official" PPA back...

Yes, his ppa was not intended for anyone else but himself -- he clearly stated this (it wasn't even "pure" upstream source, he had made his own modifications), but people are desperate (like me!) for a working ppa. Of course, I solved the issue by reuniting with firefox (after being impressed so much by firefox mobile).

---

### Post by screaminj3sus on 2012-07-10
I just use official google chrome, it saves a lot of trouble since google has its own repo that's always up to date, and you get the pdf reader, pepper flash, codecs.

You can disable stuff like "Automatically send usage statistics and crash reports to Google" from the chrome settings. I see little reason to use chromium unless you are truly paranoid :)

I've heard chromium is a pain in the *** to build, so you guys may be waiting a while for a reliable ppa.

---

### Post by jbicha on 2012-07-10
Chromium being out of date in Quantal has nothing to do with developers being lazy. It is a difficult package to keep building.

---

### Post by vasa1 on 2012-07-10
> **screaminj3sus said:**
> I just use official google chrome, it saves a lot of trouble since google has its own repo that's always up to date, and you get the pdf reader, pepper flash ...
Me too.
> **screaminj3sus said:**
> 
You can disable stuff like "Automatically send usage statistics and crash reports to Google" from the chrome settings. I see little reason to use chromium

I've heard chromium is a pain in the *** to build, so you guys may be waiting a while for a reliable ppa.
I haven't come across a convincing argument for those who _aren't_ testers or developers to prefer Chromium over Chrome.

Given that browsers now seem to have a fairly rapid release cycle and constantly fiddle with their UIs, keeping updated is going to be a heavy toll on the folks of Ubuntu's  various browser ppa teams. I'm not even sure how necessary these ppas are.

---

### Post by CaptainMark on 2012-07-12
> **guitara said:**
> I solved the issue by reuniting with firefox (after being impressed so much by firefox mobile).

I wish I could say the same, its not fiefox mobile so much that I hated but the gecko engine that just doesnt display any decent mobile sites because they are almost all written for webkit :(

---

### Post by VinDSL on 2012-07-15
> **cimdrap said:**
> try this [https://launchpad.net/~towolf/+archive/crack](https://launchpad.net/~towolf/+archive/crack)

> **jfernyhough said:**
> Ack, Tobias has removed Chromium from his PPA. Probably just as well, it would better to get the "official" PPA back...

Heh!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-15-jul-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-15-jul-2012-1.png")[/INDENT]


> "The reports of my death are greatly exaggerated."
[INDENT][INDENT]~Mark Twain[/INDENT][/INDENT]

---

### Post by jbicha on 2012-07-16
> **vasa1 said:**
> 
I haven't come across a convincing argument for those who _aren't_ testers or developers to prefer Chromium over Chrome.


Chromium is 100% open source. That matters to some people who aren't developers or testers.

Also because Google Chrome is not 100% open source, it cannot be distributed in the normal Ubuntu repositories.

---

### Post by vasa1 on 2012-07-16
> **jbicha said:**
> Chromium is 100% open source. That matters to some people who aren't developers or testers.

Also because Google Chrome is not 100% open source, it cannot be distributed in the normal Ubuntu repositories.

I understand the second part. I don't want to argue about the first part.

---

### Post by screaminj3sus on 2012-07-16
> **jbicha said:**
> 

it cannot be distributed in the normal Ubuntu repositories.

But does that really matter, when installing chrome automatically adds google's repository?

I'd also go so far as to say chrome is more convenient for testers as well, with google's repo its super easy to switch channel. lets say you are using beta and want to switch to dev channe. Running sudo apt-get install google-chrome-unstable automatically uninstalls beta and installs dev.

---

### Post by VinDSL on 2012-07-16
> **jbicha said:**
> Chromium is 100% open source. That matters to some people who aren't developers or testers.

Also because Google Chrome is not 100% open source, it cannot be distributed in the normal Ubuntu repositories.

> **vasa1 said:**
> I understand the second part. I don't want to argue about the first part.
I must say...

The reason I do not use Google Search, Google Chrome, et cetera is my lack of trust in the growing Google-NSA alliance since "911".

I know they're trying to be helpful in the ongoing global cyberwars, but they cannot become the antivirus provider for the world.  Google-NSA, themselves, have been the target of many successful hacking attempts, and I worry about all the info they're collecting, and into whose hands it will ultimately fall.

I sleep better at night, using Chromium & DuckDuckGo -- that's all. ;)

---

### Post by daKoolaid on 2012-07-16
So currently our Chromium choices are version 18 from the repos, or 22 from the random crack ppa. Is that what it boils down to?

---

### Post by paul_in_london on 2012-07-16
> **VinDSL said:**
> I must say...

The reason I do not use Google Search, Google Chrome, et cetera is my lack of trust in the growing Google-NSA alliance since "911".

I know they're trying to be helpful in the ongoing global cyberwars, but they cannot become the antivirus provider for the world.  Google-NSA, themselves, have been the target of many successful hacking attempts, and I worry about all the info they're collecting, and into whose hands it will ultimately fall.

I sleep better at night, using Chromium & DuckDuckGo -- that's all. ;)

I mainly use FF, but (as well as a few other browsers) I also have Iron installed:

[https://www.srware.net/en/software_srware_iron_faq.php](https://www.srware.net/en/software_srware_iron_faq.php)

Latest Linux version:

[https://www.srware.net/forum/viewtopic.php?f=18&t=3755](https://www.srware.net/forum/viewtopic.php?f=18&t=3755)

Btw, this is worth a read:

[The Importance of Anonymity on the Web](www.omgubuntu.co.uk/2012/01/the-importance-of-anonymity-on-the-web)

---

### Post by cariboo on 2012-07-16
> **daKoolaid said:**
> So currently our Chromium choices are version 18 from the repos, or 22 from the random crack ppa. Is that what it boils down to?

I'm running chromium-browser version:

```
Chromium 20.0.1132.47 Ubuntu 12.10
```

Where are you getting version 18 from?

---

### Post by paul_in_london on 2012-07-16
> **cariboo907 said:**
> I'm running chromium-browser version:

```
Chromium 20.0.1132.47 Ubuntu 12.10
```

Where are you getting version 18 from?

The latest version I got before it was apparently pulled from the ppa:

```
paul@quantal-64:~$ apt-cache policy chromium-browser                            
chromium-browser:
  Installed: 22.0.1201.0~r145644-0ubuntu6
  Candidate: 22.0.1201.0~r145644-0ubuntu6
```

---

### Post by daKoolaid on 2012-07-16
> **cariboo907 said:**
> I'm running chromium-browser version:

```
Chromium 20.0.1132.47 Ubuntu 12.10
```Where are you getting version 18 from?

I just refreshed Synaptic, I have                  18.0.1025.168~r134367-0ubuntu0.12.04.1 available. The same as the PPA's stable channel.

---

### Post by VinDSL on 2012-07-16
> **daKoolaid said:**
> I just refreshed Synaptic, I have                  18.0.1025.168~r134367-0ubuntu0.12.04.1 available. The same as the PPA's stable channel.
Must have been in universe, a while back...

```
vindsl@Zuul:~$ apt-cache policy chromium-browser
chromium-browser:
  Installed: 22.0.1201.0~r145644-0ubuntu2~precise
  Candidate: 22.0.1201.0~r145644-0ubuntu2~precise
  Version table:
 *** 22.0.1201.0~r145644-0ubuntu2~precise 0
        500 http://ppa.launchpad.net/towolf/crack/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
     20.0.1132.47~r144678-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/universe i386 Packages
vindsl@Zuul:~$ 

```

---

### Post by hugmenot on 2012-07-17
The 22 version in that PPA is clean.

```
chromium-browser (22.0.1201.0~r145644-0ubuntu2~precise) precise; urgency=low

  * Remove a_few_customized_shortcuts.patch because people started linking to
    my /aptly/ named »random crack« PPA.


```

---

### Post by daKoolaid on 2012-07-17
> **hugmenot said:**
> The 22 version in that PPA is clean.

```
chromium-browser (22.0.1201.0~r145644-0ubuntu2~precise) precise; urgency=low

  * Remove a_few_customized_shortcuts.patch because people started linking to
    my /aptly/ named »random crack« PPA.


```
What do you mean that it's "clean", just that his patch was removed?

Has anyone tried the Chromium snapshots from here?
[http://commondatastorage.googleapis.com/chromium-browser-continuous/index.html](http://commondatastorage.googleapis.com/chromium-browser-continuous/index.html)

---

### Post by cariboo on 2012-07-17
> **daKoolaid said:**
> I just refreshed Synaptic, I have                  18.0.1025.168~r134367-0ubuntu0.12.04.1 available. The same as the PPA's stable channel.

This is the Quantal testing sub-forum, if you have issues with previous versions, use general help.

---

### Post by daKoolaid on 2012-07-17
> **cariboo907 said:**
> This is the Quantal testing sub-forum, if you have issues with previous versions, use general help.
Ah, didn't see Quantal, just found the thread in a search.

---

### Post by FishboyFive on 2012-07-19
doesnt the browser just update every day to the latest version ?

if not they should add that :)

---

### Post by meilin on 2012-09-05
Don't use  Tobias Wolf PPA to get the latest Chromium as its PPA description has said.  While Chromium Team won't release new versions of Chromium browser, [ppa:a-v-shkop/chromium-dev]("https://launchpad.net/~a-v-shkop/+archive/chromium-dev") will try to maintain more-or-less fresh releases of Chromium (now only for Ubuntu 12.04).

Or download the latest version of Chromium from [http://download-chromium.appspot.com/]("http://download-chromium.appspot.com/"), it's a non-installed version. Just extract and run the chrome executable, and then lock to launcher. See also:

[http://handytutorial.com/install-latest-chromium-browser-in-ubuntu/]("http://handytutorial.com/install-latest-chromium-browser-in-ubuntu/")

---

### Post by CaptainMark on 2012-10-10
There is a new ppa by Alex Shkop that has a nice up to date stable branch, and a dev branch,(i havent looked at this one yet)

---

### Post by VinDSL on 2012-10-11
> **CaptainMark said:**
> [...] and a dev branch,(i havent looked at this one yet)
Been running the dev branch, for a week or so.  Works great!

The Tobias Wolf PPA version worked okay, most of the time, but it had issues.  

Can't remember what the issues were (a week or so is a long time in tester's years), but I was about to downgrade to a much older, stable version, when I discovered the Alex Shkop PPA...

```
vindsl@Zuul:~$ apt-cache policy chromium-browser
chromium-browser:
  Installed: 23.0.1271.1~svn20120922r157674-0ubuntu1~quantal1
  Candidate: 23.0.1271.1~svn20120922r157674-0ubuntu1~quantal1

```

---

