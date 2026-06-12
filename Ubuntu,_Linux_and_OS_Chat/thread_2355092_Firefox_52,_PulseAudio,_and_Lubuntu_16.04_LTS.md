---
title: "Firefox 52, PulseAudio, and Lubuntu 16.04 LTS"
date: 2017-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2017-03-09
Firefox 52 on Linux [needs PulseAudio]("https://bugzilla.mozilla.org/show_bug.cgi?id=1247056") to play audio. The [release notes]("https://www.mozilla.org/en-US/firefox/52.0/releasenotes/") don't make mention of this. I think Lubuntu is the only official flavor that does not include PulseAudio by default.

Edit: by official flavors, I mean complete flavors here, *not* minimal installs or server installs :)

Edit 2: changed the title of the thread to include the supported version of Lubuntu which is affected.

---

### Post by asgard2 on 2017-03-09
Pulseaudio is installed, but audio isn't working on ff 52.

```
 dpkg -l | grep pulsea
ii  gstreamer0.10-pulseaudio:amd64        0.10.31-3+nmu4ubuntu2.16.04.2              amd64        GStreamer plugin for PulseAudio
ii  pulseaudio                            1:8.0-0ubuntu3.2                           amd64        PulseAudio sound server
ii  pulseaudio-module-x11                 1:8.0-0ubuntu3.2                           amd64        X11 module for PulseAudio sound server
ii  pulseaudio-utils                      1:8.0-0ubuntu3.2                           amd64        Command line tools for the PulseAudio sound server


```

---

### Post by vasa1 on 2017-03-09
I have```
dpkg -l | grep pulsea
ii  pulseaudio                                  1:8.0-0ubuntu3.2                           amd64        PulseAudio sound server
ii  pulseaudio-module-x11                       1:8.0-0ubuntu3.2                           amd64        X11 module for PulseAudio sound server
ii  pulseaudio-utils                            1:8.0-0ubuntu3.2                           amd64        Command line tools for the PulseAudio sound server
```
I installed PA after upgrading to Fx52 and finding no audio via Fx on Lubuntu 16.04. That fixed it for me.

```
Start-Date: 2017-03-07  21:22:54
Commandline: apt-get install pulseaudio
Requested-By: vasa1 (1000)
Install: libpulsedsp:amd64 (1:8.0-0ubuntu3.2, automatic), pulseaudio:amd64 (1:8.0-0ubuntu3.2), rtkit:amd64 (0.11-4, automatic), libwebrtc-audio-processing-0:amd64 (0.1-3ubuntu1~gcc5.1, automatic), pulseaudio-module-x11:amd64 (1:8.0-0ubuntu3.2, automatic), pulseaudio-utils:amd64 (1:8.0-0ubuntu3.2, automatic), libfftw3-single3:amd64 (3.3.4-2ubuntu1, automatic)
End-Date: 2017-03-07  21:23:27

```

Let's hope someone who knows more about audio comes along.

Meanwhile, if you don't mind, please provide some detail about your OS. Is it Lubuntu?

---

### Post by asgard2 on 2017-03-09
It is lubuntu 16.04 64Bit.
@youtube, firefox gives me a message at the top, that I may need to install "PulseAudio", it is not detected.

> $ ps aux | grep pulseaudio
asgard2      1747  0.0  0.3 420160 11276 ?        S<l  10:29   0:00 /usr/bin/pulseaudio --start --log-target=syslog
asgard2      4408  0.0  0.0  15796   988 pts/2    S+   13:04   0:00 grep --color=auto pulseaudio


Maybe this is the problem:
> $ sudo service pulseaudio restart
Failed to restart pulseaudio.service: Unit pulseaudio.service not found.



---

### Post by vasa1 on 2017-03-09
> **asgard2 said:**
> It is lubuntu 16.04 64Bit.
@youtube, firefox gives me a message at the top, that I may need to install "PulseAudio", it is not detected.
...
Yes, I saw that as well and, after installing pulseaudio, I didn't have to run```
sudo service pulseaudio restart
```I just restarted Firefox and could get audio on YouTube.

Let's see what other Lubuntu users experience.

---

### Post by Ahunt on 2017-03-09
You can note that there is a year old Firefox bug on this marked closed: 

* [Firefox Bug 1247056]("https://bugzilla.mozilla.org/show_bug.cgi?id=1247056")

and two brand new bugs:

* [Firefox Bug 1345661]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661")
* [Firefox Bug 1345439]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345439")

---

### Post by vasa1 on 2017-03-09
> **Ahunt said:**
> You can note that there is a year old Firefox bug on this marked closed: 

* [Firefox Bug 1247056]("https://bugzilla.mozilla.org/show_bug.cgi?id=1247056")

and two brand new bugs:

* [Firefox Bug 1345661]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661")
* [Firefox Bug 1345439]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345439")
Bug 1345439 is about the wrong url being linked to in the pop-up.

The direction Firefox is heading, my guess is Bug 1345661 will soon be marked a WontFix.

---

### Post by Ahunt on 2017-03-09
> **vasa1 said:**
> Bug 1345439 is about the wrong url being linked to in the pop-up.

The direction Firefox is heading, my guess is Bug 1345661 will soon be marked a WontFix.

Since the [original bug from a year ago]("https://bugzilla.mozilla.org/show_bug.cgi?id=1247056") was closed and they bashed ahead with dropping ALSA support over the objections made, I agree that it will likely be marked as "wontfix".

This leaves the Lubuntu devs with a dilemma, since the default browser now has no sound with the default audio instalation, ALSA. They may decide to provide pulseaudio as one way to fix this through the update process.

Other possible fixes the user can do is install pulse audio as you noted above, or use another browser. I am using Chromium 56 from the repos and it is working just fine.

One comment from the original Mozilla bug is worth quoting, as Thomas Wisniewski said:

> I'm sure I'm not the only one would rather not suffer PulseAudio on their systems, given that Firefox would be the only software (including other browsers) that would have it as a hard requirement (and given that PulseAudio still does not run well on some of the systems where I use Firefox as my main browser).

---

### Post by vasa1 on 2017-03-09
> **Ahunt said:**
> ...
This leaves the Lubuntu devs with a dilemma, since the default browser now has no sound with the default audio instalation, ALSA. They may decide to provide pulseaudio as one way to fix this through the update process.
...
There's still no discussion of this issue as of March 10 2017 in the [Lubuntu users mailing list]("https://lists.ubuntu.com/archives/lubuntu-users/2017-March/date.html") or in the [developers' mailing list]("https://lists.ubuntu.com/archives/lubuntu-devel/"). Maybe it's being discussed in some Facebook group. IDK.

As for ALSA and PulseAudio, such discussions turn warm quite fast so I hope this thread doesn't morph into one of those ;)

---

### Post by Ahunt on 2017-03-09
If you do see anything on the dev mailing lists it would be great if you could post it here for the record!

I was going to file a bug on this for Lubuntu, but not sure what to file it against. Firefox would be obvious but it works fine on all flavours but Lubuntu. It isn't really appropriate to tag ALSA, since it works fine or PulseAudio, since it isn't the problem and isn't even installed. I am was hoping that the Lubuntu devs would be using the default browser on Lubuntu themselves and would quickly notice the issue. Perhaps they have but there isn't an obvious solution beyond installing PulseAudio.

I am keeping an eye on the updates to see if anything gets pushed out to fix this.

Don't worry I certainly won't get into a PulseAudio vs ALSA flame war. I don't have a horse in that race.

---

### Post by vasa1 on 2017-03-09
> **Ahunt said:**
> If you do see anything on the dev mailing lists it would be great if you could post it here for the record!
...
Both mailing lists are viewable without the need to sign in. In other words, anyone can read them. Signing up isn't too difficult for the users' list. I don't know what the requirements are for the dev list.

Someone has filed a bug: [PulseAudio requirement breaks Firefox on ALSA-only systems]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671273")

If you have a Launchpad account, you can mark the bug "affects me too".

---

### Post by Ahunt on 2017-03-10
Super, thanks for finding that Ubuntu bug! I have marked it as affecting me. As noted there it may be possible for the Ubuntu version of Firefox to be recompiled with "--enable-alsa" as one possible solution to this issue.

---

### Post by Ahunt on 2017-03-10
There are also some other solutions being discussed on Mozilla Support at [No ALSA support after upgrade to 52?]("https://support.mozilla.org/t5/Firefox/No-ALSA-support-after-upgrade-to-52/m-p/1372446#M1037477"). At least people have noticed!

---

### Post by vasa1 on 2017-03-10
> **Ahunt said:**
> There are also some other solutions being discussed on Mozilla Support at [No ALSA support after upgrade to 52?]("https://support.mozilla.org/t5/Firefox/No-ALSA-support-after-upgrade-to-52/m-p/1372446#M1037477"). At least people have noticed!
Those require compiling, if I understood the posts correctly. That would be beyond the "average" user and require recompiling for each update.

---

### Post by Ahunt on 2017-03-10
Yes, absolutely! Most of what is being discussed in the various bug reports and such are all dev-level fixes. So far, for the average Lubuntu user we only have two possible fixes: 

1. Install PulseAudio, with whatever minuses or risks that comes with.
2. Use a different browser.

---

### Post by vasa1 on 2017-03-10
> **Ahunt said:**
> Yes, absolutely! Most of what is being discussed in the various bug reports and such are all dev-level fixes. So far, for the average Lubuntu user we only have two possible fixes: 

1. Install PulseAudio, with whatever minuses or risks that comes with.
2. Use a different browser.
I think the Lubuntu devs consciously avoided going with PulseAudio. There may have been some discussion of the rationale when the decision was made but it's going to be hard to dig out.

I've been using Google Chrome for the past month or so after trying out Vivaldi. Firefox (with PulseAudio installed) is now a fallback.

Let's see what Canonical decides because Firefox is in "main".

---

### Post by Ahunt on 2017-03-10
I agree it does look like the Lubuntu devs avoided PulseAudio intentionally. It certainly does have its detractors on-line, who seem to cite performance and stability issues. Like you I have gone with a different browser, rather than installing PulseAudio for now.

The devs have several ways of fixing this at a distro level, but it does need addressing there in some way soon. You can't provide an ISO file that, when installed, provides a broken browser by default! I am keen to hear what the devs have to say.

---

### Post by poorguy on 2017-03-10
Is there a security risk using Pulse Audio or what seems to be the issue it.
I'm confused.

It is installed in my Debian Based Distros and is working well with FF 52.0 no problems with youtube audio.

---

### Post by yoshii on 2017-03-10
I also had problems getting PulseAudio to work within Lubuntu 16.04.2 64-bit
I even tried to install some XFCE stuff, but everything worked except PulseAudio, even after removing all traces of PulseAudio and reinstalling.  
Eventually I gave up and tried a different Ubuntu version, and I don't have that problem.  It's too bad, because I like Lubuntu for other reasons.  

Nevertheless PCmanFM and Gnome-Disk-Utility (disks) can still be installed on the other Ubuntus.  So at least those are OK.  
I even use Lubuntu Software Center for some things too.  It's not foolproof, but it does offer some goodies not found elsewhere.

---

### Post by Ahunt on 2017-03-10
I haven't seen any evidence of security issues with installing PulseAudio, just issues of whether it works reliably or not.

---

### Post by PaulBx on 2017-03-10
I sure noticed this (Lubuntu 16.04LTS 64-bit). Interestingly, the note you get at the top of the page when you try to run a youtube points at a mozilla support page that doesn't exist.

"dpkg -l | grep pulsea"'
You get more results with "dpkg -l | grep -i pulsea". I show libpulse-mainloop-glib0 and libpulse0. I was going to try removing them and then installing pulseaudio completely but the vast number of packages involved discouraged me. I'm thinking of dumping firefox (my old seamonkey install plays youtubes just fine).

---

### Post by Ahunt on 2017-03-10
[Firefox Bug 1345439]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345439") is actually about the fact that the pop up bar URL leads to a non-existent page. Really doesn't help users!

---

### Post by Yellow Pasque on 2017-03-11
> **vasa1 said:**
> Those require compiling, if I understood the posts correctly. That would be beyond the "average" user and require recompiling for each update.

Debian and/or Lubuntu could build firefox with --enable-alsa so it could continue to use the old ALSA/asound backend. That would only be a stopgap measure though, since Mozilla devs are looking to drop the asound backed completely in FF 54. Some options:

1. Use a different default browser
2. Use pulseaudio in Lubuntu
3. Use some sort of pulseaudio emulation: [https://github.com/i-rinat/apulse](https://github.com/i-rinat/apulse) is an option. Its dev (the same one that developed the freshplayer plugin) claims no further development is planned, but there have been a bunch of commits in the past few days, possibly because of this FF change.
4. There may be some community effort to maintain the asound backend, and that could be patched in for a Lubuntu version of FF. They may not be able to use the Firefox branding/logo for it (bring back the iceweasel?).

> Since the original bug from a year ago was closed and they bashed ahead with dropping ALSA support over the objections made, I agree that it will likely be marked as "wontfix".

Yeah, they seem pretty dismissive of users who don't want/need pulseaudio.

---

### Post by poorguy on 2017-03-11
What a bummer now I have to find a different distro for the laptop I just installed Lubuntu on. :-k

I'm beginning to HATE Mozilla as much as I HATE Google Chrome.

---

### Post by Ahunt on 2017-03-11
> **poorguy said:**
> What a bummer now I have to find a different distro for the laptop I just installed Lubuntu on. :-k

I'm beginning to HATE Mozilla as much as I HATE Google Chrome.

If you like Lubuntu (like I do) you could just use another browser. There are many to choose from.

---

### Post by poorguy on 2017-03-11
> **Ahunt said:**
> If you like Lubuntu (like I do) you could just use another browser. There are many to choose from.
You are right and I do like Lubuntu.

I just need to do some browser investigation.

I don't use the laptop except when I'm out and about so FF can still be used for standard browsing.

Just a minor irritation.

---

### Post by Ahunt on 2017-03-11
> **poorguy said:**
> You are right and I do like Lubuntu.

I just need to do some browser investigation.

I don't use the laptop except when I'm out and about so FF can still be used for standard browsing.

Just a minor irritation.

As long as you never use sound on your laptop, then Firefox will work okay.

As noted earlier in this thread, other users have just switched browsers. One mentioned installing Vivaldi or Chrome directly. The repos also offer Chromium (which I am now using), Web (package name = *epiphany-browser*) and Midori, among other options.

---

### Post by Yellow Pasque on 2017-03-11
I just upgraded to FF 52 on my Debian sid install. I then installed apulse, which I mentioned in my previous post. So far, it seems to be working well, so it may be something you want to try if you really like Firefox and Lubuntu.

---

### Post by u._newbie on 2017-03-11
> **vasa1 said:**
> Firefox 52 on Linux [needs PulseAudio]("https://bugzilla.mozilla.org/show_bug.cgi?id=1247056") to play audio. The [release notes]("https://www.mozilla.org/en-US/firefox/52.0/releasenotes/") don't make mention of this. I think Lubuntu is the only official flavor that does not include PulseAudio by default.

My vanilla Ubuntu 16.04.2 LTS does not have PulseAudio installed either. Probably because it was a server install.

---

### Post by vasa1 on 2017-03-11
> **u._newbie said:**
> My vanilla Ubuntu 16.04.2 LTS does not have PulseAudio installed either. Probably because it was a server install.

Thanks! I fixed my post to exclude minimal installs and servers ;)

---

### Post by Ahunt on 2017-03-14
Just for anyone continuing to follow this thread, the debate is all happening over on the [Mozilla bug page]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661"). Mostly it is a lot of complaints from users and defensiveness from devs, but no new solutions in the immediate offing.

---

### Post by Yellow Pasque on 2017-03-14
Has anyone made a PPA yet to build FF with --enable-alsa?

---

### Post by Ahunt on 2017-03-14
It has been discussed, but not done yet. See for instance [Comment 54 on the Firefox bug discussion]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661").

---

### Post by John_Patrick_Mason on 2017-03-14
OK, semi-noob here. What commands do I need to input to install AudioPulse.

When I type:

```
dpkg -l | grep pulsea
```

I get nothing. No output.

---

### Post by Ahunt on 2017-03-14
How about:

```
$ sudo apt install pulseaudio
```

---

### Post by asgard2 on 2017-03-15
If it is only a recomplile with "--enable-alsa", why is the ubuntu team not just recompling firefox directly at the ubuntu repository?

Almost a week now with a broken firefox and nothing happened ... :sad:

---

### Post by Ahunt on 2017-03-15
> **asgard2 said:**
> If it is only a recomplile with "--enable-alsa", why is the ubuntu team not just recompling firefox directly at the ubuntu repository?

Almost a week now with a broken firefox and nothing happened ... :sad:

That is a good question! The Ubuntu Firefox bug was filed a week ago and is found [here]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671273"). It has been rated "importance: High"  and "status: Confirmed", but it is still "Unassigned" to anyone to fix. I don't think it will get fixed until someone is assigned to address it.

---

### Post by Ahunt on 2017-03-15
It is worth noting that over on the Mozilla bug on this issue, the dev who initiated ending ALSA support on Firefox, Anthony Jones, has [now replied]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661#c83") to many of the comments and questions raised. His opening statement however summarizes where Mozilla is going with this as he says, "TL;DR We're trying to do what is best for Linux and Firefox, so please file bugs if you have Pulse Audio issues."

Basically Mozilla isn't going to fix this, they want you to install PulseAudio. From an average Lubuntu user point of view it seems we have the choice of installing PulseAudio and seeing if it works or not and filing bugs if it doesn't, or switching to another browser. Judging by the comments in the various bug reports and forums it seems that most users have had enough problems with PulseAudio that they are switching browsers instead. 

Any other action will have to come from the Ubuntu devs as a response to the [Ubuntu bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671273") on this issue.

---

### Post by vasa1 on 2017-03-15
> **asgard2 said:**
> If it is only a recomplile with "--enable-alsa", why is the ubuntu team not just recompling firefox directly at the ubuntu repository?

Almost a week now with a broken firefox and nothing happened ... :sad:```
sudo apt-get install --reinstall pulseaudio
```may fix a bad install.

As to why they aren't "fixing" things, it maybe that they agree with Mozilla's thinking. I've changed browsers, not because of PulseAudio, but because I believe that the devs will move to [Web Extensions come Fx57]("https://ubuntuforums.org/showthread.php?t=2350907") and, in the process, cause an extension I rely on to be deprecated.

---

### Post by asgard2 on 2017-03-15
@vasa1: I already tried, it does not fix it.

Pale Moon is the v27 (from Firefox), it is too old to install all my required plugins, for example noscript.
I tried the tar archiv, from [palemoon]("http://linux.palemoon.org/download/mainline/"), the yt videos don't start ... no luck

---

### Post by Yellow Pasque on 2017-03-15
Again, try apulse. First, build it:
```
sudo apt-get install build-essential git pkg-config libasound2-dev libglib2.0-dev cmake
cd ~/     #or whatever directory you want to use
git clone https://github.com/i-rinat/apulse.git
cd apulse/
mkdir build && cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release ..
make
sudo make install
```
Then, try it:
```
apulse firefox
```
Sound?

---

### Post by Ahunt on 2017-03-15
It seems that the management at Mozilla is not happy with [the response that they are getting to this issue]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661#c98").

---

### Post by chaleep on 2017-03-15
@Temüjin: In **Linux Mint 17.3 MATE, 64bit (basing on Ubuntu 14.04 LTS)** we get following error-messages in log while trying to build apulse:
```

~/apulse/build > cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=trusty
-- The C compiler identification is GNU 4.8.5
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Found PkgConfig: /usr/bin/pkg-config (found version "0.26") 
-- checking for modules 'glib-2.0;alsa'
--   found glib-2.0, version 2.40.2
--   found alsa, version 1.0.27.2
-- Configuring incomplete, errors occurred!
See also "/home/studio/apulse/build/CMakeFiles/CMakeOutput.log".
See also "/home/studio/apulse/build/CMakeFiles/CMakeError.log".
```

[B]Cmake-error.log:
[/B]
```
Compiling the CXX compiler identification source file "CMakeCXXCompilerId.cpp" failed.
Compiler: CMAKE_CXX_COMPILER-NOTFOUND 
Build flags: 
Id flags: 


The output was:
No such file or directory




Compiling the CXX compiler identification source file "CMakeCXXCompilerId.cpp" failed.
Compiler: CMAKE_CXX_COMPILER-NOTFOUND 
Build flags: 
Id flags: -c


The output was:
No such file or directory




Checking whether the CXX compiler is IAR using "" did not match "IAR .+ Compiler":

```

This was the third time to try skype and now firefox running without Pulseaudio using apulse and i give up!

Maybe my system (and its compiler) is not compatible with apulse.

Also it's something like a "hack" and an app with alpha-status. 

It's a little workaround that maybe works for some users - but could NOT be the solution to this mind**** Mozilla gave to pure ALSA-based-Linux-systems now.

Not a solution for not-advanced beginners.

I have little hope that Mozilla returns to supporting ALSA again and i can't understand this decision they made.

The main reason for this (too much work with ALSA!? and 5.1 surround-sound with Pulseaudio..) is a bad promotion in Linux world.
 

@asgard: as we affected from this "bug" too and have to rebuild our little distro again because of this - we found many great browser-alternatives.

**Palemoon, Midori and Vivaldi **are our favourites at this time: [http://mayastudio.tumblr.com/firefox52](http://mayastudio.tumblr.com/firefox52)


For **Palemoon** there existing some great** PPA** for Ubuntu and Linux Mint users: 

[https://software.opensuse.org/download.html?project=home%3Astevenpusser&package=palemoon](https://software.opensuse.org/download.html?project=home%3Astevenpusser&package=palemoon)

unmaintend:
[https://launchpad.net/~marian.kadanka/+archive/ubuntu/palemoon](https://launchpad.net/~marian.kadanka/+archive/ubuntu/palemoon)

---

### Post by chaleep on 2017-03-15
**Palemoon** is really great and basing on Firefox (ESR) code - but has independent development!

Really oldschool, lightweight and powerful and compatible to a lot of firefox themes and plugins:

(httpseverywhere, ublock, noscript..)

Also they have own plugins and htemes.


**Vivaldi** (basing on Chrome) is really fast, powerful and nice too!


**Midori and Epiphany (Gnome-Browser) **really minimalistic and fast.


So there are much alternatives. :)


To install Pulseaudio -just because of firefox - is no option for me for many reasons.

I thought the ALSA vs. Pulseaudio-debate was going really silently - but Microsofts Skype and Mozillas FF bring it back to the masses.

lol.

Where is the problem to accept, that ALSA is the main sounddriver in most Linux distros and has to be used from every app.

PA is just a sound-server for desktop-use and the Jack-Audio-Connection-Kit for proffesional audio-use.

I love this modular way and freedom to choose the right soundsystem under Linux for my needs.

And will boycott big companys that don't respect the Linux-standard or want to compromise it, while pushing PA as a hard dependency.

---

### Post by Yellow Pasque on 2017-03-15
> **chaleep said:**
> get following error-messages in log while trying to build apulse:
```

CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.

```


You don't have g++ installed?

---

### Post by Ahunt on 2017-03-16
For anyone who hasn't been reading the [Mozilla bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661") on this issue it has become pretty clear in the last two days that a fix will not be coming from Mozilla. They closed the bug commenting to outside users, limiting it to the developer who removed the ALSA support in the first place. He has replied, basically dismissing all complaints. So far the bug remains open, but he has said about restoring ALSA support "That isn't going to happen. Sorry."

At this point it looks like it will fall to the Ubuntu devs to come up with some sort of fix to this, although the [Ubuntu bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671273") remains unassigned and unaddressed. Perhaps they were waiting to see what Mozilla would conclude?

Otherwise it is up to the users to solve by either installing Pulse Audio or a new browser.

---

### Post by jbicha on 2017-03-16
> **asgard2 said:**
> Pulseaudio is installed, but audio isn't working on ff 52.
ii  gstreamer0.10-pulseaudio:amd64        0.10.31-3+nmu4ubuntu2.16.04.2              amd64        GStreamer plugin for PulseAudio
[/codE]

You probably need gstreamer**1.0**-pulseaudio

---

### Post by poorguy on 2017-03-16
> **Ahunt said:**
> If you like Lubuntu (like I do) you could just use another browser. There are many to choose from.
I understand why all of this is happening and don't like it and no change if any at all from the Lubuntu Devs or Mozilla.
[COLOR=#0000ff]this is not a bashing comment towards Lubuntu Devs or Mozilla.[/COLOR] 

It's easier to use Chromium Browser then try to fix a problem I didn't create.

Lubuntu still rocks IMO. :guitar:

Mozilla. [-X

---

### Post by vasa1 on 2017-03-16
> **poorguy said:**
> I understand why all of this is happening and don't like it and no change if any at all from the Lubuntu Devs or Mozilla.
[COLOR=#0000ff]this is not a bashing comment towards Lubuntu Devs or Mozilla.[/COLOR] 

It's easier to use Chromium Browser then try to fix a problem I didn't create.

Lubuntu still rocks IMO. :guitar:

Mozilla. [-XJust to clarify, I'm not sure the Lubuntu devs can, in reality, do anything about this even if they could do so theoretically. Firefox is in "main" and that means it is up to the Canonical devs to do whatever they think fit. I further understand that Canonical has some sort of working agreement with Mozilla about how things should be handled. It's *possible* that compiling Firefox with --enable-alsa (or whatever) isn't permissible even though certain other customizations are allowed.

Edit: 
I just read [URL="http://www.omgubuntu.co.uk/2017/03/firefox-52-no-sound-pulseaudio-alsa-linux"]Firefox Goes PulseAudio Only, Leaves ALSA Users With No Sound
A change they left out of the release notes[/URL]> Lubuntu 16.04 LTS is one of the distros that use ALSA by default. Lubuntu users who upgraded to Firefox 52 through the regular update channel were, without warning, left with a web browser that plays no sound.

Lubuntu 16.10 users are not affected as the distro switched to PulseAudio. The OMG article points out that the dropping of Alsa was not mentioned in the Release Notes which sort of jives with the feeling that some long-time Firefox users have that things aren't the same over at Mozilla vis-à-vis openness :(

BTW, [Ahunt]("https://ubuntuforums.org/member.php?u=282201") has been thanked and that implies, to me, that OMG too would have not known about the dropping of Alsa.

---

### Post by Ahunt on 2017-03-16
> **poorguy said:**
> I understand why all of this is happening and don't like it and no change if any at all from the Lubuntu Devs or Mozilla.
[COLOR=#0000ff]this is not a bashing comment towards Lubuntu Devs or Mozilla.[/COLOR] 

It's easier to use Chromium Browser then try to fix a problem I didn't create.

Lubuntu still rocks IMO. :guitar:

Mozilla. [-X

I agree, Lubuntu 16.04 LTS has been almost flawless, right from its release. 

This problem was created upstream by Mozilla developers. As they made it clear, they decided to remove ALSA support on the basis that Firefox telemetry showed very few users not using PulseAudio already. They failed to realize that the telemetry data was very flawed, in part because widely used distros, like Lubuntu and Puppy Linux, disable Firefox telemetry by default (for privacy reasons, I presume) and thus they missed that several million users would be affected. Even though they [admitted the error]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661#c122"), they have indicated that they are not going to fix this.

We have yet to hear from the Lubuntu developers on what they will do about this, but they have several options. They could push out PulseAudio (unlikely), could change default browsers to one that works with ALSA , could recompile Firefox 52 with ALSA support (at least for now) or perhaps other possibilities. Ironically Lubutu's default browser up until Lubuntu 13.10 was Chromium.

In the meantime it is up to us mere users to solve this for ourselves. Installing a new browser is the easiest solution by far. So far I am actually enjoying using Chromium 56, it actually works very well.

---

### Post by Ahunt on 2017-03-16
> **vasa1 said:**
> 
BTW, [Ahunt]("https://ubuntuforums.org/member.php?u=282201") has been thanked and that implies, to me, that OMG too would have not known about the dropping of Alsa.

Um, yeah, OMG hadn't heard about the issue either. I might have let them know...

---

### Post by vasa1 on 2017-03-16
> **Ahunt said:**
> ... on the basis that Firefox telemetry ...
The issue with telemetry, on any OS, is that knowledgeable users may disable it. So telemetry data maybe derived largely from users who don't know or don't care.

That's possibly why Mozilla can make statements like [40% of its users don't use any extensions]("http://www.ghacks.net/2016/01/06/surprise-40-of-firefox-users-dont-use-add-ons/") :(

---

### Post by Ahunt on 2017-03-16
> **vasa1 said:**
> The issue with telemetry, on any OS, is that knowledgeable users may disable it. So telemetry data maybe derived largely from users who don't know or don't care.

That's possibly why Mozilla can make statements [like 40% of its users don't use any extensions]("http://www.ghacks.net/2016/01/06/surprise-40-of-firefox-users-dont-use-add-ons/") :(

That seems to have been the really big mistake in the rush to push this through, not realizing that the data was very poor.

Sneddon's article on OMG says that Lubuntu 16.10 introduced Pulse Audio, but [the release notes]("https://wiki.ubuntu.com/YakketyYak/ReleaseNotes/Lubuntu") make no mention of that, while noting much more minor things. Is that right or not?

---

### Post by vasa1 on 2017-03-16
> **Ahunt said:**
> ...
Sneddon's article on OMG says that Lubuntu 16.10 introduced Pulse Audio, but [the release notes]("https://wiki.ubuntu.com/YakketyYak/ReleaseNotes/Lubuntu") make no mention of that, while noting much more minor things. Is that right or not?
I was too embarrassed to admit it, but I visited "Lubuntu Offical" on Facebook which needs you to register before access.

And, a dev team member did say something related but didn't mention the version.

---

### Post by sudodus on 2017-03-17
I checked in current Lubuntu versions and the next version (Zesty Zapus to become 17.04)

14.04.1: alsamixer
16.04.1: alsamixer
16.04.2: alsamixer

16.10: pulseaudio
17.04: pulseaudio

-o-

I have been installing pulseaudio and pavucontrol into Lubuntu for several years because it is so much easier to configure (and my computers are powerful enough to work well with pulseaudio). But I understand that there can be reasons to use alsamixer.

---

### Post by poorguy on 2017-03-17
> **vasa1 said:**
> Just to clarify, I'm not sure the Lubuntu devs can, in reality, do anything about this even if they could do so theoretically. Firefox is in "main" and that means it is up to the Canonical devs to do whatever they think fit. I further understand that Canonical has some sort of working agreement with Mozilla about how things should be handled. 

[IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **poorguy** [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13621354#post13621354")                 
I understand why all of this is happening and don't like it and no change if any at all from the [COLOR=#0000ff]Lubuntu[/COLOR] Devs or Mozilla.
[COLOR=#0000ff]this is not a bashing comment towards Lubuntu Devs or Mozilla.[/COLOR] 

Perhaps I was wrong in using Lubuntu in my comment above and should have said:

I understand why all of this is happening and don't like it and no change if any at all from the[COLOR=#0000ff] Canonical [/COLOR]Devs or Mozilla.
[COLOR=#0000ff]this is not a bashing comment towards Lubuntu Devs or Mozilla.
[/COLOR] 
I understand that we are not consumers / customers and this open-source OS is given to end-users free of charge.

I also have to agree with vasa1 as Lubuntu Devs pretty much are at the hands of Canonical Devs and Mozilla Devs.

 Canonical and Mozilla are "Typical Big Corporations" and are going to do what benefits them without concern for the end-user.
[COLOR=#0000ff]this is not a bashing comment just reality[/COLOR]

---

### Post by Ahunt on 2017-03-17
> **sudodus said:**
> I checked in current Lubuntu versions and the next version (Zesty Zapus to become 17.04)

14.04.1: alsamixer
16.04.1: alsamixer
16.04.2: alsamixer

16.10: pulseaudio
17.04: pulseaudio

-o-

I have been installing pulseaudio and pavucontrol into Lubuntu for several years because it is so much easier to configure (and my computers are powerful enough to work well with pulseaudio). But I understand that there can be reasons to use alsamixer.

Well that is interesting. That is by far a big enough change that it should have been mentioned in the release notes for Lubuntu 16.10, you would think.

Then again removing ALSA support was apparently not a big enough deal for Mozilla to mention in their release notes for Firefox 52...

---

### Post by sudodus on 2017-03-17
@Ahunt,

I think the Lubuntu team would be happy if you volunteer and help to write/edit the release notes :-)

[Contribute_to_Lubuntu](https://wiki.ubuntu.com/Lubuntu#Contribute_to_Lubuntu)

---

### Post by Ahunt on 2017-03-17
> **sudodus said:**
> @Ahunt,

I think the Lubuntu team would be happy if you volunteer and help to write/edit the release notes :-)

[Contribute_to_Lubuntu](https://wiki.ubuntu.com/Lubuntu#Contribute_to_Lubuntu)

Probably more help is always appreciated!

---

### Post by Ahunt on 2017-03-19
New version just released, Firefox 52.0.1. No it doesn't fix the ALSA issue, [just some security fixes]("https://www.mozilla.org/en-US/firefox/52.0.1/releasenotes/").

---

### Post by vasa1 on 2017-03-19
> **Ahunt said:**
> New version just released, Firefox 52.0.1. No it doesn't fix the ALSA issue, [just some security fixes]("https://www.mozilla.org/en-US/firefox/52.0.1/releasenotes/").
At least one fix relates to the Pwn2Own contest:
[https://ubuntuforums.org/showthread.php?t=2355757&p=13621975#post13621975](https://ubuntuforums.org/showthread.php?t=2355757&p=13621975#post13621975)

---

### Post by Ahunt on 2017-03-19
> **vasa1 said:**
> At least one fix relates to the Pwn2Own contest:
[https://ubuntuforums.org/showthread.php?t=2355757&p=13621975#post13621975](https://ubuntuforums.org/showthread.php?t=2355757&p=13621975#post13621975)

That is really quite interesting. Thanks for finding that! :)

---

### Post by Ahunt on 2017-03-22
At last this issue has been brought directly to the Lubuntu devs, by Simon Quigley, who posted to the [Lubuntu dev list]("https://lists.ubuntu.com/archives/lubuntu-devel/2017-March/subject.html") with [this post today]("https://lists.ubuntu.com/archives/lubuntu-devel/2017-March/000994.html"). I think he has hit the main issue and possible solutions, so let's see what the response is!

---

### Post by Ahunt on 2017-03-22
A [request has also been made]("https://groups.google.com/forum/#!topic/mozilla.dev.platform/jRAqSTri66I") by Botond Bello on the original Google Groups discussion that Mozilla reconsider the decision on the basis that the original decision was based on bad telemetry data.

---

### Post by vasa1 on 2017-03-22
Thanks for the links.

[An earlier post]("https://groups.google.com/d/msg/mozilla.dev.platform/jRAqSTri66I/ixtsD3k_BgAJ") in that Google group is this: > This is a good point. We worked with Ubuntu to make sure that we are 
receiving Telemetry from there, but for other distributions it is not very 
clear. 

This gives an overview of the current incoming Telemetry for Linux (from a 
1% sample of our data, "canonical" is the Ubuntu distribution): 
[https://sql.telemetry.mozilla.org/queries/678#table](https://sql.telemetry.mozilla.org/queries/678#table) 
Also keep in mind, unless using opt-out probes, that the opt-in rates for 
Telemetry are low: 
[https://sql.telemetry.mozilla.org/queries/682#table](https://sql.telemetry.mozilla.org/queries/682#table) Whatever that means.

I will keep Firefox as a backup browser.

---

### Post by Ahunt on 2017-03-22
The Lubuntu dev list is at least getting [some traffic]("https://lists.ubuntu.com/archives/lubuntu-devel/2017-March/subject.html") on the subject!

---

### Post by Ahunt on 2017-03-23
It looks like the Lubuntu devs [have some solutions]("https://lists.ubuntu.com/archives/lubuntu-devel/2017-March/001000.html"). In the short term they will recompile Firefox to re-enable ALSA support and are looking at switching browsers as a longer term solution.

---

### Post by Yellow Pasque on 2017-03-23
I think they should just use Firefox 52.x ESR (built with --enable-alsa) as the default Lubuntu 16.04.x browser. At least they know that it will have ALSA support built in until 2018. At that time, Firefox 60 will be out and the devs will have a better idea of where this whole thing is heading.

---

### Post by Ahunt on 2017-03-23
One of the ironies here is that from its inception until the 13.10 release, Lubuntu's default browser was Chromium.

---

### Post by Yellow Pasque on 2017-03-23
Ubuntu devs were considering switching to Chromium/Chrome at one point. IIRC, Shuttleworth was a big fan.

---

### Post by sudodus on 2017-03-23
Chromium-browser has abandoned 32-bit architecture, which is necessary for some of the computers, that are running Lubuntu. So it is not an option. Maybe light-weight Midori would be an option, if people cannot use PulseAudio in their [old] computers. But compiling Firefox with --enable-alsa seems a better alternative.

---

### Post by Ahunt on 2017-03-23
> **Temüjin said:**
> Ubuntu devs were considering switching to Chromium/Chrome at one point. IIRC, Shuttleworth was a big fan.

That was back at Ubuntu 13.10 *Saucy Salamander*, which was when Lubuntu went to Firefox. Articles on that from 2013:

[LIST]
[*][Chromium Likely to Replace Firefox As Default Browser in Ubuntu 13.10]("http://www.omgubuntu.co.uk/2013/05/chromium-to-replace-firefox-as-default-browser-in-ubuntu") 
[*][Firefox To Remain Default Browser in Ubuntu 13.10]("http://www.omgubuntu.co.uk/2013/08/firefox-to-remain-default-browser-in-ubuntu-13-10")
[/LIST]

---

### Post by Ahunt on 2017-03-23
> **sudodus said:**
> Chromium-browser has abandoned 32-bit architecture, which is necessary for some of the computers, that are running Lubuntu. So it is not an option. Maybe light-weight Midori would be an option, if people cannot use PulseAudio in their [old] computers. But compiling Firefox with --enable-alsa seems a better alternative.

The main issue with just compiling with "--enable-alsa" is that Mozilla is planning to remove all ALSA code by Firefox 56, which is due out mid-2017. It would work up until then.

I have used Midori and it is "okay", but lacks a lot of features people expect in a browser.

---

### Post by sudodus on 2017-03-23
> **Ahunt said:**
> The main issue with just compiling with "--enable-alsa" is that Mozilla is planning to remove all ALSA code by Firefox 56, which is due out mid-2017. It would work up until then.
Unless the developers from Canonical can make them change their minds.> 
I have used Midori and it is "okay", but lacks a lot of features people expect in a browser.

Yes Midori is light-weight - lacks features that some people expect in a browser. But it a good alternative for old or weak computers.

Compare with the office programs: Lubuntu comes with Abiword and Gnumeric which are light-weight. I think many people install LibreOffice (I do), but there are these light-weight options for old or weak computers.

---

### Post by Ahunt on 2017-03-23
> **sudodus said:**
> Compare with the office programs: Lubuntu comes with Abiword and Gnumeric which are light-weight. I think many people install LibreOffice (I do), but there are these light-weight options for old or weak computers.

That is quite true, Midori is a sort of match for Abiword and Gnumeric in terms of "lightness". My Lubuntu is kind of "fattened up", with LibreOffice and now Chromium, but I am using modern hardware, dual core CPU, 6 GB of RAM. For older equipment Midori may make sense.

Of course Lubuntu 16.10 and later already come with PulseAudio installed, so no problem with continuing with Firefox normal releases there. It is just 16.04 LTS that needs a fix and then only until its end of life in 2019.

---

### Post by opmartin2 on 2017-03-23
> **Temüjin said:**
> Again, try apulse. First, build it:
...
```
apulse firefox
```
Sound?

Thank you for the suggestion.

This apulse script did not solve the problem for me.  I am on Mint with Jack installed via kxstudio.  But by the grace of God I discovered that I can install the pulseaudio-module-jack package from the kxstudio repository, then I can enable the Pulseaudio bridge to Jack from within Cadence (also called Jack Sink, module-jack-sink).  After that, Firefox could hear the sound again.  Fixed in two clicks!

Maybe this will help someone out there.

---

### Post by Yellow Pasque on 2017-03-23
> **opmartin2 said:**
> This apulse script did not solve the problem for me.

The suggestion was directed at Lubuntu 16.04 users with ALSA (and no pulseaudio or JACK). I thought that was clear, but if not, let me state it explicitly.

---

### Post by Ahunt on 2017-03-23
LOL, now Mozilla has retroactively added the existence of this issue to the[ release notes]("https://www.mozilla.org/en-US/firefox/52.0/releasenotes/") for Firefox 52.0:

> On Linux, Firefox now requires PulseAudio to play sound and no longer plays sound directly with ALSA.

---

### Post by vasa1 on 2017-03-28
And no joy with [version 52.0.2]("https://www.mozilla.org/en-US/firefox/52.0.2/releasenotes/").

---

### Post by Ahunt on 2017-03-28
> **vasa1 said:**
> And no joy with [version 52.0.2]("https://www.mozilla.org/en-US/firefox/52.0.2/releasenotes/").

At this point Mozilla has not committed to fixing this at all. Judging by the traffic on their discussion about it, I suspect that there is much behind the scenes chat going on. Based on the Lubuntu dev discussion, I suspect the next thing we will see is a new build of FF with ALSA turned back on, at least for now.

---

### Post by Ahunt on 2017-03-31
The Lubuntu dev team pushed out a new version of Firefox,* 52.0.2+build1-0ubuntu0.16.04.1* late yesterday, 30 March 2017, [as listed in the history]("https://launchpad.net/ubuntu/+source/firefox/+publishinghistory").  

This Firefox build re-enables ALSA audio and fixes the issue, at least for now. Last news was that Mozilla still plans to remove the ALSA coding from Firefox later this summer, though, which would undo this fix. As [per Simon Quigley's plan]("https://lists.ubuntu.com/archives/lubuntu-devel/2017-March/001000.html") if Mozilla does remove the code they will look at a new browser.

[Ubuntu bug 1671273 has been marked as fixed]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671273").

If anyone is interested I have a complete history on my website in [this article]("http://web.ncf.ca/fn352/ubuntu3.html#09Mar17").

---

### Post by vasa1 on 2017-03-31
> **Ahunt said:**
> The Lubuntu dev team pushed out a new version of Firefox,* 52.0.2+build1-0ubuntu0.16.04.1* late yesterday, 30 March 2017, [as listed in the history]("https://launchpad.net/ubuntu/+source/firefox/+publishinghistory"). ...
I think it's actually done by the Canonical guys. They note that```
  * Fix LP: #1671273 - Build with --enable-alsa for now to re-enable the
    unmaintained ALSA backend. Note that problems with the ALSA backend will
    not block future updates and Ubuntu flavors that ship without Pulseaudio
    need to participate in maintaining this code

```I wonder how that will play out for the life of Lubuntu 16.04 LTS.

---

### Post by Ahunt on 2017-03-31
> **vasa1 said:**
> I think it's actually done by the Canonical guys....I wonder how that will play out for the life of Lubuntu 16.04 LTS.

Yes, quite correct. I suspect that the Lubuntu devs sent it upstream where the Canonical people who maintain the Firefox package took action. [That is listed as the Ubuntu-Mozilla-Team]("https://launchpad.net/ubuntu/+source/firefox"), but it is clear from the [Lubuntu-Devel list]("https://lists.ubuntu.com/archives/lubuntu-devel/2017-March/001000.html") that this was pushed by them.

The key future event will be if Mozilla carry out their intention to remove the ALSA support coding in Firefox this summer. If that happens it can't be just re-enabled. [Simon Quigley has said]("https://lists.ubuntu.com/archives/lubuntu-devel/2017-March/001000.html"), "More options for web browsers will be explored, just in case ALSA support in Firefox breaks once again. We may implement this sooner than that, but nothing has been decided on yet, and that's a whole separate discussion. Feedback is welcome on this."

---

### Post by pete5 on 2017-03-31
I just installed Lubuntu 16.10 on this PC last night. It found/installed a bunch of updates after a reboot or two. I'm listening to a music video on YouTube as I write this post. Didn't have to do anything special.

---

### Post by Yellow Pasque on 2017-03-31
> **pete5 said:**
> I just installed Lubuntu 16.10 on this PC last night. It found/installed a bunch of updates after a reboot or two. I'm listening to a music video on YouTube as I write this post. Didn't have to do anything special.
...
> Lubuntu 16.10 users are not affected as the distro switched to PulseAudio. 

---

### Post by Ahunt on 2017-04-01
Well happy April, everyone! 

No April fools here, but the new browser market share data is out for March now. I was keen to see how Firefox fared last month and whether this issue had any effect on their market share. So here is what I found:

Stats Counter [shows]("http://gs.statcounter.com/browser-market-share#monthly-200901-201703") that since February Firefox's market share fell from 6.73% to 6.67%, a loss of 0.06% of the market. This shows they lost about 1% of their users over the month.

W3 Counter [showed]("https://www.w3counter.com/trends") a rather sharp drop from 9% to 7.2%, a loss of 1.8% of the market. This shows they lost 20% of their users over the month.

The next couple of months will show whether this trend continues and whether March was a particularly bad month for Firefox use.  Keep in mind that back in 2009-10 Firefox had 33-34% of the browser market.

---

### Post by Ahunt on 2017-04-03
The latest on the [Mozilla discussion]("https://groups.google.com/forum/#!topic/mozilla.dev.platform/jRAqSTri66I") is that they are asking the distros and users to turn on telemetry.

---

### Post by vasa1 on 2017-04-03
> **Ahunt said:**
> The latest on the [Mozilla discussion]("https://groups.google.com/forum/#!topic/mozilla.dev.platform/jRAqSTri66I") is that they are asking the distros and users to turn on telemetry.
Chris Coulson's [comment]("https://groups.google.com/d/msg/mozilla.dev.platform/jRAqSTri66I/CynFrwt8CwAJ") is worth noting:> It's enabled, but please see the small-print in the changelog 
description at 
[https://launchpad.net/ubuntu/+source/firefox/52.0.2+build1-0ubuntu0.16.04.1](https://launchpad.net/ubuntu/+source/firefox/52.0.2+build1-0ubuntu0.16.04.1). 
The Firefox package in Ubuntu is maintained by 1 contributor in his 
spare time and myself who is only able to do the minimum in order to 
provide updates, so Ubuntu flavors that don't ship Pulseaudio need to 
step up to maintain this code if they want it to continue working and 
don't want it to be disabled again in a future update. 

---

### Post by Ahunt on 2017-04-03
> **vasa1 said:**
> Chris Coulson's [comment]("https://groups.google.com/d/msg/mozilla.dev.platform/jRAqSTri66I/CynFrwt8CwAJ") is worth noting:

I did note that. I am not sure what the issue is there. My understanding is that Firefox is compiled from source for Ubuntu with each new Firefox version released. It is only one line of code to cut 'n paste in to enable ALSA, at least until Mozilla removes the ALSA support, but perhaps I don't understand the technical complexities and work involved?

---

### Post by Ahunt on 2017-04-03
> **sudodus said:**
> Chromium-browser has abandoned 32-bit architecture, which is necessary for some of the computers, that are running Lubuntu. So it is not an option. Maybe light-weight Midori would be an option, if people cannot use PulseAudio in their [old] computers. But compiling Firefox with --enable-alsa seems a better alternative.

I did think that, too, but just checked on the current Chromium version, 56.0.2924.76-0ubuntu0.16.04.1268, in the Ubuntu repos and found [an i386 version]("https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage/+build/12053882").

---

### Post by vasa1 on 2017-04-03
> **Ahunt said:**
> ... don't understand the technical complexities and work involved?
Same here but I'm guessing there's something that prevents a clear assurance that Firefox will continue to be built with --enable-alsa as long as that is possible.

---

### Post by Ahunt on 2017-04-03
> **vasa1 said:**
> Same here but I'm guessing there's something that prevents a clear assurance that Firefox will continue to be built with --enable-alsa as long as that is possible.

I guess we'll see how hard it is when the next Firefox version comes out. FF53 should be out in the middle of this month. I'll be checking to see if it still has ALSA enabled!

---

### Post by Yellow Pasque on 2017-04-03
> **vasa1 said:**
> Same here but I'm guessing there's something that prevents a clear assurance that Firefox will continue to be built with --enable-alsa as long as that is possible.

This is how I understand it:

1. Mozilla could make changes to their audio system that break the ALSA backend. In that case, a patch would be needed and it would be Lubuntu's responsibility to maintain that patch (create it or adapt it from another distro/developer). Depending on what changed, it could be a lot of time and effort involved.

2. Mozilla could rip out the ALSA backend completely. If it's still functional, adding it back in could be fairly straightforward (copy/paste the removed code and other minor cleanups), but it would still take some time/effort, and that's the best case scenario. I've heard different things about if/when Mozilla plans to remove the ALSA backend completely, but I have a feeling it's still undecided.

3. Mozilla could make changes to their audio system that bring new functionality, but won't work with pulseaudio's asound plugin. At this point, Chris Coulson could decide to buld the main FF package with pulseaudio so the majority of Ubuntu-based distros/flavors could enjoy the new feature(s). Lubuntu would have to create a separate package if they wanted to continue using FF as default.

I still think building the ESR package with --enable-alsa is the way to go and will safely get Lubuntu 16.04 LTS users into 2018 without package maintenance issues or inconveniencing other Ubuntu users. At that point, it is up to users to find a different browser or upgrade to Lubuntu 18.04 if they want to continue to use Firefox. It is a compromise of sorts since Lubuntu was supposed to have security updates until April 2019, but other methods (such as apulse or a PPA with Firefox ALSA) could ease the pain.

---

### Post by Ahunt on 2017-04-04
> **Temüjin said:**
>  I still think building the ESR package with --enable-alsa is the way to go and will safely get Lubuntu 16.04 LTS users into 2018 without package maintenance issues or inconveniencing other Ubuntu users.

Wouldn't this force all Ubuntu users into using the ESR? Or do you think this should be a new package, like *firefox-esr* and leave everyone one else on the 'buntus with the existing *firefox* package? 

Because the ESR expires before Lubuntu 16.04 LTS does, this would require further action of some kind to take the LTS to EOL in April 2019.

Also Anthony Jones, The Mozilla engineer responsible for disabling ALSA, [just posted]("https://groups.google.com/forum/#!topic/mozilla.dev.platform/jRAqSTri66I") in response to turning on ALSA in FF52ESR, "That would mean having to support ALSA until the ESR expires," and "The problem with re-enabling ALSA is that people will get the impression that we're still actively maintaining it. We're no longer maintaining the ALSA backend." This seems to imply that either they will remove the backend from the ESR as an update or if it breaks, just leave it broken.

---

### Post by poorguy on 2017-04-04
I don't care who did what it is fixed and that is great and hopefully it will continue to remain great.
Way to go to whoever did what.

Thanks :)

---

### Post by Ahunt on 2017-04-04
> **poorguy said:**
> I don't care who did what it is fixed and that is great and hopefully it will continue to remain great.
Way to go to whoever did what.

Thanks :)

I agree, but it is unlikely to stay fixed for the life of Lubuntu 16.04 LTS. The story isn't done yet!

---

### Post by poorguy on 2017-04-04
You are probably right but at least it does show a sign of hope.

---

### Post by Ahunt on 2017-04-04
> **poorguy said:**
> You are probably right but at least it does show a sign of hope.

LOL! well, yes. At least it is working right now!

I actually owe Anthony Jones, the Mozilla dev who broke the ALSA audio, a vote of thanks. Because he broke my audio I switched to Chromium, a browser I haven't used in 3 1/2 years and I have to admit that I like it better than Firefox.

---

### Post by poorguy on 2017-04-04
Yes I to have started trying different browsers and yes Chromium has improved from what I remember.

I have been playing with Vivaldi but don't seem to find it as great as I read about.

[https://vivaldi.com/?lang=en_US](https://vivaldi.com/?lang=en_US)

---

### Post by Ahunt on 2017-04-04
> **poorguy said:**
> Yes I to have started trying different browsers and yes Chromium has improved from what I remember.

I have been playing with Vivaldi but don't seem to find it as great as I read about.

[https://vivaldi.com/?lang=en_US](https://vivaldi.com/?lang=en_US)

If you are interested I [recently did a review of Chromium]("http://web.ncf.ca/fn352/ubuntu3.html#01Mar17").

---

### Post by poorguy on 2017-04-04
> **Ahunt said:**
> If you are interested I [recently did a review of Chromium]("http://web.ncf.ca/fn352/ubuntu3.html#01Mar17").
Pretty interesting website you have there.

---

### Post by Ahunt on 2017-04-04
> **poorguy said:**
> Pretty interesting website you have there.

Glad that you found something of interest. I have been writing up my Ubuntu experiences since 2007 there. Feel free to poke around!

---

### Post by vasa1 on 2017-04-04
The version number of chromium-browser, as provided by the standard repos, often lags that of Google Chrome. Now, chromium-browser is at 56.0.2924.76 whereas google-chrome version 57 was first released on [Mar 09]("https://chromereleases.googleblog.com/2017/03/stable-channel-update-for-desktop.html"), with subsequent updates on [Mar 16]("https://chromereleases.googleblog.com/2017/03/stable-channel-update-for-desktop_16.html") and [Mar 29]("https://chromereleases.googleblog.com/2017/03/stable-channel-update-for-desktop_29.html").

Firefox updates reach Ubuntu users pretty quickly.

---

### Post by Ahunt on 2017-04-04
> **vasa1 said:**
> The version number of chromium-browser, as provided by the standard repos, often lags that of Google Chrome. Now, chromium-browser is at 56.0.2924.76 whereas google-chrome version 57 was first released on [Mar 09]("https://chromereleases.googleblog.com/2017/03/stable-channel-update-for-desktop.html"), with subsequent updates on [Mar 16]("https://chromereleases.googleblog.com/2017/03/stable-channel-update-for-desktop_16.html") and [Mar 29]("https://chromereleases.googleblog.com/2017/03/stable-channel-update-for-desktop_29.html").

Firefox updates reach Ubuntu users pretty quickly.

Yes, that is the case. As [OMG noted in 2013]("http://www.omgubuntu.co.uk/2013/08/firefox-to-remain-default-browser-in-ubuntu-13-10") that may have been one of the reasons whey Firefox wasn't replaced by Chromium back in Ubuntu 13.10 when it had been planned to do so. The current package maintainer is "[Ubuntu Developers]("https://launchpad.net/ubuntu/+source/chromium-browser")", but still the updates do seem to run behind. The current Chromium in the repos is 56.0.2924.76 which [was released]("https://launchpad.net/ubuntu/+source/chromium-browser/56.0.2924.76-0ubuntu0.16.04.1268") on 01 March 2017, whereas the same version of Chrome[ had been released]("https://chromereleases.googleblog.com/2017/01/stable-channel-update-for-desktop.html") on 25 January, exactly a five weeks earlier. In this case there were 51 security fixes included, but no major changes, otherwise.

---

### Post by Ahunt on 2017-04-05
And then the next day [Ubuntu upgraded]("https://launchpad.net/ubuntu/+source/chromium-browser") to Chromium 57.0.2987.98 just four weeks after [Chrome did]("https://chromereleases.googleblog.com/2017/03/stable-channel-update-for-desktop.html"). At least they are getting faster!

---

### Post by Ahunt on 2017-05-06
I was just checking the [W3Counter market share stats]("https://www.w3counter.com/trends") to see if this ALSA issue has impacted Firefox use. Interesting to note that they have dropped from 9% to 6.3%, a loss of 2.7% of the total browser market, indicating 30% of Firefox users stopped using it during the two month period since the ALSA issue started. Not sure you can lay this all at the feet of bad decisions like the ALSA issue, as Firefox market share was falling before, but I am sure that this didn't help matters.

---

### Post by Ahunt on 2017-05-29
and the original [Mozilla bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=1345661") has been closed, without any surprises there:

Anthony Jones (:kentuckyfriedtakahe, :k17e)	-
Updated • 8 hours ago
Status: NEW &#8594; RESOLVED
Last Resolved: 8 hours ago
Resolution: --- &#8594; WONTFIX

---

### Post by vasa1 on 2017-05-29
> **Ahunt said:**
> ... without any surprises there:
... WONTFIX
And no surprises here either: [https://andreasgal.com/2017/05/25/chrome-won/](https://andreasgal.com/2017/05/25/chrome-won/)

---

### Post by Ahunt on 2017-05-29
I am wondering what the future is for Mozilla. With a Firefox user base that will probably drop below 5% at the end of this month they are sliding into irrelevance. All these bad decisions have driven users away.

---

### Post by vasa1 on 2017-08-16
And I'm guessing ALSA support is gone in v55!
> * Disable ALSA backend for Firefox 55 because it makes the build failure.
    This will remain disabled until somebody steps up to maintain it
 
Source: [https://launchpad.net/ubuntu/+source/firefox/55.0.1+build2-0ubuntu0.16.04.2](https://launchpad.net/ubuntu/+source/firefox/55.0.1+build2-0ubuntu0.16.04.2)

---

### Post by Ahunt on 2017-08-16
That was not unexpected. I just received  Firefox 55 and can confirm that the audio is once again broken. I suspect that Mozilla have removed the code that supports ALSA as promised, and so it is no longer a matter of just "turning it back on". Likely this can no longer be fixed by just recompiling it. I think it is time for ALSA-only Firefox users (like Lubuntu 16.04 LTS, Ubuntu Server, etc) to just move on and get a browser that works.

---

### Post by Yellow Pasque on 2017-08-16
I've been humming along with apulse here on Debian.

---

### Post by sudodus on 2017-08-17
Since several years I have installed pulseaudio and pavucontrol into Lubuntu because I prefer them to alsa[mixer]. Pulseaudio has been working well for me also in old computers and pavucontrol provides much better control of the audio settings (compared to alsamixer).

---

### Post by jbrid2 on 2017-08-24
> **Ahunt said:**
> move on and get a browser that works.

I am going to try Pale Moon.

---

### Post by tsimonq2 on 2017-08-27
Hey. I'm the Lubuntu Release Manager, I'm seeing this thread after a while, sorry for the delay.

> If you do see anything on the dev mailing lists it would be great if you could post it here for the record!

I was going to file a bug on this for Lubuntu, but not sure what to file  it against. Firefox would be obvious but it works fine on all flavours  but Lubuntu. It isn't really appropriate to tag ALSA, since it works  fine or PulseAudio, since it isn't the problem and isn't even installed.  I am was hoping that the Lubuntu devs would be using the default  browser on Lubuntu themselves and would quickly notice the issue.  Perhaps they have but there isn't an obvious solution beyond installing  PulseAudio.

I am keeping an eye on the updates to see if anything gets pushed out to fix this.

Turns out that it was just a build flag that was disabled, we turned it on back in Ubuntu's build, but the ALSA support that we enabled and that's still there but isn't being maintained is eventually subject to bitrot, which is what happened in the 55 update.

I don't think we have a choice at this point, except to just add a dependency on PulseAudio one way or another. I'm not a fan of that option, but I don't want to break compatibility... I'll take one more look to see if I can fix it, but otherwise that's it.

We'll announce something on lubuntu.me and the mailing lists once action has been taken.

EDIT: Bah, I just realized that I responded to a post on the first page, I don't know the Ubuntu Forums well... :P

---

### Post by casperbuntu on 2017-09-30
Hi, first time here. I didn't want to stop using Firefox since is the best for my very old system. So I installed pulseaudio. All I did was typing **sudo apt-get install pulseaudio pavucontrol** in the terminal. After a couple of minutes it works like a charm.

I wanna add that now audio is definitely louder. Without pulseaudio I kept it always at 100%, now 70-80% is enough. Maybe for old systems is a better choice.

I'm just a newbie but I think next 16.04 updates should support those needed packages like most recent lubuntu versions. Firefox isn't Internet Explorer, you can't leave an LTS edition without full firefox compatibility. Just my 2c.

In this occasion I want to also thank the developers. Lubuntu is one of very few easy to use options for aged/low powered systems. So, you guys are great! LLAP!

---

### Post by Ahunt on 2017-11-15
I am please to report that this issue has a final fix on Lubuntu 16.04 LTS as of today! Simon (tsimonq2 ) and the other Lubuntu and Ubuntu devs finished testing a solution and sent it out via the update process. It involves installing PulseAudio and all the supporting files needed, plus lots of testing to make sure noting got missed (like the sound control). I just got the fix today, installed it and tested it at my end and everything seems to work. Firefox now has sound and nothing else has lost sound, plus the audio controls work.

A big "thank you" to Simon and the Lubuntu team for addressing this issue that Mozilla created.

---

### Post by vasa1 on 2017-11-17
> **Ahunt said:**
> I am please to report that this issue has a final fix on Lubuntu 16.04 LTS as of today! Simon (tsimonq2 ) and the other Lubuntu and Ubuntu devs finished testing a solution and sent it out via the update process. It involves installing PulseAudio and all the supporting files needed, plus lots of testing to make sure noting got missed (like the sound control). I just got the fix today, installed it and tested it at my end and everything seems to work. Firefox now has sound and nothing else has lost sound, plus the audio controls work.

A big "thank you" to Simon and the Lubuntu team for addressing this issue that Mozilla created.
Thanks for this news! Can you share a link to where this was reported? At least on my system, the update
has brought in quite a few things that don't seem obviously related to Pulseaudio.

---

### Post by Yellow Pasque on 2017-11-17
[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1710993](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1710993)

---

### Post by Ahunt on 2017-11-17
Yes, thank you Temüjin! [That is it]("https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1710993"). That thread does explain that the fix, PulseAudio, does come witha lot of other packages. Some are dependencies and such, while others were required to fix related things, like the GUI volume control, etc. At least on both my computers it all works now.

---

### Post by Ahunt on 2017-11-22
Just for the record apparently pulseaudio also installs the following packages as dependencies:

apg bluez-obexd cheese-common cups-pk-helper dconf-cli evolution-data-server evolution-data-server-common evolution-data-server-online-accounts geoclue
  geoclue-ubuntu-geoip gir1.2-ibus-1.0 gkbd-capplet gnome-bluetooth gnome-desktop3-data gnome-session-bin gnome-settings-daemon-schemas gnome-user-share
  gsettings-ubuntu-schemas gstreamer1.0-clutter-3.0 gstreamer1.0-x hwdata ibus indicator-bluetooth indicator-datetime indicator-keyboard indicator-power
  indicator-sound indicator-sound-gtk2 libaccounts-glib0 libaccounts-qt5-1 libcanberra-pulse libcheese-gtk25 libcheese8 libclutter-gst-3.0-0 libebackend-1.2-10
  libebook-1.2-16 libebook-contacts-1.2-2 libecal-1.2-19 libedata-book-1.2-25 libedata-cal-1.2-28 libedataserver-1.2-21 libfftw3-single3 libgee-0.8-2
  libgeocode-glib0 libgeonames0 libgnome-bluetooth13 libgnome-desktop-3-12 libgnomekbd-common libgnomekbd8 libgweather-3-6 libgweather-common libibus-1.0-5
  libido-0.1-0 libpulsedsp libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libtimezonemap-data libtimezonemap1
  libunity-control-center1 libunity-settings-daemon1 liburl-dispatcher1 libwebrtc-audio-processing-0 mousetweaks nautilus-data pulseaudio pulseaudio-module-x11
  pulseaudio-utils rtkit session-migration signon-plugin-password signon-ui signon-ui-service signon-ui-x11 signond ubuntu-system-service ubuntu-touch-sounds
  unity-control-center unity-control-center-faces unity-settings-daemon

Some are real puzzlers, like the cheese packages (a webcam application)

---

### Post by vasa1 on 2017-11-22
> **vasa1 said:**
> ... At least on my system, the update
has brought in quite a few things that don't seem obviously related to Pulseaudio.

> **Ahunt said:**
> Just for the record apparently pulseaudio also installs the following packages as dependencies:
...
Some are real puzzlers, like the cheese packages (a webcam application)
My guess is that they were pressed for time and so didn't untangle the "dependencies"?

---

### Post by Yellow Pasque on 2017-11-23
> **vasa1 said:**
> My guess is that they were pressed for time and so didn't untangle the "dependencies"?

My guess is that a lot of stuff on that list gets pulled in because of "Recommends", as opposed to strict "Depends". So maybe use Synaptic and turn off recommended packages for this particular upgrade if you don't want all that gnome bloat.

Sorry, but installing pulseaudio this far into an LTS on a distro that wasn't originally configured for it seems like overkill for this issue ("sledgehammer to kill a fly").
IMO, apulse would have been a better solution. It's even been pulled into Debian: [https://packages.debian.org/buster/apulse](https://packages.debian.org/buster/apulse)

---

### Post by vasa1 on 2017-11-23
According to *apt show pulseaudio*:```
Depends: libasound2 (>= 1.0.24.1), libc6 (>= 2.15), libcap2 (>= 1:2.10), libdbus-1-3 (>= 1.9.14), libfftw3-single3, libltdl7 (>= 2.4.6), liborc-0.4-0 (>= 1:0.4.25), libpulse0 (= 1:8.0-0ubuntu3.4), libsndfile1 (>= 1.0.20), libspeexdsp1 (>= 1.2~beta3.2-1), libstdc++6 (>= 4.1.1), libsystemd0, libtdb1 (>= 1.2.7+git20101214), libudev1 (>= 183), libwebrtc-audio-processing-0, libx11-6, libx11-xcb1, libxcb1, adduser, lsb-base (>= 3.2-13), libpam-systemd, udev (>= 143), libasound2-plugins, pulseaudio-utils
Recommends: pulseaudio-module-x11, rtkit
Suggests: pavumeter, pavucontrol, paman, paprefs
```So who did what or why remains a puzzle!

---

### Post by Yellow Pasque on 2017-11-23
It's the addition of indicator-sound-gtk2 that is pulling in all of the bloat:
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound-gtk2/+bug/1734100](https://bugs.launchpad.net/ubuntu/+source/indicator-sound-gtk2/+bug/1734100)

---

### Post by vasa1 on 2017-11-23
*apt show indicator-sound-gtk2* doesn't explain all the Unity packages shown in AHunt's post and what I saw as well :???:

---

### Post by Yellow Pasque on 2017-11-23
indicator-sound-gtk2 depends on indicator-sound.
indicator-sound recommends:
```
unity-control-center
    utilities to configure the GNOME desktop 
or gnome-control-center
    utilities to configure the GNOME desktop 
or ubuntu-system-settings
    System Settings application for Ubuntu Touch 
or pavucontrol
    PulseAudio Volume Control 
or mate-media
    MATE media utilities
```

So I think lubuntu should somehow prefer pavucontrol over unity-control-center, which drags in all sorts of extra packages. Does installing pavucontrol before trying to update solve the issue?

---

### Post by vasa1 on 2017-11-23
> **Temüjin said:**
> indicator-sound-gtk2 depends on indicator-sound.
indicator-sound recommends:
```
unity-control-center
    utilities to configure the GNOME desktop 
or gnome-control-center
    utilities to configure the GNOME desktop 
or ubuntu-system-settings
    System Settings application for Ubuntu Touch 
or pavucontrol
    PulseAudio Volume Control 
or mate-media
    MATE media utilities
```

So I think lubuntu should somehow prefer pavucontrol over unity-control-center, which drags in all sorts of extra packages. Does installing pavucontrol before trying to update solve the issue?
Thanks for clearing the mystery!

I no longer use Lubuntu actively. Once in a while, I just keep the system updated!

---

### Post by Yellow Pasque on 2017-11-23
If installing pavucontrol doesn't prevent the flood, then I would run this before trying to do full update:
```
sudo apt-get install --no-install-recommends indicator-sound indicator-sound-gtk2
```

---

### Post by Ahunt on 2017-11-23
There is now a bug filed against the large number of dependencies:

* [Installation of indicator-sound-gtk2 brings unnecessary packages on Lubuntu]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound-gtk2/+bug/1734100")

---

### Post by vasa1 on 2017-11-23
> **Ahunt said:**
> There is now a bug filed against the large number of dependencies:

* [Installation of indicator-sound-gtk2 brings unnecessary packages on Lubuntu]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound-gtk2/+bug/1734100")
Already posted: [https://ubuntuforums.org/showthread.php?t=2355092&p=13714401#post13714401](https://ubuntuforums.org/showthread.php?t=2355092&p=13714401#post13714401)

---

### Post by Ahunt on 2017-11-23
> **vasa1 said:**
> Already posted: [https://ubuntuforums.org/showthread.php?t=2355092&p=13714401#post13714401](https://ubuntuforums.org/showthread.php?t=2355092&p=13714401#post13714401)

Sorry, I read the discussion but missed that one!

---

