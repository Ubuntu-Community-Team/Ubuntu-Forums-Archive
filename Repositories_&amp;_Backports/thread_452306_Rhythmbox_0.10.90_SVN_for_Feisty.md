---
title: "Rhythmbox 0.10.90 SVN for Feisty"
date: 2007-05-23
forum: Repositories &amp; Backports
---

### Post by DtJee on 2007-05-23
I've uploaded the rhythmbox deb to my site

[_http://www.sernetz.com/wordpress/?p=78_]("http://www.sernetz.com/wordpress/?p=78")

It's todays SVN version. Give it a try, if it works for you, be happy. Actually it works for me :)

---

### Post by Hairy_Palms on 2007-05-24
thanks! works awesome, and i like the new way of laying out the side panel too :)

---

### Post by deadlydeathcone on 2007-05-24
Thanks a lot, it works fine for me as well.

By the way, in Preferences there's a new tab for enabling crossfading, but one thing that's not mentioned is that it (apparently) also enables gapless playback, which is pretty cool as if it's actually working yet it brings the number of gapless players for Linux up to a good 2½ (sorry, Amarok).

---

### Post by DtJee on 2007-05-25
Gapless playback is really nice.. especially if you're using the partymode... :p. I although like the new icons.. much more polished...

---

### Post by bofphile on 2007-05-26
Thanks a lot DtJee ! At last with have the gapless feature. :D

---

### Post by deadlydeathcone on 2007-05-26
If anyone here uses last.fm, you might be interested [in an improved scrobbler plugin]("http://blog.blackdown.de/2007/05/19/lastfm-for-rhythmbox-new-style"). There were only debs for Gutsy, though, so I backported Rhythmbox from Gutsy (which is basically the latest svn with some extra radio stations patched in) and added the last.fm patch from the site. It was made with pbuilder and can be found [here]("http://www.box.net/shared/0fueun6o7i"). Goes well with the [last.fm beta client]("http://www.last.fm/group/Audioscrobbler+Beta/forum/30705/_/278066"), I think.

---

### Post by smbm on 2007-05-27
> **deadlydeathcone said:**
> If anyone here uses last.fm, you might be interested [in an improved scrobbler plugin]("http://blog.blackdown.de/2007/05/19/lastfm-for-rhythmbox-new-style"). There were only debs for Gutsy, though, so I backported Rhythmbox from Gutsy (which is basically the latest svn with some extra radio stations patched in) and added the last.fm patch from the site. It was made with pbuilder and can be found [here]("http://www.box.net/shared/ya7ze1i5p0"). Goes well with the [last.fm beta client]("http://www.last.fm/group/Audioscrobbler+Beta/forum/30705/_/278066"), I think.

Hi

Firstly, thanks so much to everyone in this thread for taking the time to make new packages.

I just installed the package from the post above. Mostly it works great, one small problem though is that the tray icon is massive. Anyone got any clue how to fix that?

[IMG]http://img185.imageshack.us/img185/1651/gfhfghvg5.png[/IMG]

If it needs to be recompiled I'm happy to do that but may require some pointers from people about packaging.  Also I think there is an updated new style last.fm plugin too that automatically launches the last.fm player so I just recompile anyway.

[Edit] I just read your post on the last.fm forum and stand corrected on the version of the plugin you compiled in. It doesn't seem to auto launch the client though. Bizarre

Thanks again everyone

Tom

---

### Post by junior aspirin on 2007-05-27
icon was fine for me.

2 things about the last.fm plugin:
1. for some reason the old style plugin did not seem to submit any tracks
2. i hope the old style is not going to be phased out. i really don't want to have another application running just to submit tracks

other than that it looks good, nice new icons, and the crossfade is great.
any other changes made/planned before 0.11?

---

### Post by smbm on 2007-05-27
> **junior aspirin said:**
> icon was fine for me.

2 things about the last.fm plugin:
1. for some reason the old style plugin did not seem to submit any tracks
2. i hope the old style is not going to be phased out. i really don't want to have another application running just to submit tracks

other than that it looks good, nice new icons, and the crossfade is great.
any other changes made/planned before 0.11?

Did it queue the tracks for submission but not actually submit them?

---

### Post by smbm on 2007-05-27
> **smbm said:**
> Hi

Firstly, thanks so much to everyone in this thread for taking the time to make new packages.

I just installed the package from the post above. Mostly it works great, one small problem though is that the tray icon is massive. Anyone got any clue how to fix that?

[IMG]http://img185.imageshack.us/img185/1651/gfhfghvg5.png[/IMG]

If it needs to be recompiled I'm happy to do that but may require some pointers from people about packaging.  Also I think there is an updated new style last.fm plugin too that automatically launches the last.fm player so I just recompile anyway.

[Edit] I just read your post on the last.fm forum and stand corrected on the version of the plugin you compiled in. It doesn't seem to auto launch the client though. Bizarre

Thanks again everyone

Tom

Managed to fix the icon problem. It was caused by my icon theme. Still haven't figured out why the client isn't launching automatically but it's not too big a deal. 

Thanks to everyone.

---

### Post by deadlydeathcone on 2007-05-27
> **smbm said:**
> Managed to fix the icon problem. It was caused by my icon theme. Still haven't figured out why the client isn't launching automatically but it's not too big a deal. 

Thanks to everyone.

I didn't have the icon problem, but I updated the deb on my other post that SHOULD fix it. Good catch with the launcher bug, too, the patch was looking in /bin but the last.fm beta deb installs to /opt so that's fixed too.

If there are other people who had a million last.fm stations saved in Rhythmbox, you can keep them around if you leave both of the plugins and only but turn off scrobbling for the official client. It still shows artist info and lets you love a track, though, so it all works out the same. :p

---

### Post by junior aspirin on 2007-05-27
> **smbm said:**
> Did it queue the tracks for submission but not actually submit them?

indeed it did. according to the plugin anyhow

---

### Post by deadlydeathcone on 2007-05-28
> **junior aspirin said:**
> indeed it did. according to the plugin anyhow

It saves all failed submissions to a file, so you might want to enter "less ~/.gnome2/rhythmbox/audioscrobbler.queue" in a terminal and see if anything comes up.

Also, if you start Rhythmbox using "rhythmbox -D audioscrobbler" it might reveal what the error is.

---

### Post by junior aspirin on 2007-05-28
> **deadlydeathcone said:**
> It saves all failed submissions to a file, so you might want to enter "less ~/.gnome2/rhythmbox/audioscrobbler.queue" in a terminal and see if anything comes up.

Also, if you start Rhythmbox using "rhythmbox -D audioscrobbler" it might reveal what the error is.

meh. works now. i did install the deb in the 1st post this time though instead of the one deadlydeathcone posted. maybe there is a problem with that version.

---

### Post by dlai on 2007-05-28
Hey, the 0.11 is out, I'm not familiar with the build system used with rhythmbox, would you be so kind as to provide a new deb with this release?

---

### Post by bofphile on 2007-05-28
I second that request. Thanks in advance.:)

---

### Post by smbm on 2007-05-28
> **deadlydeathcone said:**
> I didn't have the icon problem, but I updated the deb on my other post that SHOULD fix it. Good catch with the launcher bug, too, the patch was looking in /bin but the last.fm beta deb installs to /opt so that's fixed too.

If there are other people who had a million last.fm stations saved in Rhythmbox, you can keep them around if you leave both of the plugins and only but turn off scrobbling for the official client. It still shows artist info and lets you love a track, though, so it all works out the same. :p

It worked amazingly. Thanks again for your time. I have a couple of ideas for other plugins/improvements but zero coding experience. Where do I even start with something like that?

Cheers

Tom

---

### Post by deadlydeathcone on 2007-05-28
Here you go:

[rhythmbox_0.11.0-0lastfm2_i386.deb]("http://www.box.net/shared/atn9lxglh6")

I added in a few patches from the RB bugtracker that fix some icon related stuff, make the tooltips prettier and some other good stuff.

Anyways, enjoy, there's a changelog on the [mailing list]("http://mail.gnome.org/archives/rhythmbox-devel/2007-May/msg00107.html").

Updated: added a few icons from [this thread]("http://ubuntuforums.org/showpost.php?p=2722357&postcount=3") and a 24x24 app icon so that the menu icon wouldn't look terrible.

---

### Post by deadlydeathcone on 2007-05-29
> **smbm said:**
> It worked amazingly. Thanks again for your time.
No prob :)
> **smbm said:**
> I have a couple of ideas for other plugins/improvements but zero coding experience. Where do I even start with something like that?

First step would be picking up a beginners programming book, and I recommend one for either C or Python. You can start with either; C if you want to get the fundamentals down, or Python if you really want to jump into the fray right away. Sams make good, comprehensive, and really really dull programming books which makes them pretty much perfect for C, but with Python you could go with something more fun. I started with [this one]("http://www.amazon.com/Python-Programming-Absolute-Beginner-Michael/dp/1592000738") , and it's actually pretty fun in places, plus it gets into the pygame api a bit at the end.

After that, check out something somewhat simple like a [plugin]("http://usrportage.de/archives/763-the-last-rhythm-for-me.html"), or look at some patches on a [bugtracker]("http://bugzilla.gnome.org/browse.cgi?product=rhythmbox") to see what they did, or start writing something on your own. Just remember that you have to learn to spell before you write the great american novel.

---

### Post by Kobalt on 2007-05-29
Thanks a bunch for the deb deadlydeadcone ! RB 0.11 looks just great.

---

### Post by smbm on 2007-05-30
> **deadlydeathcone said:**
> No prob :)


First step would be picking up a beginners programming book, and I recommend one for either C or Python. You can start with either; C if you want to get the fundamentals down, or Python if you really want to jump into the fray right away. Sams make good, comprehensive, and really really dull programming books which makes them pretty much perfect for C, but with Python you could go with something more fun. I started with [this one]("http://www.amazon.com/Python-Programming-Absolute-Beginner-Michael/dp/1592000738") , and it's actually pretty fun in places, plus it gets into the pygame api a bit at the end.

After that, check out something somewhat simple like a [plugin]("http://usrportage.de/archives/763-the-last-rhythm-for-me.html"), or look at some patches on a [bugtracker]("http://bugzilla.gnome.org/browse.cgi?product=rhythmbox") to see what they did, or start writing something on your own. Just remember that you have to learn to spell before you write the great american novel.


Cheers, I'll dig out the book and see what I can do.

One thing I'd like to be able to do is find out how to patch it to remove its entry in the Window List.
It sounds to me like that wouldn't be too challenging. I'll let you know how I get on if you like.

One other question I have: the version number of your version has now been superseded by a new Ubuntu version (which probably won't have the new style last.fm plugin), is there any way I can change it to be a higher version number so I don't have the update icon in my tray all the time?


Thanks

Tom

---

### Post by ravanwin on 2007-05-30
Hello there:

I'm a complete newbie to Ubuntu, I am using Ubuntu 7.04 Feisty Fawn and the GNOME desktop.

I just downloaed this to see if it would work with my creative zen vplus. a person in another forum recomended it so, I thought I'd give it a shot.

Truthfully, the whole thing looks REALLY good, and seems to work pretty seamlessly. However, there seems to be no recognition of my little ol' creative zen plus mp3 player. 

Am I missing something? I did a scan for removeable media but found nada. Let me know if there is a way for RB to recognize my mp3. I am finding the new mp3 player very difficult as the only software I can use is GoNomad2 and Anarok (which isn;t for a gnome desktop....)

Anyway, thanks for the good update of RB. And thanks in advance for any help you can give. Remember, I am a newbie and don't understand too much programing talk etc.

All best,
rv

---

### Post by adamJ5 on 2007-05-30
Screenz Plx!! :)

---

### Post by DtJee on 2007-05-31
> **smbm said:**
> Cheers, I'll dig out the book and see what I can do.

One thing I'd like to be able to do is find out how to patch it to remove its entry in the Window List.
It sounds to me like that wouldn't be too challenging. I'll let you know how I get on if you like.

One other question I have: the version number of your version has now been superseded by a new Ubuntu version (which probably won't have the new style last.fm plugin), is there any way I can change it to be a higher version number so I don't have the update icon in my tray all the time?


Thanks

Tom


Try to run synaptic and select the rhythmbox package inside the manager. Then go to the package menu and select force version .. (or something like this). There you can select the version you want.. and normally the update-manager should ignore any newer package.


Hm this is just recognized by synaptic it seems. Too bad, would be a nice feature... :)

---

### Post by smbm on 2007-05-31
It seems to have worked in update manager too for me. 

Cheers

---

### Post by deadlydeathcone on 2007-05-31
> **adamJ5 said:**
> Screenz Plx!! :)
[Here ya go.]("http://ubuntuforums.org/showpost.php?p=2746334&postcount=9")

> **ravanwin said:**
> 
Am I missing something? I did a scan for removeable media but found nada. Let me know if there is a way for RB to recognize my mp3. I am finding the new mp3 player very difficult as the only software I can use is GoNomad2 and Anarok (which isn;t for a gnome desktop....)

Rhythmbox only works with iPods, and as far as I know Gnomad and Amarok are all that there is, unfortunately. Not a lot of devs seem to have mtp devices (which is what Creative mp3 players are) so linux support for them is really spotty right now. There are patches out there for Rhythmbox and Banshee, but neither really work all that well.

---

### Post by ravanwin on 2007-06-01
> **deadlydeathcone said:**
> 

Rhythmbox only works with iPods, and as far as I know Gnomad and Amarok are all that there is, unfortunately. Not a lot of devs seem to have mtp devices (which is what Creative mp3 players are) so linux support for them is really spotty right now. There are patches out there for Rhythmbox and Banshee, but neither really work all that well.

thanks for adressing that. in another forum, someone suggested that rhythm box would somehow work with this mp3 player of mine. alas, it doesn't seem to.

oh well, thanks for your time everyone.

Rvan

---

### Post by Hairy_Palms on 2007-06-03
rhythmbox definately also works with the iriver H320, and the samsung YP-U2R, because ive had them both and they both work :)

---

### Post by ravanwin on 2007-06-03
so... is RB meant to work with this Zen Vplus or what?
r

---

### Post by DtJee on 2007-06-03
RB although works with my k750i Sony Handy... :) but you've got to have a recent hal version...

---

### Post by alaaji on 2007-06-04
It also works with my Sandisk Sansa e250. :p

Oh, thanks for the updated rhythmbox version.  Man, it's great!

---

### Post by doclivingston on 2007-06-06
> **deadlydeathcone said:**
> Not a lot of devs seem to have mtp devices (which is what Creative mp3 players are) so linux support for them is really spotty right now. There are patches out there for Rhythmbox and Banshee, but neither really work all that well.

There has been recent work on the MTP support for Rhythmbox, and if all goes well it should be in 0.11.1. [http://bugzilla.gnome.org/show_bug.cgi?id=345006](http://bugzilla.gnome.org/show_bug.cgi?id=345006) has the patch and details.

---

### Post by deadlydeathcone on 2007-07-02
So, [Rhythmbox 11.1 is out]("http://www.box.net/shared/kx8j71rgpb").

Changelog [here]("http://mail.gnome.org/archives/rhythmbox-devel/2007-June/msg00063.html"); the major thing is, as doclivongston mentioned MTP support is now in!

---

### Post by smbm on 2007-07-02
Does this have the new style last.fm plugin and all the patches you'd applied on the previous builds? 

Thanks again for all your work.

---

### Post by obbe on 2007-07-15
hi all, i'm using rhythmbox 0.11.1 but i've a problem.. sometimes when i'm listening musics with last.fm it stops working.. is it normal?

---

### Post by deadlydeathcone on 2007-08-23
[Rhythmbox 11.2]("http://www.box.net/shared/o8asyv6d9j") is out!

A uPnP plugin has been added in this release, but don't try to activate it unless you have both python-coherence and python-louie installed or it will crash mightily. They haven't been packaged for Ubuntu as far as I know, and their counterparts in Debian didn't work properly when I tried them.

> **smbm said:**
> Does this have the new style last.fm plugin and all the patches you'd applied on the previous builds?
Yes. I'll be sure to keep adding them with every release.

I haven't been around the forums for a while, so sorry for the late reply.

---

### Post by ignignokt00 on 2007-09-05
Gapless playback isn't working for me.

---

