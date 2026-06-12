---
title: "An Open Letter to Mozilla: RE Ubuntu"
date: 2010-01-28
forum: The Cafe
---

### Post by Limulus on 2010-01-28
The Mozilla release schedule and the Ubuntu release cycle are completely out of synch.  What can be done?

[http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/](http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/)

My suggestion: **Mozilla needs to make an official repository for Ubuntu.**

Please repost this on Twitter (from here [http://twitter.com/ConradKnauer/status/8314504292](http://twitter.com/ConradKnauer/status/8314504292)), Facebook, etc. as you see fit and maybe send a message to Mozilla if you feel so inclined :)

[http://hendrix.mozilla.org/](http://hendrix.mozilla.org/)

---

### Post by siimo on 2010-01-28
Not needed.  You can just get Firefox from [www.getfirefox.com](www.getfirefox.com) and install it in /opt

I hate this whole "repository for this, repository for that" model in linux which causes a "lock-in" and user has to rely on the repository or compile it themselves.  What is wrong with making a binary available that works on most linux distros.  I have been using firefox like that on every linux distro since i started using linux.

apt-get remove mozilla-firefox and install from the official tar.bz2 binary package [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2)

---

### Post by Techsnap on 2010-01-28
Why should they? I'm sure it's not on the top of their list of priorities in all honesty. Then you'll get users of other distros complaining, ideally you need to talk to the people who package Firefox on Ubuntu and ask them to be more prompt with newer versions.

---

### Post by Xbehave on 2010-01-28
Nah, if people want a new version they can get it almost instantly using ubuntuzilla* (stable) or ppa:mozilla-daily (dailys), the official repos should stick to 1 version per release. There is a lot of software that depends on xulrunner ( **python-gtkmozembed** eclipse-platform videolink tuxguitar **python-hulahop** prism miro **libgtk2-mozembed-perl** **libgtk-mozembed-ruby1.8** kazehakase-gecko gnome-web-photo galeon fennec eclipse-platform conkeror chmsee yelp couchdb-bin), as soon as you start updating xulrunner during a release, that is a lot of testing, and if somebody has used ubuntu as a base from which to develop it would be a terrible idea to mess with any of the bold packages (except for security patches )

*The only thing that is missing is stable 64bit builts, but they don't exist anyway, so while i'd like ubuntuzilla to fake them I can understand why they don't.

> **Techsnap said:**
> Why should they? I'm sure it's not on the top of their list of priorities in all honesty. Then you'll get users of other distros complainingI agree that it's not needed, but if it was done, they could use a packaging system like operas that seams to push out support for most distros. As most distros are binary compatible (hence the single tar.gz.bz works), it's just the packaging that is complicated (but that is a relatively cheap step compared to writing/building/distributing).

---

### Post by SilverWave on 2010-01-28
> **Limulus said:**
> My suggestion: **Mozilla needs to make an official repository for Ubuntu.**


Agreed

---

### Post by Giant Speck on 2010-01-28
I forgot that Ubuntu is the center of the universe around which Mozilla revolves.

---

### Post by Tristam Green on 2010-01-28
lol.  You'd think from the tone of the OP that Firefox was the official browser designed specifically for Ubuntu.

---

### Post by beastrace91 on 2010-01-28
> **siimo said:**
> Not needed.  You can just get Firefox from [www.getfirefox.com](www.getfirefox.com) and install it in /opt

One of the things I love about Linux is the fact that it has a package manager, if you start installing software outside of that its no better than Windows IMO.

> I forgot that Ubuntu is the center of the universe around which Mozilla revolves. 

The OP nor anyone else said that, however Ubuntu  is top dog of Linux distros by a good deal.

Honestly if they aren't going to provide a .deb/repository for Firefox they should at the very least provide a .bin installer (meaning it would work on most distros). It is ***-backwards that is it easier to install a piece of FOSS software on Windows than it is on Nix IMO

Regards,
~Jeff

---

### Post by Tristam Green on 2010-01-28
> **beastrace91 said:**
> Ubuntu  is top dog of Linux distros by a good deal.

Ubuntu is big, but let's not get carried away making claims we can't support.

---

### Post by MelDJ on 2010-01-28
> **Giant Speck said:**
> I forgot that Ubuntu is the center of the universe around which Mozilla revolves.

:)

---

### Post by RiceMonster on 2010-01-28
> **beastrace91 said:**
> The OP nor anyone else said that, however Ubuntu  is top dog of Linux distros by a good deal.

It is only the "top dog of Linux distros" in the home desktop market.

---

### Post by Bob Appleby on 2010-01-28
I used getfirefox and downloaded the latest version successfully but could not install it. I tried various combinations of open and extract. (extraction did say it was completed successfully) The newest version is still not installed. What next?

Bob

> **siimo said:**
> Not needed.  You can just get Firefox from [www.getfirefox.com](www.getfirefox.com) and install it in /opt

I hate this whole "repository for this, repository for that" model in linux which causes a "lock-in" and user has to rely on the repository or compile it themselves.  What is wrong with making a binary available that works on most linux distros.  I have been using firefox like that on every linux distro since i started using linux.

apt-get remove mozilla-firefox and install from the official tar.bz2 binary package [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2)

---

### Post by scouser73 on 2010-01-28
> **Limulus said:**
> The Mozilla release schedule and the Ubuntu release cycle are completely out of synch.  What can be done?

[http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/](http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/)

My suggestion: **Mozilla needs to make an official repository for Ubuntu.**

Please repost this on Twitter (from here [http://twitter.com/ConradKnauer/status/8314504292](http://twitter.com/ConradKnauer/status/8314504292)), Facebook, etc. as you see fit and maybe send a message to Mozilla if you feel so inclined :)

[http://hendrix.mozilla.org/](http://hendrix.mozilla.org/)

I don't think that it's a bad idea for Mozilla to be in sync with Ubuntu but you could just update the Mozilla products as and when new releases come out.

---

### Post by Xbehave on 2010-01-28
> **Bob Appleby said:**
> I used getfirefox and downloaded the latest version successfully but could not install it. I tried various combinations of open and extract. (extraction did say it was completed successfully) The newest version is still not installed. What next?

Bob
If you are on 32bit use ubuntuzilla it makes this sooo much easier, however if you must use the tar.gz

1)download it
2)```
sudo mv firefox*.tar.gz /opt ; cd /opt
sudo tar -xf firefox*.tar.gz
sudo ln -sv /opt/firefox/firefox /usr/bin/firefox
```
3)make gui launcher shortcuts
4)remember to launch firefox as root every so often to update it.

---

### Post by Praxicoide on 2010-01-28
Let's hear it for Ubuntu advocates and their negativity! I agree, let's not request anything, because nobody should care about Linux or Ubuntu.

Way to go.

---

### Post by mpt on 2010-01-28
> **siimo said:**
> I hate this whole "repository for this, repository for that" model in linux which causes a "lock-in"

What? How does it “cause a ‘lock-in’”?

> *What is wrong with making a binary available that works on most linux distros.*

Two things. First, even if it happens to contain self-updating code, it would be neither consistent with, nor integrated with, updates for the rest of the system. So for example if you’re a system administrator for a company with 200 Ubuntu installations, it would be much harder for you to update the browser on all of them.

Second, if it uses its own copies of libraries for the sake of portability across “distros”, and a security flaw is discovered in one of those libraries, there’s a much greater chance that the browser will need to be updated as well as the library.

---

### Post by pwnst*r on 2010-01-28
> **Giant Speck said:**
> I forgot that Ubuntu is the center of the universe around which Mozilla revolves.

Good, I thought I was the only one that made this distinction.

---

### Post by lykwydchykyn on 2010-01-28
> **mpt said:**
> 
Two things. First, even if it happens to contain self-updating code, it would be neither consistent with, nor integrated with, updates for the rest of the system. So for example if you’re a system administrator for a company with 200 Ubuntu installations, it would be much harder for you to update the browser on all of them.

Second, if it uses its own copies of libraries for the sake of portability across “distros”, and a security flaw is discovered in one of those libraries, there’s a much greater chance that the browser will need to be updated as well as the library.

I agree with you that static binaries have problems, but I also think that if they're going to release a static binary anyway (which they do), they ought to release it with an installer.  Linux culture has changed, and people who are releasing software for it need to recognize that.

After all, static binaries are for individual users who want the latest stuff.  The admin of a large network of installations is going to stick with the stable .deb in the repos or backport their own.

---

### Post by nmccrina on 2010-01-28
> **beastrace91 said:**
> One of the things I love about Linux is the fact that it has a package manager, if you start installing software outside of that its no better than Windows IMO.


The difference is that you know exactly what every file is and where it went during the installation. In the case of Firefox, Eclipse, Java, Songbird, and probably a bunch of others they go one better and just create ONE directory that you can put anywhere you want. To uninstall, you just have to remove that directory. No broken uninstall scripts or leftover registry entries, as in that other OS.

---

### Post by Merk42 on 2010-01-28
[Prepare Firefox for Major-Minor Version upgrades](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)
It's not exactly what you asked for but it is a step in the right direction

---

### Post by Zoot7 on 2010-01-28
> **siimo said:**
> Not needed.  You can just get Firefox from [www.getfirefox.com](www.getfirefox.com) and install it in /opt

I hate this whole "repository for this, repository for that" model in linux which causes a "lock-in" and user has to rely on the repository or compile it themselves.  What is wrong with making a binary available that works on most linux distros.  I have been using firefox like that on every linux distro since i started using linux.

apt-get remove mozilla-firefox and install from the official tar.bz2 binary package [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2)
+1 to the entirity of this statement. I've been running the precompiled binaries that they offer for Firefox in /opt in a multitude of distros for years now.
> **Giant Speck said:**
> I forgot that Ubuntu is the center of the universe around which Mozilla revolves.
As did I! :lolflag:

---

### Post by KiwiNZ on 2010-01-28
> **Limulus said:**
> The Mozilla release schedule and the Ubuntu release cycle are completely out of synch.  What can be done?

[http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/](http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/)

My suggestion: **Mozilla needs to make an official repository for Ubuntu.**

Please repost this on Twitter (from here [http://twitter.com/ConradKnauer/status/8314504292](http://twitter.com/ConradKnauer/status/8314504292)), Facebook, etc. as you see fit and maybe send a message to Mozilla if you feel so inclined :)

[http://hendrix.mozilla.org/](http://hendrix.mozilla.org/)

We are but one cog in a very large wheel. Mozilla is by far way bigger than Ubuntu I would suggest it is Ubuntu that should change if anyone should change.

But really no one need change. I don't see a problem. When a new version of Mozilla comes out install it , it takes a few seconds , have a cup of coffee , relax , there done.


Remember all that glitters is not Ubuntu....  Yuk that corny

---

### Post by michaelpagz on 2010-01-28
I think what many linux users want is a Firefox disbursement similar to Google Chrome's. They have .deb and .rpm which hits the majority of linux users (and adds a repo for updates) and then if you want the .tars they have them available also. I use Firefox primarily but when I added Chrome I was really happy with the ease of installation. Mozilla could really benefit from having that same process. The only real issue I have with the mozilla-daily ppa is that I am not sure how pure the release is and if I am getting all of the cool new features. I personally use the binaries because I don't really know what the mozilla daily ppa means when they say they don't do top level UI updates. I want all the updates so I use the mozilla-builds.

---

### Post by Xbehave on 2010-01-28
found [this]("https://launchpad.net/~mozillateam/+archive/firefox-stable?field.series_filter=karmic") today, just put a link to that somewhere high profile so people can run
[SIZE="5"]```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```[/SIZE]
and the rest can have a stable firefox release for the cycle of a stable distro.

The next person who asks for an easy way to install firefox 3.6 will be yelled at and told to get off my lawn, *shakes fist*

---

### Post by siimo on 2010-01-28
> **mpt said:**
> What? How does it &#8220;cause a &#8216;lock-in&#8217;&#8221;?


For example Google Chrome.  It provides .deb and .rpm binaries only.  What about for other linux distro users?  If they provide a binary that was just a tar.gz anyone can extract and run it.

Now we have to extract stuff out of a .deb or .rpm and inside it isn't all self contained but files goto /usr/lib /usr/bin etc.  It is easier to just compile it from scratch than messing about with that.

---

### Post by lykwydchykyn on 2010-01-28
> **siimo said:**
> For example Google Chrome.  It provides .deb and .rpm binaries only.  What about for other linux distro users?  If they provide a binary that was just a tar.gz anyone can extract and run it.

Supposing they provided all three?  Which part of having a repo precludes that possibility?

---

### Post by Xbehave on 2010-01-28
> **lykwydchykyn said:**
> Supposing they provided all three?  Which part of having a repo precludes that possibility?
+1 that is exactly what opera do.

---

### Post by RabbitWho on 2010-01-28
I don't get it.. firefox (swiftfox) automatically updates itself for me and I'm on Jaunty.. what's everybody else talking about!?

---

### Post by squilookle on 2010-01-28
> **siimo said:**
> Not needed.  You can just get Firefox from [www.getfirefox.com]("http://www.getfirefox.com") and install it in /opt

I hate this whole "repository for this, repository for that" model in linux which causes a "lock-in" and user has to rely on the repository or compile it themselves.  What is wrong with making a binary available that works on most linux distros.  I have been using firefox like that on every linux distro since i started using linux.

apt-get remove mozilla-firefox and install from the official tar.bz2 binary package [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2)

+1 - I did that for a long time in Ubuntu, it worked perfectly well and I always had the most up to date Firefox.

---

### Post by Xbehave on 2010-01-28
> **RabbitWho said:**
> I don't get it.. firefox (swiftfox) automatically updates itself for me and I'm on Jaunty.. what's everybody else talking about!?
swiftfox is from a 3rd party repo, by default ubuntu sticks with the version of programs it had when it was released (and for good reason too). But it's not exactly rocket surgery to make an exception for firefox.
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

---

### Post by RabbitWho on 2010-01-28
> **Xbehave said:**
> swiftfox is from a 3rd party repo


Ah ha! Cheers for the explanation.

---

### Post by Twitch6000 on 2010-01-28
Breaking NEws: The world does not revolve around Ubuntu it revolves around the sun..

Really I rather firefox work on fixing bugs and making firefox faster rather then wasting time making a repo for ubuntu or worse changing their release schedule.

---

### Post by SilverWave on 2010-01-29
> [Mike Beltzner]("http://beltzner.ca/mike") Says:						
 			[January 28, 2010 at 10:11 am]("http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/#comment-5344") | [Reply]("http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/?replytocom=5344#respond")   			Working on it …


[http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/](http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/)

---

### Post by Giant Speck on 2010-01-29
> **Praxicoide said:**
> Let's hear it for Ubuntu advocates and their negativity! I agree, let's not request anything, because nobody should care about Linux or Ubuntu.

Way to go.

There is no "not caring" involved.  Ubuntu has a relatively minuscule footprint in terms of operating system use worldwide.  If Mozilla doesn't even center Firefox releases around Microsoft Windows releases, why should they center Firefox releases around an operating system that has approximately one ninetieth the market share of Windows?

---

### Post by SilverWave on 2010-01-29
> **Giant Speck said:**
> There is no "not caring" involved.  Ubuntu has a relatively minuscule footprint in terms of operating system use worldwide.  If Mozilla doesn't even center Firefox releases around Microsoft Windows releases, why should they center Firefox releases around an operating system that has approximately one ninetieth the market share of Windows?

I think of it this way...
Mozilla's whole reason for existing is to provide a great web browser to users.

I am a Firefox user on Ubuntu, Mozilla wish for me to have easy access to their browser regardless of OS. Making a repository available would be very helpful. Indeed, they apparently agree and are "working on it".

---

