---
title: "Hey Ubuntu, Amarok says &quot;That's your problem, not ours.  Sorry!&quot;"
date: 2009-01-31
forum: The Cafe
---

### Post by diablo75 on 2009-01-31
[http://amarok.kde.org/forum/index.php/topic,16433.0.html](http://amarok.kde.org/forum/index.php/topic,16433.0.html)

This reminds me of calling a tech support hotline after being told by another tech support hotline to take it elsewhere, only to be told to go back to where I came from.  Splendid!

So who's fault is this?

---

### Post by Eclipse. on 2009-01-31
Ubuntu cant give mp3 support out the box because of licencing problems, although there is packages in multiverse that will give you mp3 support.

---

### Post by Frak on 2009-01-31
It's nobodies fault, but they should at least put the xine plugins in recommended when you install.

---

### Post by Polygon on 2009-01-31
ubuntu cannot ship with mp3 support out of the box, as it could be illegal.

---

### Post by Frak on 2009-01-31
> **Polygon said:**
> ubuntu cannot ship with mp3 support out of the box, as it could be illegal.
Only a couple more years (December 2012) and the MP3 codec will be public domain.

---

### Post by Tomatz on 2009-01-31
Its crud! No ones fault as they both cant "legally" supply the codecs (but they are in the repos anyway)...

Used to love amarok but amarok 2 is overrated IMO and too heavy. Songbird 2 is better if you want a "bells and whistles" player.

---

### Post by Tomatz on 2009-01-31
> **Frak said:**
> Only a couple more years (December 2012) and the MP3 codec will be public domain.

Then the world will adopt ogg vorbis :lolflag:

---

### Post by Frak on 2009-01-31
> **Tomatz said:**
> Then the world will adopt ogg vorbis :lolflag:
Or worse, MP3v2

---

### Post by Polygon on 2009-01-31
there is a mp3v2? what about mp3 needs improving?

---

### Post by Frak on 2009-01-31
> **Polygon said:**
> there is a mp3v2? what about mp3 needs improving?
I remember hearing about someone working on it, though I don't think they are anymore. There are more and more alternatives being released.

---

### Post by diablo75 on 2009-01-31
Look Mom!  I [filed a bug report]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/323647")!

---

### Post by Skripka on 2009-01-31
> **Frak said:**
> Or worse, MP3v2

Which will include such FEATURES as:

-An audio "Greeting" appended to the beginning of each track that is a 5 minute lecture on how great MP3v2 is, as well as a verbal chewing out-for even THINKING about ripping the track
-The inability to fast forward through tracks or the "Greeting" above
-The inability to skip tracks on a playlist
-The inability to rip anything but an entire CD-not individual tracks
-The DRM will also prevent you from even THINKING about the music without RIAA written permission
-Said DRM will also prevent you from singing or whistling tunes in your off hours.

---

### Post by jrusso2 on 2009-01-31
> **Eclipse. said:**
> Ubuntu cant give mp3 support out the box because of licencing problems, although there is packages in multiverse that will give you mp3 support.

Not true MP 3 is available in many distros and the gstreamer plugin is free even.  Its the Ubuntu only free software philosophy in this case.

The Amarok developer was correct in this case.

[http://www.fluendo.com/shop/product/fluendo-mp3-decoder/](http://www.fluendo.com/shop/product/fluendo-mp3-decoder/)

If you are living in a country where the mp3 patents don't apply you can of course use the source code provided by Fluendo (or anyone else) to get legal mp3 support onto your Unix/GNU/Linux desktop.

---

### Post by p_quarles on 2009-01-31
Hmm. Since you say this behavior continued after installing kubuntu-restricted-extras, I'm curious what codec this might be. It's obviously not MP3, since that is included with that metapackage. Which radio station(s) presented this problem?

---

### Post by diablo75 on 2009-01-31
> **p_quarles said:**
> Hmm. Since you say this behavior continued after installing kubuntu-restricted-extras, I'm curious what codec this might be. It's obviously not MP3, since that is included with that metapackage. Which radio station(s) presented this problem?

I just tried EVERY station in the Cool Streams playlist section.  NONE of them play.

---

### Post by p_quarles on 2009-01-31
> **diablo75 said:**
> i just tried every station in the cool streams playlist section.  None of them play.
url?

---

### Post by diablo75 on 2009-01-31
> **p_quarles said:**
> url?

Here are a few:

[http://scfire-ntc-aa01.stream.aol.com:80/stream/1035](http://scfire-ntc-aa01.stream.aol.com:80/stream/1035)
[http://scfire-dtc-aa01.stream.aol.com:80/stream/1003](http://scfire-dtc-aa01.stream.aol.com:80/stream/1003)
[http://streamer-mtc-aa02.somafm.com:80/stream/1032](http://streamer-mtc-aa02.somafm.com:80/stream/1032)
[http://electro.mthn.net:8400](http://electro.mthn.net:8400)
[http://www.protonradio.com:8000](http://www.protonradio.com:8000)

I'm sure you'll get them to play in vlc or totem.

---

### Post by p_quarles on 2009-01-31
> **diablo75 said:**
> Here are a few:

[http://scfire-ntc-aa01.stream.aol.com:80/stream/1035](http://scfire-ntc-aa01.stream.aol.com:80/stream/1035)
[http://scfire-dtc-aa01.stream.aol.com:80/stream/1003](http://scfire-dtc-aa01.stream.aol.com:80/stream/1003)
[http://streamer-mtc-aa02.somafm.com:80/stream/1032](http://streamer-mtc-aa02.somafm.com:80/stream/1032)
[http://electro.mthn.net:8400](http://electro.mthn.net:8400)
[http://www.protonradio.com:8000](http://www.protonradio.com:8000)

I'm sure you'll get them to play in vlc or totem.
All of those play fine for me in Amarok 2 (which, incidentally, doesn't come with the Cool Streams directory at all any longer). I don't think this is actually a codecs issue, in fact, but probably more a legit bug in the code.

---

### Post by diablo75 on 2009-01-31
> **p_quarles said:**
> All of those play fine for me in Amarok 2 (which, incidentally, doesn't come with the Cool Streams directory at all any longer). I don't think this is actually a codecs issue, in fact, but probably more a legit bug in the code.

This thread:

[https://answers.launchpad.net/ubuntu/+source/amarok/+question/4862](https://answers.launchpad.net/ubuntu/+source/amarok/+question/4862)

Says you're wrong.  And I do remember installing this codec package (libxine1-ffmpeg) on previous installations in the past and it solved the problem.  Installing it just now also solved the problem.

So the question remains, why can't libxine1-ffmpeg be included as a dependency of Amarok when you check it off in Synaptic?

---

### Post by p_quarles on 2009-01-31
> **diablo75 said:**
> This thread:

[https://answers.launchpad.net/ubuntu/+source/amarok/+question/4862](https://answers.launchpad.net/ubuntu/+source/amarok/+question/4862)

Says you're wrong.  And I do remember installing this codec package (libxine1-ffmpeg) on previous installations in the past and it solved the problem.  Installing it just now also solved the problem.

So the question remains, why can't libxine1-ffmpeg be included as a dependency of Amarok when you check it off in Synaptic?
Wait, but you indicated in your bug report that you had installed kubuntu-restricted-extras, and still couldn't play these streams. libxine1-ffmpeg is part of the kubuntu-restricted-extras package. So either you hadn't actually installed it, or that package didn't fix the issue. Either way, what you're saying is getting very confusing. 

I don't see what the problem is. This is not a bug.

---

### Post by smartboyathome on 2009-01-31
> **Frak said:**
> Or worse, MP3v2

Don't you mean mp4? :P

---

### Post by Eclipse. on 2009-01-31
> **Frak said:**
> Only a couple more years (December 2012) and the MP3 codec will be public domain.

Cant wait for that day to come.;)

---

### Post by diablo75 on 2009-01-31
> **p_quarles said:**
> Wait, but you indicated in your bug report that you had installed kubuntu-restricted-extras, and still couldn't play these streams. libxine1-ffmpeg is part of the kubuntu-restricted-extras package. So either you hadn't actually installed it, or that package didn't fix the issue. Either way, what you're saying is getting very confusing. 

I don't see what the problem is. This is not a bug.

libxine1-ffmpeg is not included with the restricted extras.  I just formated two PCs yesterday and can confirm that Amarok does not play any of those stations after a fresh install with the restricted extras installed.  If you really don't believe me, install Ubuntu inside Virtualbox and try it out for yourself.  libxine1-ffmpeg was missing from my system after installing the extras via Add/Remove.

---

### Post by p_quarles on 2009-01-31
> **diablo75 said:**
> libxine1-ffmpeg is not included with the restricted extras.  I just formated two PCs yesterday and can confirm that Amarok does not play any of those stations after a fresh install with the restricted extras installed.  If you really don't believe me, install Ubuntu inside Virtualbox and try it out for yourself.  libxine1-ffmpeg was missing from my system after installing the extras via Add/Remove.
Add/Remove has very limited functionality. What you installed is the restricted extras designed to work with Rhythmbox and Totem, not KDE. Add/Remove, being a simplified Gnome front-end for apt-get, should not be expected to help much with KDE applications. 

And, yes, libxine1-ffmpeg is in fact included in the *correct* package:
```
~$ apt-cache depends kubuntu-restricted-extras
kubuntu-restricted-extras
  Recommends: flashplugin-nonfree
    adobe-flashplugin
  Recommends: libxine1-ffmpeg
  Recommends: libavcodec-unstripped-51
  Recommends: libdvdread3
  Recommends: libk3b2-extracodecs
  Recommends: libmp3lame0
  Recommends: unrar
  Recommends: libtunepimp5-mp3
  Recommends: sun-java6-jre
  Recommends: msttcorefonts
```
Again, this is *not* a bug.

---

### Post by diablo75 on 2009-01-31
So if I had installed the KDE Restricted Extras instead of the GNOME restricted extras, I wouldn't have had this problem.

---

### Post by p_quarles on 2009-01-31
> **diablo75 said:**
> So if I had installed the KDE Restricted Extras instead of the GNOME restricted extras, I wouldn't have had this problem.
Exactly.

---

### Post by diablo75 on 2009-01-31
Can anything be done for the sake of GNOME users who aren't familiar with Linux so that they can just, you know... install the program and it just works they way they would expect it to?  If this isn't a bug, what is it?  Because I hate imaging a person installing an app like Amarok in GNOME, find it doesn't do what it says it does (per the application description in the installer they use) and think badly of Ubuntu and Amarok as a result.  I'm just trying to come up with a way to make the user experience for first timers less cumbersome so they don't feel intimidated or obligated to go on a goose chase through forums or google to get something simple to work because it was just missing one package that they shouldn't be required to be aware of.

---

### Post by Frak on 2009-01-31
> **smartboyathome said:**
> Don't you mean mp4? :P
Wewt Apple Quicktime? :P

---

### Post by Elfy on 2009-01-31
> **diablo75 said:**
> Can anything be done for the sake of GNOME users who aren't familiar with Linux so that they can just, you know... install the program and it just works they way they would expect it to? ...

Didn't it tell you that it needed to install a file and then open synaptic in the right place to finish the job - it did for me when I last forgot to install the correct package.

---

### Post by diablo75 on 2009-01-31
> **forestpixie said:**
> Didn't it tell you that it needed to install a file and then open synaptic in the right place to finish the job - it did for me when I last forgot to install the correct package.

Did you install using Add/Remove or Synaptic?  I'm setting up a fresh VM with Ubuntu right now for testing with revert snapshots so I can try both methods on a truly clean system to see if I notice what you are referring to.  But in the past experience, with installing Amarok several times via Add/Remove, I don't recall any message appearing to notify me that any additional packages would have to be installed manually.

---

### Post by gnomeuser on 2009-01-31
> **Frak said:**
> It's nobodies fault, but they should at least put the xine plugins in recommended when you install.

Depends on how you look at it.. didn't the people who made software patents legal get elected?

Tell you representative if the issue is important to you, they are your employees afterall, there to serve you.

---

### Post by Frak on 2009-01-31
> **gnomeuser said:**
> Depends on how you look at it.. didn't the people who made software patents legal get elected?

Tell you representative if the issue is important to you, they are your employees afterall, there to serve you.
I don't like to get into politics, but in the US they'd just laugh at you if you even mentioned "we should get rid of software patents, because they're bad". Employees or not, there is too much in software patents to just let it go.

---

### Post by I-75 on 2009-01-31
> **Tomatz said:**
> Then the world will adopt ogg vorbis :lolflag:

Some Linux podcasts have gone all OGG, like Linux Cranks and The Bad Apples Podcast.

[http://linuxcranks.info/ogg.xml](http://linuxcranks.info/ogg.xml)

[http://thebadapples.info/](http://thebadapples.info/)

---

### Post by diablo75 on 2009-01-31
> **forestpixie said:**
> Didn't it tell you that it needed to install a file and then open synaptic in the right place to finish the job - it did for me when I last forgot to install the correct package.

I just finished testing this out in a VM.

If you install Amarok via Add/Remove, no alerts come up at all.

If you install via Synaptic, you of course get a listing of all the specific dependencies that it will install along side amarok and _the libxine1-ffmpeg package is not one of them_.  

Attempting to play a radio station right off the bat after installing Amerok using either technique fails, unless the person installing the program know that they must manually install the libxine1-ffmpeg package (lets get a show of hands for those of you who knew this in advanced).  So, everybody running GNOME are not made aware of this while installing, and all the radio streams included will fail to play, making Amarok look like it's partially broken and/or Ubuntu look like it forgot to include/recommend the necessary package to make it work "correctly".

I feel sorry for the GNOME users who tried Amarok after hearing good things about it and walked away disappointed because nobody bothered to even scotch tape a solution on the side (have it recommend libxine1-ffmpeg during install) or mention all of the above gumshoe work people like me and others have done in the past to figure out how to get it to work the way they expected it to from the start.  

Yet this is not considered a bug?  Perhaps not even seen as a problem at all, not even in the slightest degree?  Just yesterday showed someone a screen shot of a printer sharing server settings window that told them to "click System>Administration>Firewall" and pointed out that there is no such thing as "Firewall" in the Admin menu, and they called that a bug; suggested I post it on Launchpad, so I did.  But something like this isn't a bug?  If that's the case, does that mean it will never be resolved and that a user is expected to know about all this stuff in advanced?

---

### Post by p_quarles on 2009-01-31
> **diablo75 said:**
> I just finished testing this out in a VM.

If you install Amarok via Add/Remove, no alerts come up at all.

If you install via Synaptic, you of course get a listing of all the specific dependencies that it will install along side amarok and _the libxine1-ffmpeg package is not one of them_.
No, because the fluendo MP3 codec is not, in fact, a dependency of Amarok. Why? Because you can run Amarok just fine without it. You may not get full functionality, but that is why it's also easy to install if you want it. 

As people have already attempted to explain, the MP3 codec is not included in Ubuntu/Kubuntu by default because it has chosen to to follow a policy of installing the least possible amount of non-free software by default. That policy has been long since established, and didn't suddenly arrive just yesterday when you decided to give Amarok a try.   

> Attempting to play a radio station right off the bat after installing Amerok using either technique fails, unless the person installing the program know that they must manually install the libxine1-ffmpeg package (lets get a show of hands for those of you who knew this in advanced).
Yes, and if you try to play the same stream in Rhythmbox or Banshee without installing the gstreamer MP3 codecs, they would run into the same problem.

> So, everybody running GNOME are not made aware of this while installing, and all the radio streams included will fail to play, making Amarok look like it's partially broken and/or Ubuntu look like it forgot to include/recommend the necessary package to make it work "correctly".
Yes, well, people who can't read the Ubuntu wiki instructions on enabling proprietary media codecs are going to have lots of issues with getting things to work right. That's kinda just how things are.

Installing an OS on your own is a difficult proposition. It's not recommended, I would say, for those averse to doing basic research when things go south. For them, there are the Dell machines sold with Ubuntu preinstalled, which comes with codecs for most major media formats, as well as a legally licensed DVD player. This is stuff that Ubuntu cannot give away with its free edition because they do not own the rights to it. 

> I feel sorry for the GNOME users who tried Amarok after hearing good things about it and walked away disappointed because nobody bothered to even scotch tape a solution on the side (have it recommend libxine1-ffmpeg during install) or mention all of the above gumshoe work people like me and others have done in the past to figure out how to get it to work the way they expected it to from the start. 

Yet this is not considered a bug?  Perhaps not even seen as a problem at all, not even in the slightest degree?  Just yesterday showed someone a screen shot of a printer sharing server settings window that told them to "click System>Administration>Firewall" and pointed out that there is no such thing as "Firewall" in the Admin menu, and they called that a bug; suggested I post it on Launchpad, so I did.  But something like this isn't a bug?  If that's the case, does that mean it will never be resolved and that a user is expected to know about all this stuff in advanced?
No, it is not a bug, because the behavior is not unexpected or erroneous. It might be, if phrased correctly, a feature request, insofar as you are asking for a dialogue that offers to install the necessary codecs on demand. That is a potentially workable idea, and several similar things have been implemented in the past -- Totem, for instance, got such a dialogue a while back. But the absence of a feature is not a bug.

---

### Post by diablo75 on 2009-01-31
> **p_quarles said:**
> No, it is not a bug, because the behavior is not unexpected or erroneous. It might be, if phrased correctly, a feature request, insofar as you are asking for a dialogue that offers to install the necessary codecs on demand. That is a potentially workable idea, and several similar things have been implemented in the past -- Totem, for instance, got such a dialogue a while back. But the absence of a feature is not a bug.

That being the case, what's the best way to pursue getting a feature like the one I am seeking implemented?  I would assume filing a bug report is out of the question (although I already submitted one I can now predict will be negated).  Does that narrow it down to using Ubuntu Brainstorm to submit an idea and see how it pans out, or are there additional options available I could look into.

---

### Post by 23meg on 2009-01-31
[QUOTE=diablo75]That being the case, what's the best way to pursue getting a feature like the one I am seeking implemented?[/QUOTE]

Generally it goes [like this]("http://www2.bryceharrington.org:8080/drupal/node/53").

---

### Post by p_quarles on 2009-01-31
> **diablo75 said:**
> That being the case, what's the best way to pursue getting a feature like the one I am seeking implemented?  I would assume filing a bug report is out of the question (although I already submitted one I can now predict will be negated).  Does that narrow it down to using Ubuntu Brainstorm to submit an idea and see how it pans out, or are there additional options available I could look into.
You can file feature requests at Launchpad as well, they just need to be marked and phrased as such.

By the way, though, it is extremely unlikely that this will be implemented in Amarok 1.4. Ubuntu 8.10 will ship with Amarok 2, and as far as I know will not include 1.4 at all. I could be wrong about that, but assuming I am not, it is unlikely that new features will be added to 1.4 at this point, since all Ubuntu versions that ship with it have already been released and are in bug-fix only mode as far as the official repositories go. 

A dialogue informing the user of availability of necessary codecs, and telling how to install them in K/Ubuntu specifically, would be useful for Amarok 2, though.

---

### Post by jrusso2 on 2009-01-31
> **gnomeuser said:**
> Depends on how you look at it.. didn't the people who made software patents legal get elected?

Tell you representative if the issue is important to you, they are your employees afterall, there to serve you.

Thats a good one. If only people would represent the people that voted for them this country would be in much better shape.

---

### Post by Skripka on 2009-01-31
> **jrusso2 said:**
> Thats a good one. If only people would represent the people that voted for them this country would be in much better shape.

Really?

I'd say my state legislature really represents accurately the interests and thoughtfulness of their constituency.

...a compliment-that is not, BTW.

---

### Post by Vadi on 2009-01-31
Amarok's fault for not integrating with GStreamer and offering the user to download the codecs when he's missing them.

---

### Post by p_quarles on 2009-01-31
> **Vadi said:**
> Amarok's fault for not integrating with GStreamer and offering the user to download the codecs when he's missing them.
Nonsense. That's like saying that Banshee should integrate with Xine. It is also not the upstream project's responsibility to be aware of the packaging schemes used downstream. 

Again, this is an Ubuntu-specific *feature request*, not a bug against Amarok.

---

### Post by Twitch6000 on 2009-01-31
> **diablo75 said:**
> Can anything be done for the sake of GNOME users who aren't familiar with Linux so that they can just, you know... install the program and it just works they way they would expect it to?  If this isn't a bug, what is it?  Because I hate imaging a person installing an app like Amarok in GNOME, find it doesn't do what it says it does (per the application description in the installer they use) and think badly of Ubuntu and Amarok as a result.  I'm just trying to come up with a way to make the user experience for first timers less cumbersome so they don't feel intimidated or obligated to go on a goose chase through forums or google to get something simple to work because it was just missing one package that they shouldn't be required to be aware of.

Well with a Gnome user, I would expect them to be using gnome apps instead of KDE apps. This is just for your average user though.

So instead of them using Amarok I would think they would be using Banshee or Rythmbox. I know I use Rythmbox :).

If they do this a problem like you had would not occur. Mixing such programs though cause such things to happens.

Someone correct me if I am wrong :).

---

### Post by Vadi on 2009-02-01
> **p_quarles said:**
> Nonsense. That's like saying that Banshee should integrate with Xine. It is also not the upstream project's responsibility to be aware of the packaging schemes used downstream. 

Again, this is an Ubuntu-specific *feature request*, not a bug against Amarok.

I didn't realize Xine had this capability, sorry. The point stresses was "offers the user to download the codecs".

In any case, the user is left with an inferior version of the program - and it's developers are apparently fine to leave that up to someone else to do. I personally would want my end-user to get the best experience possible - but it seems it's not the case with Amarok devs. 

For one, if they don't want to do the integration, they could have a least made the program tell the user "You don't have mp3 codecs installed" upfront instead of some error message that send them on a trip of making 3 threads and wasting a lot of time. But, their software, their time, they do it how they want to.

---

### Post by p_quarles on 2009-02-01
> **Vadi said:**
> In any case, the user is left with an inferior version of the program - and it's developers are apparently fine to leave that up to someone else to do. I personally would want my end-user to get the best experience possible - but it seems it's not the case with Amarok devs. 
I guess maybe there's some confusion here about how the upstream/downstream model works. Amarok doesn't develop primarily for the end user: they develop for packagers. Unless the user is pulling code from SVN or whatever Amarok uses specifically, the distro packager really is the one responsible for the package. It is Kubuntu's choice, in this case, not to include libxine1-ffmpeg as a dependency. They did this on the grounds that the package is encumbered by patents in a number of countries that recognize software patents. Instead, they chose to make it extremely easy to get, which satisfies the vast majority of reasonable users. 

So, reporting the fact that Kubuntu doesn't include the MP3 codec as a dependency of Amarok to the Amarok developers doesn't make any sense. The issue, such as it is, lies in Kubuntu's packaging of the product, and the extent of the issue in turn depends on how well they handle it. To me, this is the problem: 
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

That information is outdated and somewhat unhelpful, even though it does resolve this particular issue.

So, what can you do to help? Complain to the Amarok developers, who have no sway over how Kubuntu packages its product, or create a Launchpad account and edit the Wiki with some more up-to-date and less cluttered information? 

> For one, if they don't want to do the integration, they could have a least made the program tell the user "You don't have mp3 codecs installed" upfront instead of some error message that send them on a trip of making 3 threads and wasting a lot of time. But, their software, their time, they do it how they want to.
How is "you don't have mp3 codecs installed" any more helpful than "decoder not available"? To me, they mean pretty much the same thing, and if I'm at a total loss about how to proceed, neither error message really helps me.

---

### Post by Vadi on 2009-02-01
You are wrong, because the [http://amarok.kde.org/wiki/Download](http://amarok.kde.org/wiki/Download) page exists. If it did not, then you would have been right, they develop only for packagers.

Interestingly enough, they do address this issue here: [http://amarok.kde.org/wiki/MP3_on_Kubuntu](http://amarok.kde.org/wiki/MP3_on_Kubuntu)

However neither the program nor the developer bothered to point it out to the user...

---

### Post by FuturePilot on 2009-02-01
> **Vadi said:**
> You are wrong, because the [http://amarok.kde.org/wiki/Download](http://amarok.kde.org/wiki/Download) page exists. If it did not, then you would have been right, they develop only for packagers.


Notice that all the links on there for the different distros just redirect to a page on the distro's site or give instructions on how to install it from your distro's repos. Nowhere on there do I see a deb package I can download. So yes they are primarily developing for packagers.

---

### Post by diablo75 on 2009-02-01
> **Twitch6000 said:**
> Well with a Gnome user, I would expect them to be using gnome apps instead of KDE apps. This is just for your average user though.

Unfortunately most new users don't know the difference between GNOME and KDE when they first try Ubuntu, so the expectation of them to avoid using KDE apps flies out the window.  This is compounded by the fact that if you open up Add/Remove and click on Sound/Video, Amarok is simply right there for the taking, and probably gets more attention for the same reason "A-1 Appliance Repair" gets more attention from Yellow Page adverts:  It's alphabetically the foremost app of it's kind a person might be inclined to try and download.  And even though the description says it's a KDE app, that doesn't make a difference to a new user because they're still being given the opportunity to install the app via the, what I would call "Synaptic Package Manager For Dummies", which is suppose to "idiot proof" the installation of software and I would hope also "idiot proof" the experience of that software after it's installed.  

Heck, when I first started using Ubuntu, I probably thought KDE was a programming language, like Java or something, and just thought, "Well, I could care less about the silly details; lets just check this guy off here and see what this app is all about".  It's what most people actually do, believe it or not.  Former Windows and Mac users shouldn't be expected to be familiar with so much Linux lingo the first day they preview an OS just to see if they like it or not.  Otherwise you end up with articles in the NY Times talking about how unfriendly and "difficult" the whole damn thing is.

---

### Post by p_quarles on 2009-02-01
> **Vadi said:**
> You are wrong, because the [http://amarok.kde.org/wiki/Download](http://amarok.kde.org/wiki/Download) page exists. If it did not, then you would have been right, they develop only for packagers.

Interestingly enough, they do address this issue here: [http://amarok.kde.org/wiki/MP3_on_Kubuntu](http://amarok.kde.org/wiki/MP3_on_Kubuntu)

However neither the program nor the developer bothered to point it out to the user...
Well, like FuturePilot already pointed out, that page is a just a catalogue of packages for major *nix distros, so far from my being "wrong," I would say you're supporting my point. 

But you're also kind of missing my point: even if Amarok does decide to build it's own .deb packages, they are *still* not the ones who decide how to package the Amarok that ships with Kubuntu. It's pretty straightforward: Kubuntu is downstream from Amarok. Surely it is not too bizarre that the open source world, like just about everyone else, would prefer that the responsibility for an action be placed upon the person who takes the action? So, Vadi, why are you insisting that Kubuntu's Amarok packaging practices should be reported as a bug against Amarok? Why not take up the issue with those who took the action you disagree with?

---

### Post by Tomatz on 2009-02-01
Thought linux was about getting your hands dirty...

---

### Post by diablo75 on 2009-02-01
> **Tomatz said:**
> Thought linux was about getting your hands dirty...

I think you could probably say that about any operating system that has a CLI included with it.

---

### Post by Tomatz on 2009-02-01
> **diablo75 said:**
> I think you could probably say that about any operating system that has a CLI included with it.

Discussion over then ;)

---

### Post by Vadi on 2009-02-01
Yeah, it does really seem that Amarok developers don't care about the end-users experience and leave it up to the distributions - which in this case is not guaranteed to be particularly helpful.

Like I said, it's their program, they do whatever they want. But for any OSS program I help with, I make sure that the end-user has a pleasant experience - and if an issue outside is outside my bounds (like mp3 codecs), I'd at least try and reduce the user confusion to a minimum and instruct them on what to do - and not have them go on a bouncing spree which is compared to very crappy paid support.

But hey, their choice, their users :)

---

### Post by p_quarles on 2009-02-01
> **Vadi said:**
> Yeah, it does really seem that Amarok developers don't care about the end-users experience and leave it up to the distributions - which in this case is not guaranteed to be particularly helpful.
That's a pretty disrespectful thing to say about a group of developers who obviously consider Amarok to be their baby. Read Planet Amarok for five minutes and you'll see this is the case. Or visit #amarok on freenode. I really think that either this inflammatory accusation should be backed up with real evidence, or you should not make it. Turning your personal disagreements with/misapprehensions about a software project into an opportunity to question the motives of others is, for all intents a purposes, like a low blow in the boxing ring. 

> Like I said, it's their program, they do whatever they want. But for any OSS program I help with, I make sure that the end-user has a pleasant experience - and if an issue outside is outside my bounds (like mp3 codecs), I'd at least try and reduce the user confusion to a minimum and instruct them on what to do - and not have them go on a bouncing spree which is compared to very crappy paid support.
Like by hosting a web page that gives detailed instructions on how to get MP3 playback working in Kubuntu? Like the page you linked to?

> But hey, their choice, their users :)
And they do a pretty good job of satisfying the bulk of their users, by all accounts! Amarok didn't get to be one of the most popular FOSS projects out there by being mystifying and unusable.

---

### Post by Mr. Picklesworth on 2009-02-01
> **diablo75 said:**
> I think you could probably say that about any operating system that has a CLI included with it.

So do you realize that every desktop operating system on the market today has an included CLI? Even the phone ones.


I can't believe this thread. Report posted on Amarok's bug tracker regarding a packaging issue. Packaging is not handled by the Amarok project but by distributions which use the software. It was clearly suggested to file the bug report downstream where the issue can actually be resolved.
End of story.

Yes, believe it or not a bug report exists because we want the bug to be fixed; bug trackers are not complaint boards!

They cannot do anything about it themselves because a hack to support automatic codec install in Ubuntu would be idiotic, and codecs are an external dependency. Amarok applying PackageKit could be nice, though.

Sometimes I wonder...

---

### Post by diablo75 on 2009-02-01
> **Mr. Picklesworth said:**
> So do you realize that every desktop operating system on the market today has an included CLI? Even the phone ones.

The point I was trying to make is that, while almost every operating system on the planet has a CLI, it doesn't mean the OS has to be "about getting your hands dirty."  Those billboards advertising Ubuntu as "Linux for Human Beings" comes across to most as meaning, "Hooray!  Us "normal people" finally don't HAVE to get our hands dirty to use Linux!"  Anybody can get their hands dirty with any OS... if they want to.  Most people *don't* want to get their hands dirty, with a CLI or even a GUI for that matter.  What most people want is something that "just works."  Mac (and in some cases Windows) have a leg up on Linux by striving to make the OS easier and easier to use.  And I've always been under the impression that this is what Ubuntu has been uniquely striving for, too.  Not to be yet another Linux distro for Linux users, but for Windows and Mac users as well.  If it's not trying to do this, then I'd love to know what everyone thinks about [Mark Shuttleworth's vision of beating Mac at its own game]("http://itmanagement.earthweb.com/osrc/article.php/3757246/Mark+Shuttleworth+on+Ubuntu+and+the+Linux+Desktop.htm") with the end goal of appealing to "the ordinary desktop user, or the non-specialist user".

---

### Post by Vadi on 2009-02-01
> **p_quarles said:**
> That's a pretty disrespectful thing to say about a group of developers who obviously consider Amarok to be their baby.

But I'm not saying untruth - I'm just saying what you just said, they consider it to be the distribution's job, and not theirs. The guy on the amarok forum said it's not their fault either - which did make the user's instance of the app work.

Not flaming here, it's what I colleted from your responses and theirs. The upstream model, blah blah, it is someone else's job to take care of it. While I think that it's a privilege that someone downstream does *anything* for you - even include it in their repositories.

---

### Post by chucky chuckaluck on 2009-02-01
i guess by the time i've ever installed amarok in any distro, i had long since gotten all the restricted crap straightened out. i don't understand why anyone would blame amarok for any of this.

---

### Post by cardinals_fan on 2009-02-01
> **Vadi said:**
> But I'm not saying untruth - I'm just saying what you just said, they consider it to be the distribution's job, and not theirs. The guy on the amarok forum said it's not their fault either - which did make the user's instance of the app work.

Not flaming here, it's what I colleted from your responses and theirs. The upstream model, blah blah, it is someone else's job to take care of it. While I think that it's a privilege that someone downstream does *anything* for you - even include it in their repositories.
It really isn't Amarok's job to deal with issues related to individual distro packaging.  If the packager screws up, there's the problem.

---

### Post by p_quarles on 2009-02-01
> **Vadi said:**
> But I'm not saying untruth - I'm just saying what you just said, they consider it to be the distribution's job, and not theirs. The guy on the amarok forum said it's not their fault either - which did make the user's instance of the app work.

Not flaming here, it's what I colleted from your responses and theirs. The upstream model, blah blah, it is someone else's job to take care of it. While I think that it's a privilege that someone downstream does *anything* for you - even include it in their repositories.
No, you said they don't care about their users, which is utter nonsense. What you are implying, moreover, is that any statement by an Amarok developer that they are not the primary contact person for a particular issue is an attempt at absconding from responsibility for the application itself, which is also false. 

Vadi, this point I am making (in agreement with the Amarok developer) is very straightforward: A decision that was made by Kubuntu packagers led to a potentially undesirable result. You should let the person who made that decision know, because he or she is in the best position to do something about it. Do you actually disagree with that, and if so why? 

As for feeling "gratitude" for downstream work, that goes both ways. Sure, Amarok is glad that they get the exposure they do through a popular Linux distro. Canonical should be grateful for quality software like Amarok, too! Without it, they would not be in the position they are in today.

---

### Post by Vadi on 2009-02-01
Yes, but does that matter to the user? For all they care, their app is not working.

That's why a thoughtful dev would consider the possible failing points (and the lack of mp3's isn't exactly a hard case to think of / stumble on) and make the app help the user troubleshoot. Not leave them in a "wth does this message mean and why is it not working" state.

Think of this as a car. When you're out of gas, it's not the cars problem. But it does tell you you're out of gas, so you know what the issue is. Amarok-car doesn't - it think it's job it's job to, someone else is supposed to do it (which is correct). But you, the driver, are definitely more stumped as to why is the car not working.

edit: nevermind, this is getting to a rather amusing point with humorous claims - I've got more productive things to do. This was my input though, and I of course cannot change the design philosophy of someone else nor was I attempting to. It is, in my opinion, flawed, as this and potentially other examples will demonstrate.

---

### Post by cardinals_fan on 2009-02-01
> **Vadi said:**
> Yes, but does that matter to the user? For all they care, their app is not working.

That's why a thoughtful dev would consider the possible failing points (and the lack of mp3's isn't exactly a hard case to think of / stumble on) and make the app help the user troubleshoot. Not leave them in a "wth does this message mean and why is it not working" state.

Think of this as a car. When you're out of gas, it's not the cars problem. But it does tell you you're out of gas, so you know what the issue is. Amarok-car doesn't - it think it's job it's job to, someone else is supposed to do it (which is correct). But you, the driver, are definitely more stumped as to why is the car not working.
There certainly should be an intelligent error message; "unidentified file format: mp3 playback not available" or something like that.

---

### Post by Namtabmai on 2009-02-01
> **Vadi said:**
> Think of this as a car. When you're out of gas, it's not the cars problem. But it does tell you you're out of gas, so you know what the issue is. Amarok-car doesn't - it think it's job it's job to, someone else is supposed to do it (which is correct). But you, the driver, are definitely more stumped as to why is the car not working.

That's a good analogy. My petrol (gas) car's fuel gauge is showing empty so I fill it up with diesel and it still doesn't work even thou the gauge is showing full!

(BTW I hate car analogies.)

---

### Post by diablo75 on 2009-02-01
> **cardinals_fan said:**
> There certainly should be an intelligent error message; "unidentified file format: mp3 playback not available" or something like that.

Seems we end up with both sides pointing valid fingers at each other. 

Amarok:  "It's your fault you didn't bother to bundle x package with your distro."

Ubuntu:  "Amarok should have at least written in error messages that actually provide the user with info they could use to better troubleshoot whatever problems they encounter."

Am I right?

---

### Post by cardinals_fan on 2009-02-01
> **diablo75 said:**
> Seems we end up with both sides pointing valid fingers at each other. 

Amarok:  "It's your fault you didn't bother to bundle x package with your distro."

Ubuntu:  "Amarok should have at least written in error messages that actually provide the user with info they could use to better troubleshoot whatever problems they encounter."

Am I right?
Yes.  I see Amarok's point as a more valid complaint, but both make logical sense.

---

### Post by igknighted on 2009-02-01
> **Vadi said:**
> Yes, but does that matter to the user? For all they care, their app is not working.

That's why a thoughtful dev would consider the possible failing points (and the lack of mp3's isn't exactly a hard case to think of / stumble on) and make the app help the user troubleshoot. Not leave them in a "wth does this message mean and why is it not working" state.

Think of this as a car. When you're out of gas, it's not the cars problem. But it does tell you you're out of gas, so you know what the issue is. Amarok-car doesn't - it think it's job it's job to, someone else is supposed to do it (which is correct). But you, the driver, are definitely more stumped as to why is the car not working.

Your analogy is wrong.  A car is a finished product, like a distribution.  Amarok is merely a part, like the gas tank.  Amarok developers are assuming that the person who puts their app (the gas tank) hooks the sensor for how much gas is in the car into the central computer on the car, rather than build their own computer on the gas tank.

In windows, every app handles its own issues like the gastank with its own computer.  But linux separates functions.  Lots of apps need codecs.  It would be really silly for every music player to code in that function.  And it would be silly for amarok to write the code for every distro out there.  Distribution specific stuff, and code needed by a vairety of apps, is best left to the distribution to handle.  And Ubuntu does this, it's just that the code is young.  The gnome version doesn't recognize KDE, and I think only does gstreamer plugins.

---

### Post by p_quarles on 2009-02-01
> **cardinals_fan said:**
> There certainly should be an intelligent error message; "unidentified file format: mp3 playback not available" or something like that.
It already says "Decoder not available."

Part of the problem here is that those on the "Amarok should do more for its users!" side of this are relying on the old straw man of the "average user" who is by turns astonishingly ignorant of computing terms and at the same time would know exactly what to do if he were just instructed to install something called "libxine1-ffmpeg."

It's very easy to say things like "There should be better error messages," but much more difficult to figure out what exactly constitutes an error message that will be useful to the end user. 

As I've already said, I think a dialogue that attempts to install new codecs on demand would be a useful feature for Amarok. But it is a feature request, and not a bug against the current code.

EDIT: Also, just wanted to point out the following is the top hit for "[mp3 amarok kubuntu](http://www.google.com/search?hl=en&safe=off&q=mp3+amarok+kubuntu&btnG=Search)" on Google:
[http://amarok.kde.org/wiki/MP3:Kubuntu](http://amarok.kde.org/wiki/MP3:Kubuntu)

So, while I am absolutely sympathetic to new users who feel overwhelmed, there really are a vast number of resources out there to help them. If they can't figure out the search terms, they can ask here, in IRC, on mailing lists, or however else they prefer to request assistance, and they will get a relatively quick answer to this very simple-to-fix issue.

---

### Post by diablo75 on 2009-02-01
> **p_quarles said:**
> It already says "Decoder not available."


It's very easy to say things like "There should be better error messages," but much more difficult to figure out what exactly constitutes an error message that will be useful to the end user. 

I agree with that.  Further, I would imagine it would be too difficult to create more specific error messages that, as you mentioned, might explicitly say something like, "You're missing the xine1-ffmpeg package" because that package isn't always called xine1-ffmpeg in other distros (I think...).

---

### Post by diablo75 on 2009-02-01
> **p_quarles said:**
> 

EDIT: Also, just wanted to point out the following is the top hit for "[mp3 amarok kubuntu](http://www.google.com/search?hl=en&safe=off&q=mp3+amarok+kubuntu&btnG=Search)" on Google:
[http://amarok.kde.org/wiki/MP3:Kubuntu](http://amarok.kde.org/wiki/MP3:Kubuntu)

I doubt GNOME users are doing google searches about kubuntu because they aren't using it.  A search for mp3 amarok ubuntu brings up somewhat less useful results.  In fact the very first result has the solution.... in the comments following a post that instructs the user to install gstreamer, and it didn't pan out for the users who followed the instructions.  Still, I don't think having to do a search like this should be required of the average desktop user.

---

### Post by lyceum on 2009-02-01
diablo75, just switch to Kubuntu. I do not have this issue. I install, add synaptic, add the kubuntu non-free package and I am good to go. I am listening to MP3's right now and I use the internet radio all the time. Life it good and my fingers are typing, no pointing ;)

---

### Post by Vadi on 2009-02-01
> **diablo75 said:**
> Seems we end up with both sides pointing valid fingers at each other. 

Amarok:  "It's your fault you didn't bother to bundle x package with your distro."

Ubuntu:  "Amarok should have at least written in error messages that actually provide the user with info they could use to better troubleshoot whatever problems they encounter."

Am I right?

I don't represent Ubuntu's point. Ubuntu already handles lack of mp3 codecs in it's default media player nicely - tells you to get them when you encounter content that requires them. I'd need to seek Kubuntu's point here as they specialize in KDE and, if they ship Amarok by default, is their responsibility for the codec thing.

---

### Post by butlins on 2009-02-01
So then some Kde apps work better in Gnome than Gnome centric apps.

example, in my experience
K3B works better in Gnome than brasero does

---

### Post by diablo75 on 2009-02-01
> **lyceum said:**
> diablo75, just switch to Kubuntu. I do not have this issue. I install, add synaptic, add the kubuntu non-free package and I am good to go. I am listening to MP3's right now and I use the internet radio all the time. Life it good and my fingers are typing, no pointing ;)

I don't need to fix this issue; I've already done it by installing the libxine1-ffmpeg package in Ubuntu.  I didn't start this thread to look for a solution (I knew one was already out there).  I started this thread so that, hopefully, people who wander into trying Amarok out on a GNOME desktop get what they expect without the need to conduct a research project like some have done in order to determine the cause of the problem and fix it, not to mention those who won't spend a shred of time looking around for the fix because they feel it should have just worked right away without need for manual patching.  If anything come of this, I suppose it all could be thought of as a kind of case study for me and a few others to learn from when it comes to finding issues like this and determining the best course of action to take in hopes of resolving it for the masses in advanced.  Up until yesterday, I would have called this a bug.  I've learned now that it's incorrect to think so, and so I've adjusted my posture towards the issue.

---

### Post by lyceum on 2009-02-03
> **diablo75 said:**
> I don't need to fix this issue; I've already done it by installing the libxine1-ffmpeg package in Ubuntu.  I didn't start this thread to look for a solution (I knew one was already out there).  I started this thread so that, hopefully, people who wander into trying Amarok out on a GNOME desktop get what they expect without the need to conduct a research project like some have done in order to determine the cause of the problem and fix it, not to mention those who won't spend a shred of time looking around for the fix because they feel it should have just worked right away without need for manual patching.  If anything come of this, I suppose it all could be thought of as a kind of case study for me and a few others to learn from when it comes to finding issues like this and determining the best course of action to take in hopes of resolving it for the masses in advanced.  Up until yesterday, I would have called this a bug.  I've learned now that it's incorrect to think so, and so I've adjusted my posture towards the issue.

Well, if you weren't looking for a solution maybe mine will help someone else ;)

---

### Post by Grant A. on 2009-02-03
> **butlins said:**
> So then some Kde apps work better in Gnome than Gnome centric apps.

example, in my experience
K3B works better in Gnome than brasero does

I concur, K3B is a wonderful piece of software, but I think brasero is much better in XFCE than GNOME.

On topic:

Distributors are essentially end-users. It is not the developers' problem if the end-user does not run the software as specified.

---

