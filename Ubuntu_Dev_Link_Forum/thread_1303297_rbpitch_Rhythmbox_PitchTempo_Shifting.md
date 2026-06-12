---
title: "rbpitch: Rhythmbox Pitch/Tempo Shifting"
date: 2009-10-28
forum: Ubuntu Dev Link Forum
---

### Post by allquixotic on 2009-10-28
[SIZE=3]rbpitch is a plugin for Rhythmbox that lets you change the pitch, tempo, and speed in real-time while playing a song. **It needs testing, popularity, and bug fixing** -- you can help! Just trying it and reporting your findings here will be immensely helpful!

And you might find it useful, too: I've heard that it is useful for dance lessons, guitar practice, and singing. I personally just enjoy the aesthetics of changing the pitch, tempo, and speed of my music.[/SIZE]

[SIZE=3]The new homepage for rbpitch is on Launchpad: [http://launchpad.net/rbpitch](http://launchpad.net/rbpitch)[/SIZE] [SIZE=3]You can find downloads, information, source code and a bug tracker there.[/SIZE] **[SIZE=3]Binaries are available for Ubuntu 10.10, 11.04, and 11.10! Visit the Launchpad site and look for "END USER INSTALLATION INSTRUCTIONS"![/SIZE]** [SIZE=3]For those running other distros, you can check out the source code and read the file README.txt for instructions to compile from source. This thread is very old and contains obsolete / incorrect build instructions; please disregard them![/SIZE]

[SIZE=3]My plan for the future is to support the latest stable version of Ubuntu with binary packages that can be installed through Ubuntu Software Center (download a .deb file and double-click it). For other distros running a recent version of Rhythmbox (I currently require Rhythmbox v0.13.0 or later), you will have to build from source. But it is much easier now than it used to be![/SIZE]

[SIZE=3]rbpitch was inspired by Olli Parviainen's excellent PaceMaker plugin for WinAmp. WinAmp and PaceMaker won't run on GNU/Linux, though. Rhythmbox is an excellent media player, and rbpitch makes it that much better! :guitar:[/SIZE]


[IMG]http://tiyukquellmalz.org/rbpitch-0.13.0.png[/IMG]

[SIZE=3]Thanks,

Sean[/SIZE]

---

### Post by wilee-nilee on 2009-10-28
I am curious as to what you are using this for.

---

### Post by allquixotic on 2009-10-28
From the readme:

Q: What are the possible uses of rbpitch?
A: Borrowed from [http://surina.net/pacemaker](http://surina.net/pacemaker) by Olli Parviainen (no infringement intended):
*Slower music tempo eases practicing music
*Change the music key to match the singer's voice (karaoke, singing practice)
*Dancers can change the music tempo suitable for dancing
*Adjust music key instead of retuning instrument for each song
*Listen 78 RPM vinyl singles with a usual 33/45 RPM disc player
*Transcribe tunes
*Write down dictations


My "real" use of it only fits into the "change the music key to match the singer's voice for karaoke" use. However, even when I'm not singing, I use it just for fun. I find that changing the pitch/tempo of a song slightly increases the number of times I can listen to it without it getting boring -- or a song that I've worn out suddenly becomes significantly less worn out.

There is actually substantial academic research indicating that mild pitch/tempo shifting causes sounds to seem more varied and interesting, stimulating brain activity. It is frequently used in computer games for things like footsteps that play repetitively over and over.

Some people just can't fathom listening to a song in a different pitch or tempo because it deviates from the original. I don't care to break people of this kind of perception, but I know there a lot of people out there who don't hold this sort of bias.

So, aside from the "real" practical uses stated in the readme file, I'd say that I mainly pitch or tempo shift for pure fun or "ear candy". But it really is useful to train my voice (especially when singing in a foreign language!) by slowing down the tempo a lot until I can pronounce the syllables just right.

I developed this app with myself as a user in mind; hopefully other users who share similar interests will also find it useful.

**EDIT:** Even if these don't seem like compelling reasons for you to use rbpitch, keep in mind the requirements of rbpitch:

Disk space: 96KB for binaries only; the source files are just 30KB.

Runtime overhead: **zero** if the plugin is not loaded (the user can choose whether to load it or not). If the plugin is loaded but not being used for pitch shifting, runtime overhead is only a few kb of memory. And it needs about 1.5% usage of one core of a Core i7 2.6GHz while actively performing pitch shifting on a playing song.

The cost of initial integration is higher (in man-hours), but this is a one time cost that can be shared among teams from different distributions if we cooperate. I've already done the hard work and developed the code, and I am committed to continued support for bugfixes, security, and features that would not significantly add to the requirements or dependencies.

Thanks,

Sean

---

### Post by wilee-nilee on 2009-10-28
Thanks for the information, the reason I asked is that having aquired pitch myself, I wasn't born with perfect pitch but aquired it through years of playing. so having music in; A 440 reference is more enjoyable for me. Although I belive Baroque pitch was 338 I could be wrong though. I think having the option to change it and the speed is a good idea for those that it benifits. I would be curious to see the research you reference can you at least post the names of the authors I can find it for free via my college library.

---

### Post by allquixotic on 2009-10-28
Actually, I don't have a reference to a peer reviewed article or anything like that. I picked up this anecdotal thesis that "occasional pitch variation increases replayability of familiar songs and stimulates brain activity" in college -- from something I heard in a lecture. I'm not sure if the professor was referring to some literature they'd read; I wish I had asked them!

The closest thing I can find is this page from a musicology class: [http://www.musiccog.ohio-state.edu/Music829D/Notes/Scherer.html](http://www.musiccog.ohio-state.edu/Music829D/Notes/Scherer.html)

The first chart on that page seems to suggest that different pitches and tempos induce different ratings or emotional states. This is kind of a duh when you think about it -- if you listen to slow, plodding music with uniform and steady tones, it's likely to put you to sleep. But if you listen to highly varied, rapidly changing, dynamic melodies, it's likely to wake you up if you're feeling drowsy!

What this plugin allows you to do is to take any given song and pretty much tailor it to the mood you want. If I love the lyrics of a really fast song, but its pitch and tempo are too manic for my mood (maybe I want to chill out in the evening), I can shift down the pitch slightly, and the tempo even more, to make the song easier to process, and actually less stimulating. OTOH, if I want to take a relaxing song and blaze through it in a fraction of the time, I can do that -- the result will be anything but relaxing.

The other point I wanted to make is that these pitch/tempo shifts keep the music "fresh". Surely you can see that by shifting the pitch and tempo sufficiently, the similarity between the original recording and what you're hearing diverges. This creates a sense of novelty that you haven't heard these particular tones at this particular speed before, and thus can help you enjoy a song that currently instills boredom just by thinking about it.

This is actually a fertile area for higher level research in cross-disciplinary studies (music theory + sociology + psychology). I bet you could even make a compelling case for encouraging employees who listen to music while they work to vary the pitch/tempo a bit to stimulate brain activity. Especially where people listen to the same fixed set of tracks for weeks or months on end (not all that uncommon I'd think), you don't want them to become bored of what they're listening to. This boredom might reflect in their diligence and the level of effort they put into their job. Maybe all they need (besides a new, fresh set of tunes) is to start pitch/tempo shifting their existing collection of music.

I know that's probably taking it too far beyond the realm of practical believability, but I don't think I'm going out on such a shaky limb by saying there are people out there who will find interesting uses of these three simple musical transformations (namely, pitch shifting, tempo shifting, and pitch+tempo shifting together).

Anyway, that's pretty off topic even within this thread. I've established my rationale for the program's existence; if you disagree with it, nothing compels you to use it. One of the reasons I created this thread is to determine how many people actually agree with my rationale -- people who actually think, "*yeah, I could use something like that*", or "*yeah, that would be fun!*". If it turns out to be no one but me, oh well -- in the worst case, I'll have written a program that makes me happy. Too bad for those who find it doesn't do the same for them.


Thanks for your feedback,

Sean

---

### Post by wilee-nilee on 2009-10-28
The link is a good source there are other studies mentioned within it, so when I have time I will definitely look for the studies.  I like mixed media art, like mixtures of genres, spoken word and visual all together. Music and pitch and rhythm seem to be part of a hard wired structure in the brain although measuring the depth of it has so many variables. The work of biologists recording bird songs and other communications with various species find that rhythm and pitch are part of the communication and used for various activities.   For somebody like myself basically a classically trained musician, who branched out to playing Jazz professionally, along with mixed media expression that was at times completely improvisational music has different effects. I would rather play in a minor key, and when I came across a chord that was major even if it had a lot of extra altered notes like flatted 4th raised 5th etc I generally play it with the relative minor as the tone centre which gives it a interesting sound being that the relative minor is the same scale but starting on the 6th note of the scale.  There are two major figures in altered pitch expression; a more mathematical approach the first is Nicholas Slonimsky. [http://en.wikipedia.org/wiki/Nicolas_Slonimsky](http://en.wikipedia.org/wiki/Nicolas_Slonimsky) The next is George Russell who wrote a book called Lydian Chromatic Concepts which is a very interesting approach to scales and chords.  [http://en.wikipedia.org/wiki/George_Russell_%28composer%29](http://en.wikipedia.org/wiki/George_Russell_%28composer%29) George Russell influenced a ton of players from Miles Davis to John Coltrane, Frank Zappa and many others including myself. If a person has studied this book you can easily recognize somebody who is using this methodology. Although one of the best Fusion Guitarists in the world Allan Holdsworth sounds like he has studied Russells book in actuality he is self taught, but his biggest influence is John Coltrane so he is using the method but without actually studying it. Holdsworth is an amazing player I saw an interview with him and he said basically he just looks at the fret board and sees all the possibilities, this is a paraphrase, but he is truly an amazing player. [http://www.youtube.com/watch?v=Qxx9iAJdhco&feature=related](http://www.youtube.com/watch?v=Qxx9iAJdhco&feature=related) Yes that is Chad Wackerman on the drums who played with Zappa I have seen Vinnie Colaiuta play with him as well another Zappa alumnae. A little off topic but I think any investigation into music and how it might affect us is a good one. For me being that I have studied music theory and play multiple instruments and many styles and genres I fall out of the mainstream as far as what I can tolerate in speed and pitch or dissonance the more complex it is the more I like it generally, but I also like all kinds of music from Megadeath to Nirvana to John Coltrane to Duke Ellington to Thelonius Monk---etc it is all artistic expression and is all valid. Sorry for the one paragraph but I have the flash blocked so I think this keeps it all bundled together.

---

### Post by Fufkin on 2009-11-02
Thank you!

I have literally been searching and requesting exactly this since I started using linux 4 years ago.  I google "linux pacemaker equivalent" every few months hoping and praying, and today it paid off!

If it works then I would love to donate some cash to help development - I'm afraid that's the only kind of support I can offer.

I'm eager to try it out, but I've gotta be honest all this compiling stuff looks pretty intimidating.  I'll see how far I get.

---

### Post by allquixotic on 2009-11-02
Fufkin,

Don't worry -- what I'm going to do is build a .deb package that you can install for the version of Ubuntu you're using.

Please state the version of Ubuntu you use and the architecture (32-bit or 64-bit).

Please keep in mind that, if things go well, this plugin will be shipped by default in a future version of Ubuntu. The manual compiling step is a temporary thing while I try to get this integrated upstream.

Until then I will provide a hand-rolled .deb that's convenient for you to install.

Best,

Sean

---

### Post by Fufkin on 2009-11-02
> **allquixotic said:**
> Fufkin,

Don't worry -- what I'm going to do is build a .deb package that you can install for the version of Ubuntu you're using.

Please state the version of Ubuntu you use and the architecture (32-bit or 64-bit).

Please keep in mind that, if things go well, this plugin will be shipped by default in a future version of Ubuntu. The manual compiling step is a temporary thing while I try to get this integrated upstream.

Until then I will provide a hand-rolled .deb that's convenient for you to install.

Best,

Sean

Thanks man, that's great!  I've got to admit I gave up on the manual compiling.

I am using Ubuntu 9.10 32bit.

---

### Post by mike.thorton on 2009-11-03
I don't understand wilee-nilee's replys at all, but... I'm really interested to the plugin. I need it to practice playing the guitar.

I'm not familiar with the compiling and programming though.

I've already managed to do:
```
git clone git://tiyukquellmalz.org/rbpitch
```

but I'm not able to do anything else. See the output of next command:
```
sudo bash local-install
make: *** No rule to make target `clean'.  Stop.
```

Would be nice to give us step by step instructions. Linux for human beings ;)

Thanks very much! Good job. Looking forward to test it.

P.S. If you want, you are free to set up your own PPA on launchpad...then it's just a short step to 1) distribute it to people via adding PPA, 2) ask ubuntu maintainers to include the plugin by default. I would like to see it by default in 10.04.

---

### Post by allquixotic on 2009-11-05
Right now I really don't want to deal with getting this plugin in default Ubuntu unless the Rhythmbox developers first integrate it upstream into their own source tree. Otherwise I would have to effectively patch the rhythmbox package in Ubuntu, which is a lot more work. A PPA should be easier, and providing end-user instructions is yet easier for me :)

If I ever get this upstream to the Rhythmbox maintainers, all of this distribution headache will disappear automatically. **If you want to help get rbpitch into upstream Rhythmbox, you can help!** Contact Jonathan Matthew, current maintainer of Rhythmbox, and ask him to work with the author of rbpitch (he'll know who that is, me) to get it into upstream Rhythmbox. His contact info is at [http://live.gnome.org/JonathanMatthew](http://live.gnome.org/JonathanMatthew)

I may soon put this up on a PPA, but I've never done it before, so it will likely take me a lot of time and lost hair. Just reading the packaging guide is making my head spin, and I've used Linux (with heavy CLI usage) for 9 years.

For the more adventurous type, I'll post a concise guide of the build steps, but I can't give click-by-click / keystroke-by-keystroke instructions. This guide assumes familiarity with compiling software from source using the CLI.

You can either do all of the following using a root shell (e.g. **sudo bash**), or add **sudo** to each of the commands that require root privileges (apt*, make install, etc.)

```

apt-get build-dep rhythmbox
aptitude install build-essential valac libvala-dev vala-utils gstreamer0.10-plugins-bad git-core autoconf automake
apt-get source rhythmbox
cd rhythmbox-*
git clone git://tiyukquellmalz.org/rbpitch.git plugins/rbpitch
cd plugins
patch -p0 < rbpitch/patches/ubuntu/9.10/Makefile.am.patch
cd ..
patch -p0 < plugins/rbpitch/patches/ubuntu/9.10/configure.ac.patch
./autogen.sh
./configure --prefix=/usr --enable-vala
make -j2
make install

```

You can be reasonably certain that the install succeeded if the contents of the /usr/lib/rhythmbox/plugins/rbpitch/ directory are as follows:
```
librbpitch.a  librbpitch.la  librbpitch.so  rbpitch.rb-plugin rbpitch-layout.xml
```

If you have problems once those files exist, it's probably a coding error on my part.

I have yet to document how to use the GUI, but very briefly, you will see "Pitch and Tempo Shifting" in Edit -> Plugins. Make sure it's checked. Then another button will appear next to the shell player (play/pause/next/prev buttons). Click that and the main window appears. You can either close the rbpitch window or toggle the button to make the rbpitch UI go away, but its changes will remain in effect.

P.S. -- If you have a pre-existing rbpitch source tree that you want to reuse, make sure to run `git pull' -- I have made several updates and fixes very recently.

Let me know if you have any further problems with the instructions I posted here. If you check the README.txt in the distribution, I also posted instructions for doing this with vanilla Rhythmbox -- but Ubuntu ships some patches to Rhythmbox, so I thought it was worthwhile to use the Ubuntu sources.

Finally, I will only support rbpitch on Ubuntu 9.10 or later. I'll happily also support it on prereleases of 10.04, but don't ask me about 9.04 or earlier please.

---

### Post by wilee-nilee on 2009-11-09
> **mike.thorton said:**
> I don't understand wilee-nilee's replys at all, 

I had the wrong set up on the forums so I was unable to make correct paragraphs.

If there was something in there that you didn't understand but want to feel free to post again or PM me. I have studied music for years and advanced music theory so some of the things I mentioned although are very basic music theory they are things everybody should know like relative minor.

I wont deny it could of been gibberish on my part I haven't looked through my posts at this time.

Good job to the OP in getting a usable program many can use pushed forward.

---

### Post by allquixotic on 2009-11-09
Can anyone test this and let me know if it works? Over here, on a **clean** 64-bit Ubuntu 9.10 Final system (before applying updates or anything), I was able to get this working by following these "Steps For Dummies":

1. Applications -> Accessories -> Terminal
2. Type **sudo bash**. When prompted to enter your password, do so and press **Enter**.
3. Copy and paste or type in each of these lines exactly in the Terminal:
```
apt-get build-dep rhythmbox
aptitude install build-essential valac libvala-dev vala-utils gstreamer0.10-plugins-bad git-core autoconf automake
apt-get source rhythmbox
cd rhythmbox-*
git clone git://tiyukquellmalz.org/rbpitch.git plugins/rbpitch
cd plugins
patch -p0 < rbpitch/patches/ubuntu/9.10/Makefile.am.patch
cd ..
patch -p0 < plugins/rbpitch/patches/ubuntu/9.10/configure.ac.patch
./autogen.sh
./configure --prefix=/usr --enable-vala
make -j2
make install
```
4. Applications -> Sound & Video -> Rhythmbox Music Player
5. In Rhythmbox, go to Edit -> Plugins and check the box in the **Enabled** column next to the "Pitch and Tempo Shifting" entry.
6. Click the Close button in the popup window.
7. Click the "Pitch and Tempo Control" button next to the "Start or stop visualization" button. The default icon for my button is a stock GTK icon, which is a blue *i* on Ubuntu 9.10.
8. The "Rhythmbox Pitch Control" window should pop up.
9. Drag the sliders, click the SpinButton arrows, or type in the SpinButton. Note that if you type in the SpinButton, your changes will not take effect until you focus on some other component, which means you need to close out the window, press TAB, or click somewhere else in the window. I am working on smoothing this out.
10. You should now hear music at a different pitch or tempo than normal.

That's about as user friendly as I can make it for now. Let me know if you run into any more problems.

By the way, I am aware of a bug with the way the playback progress bar displays the time elapsed. You might also get unexpected effects if you try to seek when the pitch or speed is/are shifted. This is in the works now: [http://mail.gnome.org/archives/rhythmbox-devel/2009-November/msg00033.html](http://mail.gnome.org/archives/rhythmbox-devel/2009-November/msg00033.html)

---

### Post by Fufkin on 2009-11-13
Hi allquixotic,

I am still very keen to get this working, and your step-by-step instructions look achievable even for me.

Unfortunately I'm away from my ubuntu laptop for another week or so, but I'll try it asap.

Just wanted to assure you that there is still interest ;)

---

### Post by Fufkin on 2009-11-18
It works!

Followed your guide above and every step went fine.

It works really well - with pacemaker the sound used to get really distorted when the pitch or speed changed too much, but this is really clear.  Also the changes are instant and work during playback - I had no trouble with skipping through songs.

A couple of things that I'm sure you are already thinking of:
* a "remember settings for this song" would be great
* The sliders could be a little easier to understand - like if it went up in semi-tones.

But I am really happy - you have solved a problem that has been bugging me for years :D

---

### Post by allquixotic on 2009-11-18
I am glad this worked for you. Some comments on your feature requests:

> * a "remember settings for this song" would be great

This would be pretty difficult to implement, relatively speaking. I can see how it would be done, but it may add dependencies (some RDBMS like sqlite for keeping track of (song,settings) pairs) and there are some unresolved issues. I would need to link against RhythmDB (which would involve creating new Vala bindings for RhythmDB) to uniquely identify playing tracks so I know how to store this info. Or I could directly modify the existing RhythmDB code, but that would eliminate the "plugin" idea of rbpitch. Much to think about here.

> * The sliders could be a little easier to understand - like if it went up in semi-tones.

I got formulas for percentage to semitones conversion for the pitch slider from Olli Parviainen, author of Pacemaker. Now I just need to set up those formulae in the code and this will be done. I expect this little enhancement to hit git master some time in November 09, so within the next week or two.

Along with that, I'm thinking of reducing the slider range from 10% to 900% (which is the full range of the underlying library) to 10% to 400% instead. Or maybe 200% (i.e. double speed). What do you think of this? Do you have any use for settings above 200%? Should I leave the whole entire range in?

The complaint from the Rhythmbox developers was that, the larger I make the range, the less granularity the slider has. For a small range, it's very natural to drag the slider and see a noticeable but small change in the value. For huge ranges mapped onto small sliders, you don't get the control you want. Now given, that's what the text field (SpinButton) is for, when you want an exact value; but the sliders should nevertheless be somewhat useful.

So we'll have to reach a compromise between slider width -- too wide and netbooks won't be able to use it -- and slider range -- too large and granularity is too large to give any sort of meaningful control; too small and people won't be able to select values they actually want.

I could also enable horizontal resizing and start with a sane (but conservative) default width. Then people can just drag the UI wider on large screens so they can get some excellent granularity on the sliders.

---

### Post by Fufkin on 2009-11-19
> **allquixotic said:**
> 
What do you think of this? Do you have any use for settings above 200%? Should I leave the whole entire range in?


I use it for guitar playing, and I can't imagine a time when I would need anything beyond 50% to 150% (for both tempo and pitch).  But of course it's better to have too much range than not enough!

---

### Post by mirak63 on 2010-01-04
```
aking all in sample-vala
make[3]: Entering directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins/sample-vala'
make[3]: Leaving directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins/sample-vala'
Making all in rbpitch
make[3]: Entering directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins/rbpitch'
make[3]: *** No rule to make target `rbpitch-layout.xml', needed by `all-am'.  Stop.
make[3]: *** Waiting for unfinished jobs....
make[3]: Leaving directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins/rbpitch'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5'
make: *** [all] Error 2

```

I have this error

I am trying to make a ubuntu package

however it works when I do a make like you describe

---

### Post by Paul41 on 2010-01-19
I installed according to the above instructions on 64 bit and it is working well. My vote for the sliders would be to go 10% to 200% to make them more useful (at least for me they would be).

I am using this guitar also and it would be nice if there was a way to loop certain parts of a song but I don't know if that would be possible.

---

### Post by allquixotic on 2010-01-20
> **mirak63 said:**
> ```
aking all in sample-vala
make[3]: Entering directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins/sample-vala'
make[3]: Leaving directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins/sample-vala'
Making all in rbpitch
make[3]: Entering directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins/rbpitch'
make[3]: *** No rule to make target `rbpitch-layout.xml', needed by `all-am'.  Stop.
make[3]: *** Waiting for unfinished jobs....
make[3]: Leaving directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins/rbpitch'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/karim/Dev/plugrmbox/rhythmbox-0.12.5'
make: *** [all] Error 2

```

I have this error

I am trying to make a ubuntu package

however it works when I do a make like you describe

Looks like you ran `make clean' -- oops. That was an error on my part. Fixed in git. See [http://tiyukquellmalz.org/cgit/rbpitch/commit/?id=626ef94895000fde7c9076c3b9ce05b67c1d6e8f](http://tiyukquellmalz.org/cgit/rbpitch/commit/?id=626ef94895000fde7c9076c3b9ce05b67c1d6e8f)

---

### Post by allquixotic on 2010-02-02
Just a quick update for anyone who tries to compile this fresh against the current git master:

I have migrated away from maintaining just rbpitch, and a set of version-specific patches against common stable releases. The new organization of my git repository is that I completely clone the rhythmbox master branch from git://git.gnome.org/rhythmbox . That way, when I am finished making changes, all I have to do is request that a Rhythmbox maintainer "pull" my Git tree and perform merges, which will send my plugin to upstream.

The new build process (should work on a clean Ubuntu 9.10+ installation):

```
sudo apt-get build-dep rhythmbox
sudo aptitude install valac libvala-dev vala-utils gstreamer0.10-plugins-bad git-core build-essential
sudo aptitude hold rhythmbox
git clone git://tiyukquellmalz.org/git/rbpitch-old
cd rbpitch
./autogen.sh
./configure --prefix=/usr --enable-vala && make -j2 && sudo make install

```


Tested against Ubuntu 9.10.

If the build is broken, let me know and I will try to fix it and/or merge fixes from master. I merge from master occasionally anyway so my tree doesn't fall too far out of sync.

**EDIT:** These instructions are now obsolete, especially if you are running Lucid. These instructions might work on Ubuntu 9.10 or earlier, but if you're using Lucid, see page 5 for the updated instructions. Sorry for the confusion!

---

### Post by allquixotic on 2010-02-10
Just thought I'd provide a quick update to anyone using rbpitch: I have released version 0.2. This is a feature release, which adds the things detailed [here](http://tiyukquellmalz.org/cgit/rbpitch/commit/?id=e181d35b2086720493aa504e6e5dfadda97e84f9).

The new features need testing, and feedback. The main thing I added is the ability to change the ranges on the sliders by manipulating -- you guessed it -- more sliders! I've introduced a "Configure..." dialog box that is accessible from Rhythmbox's Edit -> Plugins menu item.

To compile rbpitch v0.2, please refer to my previous post in this thread.

---

### Post by EzlyConfuzed on 2010-02-10
Where do I download this?  I went to that website, and there's just a buncha computer mumbo jumbo I can't understand.  I got 8.10 if that matters.

---

### Post by allquixotic on 2010-02-10
> **EzlyConfuzed said:**
> Where do I download this?  I went to that website, and there's just a buncha computer mumbo jumbo I can't understand.  I got 8.10 if that matters.

I'm afraid that this software won't run on Ubuntu 8.10. It uses features of the operating system that were only available with Ubuntu 9.10. It is possible, in theory, to run it on Ubuntu 8.10, but you would need to compile several packages from source -- that's a pretty daunting task.

If you had Ubuntu 9.10, you could download and install this software by running the short script I posted in a message earlier in this thread: [see here](http://ubuntuforums.org/showpost.php?p=8766204&postcount=21). All you have to do is open up a Terminal window and paste in those commands.

But again, if you execute those commands on Ubuntu 8.10, I am fairly certain that it will not work.

---

### Post by EzlyConfuzed on 2010-02-11
Is there any other music players on linux that can do this?  If not, it's cool, I can still always pitch down music on a record palyer atleast.

---

### Post by allquixotic on 2010-02-11
No, I'm afraid not. I have searched exhaustively for a FOSS music player that has pitch/tempo shifting, and none exist.

The only application I know of that does pitch/tempo shifting is Audacity, but that's an audio editor, not a music player. Each time you want to change the pitch/tempo, you have to go through a dialog and wait for it to apply the change to the entire song, which takes a few seconds. In other words, it does not change the pitch/tempo in real time.

Your only direct alternative for real-time tempo/pitch is rbpitch, but to do that you need Ubuntu 9.10 or later.

---

### Post by swalter on 2010-03-07
Hi, for practising dance I am very interested in changing the tempo of music playing in Rhythmbox. So far I've been using the "scaletempo" plugin by Willem van Engen:

[http://willem.engen.nl/projects/musictools/](http://willem.engen.nl/projects/musictools/)

This is quite basic but works well. Is it worth switching to rbpitch? Anyway I thought I'd mention this alternative.

---

### Post by allquixotic on 2010-03-07
> **swalter said:**
> Hi, for practising dance I am very interested in changing the tempo of music playing in Rhythmbox. So far I've been using the "scaletempo" plugin by Willem van Engen:

[http://willem.engen.nl/projects/musictools/](http://willem.engen.nl/projects/musictools/)

This is quite basic but works well. Is it worth switching to rbpitch? Anyway I thought I'd mention this alternative.

I wasn't aware of the existence of scaletempo until today. Here are a few comparisons after a cursory look at it:

**Similarities:**
[list]
[*]They both use the pitch plugin (libgstsoundtouch).
[*]They both use GtkBuilder to construct the UI.
[*]They both update the pitch and tempo in near real time (the delay is a few seconds because of pulseaudio latency).
[/list]

**Differences:**
[list]
[*]scaletempo is written in Python; rbpitch is written in Vala.
[*]scaletempo only scales tempo and pitch separately. rbpitch also scales speed, which is a way of scaling tempo and pitch in the exact same ratio so there is no aliasing (artifacts).
[*]I couldn't find a license for scaletempo; rbpitch is licensed under GPLv2+ with the Rhythmbox exception (the same license as Rhythmbox itself).
[*]I couldn't find any source code control repository for scaletempo, but it appears to be maintained in cvs because it ships a .cvsignore file. rbpitch is maintained in a publicly available git repository.
[*]scaletempo does not implement variable range sliders, a feature of rbpitch which allows you to change how big the range of the sliders should be. This gives you fine grained control if you set the sliders to be in a small range, and gives you broader control if you set the sliders to cover a large range.
[*]scaletempo does not implement remembering your slider settings between launches of Rhythmbox.
[*]It has been 10 months and 3 weeks since the scaletempo website was updated (presumably to upload the release tarball); it has been 26 days since the last commit to rbpitch (and more is on the way when I have time).
[*]I am not aware of whether scaletempo is developed with the input of the Rhythmbox maintainers to get it included as a default plugin; rbpitch is slated to get integrated into Rhythmbox after a few issues raised by the maintainers are addressed.
[*]There are only minimal comments in the scaletempo code; the rbpitch code is carefully documented.
[/list]

So which one is better? You be the judge. I'd suggest that you ignore my rambling and just install both plugins, and try them one at a time. Make sure to disable one and enable the other, though -- I imagine having two pitch plugins might result in a conflict in the gstreamer pipeline.

---

### Post by burned_ on 2010-04-04
Thank you for this plugin ):P I was searching for something like this (a program or plugin for tempo shifting) for such a  long time, but I didn't found anything which was really suitable for my requirements.
I can confirm that this:
```
sudo apt-get build-dep rhythmbox
sudo aptitude install valac libvala-dev vala-utils gstreamer0.10-plugins-bad git-core build-essential
sudo aptitude hold rhythmbox
git clone git://tiyukquellmalz.org/rbpitch
cd rbpitch
./autogen.sh
./configure --prefix=/usr --enable-vala && make -j2 && sudo make install
```works on 9.10 and on 10.04 :)

PS: sry for my english, I'm german :)

---

### Post by airplus on 2010-04-09
> **allquixotic said:**
> Hello,

rbpitch is a plugin for Rhythmbox that lets you change the pitch, tempo, and speed in real-time while playing a song. Based on my own subjective evaluation of the state of the code, I deem it early beta quality. It is feature complete, as far as I am concerned, but it needs much testing and use.

Why am I making this thread? Well, for several reasons:

[LIST]
[*]To see what kind of user demand exists for these features.
[*]To see if users' expectations match the delivered functionality.
[*]To solicit comments and suggestions for the program, from developers and users.
[*]To request help from translators internationalizing the end-user interface.
[*]To request help from developers to fix bugs, critique or improve the code, or add features.
[*]To request help from distribution packagers to get rbpitch included in Ubuntu at some point (possibly 10.04).
[*]To request help from **anyone with clout in the GNOME organization** to get the attention / help of Rhythmbox maintainers. This will help me open a dialogue and attempt to convince them to include this plugin by default in the Rhythmbox source distribution. By getting this plugin upstreamed with Rhythmbox, the user base is greatly expanded, and the chance that distributions will pick it up is increased. This is also useful from a technical standpoint, because there is no out-of-tree plugin SDK for Rhythmbox -- so including it as part of the Rhythmbox source tree eliminates the need for such an SDK.
[/LIST]
Thanks,

Sean


Great!!! Finally I found it! I have been searching the Internet for hours for this.

Thanks to the developer! Now, lets get installing :)

---

### Post by allquixotic on 2010-04-09
I am glad that everyone finds this to their liking.

Please provide feedback and suggestions when you use this software. If your experience is less than ideal, tell me what needs to be improved. As you can see from the history of this thread, user feedback has been a major catalyst for actual improvements in the software.

Right now I am pretty busy with other stuff, but any requests that are both reasonable and sound might get implemented somewhere around May.

And if you know Vala/Gstreamer and want to provide patches for anything -- cleanups, bugfixes, features -- I would be more than happy to review and integrate them.

---

### Post by Paul41 on 2010-04-09
I like the slider changes you made to the last version (being able to adjust range) but one thing that went away with that was the ability to type in a specific number. I use to be able to reduce the tempo for example to 50% by typing it in the box, now the only way to change is with the slider.

---

### Post by long2dance on 2010-05-06
Hi guys,

I am  a Linux newbie but have been looking for alternative to windoze for ages.  I need ability to slow or speed music (dance professional)

rbpitch seems to offer what I need so I followed instructions as posted and all went well until line 

patch -p0 < rbpitch/patches/ubuntu/9.10/Makefile.am.patch

Error - No such file or directory.  

I am using Ubuntu 10.04 and notice reference to 9.10 in line but I 
cannot find equivalent directory in 10.04

Any assist with easy instructs would be much appreciated

---

### Post by allquixotic on 2010-05-06
> **long2dance said:**
> Hi guys,

I am  a Linux newbie but have been looking for alternative to windoze for ages.  I need ability to slow or speed music (dance professional)

rbpitch seems to offer what I need so I followed instructions as posted and all went well until line 

patch -p0 < rbpitch/patches/ubuntu/9.10/Makefile.am.patch

Error - No such file or directory.  

I am using Ubuntu 10.04 and notice reference to 9.10 in line but I 
cannot find equivalent directory in 10.04

Any assist with easy instructs would be much appreciated

I'm afraid you are following outdated instructions. On page 3 of the thread, I posted the updated instructions: [click here](http://ubuntuforums.org/showpost.php?p=8766204&postcount=21) to see them.

Please let me know if this doesn't fix your problem.

Thanks,

Sean

---

### Post by long2dance on 2010-05-06
Great, install worked perfectly.

On using rbpitch I have set 'slider bounds to +10/-15% and + - 6 st but the sliders do not seem to change.  Have I missed something?

Also in future release is it possible to have display reflect slider adjustment values in real time?

Otherwise it appears to be exactly what I have been looking for - at last it is maybe goodbye windoze for most of me needs - hooray.:cool:

---

### Post by allquixotic on 2010-05-06
> **long2dance said:**
> Great, install worked perfectly.

On using rbpitch I have set 'slider bounds to +10/-15% and + - 6 st but the sliders do not seem to change.  Have I missed something?

Also in future release is it possible to have display reflect slider adjustment values in real time?

Otherwise it appears to be exactly what I have been looking for - at last it is maybe goodbye windoze for most of me needs - hooray.:cool:

Sounds like I have some bugs to fix, but I'm glad it does most of what you want. I will try to reproduce the two issues you raised, and if I can isolate the problem, I will fix it.

Subscribe to this thread via email. I will reply again when I've made some enhancements. I expect I'll have some time to work on this in May, but I can't say when exactly.

Thanks,

Sean

---

### Post by rdingram on 2010-05-11
Thank you for your work on this project.

After following the installation instructions on 10.04 when I start Rhythmbox I receive multiple pop-ups informing me that Rhythmbox was unable to load any of the plugins, including the rbpitch plugin. Any ideas why this would happen?

Thanks for any help.

-- EDIT --

Well I feel like an idiot. I had downloaded and compiled in a subdirectory of ~/.gnome2/plugins and left all of the files there. When rhythmbox was loading it was trying to open all of the plugins in the compile subdirectories. After I moved that folder out of the plugins folder everything is working.

On a side note, all tempo shifting software I have used in Linux produces very "choppy" playback. Is this normal? I know that the few that I have used in OSX are not as noticeably choppy. Thanks for any advice!

---

### Post by allquixotic on 2010-05-23
> **rdingram said:**
> Thank you for your work on this project.

After following the installation instructions on 10.04 when I start Rhythmbox I receive multiple pop-ups informing me that Rhythmbox was unable to load any of the plugins, including the rbpitch plugin. Any ideas why this would happen?


I was getting this on my local box for 10.04 as well; I merged rhythmbox master into the rbpitch git repository and it now seems to work. Much like rbpitch itself, the rhythmbox master is experimental, so don't be surprised if there are regressions.

As a side note, it is highly recommended to run **sudo aptitude hold rhythmbox** to prevent further upgrades to Rhythmbox after compiling rbpitch. Otherwise, if you install updates without scrutinizing the list, you will possibly install an Ubuntu rhythmbox update that is incompatible with my build.

> **rdingram said:**
> 
Thanks for any help.

-- EDIT --

Well I feel like an idiot. I had downloaded and compiled in a subdirectory of ~/.gnome2/plugins and left all of the files there. When rhythmbox was loading it was trying to open all of the plugins in the compile subdirectories. After I moved that folder out of the plugins folder everything is working.

Ouch. Glad you figured it out.

> **rdingram said:**
> 
On a side note, all tempo shifting software I have used in Linux produces very "choppy" playback. Is this normal? I know that the few that I have used in OSX are not as noticeably choppy. Thanks for any advice!

I'm not sure what you mean by choppy. I do occasionally notice some artifacts for a few frames when I change the pitch or tempo, but while the music is playing (without changing the pitch/tempo/speed) I don't get choppiness at all.

Please confirm that you get choppiness when rbpitch is enabled, and *not* when rbpitch is disabled? Is that the case? If so, please also post your system specs (CPU, RAM, sound card).

You can further debug the rbpitch pipeline on the CLI:

**gst-launch-0.10 -v filesrc location=/path/to/any/audio/file.mp3 ! decodebin2 ! audioconvert ! pitch tempo=1.10 ! audioconvert ! autoaudiosink**

In the above, replace "/path/to/any/audio/file.mp3" with a real filesystem path (absolute or relative) that points to an audio file that your gstreamer has a codec for. Some stock sounds are in /usr/share/sounds usually.

The output may record anomalies (such as overruns / underruns) and also the clock sync calculations done when the tempo is not 1.

---

### Post by allquixotic on 2010-05-27
Hi folks,

I just made a new commit to the rbpitch git repo. The following changes have been applied:

[list]
[*]The slider updates the spin buttons immediately when dragged, so you can see how the sliding affects the value in the spin button. However, there is a delay of 1 second (on top of PulseAudio's default buffer size of 2 seconds) between commits of the slider value to GConf and GStreamer. The reason for this delay is two-fold: One, I have actually managed to crash the program (somewhere within GStreamer) by setting the pitch/tempo/speed values many times per second. Dragging the slider, if I didn't control it, would have the effect of setting the value many times per second. Two: there's likely to be an extreme performance hit / thrashing with that kind of rapid commit logic. It is much easier on the system to only commit to GConf and GStreamer once per second. I am now investigating clever ways to get Rhythmbox to optionally request lower latency from Pulseaudio, to cut down on the delay when it does update. This feature was requested by long2dance in [this](http://ubuntuforums.org/showpost.php?p=9251472&postcount=35) post; you're welcome. :)
[*]It is possible to edit the values in the spinbutton if they are formatted with "st" or "%" at the end. Previously, you had to delete the "st" and/or "%" to get the value to take effect. Now you can just single left-click inside the numeric value, type the value you want, and hit Tab or click on another field, to have it take effect. Under the hood, I basically tied into the GtkSpinButton input signal handler to parse the string value and see if it matches a regular expression that is aware of the "st" / "%" semantics, and extracts the numeric value out of it. This feature was requested by Paul41 in [this](http://ubuntuforums.org/showpost.php?p=9099196&postcount=32) post; you're welcome. :)
[*]More comments added to tangly code sections.
[*]Change uses of `weak' to `unowned' in Vala (syntactical change)
[/list]

If you already installed a previous version of rbpitch, change directory to the place where you originally checked out rbpitch, then run from a terminal:

```

make clean
git pull
./autogen.sh
./configure --prefix=/usr --enable-vala --sysconfdir=/etc --localstatedir=/var && make && sudo make install

```

**The above steps are upgrade instructions for people who have installed rbpitch before. For a clean install, keep reading.** If the upgrade fails for some reason, you can always follow my [original instructions](http://ubuntuforums.org/showpost.php?p=8766204&postcount=21). This will take up more bandwidth and time, but otherwise is the same. I don't mind the extra bandwidth usage; feel free to do it that way if you like. :)

The rbpitch UI is pretty great now, wouldn't you say? There are a few more things to polish (there always are...) but I think this is progress. It's nice to satisfy user requests, too. :)

Finally, this was tested on Ubuntu 10.04 64-bit. Since I am the sort of guy to prefer newer software and shun older software, I hereby withdraw my willingness to support rbpitch on Ubuntu 9.10 and earlier as of today. You are free to try rbpitch on Ubuntu 9.10, and it may in fact work -- but if it doesn't, I will not go out of my way to backport it. Either way, let me know your results if you try it. I would be interested to know whether or not it works on 9.10.

If, on the other hand, you have any problems with rbpitch on Ubuntu 10.04, that would be something I'd like to know right away, and I will work with you to make it right.

Thanks,

Sean

---

### Post by Deadite81 on 2010-05-30
Cool plugin, thanks.

Seems to work as advertised, although I've tested it for only a short time.  Once I set the speed to around +300% Rhythmbox crashes.  I can only assume that my PC can't keep up with that!  I have an older AMD X2 @2.5 GHz and onboard nvidia sound card.  I have no reason to need the music that fast anyway :)  Just thought I'd mention it if no one else has already.  Thanks!

---

### Post by allquixotic on 2010-05-30
> **Deadite81 said:**
> Once I set the speed to around +300% Rhythmbox crashes.

I will try to reproduce the crash on my system.

Please note that the only part of rbpitch's functionality that I developed is the user interface. The heavy lifting is done by Rhythmbox, which passes the work down further to GStreamer, the GNOME multimedia framework.

There is nothing I can think of in my software that would cause it to crash after setting the slider to a particular value, so I am almost certain -- without even reproducing the bug -- that the fault is somewhere in the bowels of GStreamer. This is fairly unfamiliar territory for me, because I am more a developer-user of GStreamer than a developer *of* GStreamer itself.

That said, I will try to understand this problem as well as I can, and either cook up a patch, or seek help from the GStreamer developers.

I can't provide an ETA on a fix, unfortunately.

Hope you enjoy the plugin otherwise!

-Sean

---

### Post by Paul41 on 2010-06-14
> **allquixotic said:**
> Hi folks,

I just made a new commit to the rbpitch git repo. The following changes have been applied:

[list]
[*]The slider updates the spin buttons immediately when dragged, so you can see how the sliding affects the value in the spin button. However, there is a delay of 1 second (on top of PulseAudio's default buffer size of 2 seconds) between commits of the slider value to GConf and GStreamer. The reason for this delay is two-fold: One, I have actually managed to crash the program (somewhere within GStreamer) by setting the pitch/tempo/speed values many times per second. Dragging the slider, if I didn't control it, would have the effect of setting the value many times per second. Two: there's likely to be an extreme performance hit / thrashing with that kind of rapid commit logic. It is much easier on the system to only commit to GConf and GStreamer once per second. I am now investigating clever ways to get Rhythmbox to optionally request lower latency from Pulseaudio, to cut down on the delay when it does update. This feature was requested by long2dance in [this](http://ubuntuforums.org/showpost.php?p=9251472&postcount=35) post; you're welcome. :)
[*]It is possible to edit the values in the spinbutton if they are formatted with "st" or "%" at the end. Previously, you had to delete the "st" and/or "%" to get the value to take effect. Now you can just single left-click inside the numeric value, type the value you want, and hit Tab or click on another field, to have it take effect. Under the hood, I basically tied into the GtkSpinButton input signal handler to parse the string value and see if it matches a regular expression that is aware of the "st" / "%" semantics, and extracts the numeric value out of it. This feature was requested by Paul41 in [this](http://ubuntuforums.org/showpost.php?p=9099196&postcount=32) post; you're welcome. :)
[*]More comments added to tangly code sections.
[*]Change uses of `weak' to `unowned' in Vala (syntactical change)
[/list]

If you already installed a previous version of rbpitch, change directory to the place where you originally checked out rbpitch, then run from a terminal:

```

make clean
git pull
./autogen.sh
./configure --prefix=/usr --enable-vala --sysconfdir=/etc --localstatedir=/var && make && sudo make install

```

**The above steps are upgrade instructions for people who have installed rbpitch before. For a clean install, keep reading.** If the upgrade fails for some reason, you can always follow my [original instructions](http://ubuntuforums.org/showpost.php?p=8766204&postcount=21). This will take up more bandwidth and time, but otherwise is the same. I don't mind the extra bandwidth usage; feel free to do it that way if you like. :)

The rbpitch UI is pretty great now, wouldn't you say? There are a few more things to polish (there always are...) but I think this is progress. It's nice to satisfy user requests, too. :)

Finally, this was tested on Ubuntu 10.04 64-bit. Since I am the sort of guy to prefer newer software and shun older software, I hereby withdraw my willingness to support rbpitch on Ubuntu 9.10 and earlier as of today. You are free to try rbpitch on Ubuntu 9.10, and it may in fact work -- but if it doesn't, I will not go out of my way to backport it. Either way, let me know your results if you try it. I would be interested to know whether or not it works on 9.10.

If, on the other hand, you have any problems with rbpitch on Ubuntu 10.04, that would be something I'd like to know right away, and I will work with you to make it right.

Thanks,

Sean

Excellent!  Thank you :guitar:

---

### Post by allquixotic on 2010-07-05
[SIZE=4]These instructions are now **obsolete**. Please see the first post in the thread![/SIZE]

Hello rbpitch users,

The Rhythmbox maintainers have recently released version 0.13.0 of Rhythmbox, which brings many changes. A few of them are very significant to this project, so correspondingly I have made some significant changes to the way rbpitch works.

The major change in Rhythmbox 0.13.0 is that there is now support for **out-of-tree native plugins**. This is ultimately the best way to go, because you don't have to build all of Rhythmbox just to compile a plugin.

Unfortunately, support for out-of-tree Vala plugins was not completely implemented with 0.13.0. This work is currently in progress, as you can see [here](https://bugzilla.gnome.org/show_bug.cgi?id=621246).

Until Daniel Hams' patchset is integrated into a release of Rhythmbox, it will not be possible to build rbpitch out of tree without applying his patch to your Rhythmbox source code.

Since I figured some people will want to continue to use the old version of rbpitch, I have moved the old in-tree plugin (now unmaintained) to [http://tiyukquellmalz.org/cgit/rbpitch-old](http://tiyukquellmalz.org/cgit/rbpitch-old) . I have also updated the instructions for compiling on page 3 to use this repository.

If you want to run the new out-of-tree rbpitch against Rhythmbox 0.13.0, here is how you get the new version, patch it, then build the out-of-tree plugin against it:

```
sudo aptitude install build-essential git-core patch valac libvala-dev vala-utils wget tar bzip2 patch gstreamer0.10-plugins-bad
sudo apt-get build-dep rhythmbox
wget http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.13/rhythmbox-0.13.0.tar.bz2
tar xvjf rhythmbox-0.13.0.tar.bz2
cd rhythmbox-0.13.0
wget 'http://tiyukquellmalz.org/vala-hams-20100905.patch' -O vala-hams-v6.patch
git apply vala-hams-v6.patch
./autogen.sh
./configure --prefix=/usr --enable-vala --sysconfdir=/etc && make -j2 && sudo make install
cd ..
git clone git://tiyukquellmalz.org/git/rbpitch
cd rbpitch
make && sudo make install-root && make install-nonroot

```

These instructions should work on Ubuntu 9.10, 10.04, or 10.10. I have tested them on a clean 64-bit Ubuntu 10.04 virtual machine.

My expectation is that you will be able to omit rebuilding Rhythmbox at all when 10.10 goes final -- but that will depend on whether Daniel's patch gets merged to RB master in time for an RB release which would hopefully get picked up by Ubuntu.

---

**Regardless of whether or not you use the in-tree or out-of-tree plugin**, I have provided an update (in both repositories) that fixes a regular expression parsing issue. This should resolve any weirdness you might've experienced with typing values into the spin buttons.

I also extended the pitch spinbutton to cover two decimal places, to allow for more fine-tuning of instruments (to the hundredth of a semitone). The tempo and speed controls still have a resolution of 0.1%.

Since the Rhythmbox code rbpitch-old.git is significantly older than the 0.13.0 release, at this time I am strongly recommending that users upgrade to Rhythmbox 0.13.0 and rbpitch 0.13.0.

From now on, I will be keeping my major, minor and micro version numbers in sync with Rhythmbox's. If I have multiple releases for a single version of Rhythmbox, I will use the "nano" release number, like this: v0.13.0.1, 0.13.0.2, etc.

As always, if you have any questions, problems, or comments, please post back!

Thanks,

Sean

---

### Post by Deadite81 on 2010-07-12
This worked flawlessly for the upgraded Rhythmbox 0.13.

I'm sure I speak for everyone when I say thanks for keeping everything up to date and as non-confusing as possible!

---

### Post by distratios on 2010-07-26
Hi!

Following your instructions on Lucid I run into the following error, when trying to build rbpitch:

```
error: rhythmbox not found in specified Vala API directories or GObject-Introspection GIR directories.

```Rhythmbox 0.13 built and installed succesfully. Any ideas?

Thanks

Panos


update
source was not properly patched. git complained a missing .gitignore file. I wonder how the above instructions can work without getting source through git. However going this route resulted in exit 2 of make while trying to build the vala part.

---

### Post by allquixotic on 2010-07-27
> **distratios said:**
> Hi!

Following your instructions on Lucid I run into the following error, when trying to build rbpitch:

```
error: rhythmbox not found in specified Vala API directories or GObject-Introspection GIR directories.

```Rhythmbox 0.13 built and installed succesfully. Any ideas?

Thanks

Panos


update
source was not properly patched. git complained a missing .gitignore file. I wonder how the above instructions can work without getting source through git. However going this route resulted in exit 2 of make while trying to build the vala part.

Very sorry about this. I had modified the build instructions to pull Daniel's V8 patch from the bug, but it seems that the V8 patch does not apply against the Rhythmbox 0.13.0 release tarball -- nor does it apply against git master.

Obviously it's kind of weird depending on something that is still in the works, but for now, the static configuration of RB 0.13.0 + V6 of the patch should work. I just tested that.

I updated the build instructions accordingly.

Sean

P.S. -- The author of the patch is currently away, moving house. I will ping him when he gets back to see what went wrong, and hopefully have him roll another patch that will have the V8 enhancements plus whatever corrections are needed to get it working against current git master. This should hopefully get rbpitch ready to roll for when the next release of rhythmbox comes along.

---

### Post by distratios on 2010-07-27
As you said it's work in progress. We should be patient until rb 0.13 is more or less bugfree. BTW your updated instructions worked perfect for me. Thanks a lot!

This plugin is actually not for me but for my wife. She has a dance studio (ballet) and this plugin is extremely usefull for her dancing classes. Ballet studios are really good "customers" for your plugin.

Thanks again

Panos

---

### Post by allquixotic on 2010-07-28
> **distratios said:**
> As you said it's work in progress. We should be patient until rb 0.13 is more or less bugfree. BTW your updated instructions worked perfect for me. Thanks a lot!

This plugin is actually not for me but for my wife. She has a dance studio (ballet) and this plugin is extremely usefull for her dancing classes. Ballet studios are really good "customers" for your plugin.

Thanks again

Panos

Wow! That is really an inspiring and creative use of the software. Is this being actually used in your classes now?

I won't ask for too many details, but I do love to hear user reports of making interesting use of this plugin. Personally, I use it on any of my Linux installs as a way to make the music sound more interesting. I get tired of hearing the same music tracks, but since I can't legally purchase new music for less than a dollar per song (and I don't have unlimited dollars ;)) I need some way to mix up the music I already have. I could create techno remixes or something, but instead of spending all that effort, I just change the tempo/pitch depending on my mood. :)

Oh, and an update about getting this included in Ubuntu: although it's more or less a "no, we don't need yet another plugin" for getting it included upstream in Rhythmbox, there's still a strong possibility of including it in Ubuntu's repositories (maybe as an addition to the rhythmbox-plugins package). I think my first step is to create a source package for rbpitch, as well as a source package for the patched rhythmbox (to support Daniel Hams' not-yet-pulled Vala bindings patch).

Thanks,

Sean

---

### Post by distratios on 2010-07-29
Time shifting is standard in ballet classes. They use top-loader cd players with time shifting controls. Thanks to your plugin :-) my wife will replace her scratchy cd's with playlists on rhythmbox. She has a netbook connected to the sound system. With remuco and a spare mobile she also has a great remote control which rounds up the setup.

Thanks again

Panos

---

### Post by allquixotic on 2010-07-29
> **distratios said:**
> Time shifting is standard in ballet classes. They use top-loader cd players with time shifting controls. Thanks to your plugin :-) my wife will replace her scratchy cd's with playlists on rhythmbox. She has a netbook connected to the sound system. With remuco and a spare mobile she also has a great remote control which rounds up the setup.

Thanks again

Panos

Wonderful!

I don't have any infrared remote controls (or any remote controls at all, heh) to test remuco with, unfortunately. So I am not sure how well (or if) rbpitch will work with remuco.

That said, if you run into a specific case where you can suggest usability improvements for rbpitch -- such as tighter integration with remuco -- then please let me know. I will do what I can to make rbpitch work for you.

Thanks,

Sean

---

### Post by digbysellers on 2010-07-29
> **Fufkin said:**
> I use it for guitar playing, and I can't imagine a time when I would need anything beyond 50% to 150% (for both tempo and pitch).  But of course it's better to have too much range than not enough!
Me too. If I want to learn to cover a song that was recorded in a slightly different tuning it's much easier than tuning down or pulling out another guitar. I had to look around for an audio player that would do that. For everything else I typically use vlc. Perhaps there is a plugin for vlc I don't know about?

---

### Post by allquixotic on 2010-07-29
> **digbysellers said:**
> Me too. If I want to learn to cover a song that was recorded in a slightly different tuning it's much easier than tuning down or pulling out another guitar. I had to look around for an audio player that would do that. For everything else I typically use vlc. Perhaps there is a plugin for vlc I don't know about?

I actually looked around for a VLC plugin for quite a while before I decided to write rbpitch, so no, unless one has been written since November 2009, I'm fairly certain that VLC can not do pitch/tempo shifting. Or maybe it can, but you have to manually construct a pipeline to do it (VLC has a pipeline similar to gstreamer).

---

### Post by kailynleto on 2010-08-03
E: You must put some 'source' URIs in your sources.list

this is when I am simply at the second step...

Mint 9...help please

---

### Post by allquixotic on 2010-08-04
> **kailynleto said:**
> E: You must put some 'source' URIs in your sources.list

this is when I am simply at the second step...

Mint 9...help please

Well, I haven't used Mint for a long time, but here's a shot in the dark as to what you need to do:

Edit /etc/apt/sources.list as root. For every line that starts with **deb**, make sure there is also a line that starts with **deb-src**, but is exactly the same all the way across.

So if you had a line that said

deb [http://example.com/mint/](http://example.com/mint/) main

you also need a line that says

deb-src [http://example.com/mint/](http://example.com/mint/) main

Repeat this for every line starting with **deb**.

You'll need to use a text editor as root... my suggestion is to use **sudo nano /etc/apt/sources.list** to fire up the nano text editor. Let me know if you have trouble

---

### Post by kailynleto on 2010-08-06
That did work.  But do you have a gstreamer bypass by any chance?  It can't find my gstreamer libraries, and I haven't the slightest clue where they are.

I guess I should have started with Ubuntu since it is the one I've fooled around with practically forever (I still have the 6.06 I burned when I was still in high school LOL!!!)

Thanks for any help, especially as you are not really that well-versed in Mint.  I really appreciate it.  This whole speeding up songs bit is quite literally the only thing holding me back from deleting Windows...

---

### Post by allquixotic on 2010-08-07
> **kailynleto said:**
> That did work.  But do you have a gstreamer bypass by any chance?  It can't find my gstreamer libraries, and I haven't the slightest clue where they are.

I guess I should have started with Ubuntu since it is the one I've fooled around with practically forever (I still have the 6.06 I burned when I was still in high school LOL!!!)

Thanks for any help, especially as you are not really that well-versed in Mint.  I really appreciate it.  This whole speeding up songs bit is quite literally the only thing holding me back from deleting Windows...

Hi,

There is no Gstreamer bypass -- at least, not for Rhythmbox/rbpitch.

Rhythmbox itself depends on Gstreamer to do its audio I/O. Without Gstreamer, Rhythmbox cannot play any audio, and it probably will not even compile.

Aside from that, rbpitch also directly depends on Gstreamer. But I depend on a particular package from gstreamer, not just the base package.

In the gstreamer "bad" plugins package (called gstreamer0.10-plugins-bad on Ubuntu), there is supposed to be an element called **pitch**. This is the basis of rbpitch's functionality. This element is required to be present at runtime if you want pitch/tempo shifting.

So, my question now is: what **exact** error message are you getting, and at what stage? Please describe what *worked*, and what *didn't work*, so I have a better context to understand your problem.

Thanks,

Sean

---

### Post by mogdad on 2010-08-13
> **allquixotic said:**
> 

```
sudo aptitude install build-essential git-core patch valac libvala-dev vala-utils wget tar bzip2 patch gstreamer0.10-plugins-bad
sudo apt-get build-dep rhythmbox
wget http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.13/rhythmbox-0.13.0.tar.bz2
tar xvjf rhythmbox-0.13.0.tar.bz2
cd rhythmbox-0.13.0
wget http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241 -O vala-hams-v6.patch
git apply vala-hams-v6.patch
./autogen.sh
./configure --prefix=/usr --enable-vala --sysconfdir=/etc && make -j2 && sudo make install
cd ..
git clone git://tiyukquellmalz.org/rbpitch
cd rbpitch
make && sudo make install-root && make install-nonroot

```




I followed the very clear instructions in #9552328 (thanks) and the installation seemed to go ok. Rbox 0.13.0 works perfectly and files have appeared in the plugins directory:
  $ ls -al /usr/lib/rhythmbox/plugins/rbpitch/
  total 104
  drwxr-xr-x  2 root root  4096 2010-08-13 13:25 .
  drwxr-xr-x 30 root root  4096 2010-08-13 13:25 ..
  -rwxr-xr-x  1 root root 54281 2010-08-13 13:25 librbpitch.so
  -rw-r--r--  1 root root 35341 2010-08-13 13:25 rbpitch-layout.xml
  -rw-r--r--  1 root root   278 2010-08-13 13:25 rbpitch.rb-plugin

Unfortunately, when I go to the plugins dialogue in RB to turn it on I get the error box "Unable to activate plugin..."

If anyone has any ideas about how to make it work that would be great. Maybe the lesson is don't try to install anything on Friday 13th...

---

### Post by allquixotic on 2010-08-30
> **mogdad said:**
> I followed the very clear instructions in #9552328 (thanks) and the installation seemed to go ok. Rbox 0.13.0 works perfectly and files have appeared in the plugins directory:
  $ ls -al /usr/lib/rhythmbox/plugins/rbpitch/
  total 104
  drwxr-xr-x  2 root root  4096 2010-08-13 13:25 .
  drwxr-xr-x 30 root root  4096 2010-08-13 13:25 ..
  -rwxr-xr-x  1 root root 54281 2010-08-13 13:25 librbpitch.so
  -rw-r--r--  1 root root 35341 2010-08-13 13:25 rbpitch-layout.xml
  -rw-r--r--  1 root root   278 2010-08-13 13:25 rbpitch.rb-plugin

Unfortunately, when I go to the plugins dialogue in RB to turn it on I get the error box "Unable to activate plugin..."

If anyone has any ideas about how to make it work that would be great. Maybe the lesson is don't try to install anything on Friday 13th...

Hi mogdad,

I'm very sorry for taking two weeks to respond to you! I intended to respond hours after you posted this, but I got sidetracked.

Can you please verify that you have the gstreamer0.10-plugins-bad package installed? Not having it installed is the most likely source of the error you're experiencing.

Also, please post which distribution you are using, the release number (e.g. 10.04), and the architecture (e.g., 32-bit or 64-bit).

---

### Post by alfonzjanfrithz on 2010-09-04
git clone git://tiyukquellmalz.org/rbpitch-old

when i execute that command it said

Initialized empty Git repository in /home/alfonzjanfrithz/rhythmbox-0.12.8/rbpitch-old/.git/
tiyukquellmalz.org[0: 78.46.99.110]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)


what should i do.. thanks..

---

### Post by allquixotic on 2010-09-05
> **alfonzjanfrithz said:**
> git clone git://tiyukquellmalz.org/rbpitch-old

when i execute that command it said

Initialized empty Git repository in /home/alfonzjanfrithz/rhythmbox-0.12.8/rbpitch-old/.git/
tiyukquellmalz.org[0: 78.46.99.110]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)


what should i do.. thanks..

Hi,

I've been doing some maintenance on the server (actually, migrating to a new server). I've fixed the problem.

Why don't you try the instructions [here](http://ubuntuforums.org/showpost.php?p=9552328&postcount=43), which gives you a newer version of rhythmbox? The instructions on page 3 are old; I've updated the first post accordingly. Sorry for the confusion!

In any case, when you git clone from tiyukquellmalz.org, you'll need to append the path **/git** to the checkout URL. So instead of

git://tiyukquellmalz.org/rbpitch

it is now

git://tiyukquellmalz.org/git/rbpitch

Again, my apologies for the brokenness.

---

### Post by The_Eddster on 2010-09-05
I've tried following the instructions on page 5. I got to this bit: 

wget [http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241](http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241) -O vala-hams-v6.patch


And it comes up with this error:

--2010-09-05 13:21:17--  [http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241](http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241)
Resolving bugzilla-attachments.gnome.org... 209.132.180.171
Connecting to bugzilla-attachments.gnome.org|209.132.180.171|:80... failed: Connection refused.


How do I fix this problem? If it means anything, I tried to follow the instructions on page 3 first before I realised the ones on page 5 were the correct instructions for lucid.
Thanks in advance.

OS: Linux Mint 9 Isadora (based on Ubuntu 10.04 Lucid Lynx)

---

### Post by allquixotic on 2010-09-05
> **The_Eddster said:**
> I've tried following the instructions on page 5. I got to this bit: 

wget [http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241](http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241) -O vala-hams-v6.patch


And it comes up with this error:

--2010-09-05 13:21:17--  [http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241](http://bugzilla-attachments.gnome.org/attachment.cgi?id=165241)
Resolving bugzilla-attachments.gnome.org... 209.132.180.171
Connecting to bugzilla-attachments.gnome.org|209.132.180.171|:80... failed: Connection refused.


How do I fix this problem? If it means anything, I tried to follow the instructions on page 3 first before I realised the ones on page 5 were the correct instructions for lucid.
Thanks in advance.

OS: Linux Mint 9 Isadora (based on Ubuntu 10.04 Lucid Lynx)

Hi,

GNOME Bugzilla is currently down. This is completely out of my control, as I do not run the Gnome servers (far from it!) Since this patch was hosted on GNOME Bugzilla, you can't get at it while the bugzilla is down.

You're in luck, though! I have a copy of the patch here, and I've uploaded it to my server:

[http://tiyukquellmalz.org/vala-hams-20100905.patch](http://tiyukquellmalz.org/vala-hams-20100905.patch)

I'll update the instructions on page 5 to point to this patch, because I'm not sure how long gnome bugzilla will be down.

---

### Post by allquixotic on 2010-09-05
> **allquixotic said:**
> I'll update the instructions on page 5 to point to this patch, because I'm not sure how long gnome bugzilla will be down.

Updated. Please try again.

Sorry for the trouble...

---

### Post by The_Eddster on 2010-09-05
Thanks dude. There is another error though when I try to apply the patch:

git apply vala-hams-v6.patch


Then it says this:

vala-hams-v6.patch:79: trailing whitespace.
	backends 
vala-hams-v6.patch:184: trailing whitespace.
 * Run the Vala vala-gen-introspect tool to create a vala specific GIDL file 
vala-hams-v6.patch:206: trailing whitespace.
 * Whilst it has been attempted to avoid doing any re-writing of the gobject 
vala-hams-v6.patch:207: trailing whitespace.
   introspection output, certain things are needed to get the current 
vala-hams-v6.patch:210: trailing whitespace.
 * If you are looking to modify something, you probably want to look into 
warning: squelched 24 whitespace errors
warning: 29 lines add whitespace errors.

---

### Post by allquixotic on 2010-09-05
> **The_Eddster said:**
> Thanks dude. There is another error though when I try to apply the patch:

git apply vala-hams-v6.patch


Then it says this:

vala-hams-v6.patch:79: trailing whitespace.
	backends 
vala-hams-v6.patch:184: trailing whitespace.
 * Run the Vala vala-gen-introspect tool to create a vala specific GIDL file 
vala-hams-v6.patch:206: trailing whitespace.
 * Whilst it has been attempted to avoid doing any re-writing of the gobject 
vala-hams-v6.patch:207: trailing whitespace.
   introspection output, certain things are needed to get the current 
vala-hams-v6.patch:210: trailing whitespace.
 * If you are looking to modify something, you probably want to look into 
warning: squelched 24 whitespace errors
warning: 29 lines add whitespace errors.

I'm pretty sure those aren't errors; they're just warnings. I got those same messages here and was able to build rhythmbox with vala support just fine. That's called "patch fuzz" -- when it doesn't apply exactly, but the patch program could figure out how to fix it.

Keep trying the next steps and see if it works!

---

### Post by The_Eddster on 2010-09-05
Yup, it works now. Thanks for the help, and for making such a fine plugin!

---

### Post by Pepe Lebuntu on 2010-09-08
Thanks HEAPS for this, mate! I had had to be using Audacity to speed-listen to a lecture I needed to review. It was constantly crashing and being thoroughly unhelpful. As well as that, the "chipmunk" factor was rather annoying. This will help no end.

---

### Post by mogdad on 2010-09-16
> **allquixotic said:**
> Hi mogdad,

I'm very sorry for taking two weeks to respond to you! I intended to respond hours after you posted this, but I got sidetracked.

Can you please verify that you have the gstreamer0.10-plugins-bad package installed? Not having it installed is the most likely source of the error you're experiencing.

Also, please post which distribution you are using, the release number (e.g. 10.04), and the architecture (e.g., 32-bit or 64-bit).

I've checked and gstreamer0.10-plugins-bad version 0.10.18-1ubuntu1 is installed. 
I'm using 10.04 32 bit - should have included that in my first post...
Thanks for your help btw and no problem for the delay.

---

### Post by DouglasAWh on 2010-09-23
> **allquixotic said:**
> Don't worry -- what I'm going to do is build a .deb package that you can install for the version of Ubuntu you're using.

Please state the version of Ubuntu you use and the architecture (32-bit or 64-bit).

Did this ever happen? it looks like everyone is still compiling this.

---

### Post by cyrus_the_virus on 2010-10-12
Hi,

First of all, thanks for making this plugin! This is really useful.

Unfortunately I'm not able to install this in Ubuntu 10.10 x64. I'm using the instructions [ from page 5]("http://ubuntuforums.org/showthread.php?t=1303297&page=5") of this thread.

I'm getting this error after executing the *./configure* command:
> 
checking for VALA... no
configure: error: Vala plugin support explicitly requested, but not found


Would be great if I could get this working.

Martin

---

### Post by bayonetblaha on 2010-10-19
same VALA problems here! Ubuntu 10.10 64-bit, clean install.



> error: rhythmbox not found in specified Vala API directories or GObject-Introspection GIR directories

and when I try rbpitch-old:

> checking for VALA... no
configure: error: Vala plugin support explicitly requested, but not found


---

### Post by swarfrat on 2011-01-06
I'm in the same boat. Ubuntu 10.04, can't build rbpitch due to  "rhythmbox not found in specified Vala API directories..."

I'm kind of in a pickle here - I was prepared to fork over for Transcribe, but 1) even though I don't mind paying, I despise messing with licensing during reinstalls, backups, etc... 2) it doesn't work with Jack, and I'm not going to reconfigure sound just for working out tunes.

This has been a while - does anyone have Ubuntu 10.04 compiling Rhythmbox 0.13 with rbpitch?

---

### Post by colobix on 2011-01-07
Does anyone have the download link to rbpitch?
I've tried all over the web but with no luck.
All the links are just broken.

---

### Post by daverd on 2011-01-11
I ran into the same error, "configure: error: Vala plugin support explicitly requested, but not found". It seems like configure is checking for the wrong version of vala. The version I have installed is 0.10 but configure is checking for 1.0.

The following bash script made that particular problem go away, and I at least got it to sort of compile.

```
sed -i 's/vala-1.0/vala-0.10/g' configure
```

Now I'm running into other errors though when I run `make`:

ERROR: vala_gen_introspect created an empty .gi file
ERROR: vala_gen_introspect created an empty .gi file

---

### Post by swarfrat on 2011-01-12
This thread is not that old - surely someone has it working with recent software? 

rbpitch Readme.txt says it needs gstreamer-plugins-bad with 'pitch' enabled. Can't find anything on 'enabling' this plugin, but I did see that it's now called 'soundtouch' not 'pitch'.  rbpitch claims it needs at least gstreamer0.10-plugins-bad 0.10.4. Ubuntu 10.10 ships with 0.10.20. 

I tried both Rhythmbox 0.13.0 w/ the patch and 0.13.2 without, but enabling vala. Both build ok, but when building rbpitch, Vala can't seem to find anything rhythmbox related.

---

### Post by allquixotic on 2011-01-27
Hi everyone,

I haven't abandoned you! :) Life has been a little busy lately, and seeing how rbpitch is a hobby project, I haven't had a lot of time to work on it.

The current situation is this: **I'm re-writing rbpitch in Python**. The original Vala version of rbpitch will make a return when/if Jonathan Matthew ever finally comes up with a way to properly support Vala bindings for Rhythmbox. Daniel Hams went through quite a bit of effort to try and get his patchset merged, but has stopped working on it; furthermore, newer versions of Rhythmbox will cause Daniel's patch to not apply against the latest sources. So it only gets worse from here, until/if Jonathan Matthew does something about it.

The unfortunate situation {*Aside:* because I **abhor** Python as a language -- it is literally my least favorite language on the planet and I believe that it should be burned *with fire* in a great inferno, and all those in favor of strongly typed languages that ignore whitespace will be invited to the party... **ahem**, back to the subject at hand :lolflag:} is that Python bindings support is much better in Rhythmbox. Going forward, it should be possible for you guys to simply download a bunch of files, put them in the right place, and -- bam -- you've got rbpitch support for Rhythmbox. No compilation necessary. The advantages end there. ;)

I should have it done this weekend, so if it slips until next week, keep bugging me at the email address constructed by sending mail to the user "smcnam" who uses Google's e-mail service (anti-spambot cipher :mad:). Or you can just post back here.

At the moment I am simultaneously learning Python and trying to port my plugin. It seems like the scope of this project is about 12 to 20 hours. I should be able to bang it out in one sleepless night.

Thanks for your interest in rbpitch, guys -- the end result of this rewrite is that it'll be much easier for you to install it, and it should continue to work on future versions of Ubuntu for the foreseeable future.

**Edit:** It seems that due to a limitation of the Python bindings of GTK+, it would be difficult for me to port exactly the rbpitch functionality to Python at this time. I will see what the PyGObject project comes up with after I get a chance to catch up with Martin Pitt. By that time I may end up using GTK+-3.0 (if Rhythmbox upgrades to it), which would probably fix the binding issue. So, Python is out for now. What I'm going to do instead is use a couple local tweaks to produce a .c file from the Vala source (using a properly configured build environment), and then ship the .c source to be built by your local gcc compiler. This should work on a wide variety of recent distros shipping Rhythmbox 0.13.0 or later.

**Edit x2:** We have *DOWNLOAD URLs!* [https://launchpad.net/rbpitch](https://launchpad.net/rbpitch)

See the right-side of the page where you can grab rbpitch for i386 (32-bit) or amd64 (64-bit).

---

### Post by allquixotic on 2011-01-29
Quick update: rbpitch now has a proper toolbar icon in Rhythmbox! I was previously using the "stock" icon set, which makes the icon very easy to confuse with other icons. A clever community member on the ubuntu-artwork team made me a tuning fork icon, and I've integrated it into the binary and source builds now. :)

If you are curious, read [this thread](https://lists.ubuntu.com/archives/ubuntu-art/2011-January/013041.html) in the ubuntu-art mailing list archives for the back and forth between me and the icon's author, Saleel Velankar.

---

### Post by swarfrat on 2011-01-29
Yay! and thank you. Easy as pie, I think it works, but now I need to re-do my rhythmbox pulse/jack setup since reinstalling rhythmbox a few times prior to this.

---

### Post by mc4man on 2011-01-31
just to note - on natty builds/works fine w/ rhythmbox-0.13.3
(one small edit to the Makefile and distro.sh to use 'make' and 'make install'

---

### Post by allquixotic on 2011-02-26
> **mc4man said:**
> just to note - on natty builds/works fine w/ rhythmbox-0.13.3
(one small edit to the Makefile and distro.sh to use 'make' and 'make install'

I've just recently tested this out, and I see what you mean. There is indeed some build hackery that will be needed to support Natty out of the box.

In the next few days/weeks, I will work out what build system changes are needed to support building on Natty unmodified.

My plan is to release rbpitch binaries for Natty between the day the Ubuntu 11.04 RC is released, and the 11.04 final. So rbpitch binaries (deb packages) will be available on 11.04 release day.

---

### Post by allquixotic on 2011-04-10
Hi,

Just a quick update for anyone tracking the development of rbpitch :)

As the release of Ubuntu 11.04 "Natty Narwhal" is nearing, I am planning to provide installable rbpitch packages for this release of Ubuntu. At the same time, I am working towards porting my dependencies to the new Gnome 3.0 stack! This is exciting work that should prove fairly easy, to the extent that I didn't use obsolete APIs...

So far, I've committed experimental Gtk+-3.0 modifications to Bazaar, enabling the rbpitch UI to display a native GTK3 UI in a GTK3 build of Rhythmbox. You can find such a build of Rhythmbox, for example, in Fedora 15 Alpha (though it appears that Ubuntu 11.04 will be the last release of Ubnutu to still carry GTK+-2.0 by default).

I will investigate the possibility of using GTK3 and GSettings in lieu of GTK2 and GConf, even on Ubuntu 11.04, where the dependencies should exist but the main Rhythmbox UI will still use GTK2. This could result in an inconsistent UI though, so I'm not sure I want to do that!

More than likely, the official Natty binaries of rbpitch will link against GTK2 and GConf2 and Gstreamer-0.10, one more time. For Ubuntu 11.10, Fedora 15, OpenSUSE 11.5, and so forth, it'll be the Gnome 3 stack all the way!

This is a somewhat confusing transition period, as everyone jumps from the old ABI to the new ABI at a different pace. For example, gstreamer is still in the early planning phases of breaking its ABI to release the next major release of gstreamer. GTK+ 3.0, on the other hand, is already finalized and packaged in Ubuntu 11.04.

I am not very interested in maintaining a legacy branch of rbpitch for the Gnome2 platform once I've fully ported it over to Gnome3, so it is very likely that my binaries for Ubuntu 11.04 will be the last effort I make towards supporting a GTK2/Gconf2 build of rbpitch.

Thanks,

Sean

---

### Post by Giraffemonster on 2011-05-04
> **allquixotic said:**
> Hi,

Just a quick update for anyone tracking the development of rbpitch :)

As the release of Ubuntu 11.04 "Natty Narwhal" is nearing, I am planning to provide installable rbpitch packages for this release of Ubuntu. At the same time, I am working towards porting my dependencies to the new Gnome 3.0 stack! This is exciting work that should prove fairly easy, to the extent that I didn't use obsolete APIs...

So far, I've committed experimental Gtk+-3.0 modifications to Bazaar, enabling the rbpitch UI to display a native GTK3 UI in a GTK3 build of Rhythmbox. You can find such a build of Rhythmbox, for example, in Fedora 15 Alpha (though it appears that Ubuntu 11.04 will be the last release of Ubnutu to still carry GTK+-2.0 by default).

I will investigate the possibility of using GTK3 and GSettings in lieu of GTK2 and GConf, even on Ubuntu 11.04, where the dependencies should exist but the main Rhythmbox UI will still use GTK2. This could result in an inconsistent UI though, so I'm not sure I want to do that!

More than likely, the official Natty binaries of rbpitch will link against GTK2 and GConf2 and Gstreamer-0.10, one more time. For Ubuntu 11.10, Fedora 15, OpenSUSE 11.5, and so forth, it'll be the Gnome 3 stack all the way!

This is a somewhat confusing transition period, as everyone jumps from the old ABI to the new ABI at a different pace. For example, gstreamer is still in the early planning phases of breaking its ABI to release the next major release of gstreamer. GTK+ 3.0, on the other hand, is already finalized and packaged in Ubuntu 11.04.

I am not very interested in maintaining a legacy branch of rbpitch for the Gnome2 platform once I've fully ported it over to Gnome3, so it is very likely that my binaries for Ubuntu 11.04 will be the last effort I make towards supporting a GTK2/Gconf2 build of rbpitch.

Thanks,

Sean

That's cool, I would also like to know how this project is advancing. While you say you're using the GNOME 3 Dependencies, applications can run in the GTK environment despite the currently used Desktop Environment right? I'm saying this because I'm using 11.04 Natty Xubuntu.

Anyways, good luck building your 11.04 package. I haven't been able to successfully compile this from the source packages. Also, is it okay to bump this despite the last post being three weeks? Never really made such a large bump.

---

### Post by allquixotic on 2011-05-21
> **Giraffemonster said:**
> That's cool, I would also like to know how this project is advancing. While you say you're using the GNOME 3 Dependencies, applications can run in the GTK environment despite the currently used Desktop Environment right? I'm saying this because I'm using 11.04 Natty Xubuntu.

The thing is, you can't (cleanly) integrate a GTK3 widget into the GTK2 based Rhythmbox included in Ubuntu 11.04. It is perfectly fine to run GTK3 apps and GTK2 apps in different processes, but loading GTK3 and GTK2 in the same process is either impossible, or funny things will happen (I don't even want to test it!)

And that is doubly true for me, because my application generates a widget and places it on the Rhythmbox tool bar. I don't want to pass it a widget that uses a different data structure than it's expecting (expected GTK2, got GTK3). That could crash the program. So I have to build rbpitch linking against GTK2 for Ubuntu 11.04, because Ubuntu 11.04's Rhythmbox uses GTK2. **Note:** It is currently possible to build Rhythmbox with GTK3, but that work is (as far as I know) in an experimental branch. Fedora 15 pulled that work into their distribution, which will be released in 4 days, even though it is not yet deemed stable. It works fine for me, and the UI is in GTK3. With that as my base, I can successfully use rbpitch linked against GTK3.


> **Giraffemonster said:**
> Anyways, good luck building your 11.04 package. I haven't been able to successfully compile this from the source packages. Also, is it okay to bump this despite the last post being three weeks? Never really made such a large bump.

Sure, this is pretty much the only user feedback thread for rbpitch that exists. So it's fine that you are bumping this after so long. rbpitch is more or less in maintenance mode right now; my only work on it is to fix any bugs that people trip on, and to keep it working with the latest versions of Ubuntu and Fedora.

Right now I am about to release rbpitch 0.13.3, which will work with Rhythmbox 0.13.3 on Ubuntu 11.04. I've already made the commit to bazaar that fixes up the build system to support it; I just need to build the binary packages, since they are easier for people to install than the source. Look for the 0.13.3 packages available tonight.

For anyone reading this with an interest in installing rbpitch: let me make this really easy for you.

**If you are running Ubuntu 10.10**, you have Rhythmbox version 0.13.1. Therefore, you need rbpitch version 0.13.1 also.

**If you are running Ubuntu 11.04**, you have Rhythmbox version 0.13.3. Therefore, you need rbpitch version 0.13.3 also.

For this reason, the rbpitch 0.13.1 packages will remain relevant as long as some people still use Ubuntu 10.10. I have no plans to delete the packages.

---

### Post by kailynleto on 2011-09-01
So how's progress on the Gnome 3 rbpitch plugin?  I'm literally waiting on this plugin to upgrade.  Such a nerd...oh well...

If I can help you out let me know.  I can do a USB-persistent install of 11.10 to help you test.  I'm not great at writing code but I can compile and test for bugs well...

---

### Post by allquixotic on 2011-09-01
> **kailynleto said:**
> So how's progress on the Gnome 3 rbpitch plugin?  I'm literally waiting on this plugin to upgrade.  Such a nerd...oh well...

If I can help you out let me know.  I can do a USB-persistent install of 11.10 to help you test.  I'm not great at writing code but I can compile and test for bugs well...

I actually had a working plugin for a while when Rhythmbox was in the middle of transition; they had migrated to GTK3 but they hadn't replaced GConf with GSettings or their custom plugin API with libpeas.

Now that they've actually done the transition to libpeas, I should be able to begin work on migrating from the RBPlugin API to the libpeas API. I am not familiar with libpeas, so I'll have to learn something new.

Also the vala bindings for this stuff are still in the very early stages. I may end up having to write or manually modify some bindings by hand. Last time I tried, I encountered a whole slew of compilation problems with generated Vala VAPI files that were produced by inspecting GObject-Introspection .gir files and spitting out .vapi files. I don't think that those paths are ready for production yet.

Basically, I won't have any confidence in the lasting ability of my code to work for any length of time until Rhythmbox makes a new stable release. Once that is done, I *should* be able to adjust any APIs to meet the soft-frozen ones for the stable version.

Is Ubuntu shipping gnome3-based Rhythmbox in 11.10? I haven't tried it yet.

---

### Post by isfeldt on 2011-09-15
Hello, I have tryed the .deb package of rbpitch for ubuntu 11.04 32 bit, how ever, the software center when I click install, tells me the package is of bad quality. details are: E: rbpitch: maintainer-name-missing [EMAIL="root@ubuntu"]root@ubuntu[/EMAIL].  E: rbpitch: maintainer-address-malformed [EMAIL="root@ubuntu"]root@ubuntu[/EMAIL].  I have asked another user if it worked, and he stated that when updating rbpitch, he had to actually reinstall Ubuntu, or in our case, Vinux. It was pretty bad the outcome according to him.

---

### Post by allquixotic on 2011-09-26
> **isfeldt said:**
> Vinux

I have no idea what this is. I've never heard of it before, therefore there's no way I can support it. Who knows what modifications it has on top of the ordinary Ubuntu? I generally don't support Ubuntu **derivatives** such as Mint, Vinux, etc etc. What I **do** support are Ubuntu **flavors**, such as Kubuntu, Edubuntu, Lubuntu and Mythbuntu.

You are free to use any of the official Canonical flavors of Ubuntu, but if you want to run rbpitch on Vinux, you'll probably have to build it from source. Sorry.

---

### Post by teledyn on 2011-11-02
just found this thread and thought I'd leave a note in here just so that I'm alerted to updates (rbpitch is essential to my lifestyle ;) and I unfortunately rushed into a 11.10 upgrade :( so I'm eagerly watching the conversation here!

---

### Post by Catscrash on 2011-11-06
and there I was, being practically ecstatic to find this, just to find out I installed oneiric too soon, too :-( 
Do you have any roadmap as to when you'll have a working oneiric-version?

For now I installed rhythmbox from the natty archives and pinned it... not the cleanest idea, but so far working


Thanks so much

Catscrash

---

### Post by teledyn on 2011-11-06
> **Catscrash said:**
> For now I installed rhythmbox from the natty archives and pinned it... not the cleanest idea, but so far working

I like this work-around (anything that works!!) but I'm having trouble finding the natty archives.  Where did you find the old deb file?  archive.ubuntu.com/dist/natty appears empty :(

Also the version I find referred to in natty is 0.13.2 whereas the current version is 2.90.1 ... that's quite a jump in numbers!  Is this correct?  What happened to the version 1.x editions?  It's very confusing.

---

### Post by Catscrash on 2011-11-06
[http://packages.ubuntu.com/natty-updates/rhythmbox](http://packages.ubuntu.com/natty-updates/rhythmbox) unten amd64 / i386 als Link nutzen, das ist allerdings nicht das einzige Paket was du brauchst, um die installation abzuschließen musst du noch mindestens 4-5 andere Pakete da suchen und installieren

&#8364;dit: if any non-german-capable readers are interested (sry, i mixed up the forums when I answered ;)): [http://packages.ubuntu.com/natty-updates/rhythmbox](http://packages.ubuntu.com/natty-updates/rhythmbox) use the amd64 / i386 links in the bottom, but be prepared to download another 4-5 other packages from that page to complete the installation

---

### Post by teledyn on 2011-11-06
> **Catscrash said:**
> [http://packages.ubuntu.com/natty-updates/rhythmbox](http://packages.ubuntu.com/natty-updates/rhythmbox) unten amd64 / i386 als Link nutzen, das ist allerdings nicht das einzige Paket was du brauchst, um die installation abzuschließen musst du noch mindestens 4-5 andere Pakete da suchen und installieren

vielen Dank

---

### Post by Catscrash on 2011-11-06
woups, sry for answering in german before, i completely got mixed up with the forums...

---

### Post by teledyn on 2011-11-06
> **Catscrash said:**
> woups, sry for answering in german before, i completely got mixed up with the forums...

:D not a problem: that's why god invented Google Translate; I understood your instructions and followed them through and now I have pitch and speed control, and that's the main thing :)  Thanks again for your help, in any language :)

---

### Post by Catscrash on 2011-11-06
a word of warning though: (i knew it was a really dirty workaround) unfortunately most other plugins don't work, since there's apparently a problem with the combination of the oneiric python and the natty rhythmbox... well at least pitching works ;-)

---

### Post by teledyn on 2011-11-06
so close but not quite: installing the rhythmbox 0.13 does give me a sort of pitch controller, but it is the one that is a popup that measures changes in tenths of a percent (!?) whereas the one I wanted was the display of convenient slider controls that would increment in the more intelligent and domain-friendly integer semitones and rate change by relative position of the slider (what is a 200% tempo actually mean?  3x?)

and then the plugins were broken causing my package manager to be broken unless I also downgraded the rhythmbox-plugins, but the plugins depend on libmtp8 version 1.0.6 and all the archives no longer have the libmtp-common_1.0.6 that it requires, so the package manager would stay broken, and sadly I'm unable to allow that for this particular installation, so I'm back at square one.

And now I'm thinking perhaps I am not in the right place!  Is this discussion about the rate-changer that appears as a pitchfork on the row of control icons that then pops up that dialog with the tenths-of-percent controls?  Highly awkward for my purposes, I need to be able to shift a tune by integer tones with as little motion as possible (because I am playing at the same time) and ditto with the tempo, I need to just click something simple and increase the metronome speed by an incremental but significant amount, eg when practicing passages and wanting to start slow but then play "a little" faster on each success, and 1/1000th of the current tempo is outside of the range of detection for my ears I'm afraid ;)

so I guess I'm back at square one and will have to start investigating that other slider-based rate controller's code and learning about the rhythmbox api to somehow get to where I'm wanting to be :(

Thanks for the help anyway.

---

### Post by allquixotic on 2011-12-17
Hi,

> **teledyn said:**
> so close but not quite: installing the rhythmbox 0.13 does give me a sort of pitch controller, but it is the one that is a popup that measures changes in tenths of a percent (!?) whereas the one I wanted was the display of convenient slider controls that would increment in the more intelligent and domain-friendly integer semitones and rate change by relative position of the slider (what is a 200% tempo actually mean?  3x?)

The one you're referring to is rbpitch, which is the software I wrote.

rbpitch does indeed support integer semitones; actually it supports fixed-point, double-precision semitones. The underlying library I use to provide the support, libsoundtouch (which in turn is exposed in gstreamer-plugins-bad as the "pitch" element) exposes **all three** values -- pitch, speed and tempo -- as double-precision values from -10.0 to +10.0. So I have to translate these using some algorithms I obtained from the author of libsoundtouch, since I am not mathematically inclined enough to know how to do it myself. You can see these algorithms in the source code of rbpitch; do a find for "xlate" in the rbpitch-plugin.vala sources ( at [http://launchpad.net/rbpitch](http://launchpad.net/rbpitch) )

As for the meaning of the percentages for tempo/speed: these are just percentages converted from the underlying library's native double values (-10.0 / 10.0). So 0.0% means don't touch the value; 100% means multiply it by 2x; 200% means multiply it by 3x; etc. I admit this doesn't make a whole lot of sense and I should probably offset it so that 100% means don't touch the value. I can do that for the next version.

> **teledyn said:**
> and then the plugins were broken causing my package manager to be broken unless I also downgraded the rhythmbox-plugins, but the plugins depend on libmtp8 version 1.0.6 and all the archives no longer have the libmtp-common_1.0.6 that it requires, so the package manager would stay broken, and sadly I'm unable to allow that for this particular installation, so I'm back at square one.

rbpitch itself doesn't depend on libmtp8; you must be talking about the separate "rhythmbox-plugins" package, which is unrelated to rbpitch.

Generally I can't recommend downgrading packages within a system. Because I work on rbpitch in my spare time, and because Rhythmbox has been changing a lot lately due to being ported from the Gnome2 to the Gnome3 platform (and those changes broke my plugin code), I've been having to spend a lot of time reworking rbpitch to be compatible with newer versions of Rhythmbox.

> **teledyn said:**
> And now I'm thinking perhaps I am not in the right place!  Is this discussion about the rate-changer that appears as a pitchfork on the row of control icons that then pops up that dialog with the tenths-of-percent controls?

Yes. It's called rbpitch, hence the title of this thread.

  > **teledyn said:**
> Highly awkward for my purposes, I need to be able to shift a tune by integer tones with as little motion as possible (because I am playing at the same time)

What do you mean "integer tones"? You can easily pitch-shift by arbitrary semitone values using rbpitch. Just click in the box and type "1" or "2" (delete what's there) and it'll adjust accordingly. Does this not work for you?

> **teledyn said:**
>  and ditto with the tempo, I need to just click something simple and increase the metronome speed by an incremental but significant amount, eg when practicing passages and wanting to start slow but then play "a little" faster on each success, and 1/1000th of the current tempo is outside of the range of detection for my ears I'm afraid

...Which is why the configuration panel for rbpitch allows you to fine-tune the min/max range of the adjustment. Some people want the full range, and some people want a small, restricted range. I can't satisfy both extremes simultaneously, so I made it an option. Please configure it to your discerning needs, and let me know if it helps.


> **teledyn said:**
> so I guess I'm back at square one and will have to start investigating that other slider-based rate controller's code and learning about the rhythmbox api to somehow get to where I'm wanting to be :(

The only "other" plugin I'm aware of is scaletempo. The problem with scaletempo is that it hasn't been upgraded to work with the Gnome3 version of Rhythmbox. Is it [this one](http://willem.engen.nl/projects/musictools/) you used previously?

Anyway, scaletempo is much less featureful than rbpitch, and I don't think it's been maintained since about 2008 (at least based on what's on the page). I'm here now, and actively working on rbpitch to get it working with the Gnome3 version of Rhythmbox, which will work with Ubuntu 11.10 and Ubuntu 12.04 once released. And of course, the previous releases of rbpitch for prior versions of Ubuntu will not go away, although I will cease maintaining them due to the age of those releases.

Please let me know if you have any questions.

---

### Post by allquixotic on 2011-12-17
To those of you are worried about the timeline for this next release, please take a look at the milestones and other stuff on the launchpad site for rbpitch. Also a little teaser of what's to come; if you can read source code, take a look at this: [http://bazaar.launchpad.net/~smcnam/rbpitch/gnome3/revision/14](http://bazaar.launchpad.net/~smcnam/rbpitch/gnome3/revision/14)

---

### Post by teledyn on 2011-12-17
Thanks so much for the thoughtful and detailed reply -- I have been missing this code so badly in my music studio, I do hope from your hints here that I can get it going, and I'm anxiously awaiting the up-to-date release; I know first hand how frustrating it can be when you labour over something in your spare time and get it going and then the coders of the lower-level code change something that breaks all your work and throws you into a panic-mode of development, and I think it is pretty low of the Gnome3 people not to provide a backwards-compatible interface or at least a transitional glue-code library, but sadly I think we see this gonzo-coding style far too prevalent in modern computing.  Maybe I'm just old-fashioned (I first learned on Fortran IV and LISP)

So while I am frustrated and feeling abandoned, it's not directed to you so much as it is at Gnome3, and, well, we've all been in this situation before and it all works out eventually.  I only wish my Gnome chops were up to speed enough to help you bring that about faster.

---

### Post by allquixotic on 2011-12-17
> **teledyn said:**
> Thanks so much for the thoughtful and detailed reply -- I have been missing this code so badly in my music studio, I do hope from your hints here that I can get it going, and I'm anxiously awaiting the up-to-date release; I know first hand how frustrating it can be when you labour over something in your spare time and get it going and then the coders of the lower-level code change something that breaks all your work and throws you into a panic-mode of development, and I think it is pretty low of the Gnome3 people not to provide a backwards-compatible interface or at least a transitional glue-code library, but sadly I think we see this gonzo-coding style far too prevalent in modern computing.  Maybe I'm just old-fashioned (I first learned on Fortran IV and LISP)

So while I am frustrated and feeling abandoned, it's not directed to you so much as it is at Gnome3, and, well, we've all been in this situation before and it all works out eventually.  I only wish my Gnome chops were up to speed enough to help you bring that about faster.

Well I generally get motivated when I know others are anticipating my work product, so I'll try extra hard to get this worked out before the weekend's over :)

Been wasting a few hours trying to get an Ubuntu VM going with 3d support on Fedora 16... fool's errand; too many details to work out... now I'm settling with 2D and just trying to get rbpitch compiled hehe.

Haven't decided yet if I want to build a debian package on Ubuntu first, or if I should just bite the bullet and implement GSettings and then work on the debian package... 

Eh, I guess I'll work on GSettings. But first, some dinner :)

---

### Post by giopas on 2011-12-18
thankyou allquixotic for your work, we all impatiently wait for your release... yes on ubuntu as well :)))

giopas

---

### Post by allquixotic on 2011-12-21
All,

rbpitch 2.90 (Release 1) has been released for Ubuntu 11.10!

[https://launchpad.net/~smcnam/+archive/rbpitch-release](https://launchpad.net/~smcnam/+archive/rbpitch-release)

Uploaded and seems to be working. It's ready for testing! If you don't know how to install from a PPA, you might start by reading the help instructions on the PPA page itself (linked above). If you're still confused, post back here.

Let me know if you encounter any issues.

Thanks.

P.S. -- Those of you who are running a recent version of Fedora or OpenSUSE can compile the package from source. It's been tested and works on both Fedora 16 and OpenSUSE 12.1. Building rpms for Fedora and OpenSUSE would be a completely separate effort, since the packaging systems are so different. If you are interested in me doing that, please let me know.

---

### Post by wdtd on 2012-04-15
I would like to thank you very much for this great addition to Rhythmbox.  I would also like to ask if you have suggested setting values to speed up audio. Newbies without audio experience can find tweaking the settings a little tricky.

---

### Post by allquixotic on 2012-04-15
> **wdtd said:**
> I would like to thank you very much for this great addition to Rhythmbox.  I would also like to ask if you have suggested setting values to speed up audio. Newbies without audio experience can find tweaking the settings a little tricky.

Hi,

I'm not sure what you mean by "suggested" values. It depends entirely on what you're trying to do.

What exactly is tricky about it? Is it that you don't understand what impact the different settings have on the audio? Experiment with the settings while playing music and see what effect it has.

For reference, setting a speed of +36% is like playing a 45 rpm vinyl record on a 33 rpm turntable. In case even that doesn't make sense to you: a 33 rpm turntable will rotate the vinyl record 45 times per minute. A record designed to play on a turntable that rotates the vinyl 45 times per minute in order to play at "normal" speed is going to rotate faster than it should on a 33 rpm turntable. It's going to rotate about 36% faster.

Tempo is like the effect of doing this without changing the pitch of the audio, so it plays "faster" but it doesn't sound like Alvin and the chipmunks.

Pitch is like the turntable effect also, but without affecting how long the track is -- so a 2 minute long song will still play for 2 minutes if you change the pitch only, but it will play at a higher pitch.

Speed is the "pure" turntable effect, which means that BOTH pitch AND tempo are affected together, in the same ratio.

---

### Post by kailynleto on 2012-05-28
Will the 11.10 rbpitch work with 12.04?  Or are the changes too significant?  I know I ask this every release lol but figured I would ask.

---

### Post by allquixotic on 2012-05-28
> **kailynleto said:**
> Will the 11.10 rbpitch work with 12.04?  Or are the changes too significant?  I know I ask this every release lol but figured I would ask.

Hi, kailynleto.

Due to constant changes in Rhythmbox upstream, unfortunately it breaks rbpitch in a significant way with every release. Hopefully it'll settle down after Rhythmbox 3.0 is released, but right now we are using a beta version of Rhythmbox 3.0 (versioned 2.9x) in recent versions of Ubuntu (11.04, 11.10, 12.04). These beta versions are constantly changing, as is the Vala compiler that I use to produce the code.

I have been working lately on bringing up rbpitch for Ubuntu 12.04, and I don't think it'll be too much longer. But there have been multiple issues with the new Rhythmbox, and even a bug that I had to file and get fixed, before I can provide packages. Right now, rbpitch will not even compile on 12.04's version of Rhythmbox.

I'm thinking within the next week I should be able to do something with this, but mostly it's about motivation and spare time since this is a volunteer effort for me. I'll post back here when packages have been released.

---

### Post by 3nt on 2012-07-21
I get as far as rbpitch installing in 12.04 but when I attempt to activate I get :

Pitch and Tempo Shifting can not be used with your configuration.
Please use the GStreamer-0.10 backend.
Unload the Pitch and Tempo Shifting plugin to stop this message from appearing.

Is this the currently expeced state?

---

### Post by allquixotic on 2012-07-21
> **3nt said:**
> I get as far as rbpitch installing in 12.04 but when I attempt to activate I get :

Pitch and Tempo Shifting can not be used with your configuration.
Please use the GStreamer-0.10 backend.
Unload the Pitch and Tempo Shifting plugin to stop this message from appearing.

Is this the currently expeced state?

Hi 3nt,

Actually no. I committed changes to bazaar that should make it work with Ubuntu 12.04. I've never seen that error message actually occur on my end in testing. Can you run rhythmbox from the command line and paste (as an attachment or to a pastebin service) the command line log files?

---

### Post by 3nt on 2012-07-21
This is the log prior to activating rbpitch (which does suggest I may have an other problem)

rhythmbox

** (rhythmbox:26101): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 723, in get_info
    return self.service.folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 166, in inner
    result = f(*new_args, **new_kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/logger.py", line 283, in inner
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 717, in get_info
    mdobj = self.fs_manager.get_by_path(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 794, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/brian/.ubuntuone/Purchased from Ubuntu One'


** (rhythmbox:26101): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed


And I get no further errors after I activate. I am busy over the rest of the weekend but if I get a chance I will remove and re-install rhythmbox to see if the errors persist.

I installed rbpitch by adding the launchpad directory to sources.list (oneric as I couldn't find a precise version) and then apt-get install.
 I did previously try installing from the deb on the sweb page using UbuntuOne but this did not show up in the plugins so I purged and in stalled as above.

Brian

---

### Post by allquixotic on 2012-07-21
> **3nt said:**
> This is the log prior to activating rbpitch (which does suggest I may have an other problem)

rhythmbox

** (rhythmbox:26101): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 723, in get_info
    return self.service.folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 166, in inner
    result = f(*new_args, **new_kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/logger.py", line 283, in inner
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 717, in get_info
    mdobj = self.fs_manager.get_by_path(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 794, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/brian/.ubuntuone/Purchased from Ubuntu One'


** (rhythmbox:26101): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed


And I get no further errors after I activate. I am busy over the rest of the weekend but if I get a chance I will remove and re-install rhythmbox to see if the errors persist.

I installed rbpitch by adding the launchpad directory to sources.list (oneric as I couldn't find a precise version) and then apt-get install.
 I did previously try installing from the deb on the sweb page using UbuntuOne but this did not show up in the plugins so I purged and in stalled as above.

Brian

Oh. No wonder you're having problems! The packages for older versions of Ubuntu will never work on future versions of Ubuntu, because Rhythmbox keeps changing its API/ABI. So don't do that.

You'll have to build it from source until I can get some packages out for Precise. I don't know when that'll be. But the latest source *should* work well on Precise if you compile it. There are posts throughout this thread with information on how to build it; the *most recent* instructions would tend to be the most correct.

---

### Post by teledyn on 2012-07-22
Has the software changed locations?  I followed the link above to the PPA and did the add, only aptitude update gives me a 404 error on this


W: Failed to fetch [http://ppa.launchpad.net/smcnam/rbpitch-release/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/smcnam/rbpitch-release/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/smcnam/rbpitch-release/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/smcnam/rbpitch-release/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

did I miss a memo?

---

### Post by allquixotic on 2012-07-22
> **teledyn said:**
> Has the software changed locations?  I followed the link above to the PPA and did the add, only aptitude update gives me a 404 error on this


W: Failed to fetch [http://ppa.launchpad.net/smcnam/rbpitch-release/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/smcnam/rbpitch-release/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/smcnam/rbpitch-release/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/smcnam/rbpitch-release/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

did I miss a memo?

If you're running Ubuntu 12.04 (Precise), please stop trying to download rbpitch from the PPA. The packages aren't there, so of course you're going to get a 404 not found error. I haven't uploaded the packages for Ubuntu 12.04. The packages don't exist. Creating them takes time -- time I don't have right now. I figured providing working source code would be enough for most people to muddle through the simple compilation instructions and get it installed and working... over here I've been able to run it on Ubuntu 12.04 and on Fedora 17.

The only way (right now) to run rbpitch on Ubuntu 12.04 Precise is to compile it from source code. There are already instructions in this thread and elsewhere on how to do that. It's not any more complicated than any other program that uses autoconf/automake, you just have to have the right dependency packages installed.

---

### Post by 3nt on 2012-07-22
I have downloaded the code using bzr. I had to copy a number of files from /usr/include/gstreamer-0.10/gst/pbutils/ to /usr/include/gst/pbutils/ as that is where make seems to expect them but I now get errors in the C files (I think) which I do not know enough about to fix easily. Can you point me in the right direction. 
I believe I have all the right dependencies (although some done by trial and error).
I have run ./configure --prefix=/usr with no errors but when running make I get :

brian@notebook:~/rbpitch$ make
make  all-recursive
make[1]: Entering directory `/home/brian/rbpitch'
Making all in src
make[2]: Entering directory `/home/brian/rbpitch/src'
  CC     librbpitch_la-rbpitch-plugin.lo
In file included from /usr/include/gtk-3.0/gdk/gdk.h:31:0,
                 from /usr/include/gtk-3.0/gtk/gtk.h:30,
                 from /usr/include/libpeas-1.0/libpeas-gtk/peas-gtk-configurable.h:25,
                 from /usr/include/libpeas-1.0/libpeas-gtk/peas-gtk.h:23,
                 from rbpitch-plugin.c:31:
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:137:6: error: missing binary operator before token "("
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:145:5: error: missing binary operator before token "("
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:148:5: error: missing binary operator before token "("
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:154:5: error: missing binary operator before token "("
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:162:5: error: missing binary operator before token "("
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:168:5: error: missing binary operator before token "("
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:176:5: error: missing binary operator before token "("
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:182:5: error: missing binary operator before token "("
/usr/include/gtk-3.0/gdk/gdkversionmacros.h:190:5: error: missing binary operator before token "("
In file included from /usr/include/gtk-3.0/gtk/gtkwindow.h:33:0,
                 from /usr/include/gtk-3.0/gtk/gtkdialog.h:33,
                 from /usr/include/gtk-3.0/gtk/gtkaboutdialog.h:30,
                 from /usr/include/gtk-3.0/gtk/gtk.h:31,
                 from /usr/include/libpeas-1.0/libpeas-gtk/peas-gtk-configurable.h:25,
                 from /usr/include/libpeas-1.0/libpeas-gtk/peas-gtk.h:23,
                 from rbpitch-plugin.c:31:
/usr/include/gtk-3.0/gtk/gtkapplication.h:77:1: error: unknown type name 'GMenuModel'
/usr/include/gtk-3.0/gtk/gtkapplication.h:80:49: error: unknown type name 'GMenuModel'
/usr/include/gtk-3.0/gtk/gtkapplication.h:83:1: error: unknown type name 'GMenuModel'
/usr/include/gtk-3.0/gtk/gtkapplication.h:86:49: error: unknown type name 'GMenuModel'
In file included from /usr/include/gtk-3.0/gtk/gtklabel.h:35:0,
                 from /usr/include/gtk-3.0/gtk/gtkaccellabel.h:36,
                 from /usr/include/gtk-3.0/gtk/gtk.h:33,
                 from /usr/include/libpeas-1.0/libpeas-gtk/peas-gtk-configurable.h:25,
                 from /usr/include/libpeas-1.0/libpeas-gtk/peas-gtk.h:23,
                 from rbpitch-plugin.c:31:
/usr/include/gtk-3.0/gtk/gtkmenu.h:119:44: error: unknown type name 'GMenuModel'
In file included from /usr/include/gtk-3.0/gtk/gtk.h:132:0,
                 from /usr/include/libpeas-1.0/libpeas-gtk/peas-gtk-configurable.h:25,
                 from /usr/include/libpeas-1.0/libpeas-gtk/peas-gtk.h:23,
                 from rbpitch-plugin.c:31:
/usr/include/gtk-3.0/gtk/gtkmenubar.h:73:42: error: unknown type name 'GMenuModel'
/home/brian/rbpitch/src/rbpitch-plugin.vala: In function 'rb_pitch_plugin_display_error':
/home/brian/rbpitch/src/rbpitch-plugin.vala:856:2: warning: format not a string literal and no format arguments [-Wformat-security]
make[2]: *** [librbpitch_la-rbpitch-plugin.lo] Error 1
make[2]: Leaving directory `/home/brian/rbpitch/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brian/rbpitch'
make: *** [all] Error 2


I am running 12.04 on a Dell Inspiron 9400
Thanks

---

### Post by allquixotic on 2012-11-03
rbpitch for 12.04 and 12.10 has been released, as of today. It's available in the PPA repository.

1. In the terminal, enter the following lines:

sudo apt-add-repository ppa:smcnam/rbpitch-release

sudo apt-get update

sudo apt-get install rbpitch

2. In Rhythmbox, go to the Plugins manager via the Edit -> Plugins menu. Make sure the checkbox next to "Pitch and Tempo Shifting" is checked.

And that's it -- it should then be enabled!

Feel free to report any bugs at [http://launchpad.net/rbpitch](http://launchpad.net/rbpitch) .

---

### Post by teledyn on 2012-11-03
YAY! :)

we've been waiting hundreds of years for this :guitar:

---

### Post by 3nt on 2012-11-03
Brilliant!:) Many thanks for this - I never did get it to compile form source.

---

