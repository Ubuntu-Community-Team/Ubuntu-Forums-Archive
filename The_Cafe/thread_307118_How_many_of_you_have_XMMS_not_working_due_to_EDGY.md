---
title: "How many of you have XMMS not working due to EDGY ?"
date: 2006-11-26
forum: The Cafe
---

### Post by burek on 2006-11-26
How many of you have XMMS not working due to EDGY ?

The fonts of the menus are gone. 

Thank you

---

### Post by shining on 2006-11-26
> **burek said:**
> How many of you have XMMS not working due to EDGY ?

The fonts of the menus are gone. 

Thank you

I remember having this problem at some point (maybe during edgy development), but I don't remember how to fix it.
Anyway, why are you using xmms, instead of beep-media-player, which is basically xmms ported to gtk2 (and so looks much nicer)?
Since gnome and every gnome apps use gtk2, it's better to also use it for other apps, and only use one toolkit.
This has 2 advantages : consistency, and smaller memory usage thanks to shared libraries. 
I didn't check that last point in practice though, but it makes sense to me. If you run beep-media-player, it'll use the gtk2 shared lib which is already in memory, since it's already being used. While with xmms, it'll need to load gtk1 first. (That's assuming you use gnome, and don't use other gtk1 apps)

---

### Post by PatrickMay16 on 2006-11-26
I thought beep media player was obsoleted by something. Also, can BMP use XMMS plugins? If not, I'll take something functional over something 'pretty' any day.

Also, to the OP. I have a problem with XMMS in edgy on my spare machine. When I try to put it in double-size mode, it glitches up and I have to kill it. I think this is something to do with compositing being on by default.

---

### Post by patrickfromspain on 2006-11-26
BMP isn't obsolete. As for the plugins, why don't you install and try? In 5minutes you'll see if it works ;)

---

### Post by BoyOfDestiny on 2006-11-26
> **patrickfromspain said:**
> BMP isn't obsolete. As for the plugins, why don't you install and try? In 5minutes you'll see if it works ;)

I'd say it's obsolete. The team is working on BMPx now instead... 

However, there is an excellent fork of BMP called audacious.

Excellent plugin support out of the box, mp3, wav, flac, ogg, various console formats, sids, and uade works with it too...

[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

P.S. To the other Patrick, many XMMS plugins have been ported to audacious. Is there one in particular you need (also the latest version of audacious has double size, where beep doesn't ;) )

---

### Post by burek on 2006-11-26
> **BoyOfDestiny said:**
> I'd say it's obsolete. The team is working on BMPx now instead... 

However, there is an excellent fork of BMP called audacious.

Excellent plugin support out of the box, mp3, wav, flac, ogg, various console formats, sids, and uade works with it too...

[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

P.S. To the other Patrick, many XMMS plugins have been ported to audacious. Is there one in particular you need (also the latest version of audacious has double size, where beep doesn't ;) )

I could find on my edgy computers 
only one of them as this problem of fonts that appeared after dist-upgrade
so; not that bad but quite annnoying ; I will downgrade this pc.
with edgy; I wish i had dist-downgrade :) :KS

---

### Post by karderio on 2006-11-27
I have a problem with xmms since I upgraded to edgy ([http://www.ubuntuforums.org/showthread.php?p=1815422#post1815422)](http://www.ubuntuforums.org/showthread.php?p=1815422#post1815422)).

I compared BMPx to Audacious a while back, and for some reason I decided on Audacious. It wasn' in apt though, so I made do with totem for listening to music - I've got tired of this, and want xmms back now.

Audacious has .deb packages for download, but I can't locate the Audacious-Plugins dependancy on their website, pff... I must admit that I havn't really looked, I'd rather compile it from source than trawl through their website... but instead I'm going to try BMPx. [rant] I really don't see why I should go through all this to get a decent mp3 player, it's getting to be almost as complicated as installing something on windows ;) [/rant]

Love, Karderio.

[edit]
Now here's something completely ridiculous ! BMPx isn't in apt, so I've installed BMP - thats fine, I just want to play music. However, BMP, as a winamp clone, has winamp-style skins (I have always hated these winamp-style skins (My job once once interface designer, I'm very picky)). That's fine, **I just want to play music**, but when I click the "D" (yes, it's a "D", very descriptive) to make the beast a usable size, it tells me that "Doublesize has been removed" !! -cry- Please, I don't mind using an interface I consider crap, but as it stands, I can't ***see*** the buttons, and **all I want is to play music** !
[/edit]

---

### Post by Kristen Lucas on 2006-11-27
Xmms is based on GTK1, it's obsolete, use BMP or rather Amarok.

---

### Post by karderio on 2006-11-27
> **Kristen Lucas said:**
> Xmms is based on GTK1, it's obsolete, use BMP or rather Amarok.

I'm not sure you could call Xmms "obsolete". "Obsolescence is a state of being which occurs when a person, object, or service is no longer wanted, even though it may still be in good working order." I don't want to seem pedantic by quoting the definition, it just seemed a little funny, as Xmms is just the opposite : it is still wanted (by me at least) but it doesn't work :o

Xmms was once a stable piece of software, and was the most widely used music player on GNU. Now, as you say, it has grown old, *very old* and has developed a serious case of bit rot. However, for the time being, many of the alternatives are young, very young, and have not yet become as stable as Xmms once was. In fact, they are so young they are not included in Ubuntu !

Xmms still has a wide user base, as far as I can see. On the Ubuntu side of things, if the package is there, it should work - it would be just ridiculous to say "package X is in Ubuntu, but it doesn't work, use missing package Y instead".  If something has fallen into disuse, and maintenance has become too 'expensive' a policy should be adopted to depreciate it. Leaving broken things hanging around is *not good*.

I'm sorry, I could rant on for pages about this... There are many many more reasons I feel this is a bad situation. I'll find a solution, but things just should not be so complicated. What really bugs me in all this is that it makes me wonder how I will get people to use Ubuntu if they don't have a music player that "Just works". I understand that defending Ubuntu in the face of harsh criticism (and there is a lot about) is important, but it should not entail complacency.

Love, Karderio.

[edit]
As a matter of interest, to solve this mess, I downloaded and compiled 3 packages : audacious, audacious-plugins and taglib. Just try and tell your grandma that that is what she should do to listen to her music - she'll be having you fish the gramophone out of the dumpster !

Audacious seems to work ok, the interface is simply awful however.
[/edit]

[edit]
"Audacious seems to work ok" Strike that - Audacious crashes randomly, pfff...
[/edit]

---

### Post by Johnsie on 2006-11-27
I'm sorry that you are having problems with xmms. I think it's been obseleted now but if you like it then I hope you can get it working. I'm an ex winamp user and have tried many apps while looking for an alternative. If you need an xmms replacement than try audacious. BMP is ok but as the other have said it is a dead project. Last week I downloaded Songbird and really liked that. I guess it just depends what you want you media player to do. 

If you wanna try songbird go to [http://www.songbirdsnest.com](http://www.songbirdsnest.com)

btw has anyone gotten any of the media players to broadcast to a shoutcast server? please pm me if you have as I dont wanna hijack the thread.

---

### Post by Kristen Lucas on 2006-11-27
> **karderio said:**
> I'm not sure you could call Xmms "obsolete". "Obsolescence is a state of being which occurs when a person, object, or service is no longer wanted, even though it may still be in good working order." I don't want to seem pedantic by quoting the definition, it just seemed a little funny, as Xmms is just the opposite : it is still wanted (by me at least) but it doesn't work :o

Xmms was once a stable piece of software, and was the most widely used music player on GNU. Now, as you say, it has grown old, *very old* and has developed a serious case of bit rot. However, for the time being, many of the alternatives are young, very young, and have not yet become as stable as Xmms once was. In fact, they are so young they are not included in Ubuntu !

Xmms still has a wide user base, as far as I can see. On the Ubuntu side of things, if the package is there, it should work - it would be just ridiculous to say "package X is in Ubuntu, but it doesn't work, use missing package Y instead".  If something has fallen into disuse, and maintenance has become too 'expensive' a policy should be adopted to depreciate it. Leaving broken things hanging around is *not good*.

I'm sorry, I could rant on for pages about this... There are many many more reasons I feel this is a bad situation. I'll find a solution, but things just should not be so complicated. What really bugs me in all this is that it makes me wonder how I will get people to use Ubuntu if they don't have a music player that "Just works". I understand that defending Ubuntu in the face of harsh criticism (and there is a lot about) is important, but it should not entail complacency.

Love, Karderio.

[edit]
As a matter of interest, to solve this mess, I downloaded and compiled 3 packages : audacious, audacious-plugins and taglib. Just try and tell your grandma that that is what she should do to listen to her music - she'll be having you fish the gramophone out of the dumpster !

Audacious seems to work ok, the interface is simply awful however.
[/edit]

Obsolete in three ways:

1. Obsolete as in that the dependancies are not even updated anymore

2. Obsolete as it is depending on a technology that is not developed anymore

3. The application has forked and is not developed anymore.


Use something current instead even though you can make it work, that doesn't make it anywhere near good, if an exploit is found, it will not be patched.

IOW, you run that, Ubuntu has cleared it's hands about anything security wise.

---

### Post by Bezmotivnik on 2006-11-27
I've **never** been able to get xmms properly working in *any* version of Ubuntu.

Why?  I dunno.  Don't care.  I always manage to get BMP up and it works for what I need and I don't have to think about it again.

---

### Post by Kristen Lucas on 2006-11-27
> **Bezmotivnik said:**
> I've **never** been able to get xmms properly working in *any* version of Ubuntu.

Why?  I dunno.  Don't care.  I always manage to get BMP up and it works for what I need and I don't have to think about it again.

It's very old, that's why.

GTK1 development stopped a long time ago.

BMP is a nice replacement, if you want a real application for your music there is Amakok.

---

### Post by BuffaloX on 2006-11-27
XMMS is working fine here, (Edgy)
but if it's a font problem, I installed some fonts I saw when searching something else, which I don't remember.
Saw this font package and grabbed that too.

XMMS was forked to BMP, which are both discontinued.
BMP development is now with Audacity and BmpX.
BmpX does not have XMMS compatibility. Because they wanted to do something new.
Both Audacity and BmpX supports BMP plugins.
BmpX even has Ubuntu repositories. :) 
They are maintained by the devs, so they should be pretty up to date. But they are only for edgy.

---

### Post by karderio on 2006-11-28
> **Kristen Lucas said:**
> Xmms is based on GTK1, it's obsolete, use BMP or rather Amarok.

> **Kristen Lucas said:**
> Obsolete in three ways:

1. Obsolete as in that the dependancies are not even updated anymore

2. Obsolete as it is depending on a technology that is not developed anymore

3. The application has forked and is not developed anymore.


Use something current instead even though you can make it work, that doesn't make it anywhere near good, if an exploit is found, it will not be patched.

IOW, you run that, Ubuntu has cleared it's hands about anything security wise.

You seem to be completely missing my point.

If you, or anybody else, has a suggestion for a *stable*, **GNOME based** music player, I'm still interested :o)

Love, Karderio.

---

### Post by fuscia on 2006-11-28
never knew beep was a gtk2 version of xmms. xmms has always been my first choice for music (i just need it to play music, not shovel my driveway in a blizzard). the preference menu is ugly as hell in xmms, but nice in bmp. thanks for clueing me in.

i can't see how anyone could find the almond or ater skins ugly, but i guess that's a matter of subjectivity.

xmms is about as obsolete as the AK-47.

---

### Post by eggy1962 on 2006-12-17
hello i'd like to ask a question re xmms, recently in ubuntu 6.06 xmms started to cause lockups on my pc, i was using xmms as part of streamtuner where i listen to shoutcast network radio, since switching to ubuntu 6.10 it seems to be working again even tho its same version of xmms.
Should i have further problems is there a suitable replacement audio program that will allow me to access  shoutcast radio?

---

### Post by BoyOfDestiny on 2006-12-17
> **karderio said:**
> I'm not sure you could call Xmms "obsolete". "Obsolescence is a state of being which occurs when a person, object, or service is no longer wanted, even though it may still be in good working order." I don't want to seem pedantic by quoting the definition, it just seemed a little funny, as Xmms is just the opposite : it is still wanted (by me at least) but it doesn't work :o

Xmms was once a stable piece of software, and was the most widely used music player on GNU. Now, as you say, it has grown old, *very old* and has developed a serious case of bit rot. However, for the time being, many of the alternatives are young, very young, and have not yet become as stable as Xmms once was. In fact, they are so young they are not included in Ubuntu !

Xmms still has a wide user base, as far as I can see. On the Ubuntu side of things, if the package is there, it should work - it would be just ridiculous to say "package X is in Ubuntu, but it doesn't work, use missing package Y instead".  If something has fallen into disuse, and maintenance has become too 'expensive' a policy should be adopted to depreciate it. Leaving broken things hanging around is *not good*.

I'm sorry, I could rant on for pages about this... There are many many more reasons I feel this is a bad situation. I'll find a solution, but things just should not be so complicated. What really bugs me in all this is that it makes me wonder how I will get people to use Ubuntu if they don't have a music player that "Just works". I understand that defending Ubuntu in the face of harsh criticism (and there is a lot about) is important, but it should not entail complacency.

Love, Karderio.

[edit]
As a matter of interest, to solve this mess, I downloaded and compiled 3 packages : audacious, audacious-plugins and taglib. Just try and tell your grandma that that is what she should do to listen to her music - she'll be having you fish the gramophone out of the dumpster !

Audacious seems to work ok, the interface is simply awful however.
[/edit]

[edit]
"Audacious seems to work ok" Strike that - Audacious crashes randomly, pfff...
[/edit]

Sorry it crashes for you, it's been solid as a rock for me. Version 1.2.5 for plugins and 1.2.2 for the main package? Also, libtagc0-dev is in the repos, dunno why you compiled it... 

Audacious 1.3 is in the works, has a lot of fixes and new features...

[http://audacious-media-player.org/1.3_Release](http://audacious-media-player.org/1.3_Release)

I say give it a try when it comes out... if it still crashes for you, file a bug report. Complaining in the forums here isn't going to fix it. 

Also, they are now hosting ubuntu debs, maybe try that instead of the one you compiled (sorry, just at a loss why it's not stable for you...)

[http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads)

deb [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main
deb-src [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main

Easier than compiling, but it won't be ready for "grandma" unless it's in Ubuntu's Add/Remove I guess... (EDIT: Ok I checked, it is in the ubuntu feisty fawn repos)

As for the interface, what didn't you like? It seems quite clear to me...

It can use winamp 2.x skins just as xmms can... Not to mention you can choose the option for the xmms file selector... Are you just nostalgic for GTK1?

Anyway, go to their channel or message boards and file a request if it bothers you that much...

P.S. Screenshot of interface: 
Anyway, things are a little darker due to my theme, rest assured it will look just like your other gtk2 apps...

[[IMG]http://img170.imageshack.us/img170/7677/audacious122lr3.th.png[/IMG]](http://img170.imageshack.us/my.php?image=audacious122lr3.png)

I guess to each his own, but well it's my favorite player. I'm loyal to it just for the built in console plugins. ;) It is based on bmp, which is based on xmms. It's just aims to be a great music player
and is actively developed, unlike the 2 it's based on... Also, it runs great on amd64 boxen... I had loads of trouble with xmms plugins back with hoary/breezy 64...

---

### Post by patrick295767 on 2006-12-17
> **BoyOfDestiny said:**
> Sorry it crashes for you, it's been solid as a rock for me. Version 1.2.5 for plugins and 1.2.2 for the main package? Also, libtagc0-dev is in the repos, dunno why you compiled it... 

Audacious 1.3 is in the works, has a lot of fixes and new features...

[http://audacious-media-player.org/1.3_Release](http://audacious-media-player.org/1.3_Release)

I say give it a try when it comes out... if it still crashes for you, file a bug report. Complaining in the forums here isn't going to fix it. 

Also, they are now hosting ubuntu debs, maybe try that instead of the one you compiled (sorry, just at a loss why it's not stable for you...)

[http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads)

deb [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main
deb-src [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main

Easier than compiling, but it won't be ready for "grandma" unless it's in Ubuntu's Add/Remove I guess... (EDIT: Ok I checked, it is in the ubuntu feisty fawn repos)

As for the interface, what didn't you like? It seems quite clear to me...

It can use winamp 2.x skins just as xmms can... Not to mention you can choose the option for the xmms file selector... Are you just nostalgic for GTK1?

Anyway, go to their channel or message boards and file a request if it bothers you that much...

P.S. Screenshot of interface: 
Anyway, things are a little darker due to my theme, rest assured it will look just like your other gtk2 apps...

[[IMG]http://img170.imageshack.us/img170/7677/audacious122lr3.th.png[/IMG]](http://img170.imageshack.us/my.php?image=audacious122lr3.png)

I guess to each his own, but well it's my favorite player. I'm loyal to it just for the built in console plugins. ;) It is based on bmp, which is based on xmms. It's just aims to be a great music player
and is actively developed, unlike the 2 it's based on... Also, it runs great on amd64 boxen... I had loads of trouble with xmms plugins back with hoary/breezy 64...


This is cool inforamtion > It can use winamp 2.x skins just as xmms can... Not to mention you can choose the option for the xmms file selector... Are you just nostalgic for GTK1?
great the skin compatiblity of audacious with M$ apps winamp !

---

### Post by karderio on 2006-12-17
> **BoyOfDestiny said:**
> Sorry it crashes for you, it's been solid as a rock for me. Version 1.2.5 for plugins and 1.2.2 for the main package?

Yes, those are the versions I used.

>  Also, libtagc0-dev is in the repos, dunno why you compiled it... 

Because I didn't check of course ;) My mistake.

> I say give it a try when it comes out... if it still crashes for you, file a bug report. Complaining in the forums here isn't going to fix it. 

I am quite aware of that fact, thank you. I was discussing XMMS, it was suggested I try Audacious, which I did, and I was simply reporting on my experience, not complaining.

> Also, they are now hosting ubuntu debs, maybe try that instead of the one you compiled (sorry, just at a loss why it's not stable for you...)

The links to the debs were broken the day I tried. I persisted a little with Audacious, it seemed very unstable to me, crashing with many of my tracks, sometimes refusing to open. I have abandoned it now.

This thread was about problems with XMMS, and I came here in the hope of getting XMMS working again. XMMS is mature, so much so that some consider it obsolete. I want a mature and tested media player. I hate my music keep cutting in the middle.

I do as much work as I can on free software, I already file bugs for much of it and submit patches where can, plus the projects I hack on. I do not want to have even more work, plus the frustration of music cutting off, when I had a player that worked fine until the Edgy update broke it.

> As for the interface, what didn't you like? 

 * I cannot resize it, even in "double" it is too small at my resolution.

 * The tiny buttons with just a letter on them. I don't want to seem to be insulting anybody, but this seems just plain stupid. They are too small, do not even look like buttons and what they do is anybodies guess, they don't even have a tooltip.

 * The entire interface, aside from playback, is hidden behind these buttons and a "right click", I want a player that shows me it's interface rather than hiding it. Terrible for consistency with other apps.

 * Accessibility ?

 * Does not integrate with my desktop. The sliders are too small, they do not behave like GTK+ sliders, I can move only the volume slider with the mouse wheel...

There are many many more issues with it, i think to improve usability they would have to abandon the winamp skins...

> It can use winamp 2.x skins just as XMMS can... Not to mention you can choose the option for the XMMS file selector... Or are you just nostalgic for GTK1?

No, XMMS's interface is far worse.

> Anyway, go to their channel or message boards and file a request?

I'd rather have something that just works. The design, interface wise, just seems so terrible that unless they want to redo it, my advice would not be useful. I know they must have their reasons, ie Winamp skin compatibility etc. but this is not at all something I personally consider an essential feature. I may seem to be hard on Audacious, but I have designed many user interfaces as part of my past jobs and I certainly wouldn't have been proud of such a design.

> and is actively developed, unlike the 2 it's based on...

Yes, a great advantage. XMMS has many faults also, but it worked for what I wanted.

I must seem to be very hard on Audacious, but I'm a very demanding person in these matters, that's partly why I use and contribute to free software. I admit I'm also not in the best of moods while writing this, sorry ;)

I realize Audacious may work fine for some, but it is inconceivable that a young software project this complex will work fine right away. Apart from the user interface issues it may be a fine project.

I'm wondering if I may be asking for advice in the wrong place, I should have filed a bug instead of coming here, but I just wanted to casually see if I was overlooking something. (I will now file a bug)

I think what is bugging me most about this is that I'm ashamed that there is no simple free software music play that just works, I find this rather disturbing. Lacking advice, when I get round to it I will do a survey of current players for Ubuntu/GNOME.

Hope I don't seem too pugnacious and haven't digressed too much.

Love, Karderio.

---

### Post by darkhatter on 2006-12-17
can't believe no ones recommended amarok yet. I think you should compile xmms from source if your having problems.

---

### Post by BoyOfDestiny on 2006-12-18
> **karderio said:**
> Yes, those are the versions I used.



Because I didn't check of course ;) My mistake.



I am quite aware of that fact, thank you. I was discussing XMMS, it was suggested I try Audacious, which I did, and I was simply reporting on my experience, not complaining.



The links to the debs were broken the day I tried. I persisted a little with Audacious, it seemed very unstable to me, crashing with many of my tracks, sometimes refusing to open. I have abandoned it now.

This thread was about problems with XMMS, and I came here in the hope of getting XMMS working again. XMMS is mature, so much so that some consider it obsolete. I want a mature and tested media player. I hate my music keep cutting in the middle.

I do as much work as I can on free software, I already file bugs for much of it and submit patches where can, plus the projects I hack on. I do not want to have even more work, plus the frustration of music cutting off, when I had a player that worked fine until the Edgy update broke it.



 * I cannot resize it, even in "double" it is too small at my resolution.

 * The tiny buttons with just a letter on them. I don't want to seem to be insulting anybody, but this seems just plain stupid. They are too small, do not even look like buttons and what they do is anybodies guess, they don't even have a tooltip.

 * The entire interface, aside from playback, is hidden behind these buttons and a "right click", I want a player that shows me it's interface rather than hiding it. Terrible for consistency with other apps.

 * Accessibility ?

 * Does not integrate with my desktop. The sliders are too small, they do not behave like GTK+ sliders, I can move only the volume slider with the mouse wheel...

There are many many more issues with it, i think to improve usability they would have to abandon the winamp skins...



No, XMMS's interface is far worse.



I'd rather have something that just works. The design, interface wise, just seems so terrible that unless they want to redo it, my advice would not be useful. I know they must have their reasons, ie Winamp skin compatibility etc. but this is not at all something I personally consider an essential feature. I may seem to be hard on Audacious, but I have designed many user interfaces as part of my past jobs and I certainly wouldn't have been proud of such a design.



Yes, a great advantage. XMMS has many faults also, but it worked for what I wanted.

I must seem to be very hard on Audacious, but I'm a very demanding person in these matters, that's partly why I use and contribute to free software. I admit I'm also not in the best of moods while writing this, sorry ;)

I realize Audacious may work fine for some, but it is inconceivable that a young software project this complex will work fine right away. Apart from the user interface issues it may be a fine project.

I'm wondering if I may be asking for advice in the wrong place, I should have filed a bug instead of coming here, but I just wanted to casually see if I was overlooking something. (I will now file a bug)

I think what is bugging me most about this is that I'm ashamed that there is no simple free software music play that just works, I find this rather disturbing. Lacking advice, when I get round to it I will do a survey of current players for Ubuntu/GNOME.

Hope I don't seem too pugnacious and haven't digressed too much.

Love, Karderio.

Well I hope you find a player that suits you. I'm sorry if I seemed a bit harsh too. :)

Hopefully your concerns will be addressed. I've found things to just get better and better when it comes to free software. It does take time... Hopefully the next release will be a big step up from what you got out of it... At least where you'd be comfortable recommending it.

Heck, I had trouble installing Linux a few years back. Most little issues I've had, they just start disappearing as the software improves...

Anyway, I think the issues you brought up (especially accessibility) are worth mentioning, and as for the interface, there is a "headless" mode, so I wouldn't be surprised if even a web style interface shows up...

---

### Post by BoyOfDestiny on 2006-12-18
> **patrick295767 said:**
> This is cool inforamtion 
great the skin compatiblity of audacious with M$ apps winamp !

MS didn't make winamp nor do they own it.

Ok ok... Still not a "great feature"... Some do prefer that simple layout though... :) That's all I meant by it...

---

### Post by eggy1962 on 2006-12-18
i gather then from lack of response to my question that there is no susbstitute if xmms plays me up again? does amorak allow shoutcast network radio?

---

### Post by OffHand on 2006-12-18
> **eggy1962 said:**
> i gather then from lack of response to my question that there is no susbstitute if xmms plays me up again? does amorak allow shoutcast network radio?

There is and people have suggested it: Audacious

---

### Post by eggy1962 on 2006-12-18
apologies that is one i was not aware of, i had heard of amorak

---

### Post by spockrock on 2006-12-19
yeah I used amarok stoped, to find something thats like it for gnome, and bah, nothing comes close, so I am still using amarok happily.

---

### Post by f3r0zzz on 2006-12-26
Here is the answer (and solution)

[https://launchpad.net/distros/ubuntu/+source/gtk+1.2/+bug/65708]("https://launchpad.net/distros/ubuntu/+source/gtk+1.2/+bug/65708")

is not just xmms but audacity, nero and other gtk1 based applications.

Hope it works.

---

### Post by MikeDK on 2007-01-08
hi if its the skin problem in xmms then just go to home-folder show the hidden files in home folder and open .xmms-folder ther u have skin and plugin-folders just copy or cut the skin-files to the skin folder and ur good to go

Best regards MikeDK

BTW Happy New Year

---

