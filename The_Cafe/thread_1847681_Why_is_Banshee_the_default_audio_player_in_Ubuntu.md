---
title: "Why is Banshee the default audio player in Ubuntu?"
date: 2011-09-21
forum: The Cafe
---

### Post by hzFVOW00pw on 2011-09-21
I have been using Banshee for some weeks now, instead of Rhythmbox. It has some serious and very obvious issues, and that is why I don't understand why this is now the default player in Ubuntu. Do they ever test the applications before committing them?

- There is no easy way to play files from the filesystem without adding them to the library. You have to open Nautilus and right click on the files.

- Re-reading the library crashes Banshee over and over again. Sometimes I have to re-read the library over 10 times.

- Re-reading the library does not reflect changes in the tags. for instance, I first played some files from the filesyetem adding them to the filesystem-queue. Later I moved the files to my collection directory and changed some tags. Then I re-read the library (importing the files to my collection) but the tag changes were not there.

- Banshee does not read diacritical or foreign characters (i.e. Greek). All it reads from such tags is garbage, making it impossible to find what you are looking for.

A big thumbs down for Banshee, I will revert to Rhythmbox.

---

### Post by nothingspecial on 2011-09-21
Moved to Testimonials & Experiences since it is not a support question.

---

### Post by Lars Noodén on 2011-09-21
@nothingspecial : what steps need to be taken to revert Ubuntu to a better default audio player?  There is still time before 11.10 to get a good audio player in place of Banshee.

---

### Post by regala on 2011-09-21
> **Lars Noodén said:**
> @nothingspecial : what steps need to be taken to revert Ubuntu to a better default audio player?  There is still time before 11.10 to get a good audio player in place of Banshee.

any suggestion ? Rhythmbox is not, unless you don't mind taking over the project, maintain it *upstream*: it's been dead pour quite a time now (because it is even utterer crap than banshee)

---

### Post by mörgæs on 2011-09-21
Why do you people focus so much on what is default? Linux is about choice - there are lots of media players to choose from. VLC for example.

---

### Post by Lars Noodén on 2011-09-21
> **mörgæs said:**
> Why do you people focus so much on what is default? Linux is about choice - there are lots of media players to choose from. VLC for example.

Because most people stick with the default.  It's also easier if the default is good so that it's less necessary to go to the "effort" of uninstalling it or installing an alternative.  Defaults matter a lot.

---

### Post by cbowman57 on 2011-09-21
My (current) favorite is Clementine, it only has one bug that irritates me, but it's rather minor.  As others have already stated, it's a simple process to replace default software.

In response to the initial question though, it is my understanding that Banshee is actively developed and they have made an effort to integrate it with Ubuntu One.

---

### Post by sffvba[e0rt on 2011-09-21
YMMV - For every media player that could be used as default there will be users that love it, and users that hate it.

I use Banshee and have had no issues with it as an example.


404

---

### Post by Lars Noodén on 2011-09-21
> **not found said:**
> YMMV - For every media player that could be used as default there will be users that love it, and users that hate it.


There are also characteristics which go beyond personal preferences: Freedom and Quality.  It is also inappropriate to use Banshee  for any default because of its use of Mono.

[http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono)
[http://techrights.org/2008/03/24/mono-danger-to-linux/](http://techrights.org/2008/03/24/mono-danger-to-linux/)

---

### Post by madjr on 2011-09-21
> **Lars Noodén said:**
> There are also characteristics which go beyond personal preferences: Freedom and Quality.  It is also inappropriate to use Banshee  for any default because of its use of Mono.

[http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono)
[http://techrights.org/2008/03/24/mono-danger-to-linux/](http://techrights.org/2008/03/24/mono-danger-to-linux/)

oh, please try not to bring up the mono thing as always.

Banshee is not the only mono app in ubuntu. And if the FUD ever becomes reality (which will probably not), there are dozens of other good music players in linux already to take its place or port the code to something else.

but meanwhile Banshee is actively developed and maintained at the moment, easy to use and has lots of features, so clearly is the best alternative as default since it brings tons of fixes with each release and cuts down the bug reports fast.

And for the @OP: am not sure i had that problem (what version are you using?); also submitting bug reports would help instead of wasting energy ranting in the forums. Ranting here is not going to change it as default, nor improve it, bug reports do.

---

### Post by Lars Noodén on 2011-09-21
> **madjr said:**
> 

Banshee is not the only mono app in ubuntu..
That's also a problem.

---

### Post by hzFVOW00pw on 2011-09-21
> **madjr said:**
> And for the @OP: am not sure i had that problem (what version are you using?); also submitting bug reports would help instead of wasting energy ranting in the forums. Ranting here is not going to change it as default, nor improve it, bug reports do.

I run version 2.0.1 from the PPA on Lucid and believe me, the issues are there. I am really tired of sending bug reports, I have done that for 13 years now on Mandriva and Ubuntu and even helped develop the former. There comes a time that things should just work.

If Rhythmbox is not actively developed there's a need for another player, but not until it is stable. I hate being used as an alpha tester everytime I upgrade my distro.

---

### Post by hzFVOW00pw on 2011-09-21
> **cbowman57 said:**
> In response to the initial question though, it is my understanding that Banshee is actively developed and they have made an effort to integrate it with Ubuntu One.

So it's a commercial descision?

---

### Post by zekopeko on 2011-09-21
> **Lars Noodén said:**
> There are also characteristics which go beyond personal preferences: Freedom and Quality.  It is also inappropriate to use Banshee  for any default because of its use of Mono.

Thankfully Banshee has ample "Freedom and Quality".

> [http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono)
[http://techrights.org/2008/03/24/mono-danger-to-linux/](http://techrights.org/2008/03/24/mono-danger-to-linux/)

EDIT: Do not butcher my comment please. My (removed) point stands. Anyone using techrights aka boycottnovell as a support for their argument should invest some time and money into improving their critical thinking skills. That site exists for the sole reason of promoting an agenda without any care for fact or reason.

---

### Post by zekopeko on 2011-09-21
> **maxibuntu said:**
> So it's a commercial descision?

No. It was a community decision made at a past UDS.

---

### Post by hzFVOW00pw on 2011-09-21
> **mörgæs said:**
> Why do you people focus so much on what is default? Linux is about choice - there are lots of media players to choose from. VLC for example.

VLC doesn't have a library or does it?

---

### Post by madjr on 2011-09-21
> **maxibuntu said:**
> I run version 2.0.1 from the PPA on Lucid and believe me, the issues are there. I am really tired of sending bug reports, I have done that for 13 years now on Mandriva and Ubuntu and even helped develop the former. There comes a time that things should just work.

If Rhythmbox is not actively developed there's a need for another player, but not until it is stable. I hate being used as an alpha tester everytime I upgrade my distro.

well you were ranting about the defaults.

if the issue is so big that it cant be resolved (or is marked as a "no-fix" bug), then i agree with you on changing the default.

and you're still running Lucid which has Rhythmbox by default, so how is that alpha testing?

And as for bug reports, your OP is essentially a bug report. You just did so on the forums because is faster to do so, but unfortunately the devs dont read the forums.

and bug reporting has become a lot easier and automated, is just a matter of typing in.

```
ubuntu-bug banshee
```

Like said, the devs are friendly, active and open to suggestions.

and if you dont feel like doing so, thats ok, but then there was no reason in opening this thread either in the first place.

If its too much hassle then just do what non tech users do and swap app.

---

### Post by hzFVOW00pw on 2011-09-21
> **cbowman57 said:**
> My (current) favorite is Clementine, it only has one bug that irritates me, but it's rather minor.  As others have already stated, it's a simple process to replace default software.

Well thank you so much! I had to enable backports in Lucid and installed Clementine and seems to be just what I was looking for. A no-frills player which loads its database very fast and with easy acces to folders on the filesystem. Curious what bug you are referring to though...

---

### Post by hzFVOW00pw on 2011-09-21
> **madjr said:**
> 
```
ubuntu-bug banshee
```


ubuntu-bug banshee comes up with:

---
*** Probleem in banshee
Het probleem kan niet worden gerapporteerd:
Dit is geen authentiek Ubuntu-pakket.
---

Roughly translates to:

*** Problem in banshee
The problem can't be reported:
Not an authentic Ubuntu-package.

(Package comes from banshee PPA)

Ah well, forget it. I switched to Clementine for the time being... Seems to suit my needs. Let the other users alpha-test Banshee.

---

### Post by cbowman57 on 2011-09-21
> **maxibuntu said:**
> Well thank you so much! I had to enable backports in Lucid and installed Clementine and seems to be just what I was looking for. A no-frills player which loads its database very fast and with easy acces to folders on the filesystem. Curious what bug you are referring to though...

That's what I like about it, it seems quick &  a little less resource intensive while retaining the features I find to be most useful.  It doesn't do everything that Banshee does but works for me.

The bug, when you quit it sometimes starts eating up CPU cycles.  A lot of people probably just minimize their music player anyway so they never notice it.  Easy enough to kill using the system monitor or any number of other methods.

---

### Post by Ms_Angel_D on 2011-09-21
Since this isn't actually a testimonial and we're trying to keep debate out of that section I've moved this thread to the cafe to avoid closing it.

OP you could always suggest a different default player at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by madjr on 2011-09-21
> **maxibuntu said:**
> ubuntu-bug banshee comes up with:

---
*** Probleem in banshee
Het probleem kan niet worden gerapporteerd:
Dit is geen authentiek Ubuntu-pakket.
---

Roughly translates to:

*** Problem in banshee
The problem can't be reported:
Not an authentic Ubuntu-package.

(Package comes from banshee PPA)

Ah well, forget it. I switched to Clementine for the time being... Seems to suit my needs. Let the other users alpha-test Banshee.

ok, seems doesnt work with ppas. Whenever you upgrade to 11.04, 11.10 or 12.04 you can report without problem (if the issue is not already fixed by then of course). Or just do so from launchpad.

Not sure if this might be only a lucid problem...

anyway clementine is a good player.

---

### Post by lordyosch on 2011-09-21
FWIW I've always liked Banshee since I 'went linux' a few years back. Much better than Rhythmbox.

I liked the way it could sync to my android phone and I can use my phone as a remote for it.


Jay

---

### Post by Erik1984 on 2011-09-21
> **mörgæs said:**
> Why do you people focus so much on what is default? Linux is about choice - there are lots of media players to choose from. VLC for example.

De default set of applications is in some way the 'business card' of Ubuntu. It's what Canonical (or at least the people in charge of the package selection) thinks you need for your basic desktop computing tasks. I like Banshee because of it's appearance, versatility and ability to retrieve album covers. However it crashes every few hours it seems. I can live with it, but also imagine it does not provide a good first impression for new users if their music player crashes.

---

### Post by Dyzphagia on 2011-09-21
Personally I like Banshee. Rhythmbox was the one I didn't like. For tagging I used Musicbrainz. Easy to fix all the little tagging errors and Banshee seems to read them right. I also don't understand what you mean by not having an easy way to play or place into library. Did you mean it takes forever to place them in a library? Or that you can't just hover over the file and play it? Really, Banshee is one of those players that has a few things it needs to have fixed, but the people using it now just seem to enjoy it more than others.  But hey, an opinion is an opinion

---

### Post by dniMretsaM on 2011-09-21
> **maxibuntu said:**
> - There is no easy way to play files from the filesystem without adding them to the library. You have to open Nautilus and right click on the files.

Doesn't Media -> Open Location... do this?

> **maxibuntu said:**
> - Re-reading the library crashes Banshee over and over again. Sometimes I have to re-read the library over 10 times.

Never had a problem with this. Ever. Used it on Ubuntu 10.10/11.04 and Kubuntu 11.04/

> **maxibuntu said:**
> - Re-reading the library does not reflect changes in the tags. for instance, I first played some files from the filesyetem adding them to the filesystem-queue. Later I moved the files to my collection directory and changed some tags. Then I re-read the library (importing the files to my collection) but the tag changes were not there.

Works for me (except maybe cover art sometimes).

> **maxibuntu said:**
> - Banshee does not read diacritical or foreign characters (i.e. Greek). All it reads from such tags is garbage, making it impossible to find what you are looking for.

Do most people use foreign characters in the names of their music files? I know I never have. You might try asking the Banshee dev team to implement support for this. Complaining will get you nowhere, asking/suggesting will get you everywhere. Anyway, just because one person has a bad time with an application (in this case, you) doesn't mean the application is horrible. Some people like it a lot and have really good experiences (in this case, me). Could i be improved? Sure, but what program can't? And something worth pointing out, the glitch with it crashing while reading your library could be solved in a later version if your using a version << 2.14. Make sure you have the latest version from the [daily PPA]("https://launchpad.net/%7Ebanshee-team/+archive/banshee-daily").

---

### Post by madjr on 2011-09-21
Banshee 2.2 Released:

[http://www.omgubuntu.co.uk/2011/09/banshe-2-2-released](http://www.omgubuntu.co.uk/2011/09/banshe-2-2-released)

---

### Post by dniMretsaM on 2011-09-21
> **madjr said:**
> Banshee 2.2 Released:

[http://www.omgubuntu.co.uk/2011/09/banshe-2-2-released](http://www.omgubuntu.co.uk/2011/09/banshe-2-2-released)

Oh cool! I wonder when I'll get the next update in the Daily PPA.

---

### Post by Copper Bezel on 2011-09-21
I understand that Ubuntu can't really ship with a default player that's no longer under development, but can someone chip in with some specifics about what was wrong with Rhythmbox? There's a lot of vague negativity about it, but I don't know the specific issues, and I've always found it to be quite an ideal player for my purposes. I have minor nitpicks with Banshee, and they're practically interchangeable otherwise - my biggest beef with Banshee is that the interface simply takes up too much screen space for my preference. That said, I don't know any of the specific complaints about Rhythmbox, so I'm curious to know what's so very terrible about it.

---

### Post by Gremlinzzz on 2011-09-21
> **maxibuntu said:**
> I have been using Banshee for some weeks now, instead of Rhythmbox. It has some serious and very obvious issues, and that is why I don't understand why this is now the default player in Ubuntu. Do they ever test the applications before committing them?

- There is no easy way to play files from the filesystem without adding them to the library. You have to open Nautilus and right click on the files.

- Re-reading the library crashes Banshee over and over again. Sometimes I have to re-read the library over 10 times.

- Re-reading the library does not reflect changes in the tags. for instance, I first played some files from the filesyetem adding them to the filesystem-queue. Later I moved the files to my collection directory and changed some tags. Then I re-read the library (importing the files to my collection) but the tag changes were not there.

- Banshee does not read diacritical or foreign characters (i.e. Greek). All it reads from such tags is garbage, making it impossible to find what you are looking for.

A big thumbs down for Banshee, I will revert to Rhythmbox.
 Because they had to choose one for those who cant choose for themselves.:popcorn:

---

### Post by madjr on 2011-09-21
> **Copper Bezel said:**
> I understand that Ubuntu can't really ship with a default player that's no longer under development, but can someone chip in with some specifics about what was wrong with Rhythmbox? There's a lot of vague negativity about it, but I don't know the specific issues, and I've always found it to be quite an ideal player for my purposes. I have minor nitpicks with Banshee, and they're practically interchangeable otherwise - my biggest beef with Banshee is that the interface simply takes up too much screen space for my preference. That said, I don't know any of the specific complaints about Rhythmbox, so I'm curious to know what's so very terrible about it.

it all has been covered on various websites and you can check the UDS logs.

it was voted with pros/cons (inactive development was only one of the cons, but is a big one), just like now **thunderbird** has been voted to replace evolution, again specifying all the pros/cons,  usability tests and support from upstream.

Also it seems the majority of users (not all of course) were also happy with the decisions.

---

### Post by Copper Bezel on 2011-09-21
[QUOTE=madjr]it all has been covered on various websites and you can check the UDS logs.[/QUOTE]
My Google-fu is apparently nonexistent. Where in the summit logs is this discussed? (Any general web search I try ends up looping back to someone reporting on, or complaining about, the change. I've encountered the word "mono" more times in the last half-hour than I did in living in a dormitory for two years.)

---

### Post by castrojo on 2011-09-21
> **Copper Bezel said:**
> My Google-fu is apparently nonexistent. Where in the summit logs is this discussed?

[http://askubuntu.com/questions/10911/why-is-banshee-becoming-the-default/10963#10963](http://askubuntu.com/questions/10911/why-is-banshee-becoming-the-default/10963#10963)

---

### Post by screaminj3sus on 2011-09-21
> **Copper Bezel said:**
> I have minor nitpicks with Banshee, and they're practically interchangeable otherwise - my biggest beef with Banshee is that the interface simply takes up too much screen space for my preference.
I find it funny that that is your biggest beef with banshee, because rhythmbox wastes ridiculous amounts of screen space. I hate that you can't move the seekbar on to the top toolbar, it takes up way to much space as its own toolbar.


Personally I think purely as a player clementine would be better than both as default. But ubuntu seems to want a default player that is good at managing music, and also doing stuff like syncing to devices. In that regard banshee is probably a better choice

---

### Post by johnnybgoode83 on 2011-09-21
The only problem I have with Banshee is that on my laptop it's resource usage is far too high. Apart from that it is an excellent music manager.
 
There are so many other greats out there but my personal preference is Guayadeque because it has all the features I need and it's resource usage is still excellent.

---

### Post by Copper Bezel on 2011-09-21
castrojo - thanks so much! 

Edit - And they seem to be quite sensible and enlightening reasons, too, particularly since the extensibility, schedule, and developer base are major considerations that a user doesn't see just using the application. It doesn't quite explain the negativity toward Rhythmbox, which was my question, but I guess that that, like most UI issues, is fairly subjective stuff.

screaminj3sus - vertically, yes, Banshee is more compact, and it's certainly a more practical layout for the most part, particularly with the browser turned off.

Much later edit: I find myself answering my own questions, in any case. A bit of time with Banshee, and I start to realize that Rhythmbox's UI was fairly disjointed in ways I just took for granted. Banshee wins. = )

---

### Post by hzFVOW00pw on 2011-09-22
> **dniMretsaM said:**
> Doesn't Media -> Open Location... do this?

No. Then they are added to the libary.

> Never had a problem with this. Ever. Used it on Ubuntu 10.10/11.04 and Kubuntu 11.04/

On Lucid it takes about 10 times to refresh the db. It's a known issue.

> Works for me (except maybe cover art sometimes).

Correction: The tags refresh correctly, but not in the albums list above-right. When you want to play an album the songs are jumbled in the playlist when the artist name was changed from one thing to another.

For example if you have an album by artist "Pipo and the Clown" and five songs are tagged "Pipo and the Clown" and another five "Pipo & the Clown" and you then correct the tags for all ten files to "Pipo and the Clown" the album is shown as two different albums by two different artists and you cannot play the files in the right order from the playlist.

> Do most people use foreign characters in the names of their music files? I know I never have.

That's not the point. On a default player it should just work. Even for the occasional user. It works in Rhythmbox and Clementine. And I am wondering: if someone uses Greek language, for instance a Greek person, will he be unable to read the file tags?

> You might try asking the Banshee dev team to implement support for this.

Some years ago I had the same diacritic character issue in Amarok. I talked to the devs, filed bug reports, and after 2 years there was still no fix. I changed to Rhythmbox. I'm not going over that whole thing again with Banshee. This time I just changed to Clementine.

For instance, the crashing issue dates from 2007! and it is still not fixed! If it is never goin' to be fixed, who would want to file a bug report again?

[http://ubuntuforums.org/showthread.php?t=462031](http://ubuntuforums.org/showthread.php?t=462031)

> Complaining will get you nowhere, asking/suggesting will get you everywhere. Anyway, just because one person has a bad time with an application (in this case, you) doesn't mean the application is horrible

You're not reading clearly. It is not about one person. 3 out of the 4 issues are real bugs.

> And something worth pointing out, the glitch with it crashing while reading your library could be solved in a later version if your using a version << 2.14

That's also not the point. It has been made the default player already so it should not have such obvious issues. It should have been fixed *before* it was made the default.

---

### Post by dniMretsaM on 2011-09-22
> **maxibuntu said:**
> No. Then they are added to the libary.

Ok, I didn't know. I don't actually have any music that isn't part of my library, so no easy way to test it.

> **maxibuntu said:**
> On Lucid it takes about 10 times to refresh the db. It's a known issue.

Banshee is not the default player in 10.04, so this is really irrelevant to this discussion.

> **maxibuntu said:**
> That's not the point. On a default player it should just work. Even for the occasional user. It works in Rhythmbox and Clementine. And I am wondering: if someone uses Greek language, for instance a Greek person, will he be unable to read the file tags?

The Greek version of the program probably supports Greek letters.

---

### Post by Spice Weasel on 2011-09-22
So, remind me, is there any reason not to use Mono other than Microsoft paranoia?

---

### Post by hakermania on 2011-09-22
> **mörgæs said:**
> Why do you people focus so much on what is default? Linux is about choice - there are lots of media players to choose from. VLC for example.


[SIZE=4]_**[COLOR=Red]Exactly[/COLOR]**_[/SIZE][SIZE=4]_**[COLOR=Red]: [http://ubuntuforums.org/showthread.php?t=1833926](http://ubuntuforums.org/showthread.php?t=1833926)[/COLOR]**_[/SIZE]

---

### Post by mörgæs on 2011-09-22
[]("http://ubuntuforums.org/member.php?u=904179")Spice Weasel, your post have been removed. Please don't go off-topic.

---

### Post by Zlatan on 2011-09-22
Left to Kubuntu and could not be happier with Amarok. It (at least!) has a list of internet radio stations...

---

### Post by Copper Bezel on 2011-09-22
I don't understand this comment. Both Banshee and Rhythmbox support internet radio, and Rhythmbox comes with a selection of popular stations already listed.

---

### Post by BrokenKingpin on 2011-09-22
I have used Banshee as my main media player in the past, but I have switched away from it because it is just too slow and bloated.

Whatever the default music player in Xubuntu is seems to work fine for me, so I will stick with that.

---

### Post by speedwell68 on 2011-09-22
I am playing around with Listen at the moment.  It seems very good, does everything I expect of it.

---

### Post by SlackerD on 2011-09-22
> **Lars Noodén said:**
> There are also characteristics which go beyond personal preferences: Freedom and Quality.  It is also inappropriate to use Banshee  for any default because of its use of Mono.

[http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono)
[http://techrights.org/2008/03/24/mono-danger-to-linux/](http://techrights.org/2008/03/24/mono-danger-to-linux/)

And why is that, exactly?  Those links are just spouting FUD.

---

### Post by KiwiNZ on 2011-09-22
> **Lars Noodén said:**
> Because most people stick with the default.  It's also easier if the default is good so that it's less necessary to go to the "effort" of uninstalling it or installing an alternative.  Defaults matter a lot.

So users should not have the choice to stick with the default?

I think we should have no Media players , Browsers, Email Client, Script editor,Office Suite,Photo editor etc etc etc loaded at all because the selection of any one will cause issue to someone.:rolleyes:

---

### Post by aura7 on 2011-09-22
The apt question should be why did Ubuntu switched from Rhythmbox to Banshee

---

### Post by dniMretsaM on 2011-09-22
> **KiwiNZ said:**
> So users should not have the choice to stick with the default?

I think we should have no Media players , Browsers, Email Client, Script editor,Office Suite,Photo editor etc etc etc loaded at all because the selection of any one will cause issue to someone.:rolleyes:

Yeah that'll work. Then people will complain about having to install everything. But I get your point.

> **aura7 said:**
> The apt question should be why did Ubuntu switched from Rhythmbox to Banshee

For more information on that, click [here](http://askubuntu.com/questions/10911/why-is-banshee-becoming-the-default/10963#10963)

---

### Post by hzFVOW00pw on 2011-09-23
> Banshee is not the default player in 10.04, so this is really irrelevant to this discussion.

It's the default player in Natty is it? The bugs are still the same bugs.

> The Greek version of the program probably supports Greek letters.

Then let's hope the Greeks can read tags with western characters.

---

### Post by kaldor on 2011-09-23
> **maxibuntu said:**
> It's the default player in Natty is it? The bugs are still the same bugs.



Then let's hope the Greeks can read tags with western characters.

Maybe you should try to get involved with Banshee to help with translation. I know that isn't directly what you mean, but it could help.

---

### Post by directhex on 2011-09-23
> **maxibuntu said:**
> Then let's hope the Greeks can read tags with western characters.

Banshee supports foreign-language metadata on files FINE. I have plenty in my library in Japanese.

Perhaps the problem is with your metadata, e.g. using a faulty charset?

---

### Post by dniMretsaM on 2011-09-23
> **maxibuntu said:**
> It's the default player in Natty is it? The bugs are still the same bugs.

If the bugs don't affect a certain version of an operating system, it shouldn't (and doesn't) have any affect on whether or not it's chosen as the default for that version. To suggest it should be otherwise is, quite frankly, stupid. As for the character issue, have you checked the encoding of the characters? It's possible that's the problem. I would suggest following directhex's advice as well.

---

### Post by ufugu on 2011-09-23
To the original question, I don't get it either.  I've tried Banshee many times over the years.  It still can't scan my library without crashing, it still can't browse by genre, it still doesn't see my Android player. It doesn't matter which distro or computer I use it on, I experience the same issues. These appear to be common bugs (and bugs are filed for all these things).

Meanwhile, there are half a dozen excellent Linux music players available that do these things with zero problems, and some have even more features than Banshee.

I think it's great that they are working on what will someday be a sweet media player, but until then, I don't get why it's the default either.

I used to always remove Evolution first thing on a new install (which was not easy) and glad that's gone now.  It always promised a lot, but it could never deliver.  I feel the same way about Banshee.

---

### Post by cblnchat on 2011-09-23
I've always had a horrible time with Banshee.  When i first started Ubuntu i thot id install an audio player (for some reason my download didnt come with one 0.o) so i downloaded Rythmbox and Banshee.  Banshee couldnt find my music most of the time and when it could it would take 30 seconds or so to start playing it.  But i loove Rythmbox.  Never had any trouble with it, except for the fact that i cant change the names/artists etc of some songs.  But thats not a big deal.

---

### Post by hzFVOW00pw on 2011-09-24
> **dniMretsaM said:**
> If the bugs don't affect a certain version of an operating system, it shouldn't (and doesn't) have any affect on whether or not it's chosen as the default for that version. To suggest it should be otherwise is, quite frankly, stupid. As for the character issue, have you checked the encoding of the characters? It's possible that's the problem. I would suggest following directhex's advice as well.

There's nothing wrong with the encoding. As I said, the tags are fine in any other player/tagger (rhythmbox, clementine, easytag). I'm not looking into it anymore now because I uninstalled Banshee and will keep it that way.

---

### Post by debd on 2011-09-24
I've been using Clementine for a long time and I love it.
Also there's another project am looking forward to: [http://code.google.com/p/xnoise/](http://code.google.com/p/xnoise/)

> The bug, when you quit it sometimes starts eating up CPU cycles.  A lot  of people probably just minimize their music player anyway so they never  notice it.  Easy enough to kill using the system monitor or any number of other methods.that's not a bug. that's a feature. you can turn that off from the preferences.
Look in Tools > Preferences > Behaviour

---

### Post by vehemoth on 2011-09-24
> **debd said:**
> I've been using Clementine for a long time and I love it.


that's not a bug. that's a feature. you can turn that off from the preferences.
Look in Tools > Preferences > Behaviour
It is a great music player, though I had problems with it using up cpu cycles when trying to use it with conky. I'm assuming that there's not enough space to fit two music players on the cd.

---

### Post by Mr. Picklesworth on 2011-09-24
> **regala said:**
> any suggestion ? Rhythmbox is not, unless you don't mind taking over the project, maintain it *upstream*: it's been dead pour quite a time now (because it is even utterer crap than banshee)

Rhythmbox is not dead. It is still being actively maintained and a new version is shipped with every release of the GNOME desktop. If you need any evidence of that, notice that it recently gained a shiny new icon and 2.9x has been ported to GTK3.

---

### Post by Ric_NYC on 2011-09-24
There's no need to use it or other Mono stuff.
There are alternatives.

---

### Post by Copper Bezel on 2011-09-24
[QUOTE=debd]Also there's another project am looking forward to: [http://code.google.com/p/xnoise/](http://code.google.com/p/xnoise/)[/QUOTE]
xnoise looks nice, no question. I do use internet radio, however, and it doesn't look like xnoise covers that.

> that's not a bug. that's a feature. you can turn that off from the preferences.
Look in Tools > Preferences > Behaviour
One of the nicest things about Banshee. I've been trying it out due to this thread, and the fact that I can close it, with the little X button, like any other application? Pure gold.

---

### Post by dniMretsaM on 2011-09-24
> **Copper Bezel said:**
> xnoise looks nice, no question. I do use internet radio, however, and it doesn't look like xnoise covers that.


One of the nicest things about Banshee. I've been trying it out due to this thread, and the fact that I can close it, with the little X button, like any other application? Pure gold.

What music player can't you do this with?

---

### Post by Copper Bezel on 2011-09-24
Rhythmbox. There's no way to turn off the sound menu integration as there is in Banshee, so closing the window  while playing anything effectively "minimizes to tray."

I don't understand the utility of this behavior in any sense, so I'm glad to have the option to disable it.

---

### Post by dniMretsaM on 2011-09-24
> **Copper Bezel said:**
> Rhythmbox. There's no way to turn off the sound menu integration as there is in Banshee, so closing the window  while playing anything effectively "minimizes to tray."

Really? That's a little odd. I never really noticed that when I used it. I dislike it when programs do that (usually, there are a few exceptions). I think it should have an option for minimizing to the tray when you actually minimize it.

---

### Post by Copper Bezel on 2011-09-24
Yeah, I don't mind the option so long as it *is* an option, and I understand why the feature is there - it gets the music player out of the way but keeps the basic controls accessible in the panel.

---

### Post by debd on 2011-09-25
> Rhythmbox. There's no way to turn off the sound menu integration as  there is in Banshee, so closing the window  while playing anything  effectively "minimizes to tray."

nope. you can always end the (rhythmbox) process if you want to.
File > Quit  (AFAI remember)

---

### Post by Copper Bezel on 2011-09-25
[QUOTE=Me]with the little X button[/QUOTE]
I was talking about a very specific feature. The process also ends if you simply pause playback and then close the window.

---

### Post by cbowman57 on 2011-09-27
> **debd said:**
> I've been using Clementine for a long time and I love it.
Also there's another project am looking forward to: [http://code.google.com/p/xnoise/](http://code.google.com/p/xnoise/)

that's not a bug. that's a feature. you can turn that off from the preferences.
Look in Tools > Preferences > Behaviour

Eating up CPU cycles when you close it is a feature?  Who would request that as a feature?

---

### Post by aura7 on 2011-09-27
I am still waiting for a media player as good as iTunes in windows. Hope Apple starts making iTunes for linux too...

---

### Post by Jesus_Valdez on 2011-09-27
> **aura7 said:**
> I am still waiting for a media player as good as iTunes in windows. Hope Apple starts making iTunes for linux too...
wat

---

### Post by dniMretsaM on 2011-09-30
> **aura7 said:**
> I am still waiting for a media player as good as iTunes in windows. Hope Apple starts making iTunes for linux too...

I would like iTunes for Linux, but not because it's an excellent media player (it's actually really bad in my opinion). The reason I would like a Linux version of iTunes is because it's a great podcast manager and it works with my iPod Touch. But many many FLOSS media players are much better that iTunes. They play more formats, they uses fewer resources, and they're open source/free(dom) software.

---

### Post by checoimg on 2011-09-30
I think VLC would be fine.

---

### Post by dniMretsaM on 2011-10-01
> **checoimg said:**
> I think VLC would be fine.

VLC is great, but it doesn't have a library, it doesn't sync with devices, etc. I would be better suited for the default video player, but Canonical won't use it because of patent issues (which shouldn't be a problem since Canonical is based in the UK).

---

### Post by hzFVOW00pw on 2011-11-08
I just read that Banshee will most likely be replaced by Rhythmbox in 12.04.

[http://www.webupd8.org/2011/11/rhythmbox-might-replace-banshee-in.html](http://www.webupd8.org/2011/11/rhythmbox-might-replace-banshee-in.html)

---

### Post by shuttleworthwannabe on 2011-11-08
> **maxibuntu said:**
> I just read that Banshee will most likely be replaced by Rhythmbox in 12.04.

[http://www.webupd8.org/2011/11/rhythmbox-might-replace-banshee-in.html](http://www.webupd8.org/2011/11/rhythmbox-might-replace-banshee-in.html)

I also read this elsewhere; so no more banshee--but I just hope RB turns out to be more than just a player--Amarok type player.

---

### Post by Doc on 2011-11-18
I have to weigh in on this thread for those who might have the same problems I have. I have several thousand songs in my collection of multiple formats (mp3, ogg and flac). Since upgrading to 11.10 I have been less than satisfied with Banshee as the default player to say the least. Each time it starts it freezes for about a minute before being ready to play, and the system is unusable during that time. (I will give it credit for looking great once it does finally come around, but I need something that just works.) I switched to xnoise which does exactly what I need, for anyone interested in an alternative.

---

### Post by wolfen69 on 2011-11-19
I lost 35,000 songs recently. Oh well. Talk to me.

---

### Post by wolfen69 on 2011-11-19
> **Doc said:**
> I have to weigh in on this thread for those who might have the same problems I have. I have several thousand songs in my collection of multiple formats (mp3, ogg and flac). Since upgrading to 11.10 I have been less than satisfied with Banshee as the default player to say the least. Each time it starts it freezes for about a minute before being ready to play, and the system is unusable during that time. (I will give it credit for looking great once it does finally come around, but I need something that just works.) I switched to xnoise which does exactly what I need, for anyone interested in an alternative.

I've been "less than satisfied" by A LOT of things. Are you kidding me?

---

### Post by beew on 2011-11-19
I have to say I completely disagree with those who think VLC would be a good default player. Not that they will consider it, but if it does become the default player that would be a disaster,--for VLC.  Look, one of the best features of VLC is that it can play anything that you throw at it, that is because of its codecs. If it is included as the default they would have to strip the codecs and replace it with a crippled version. Why would I want that?

 VLC is one of those things that if you can't include it properly then it is better not to offer it at all, let the users  download it from ppas so they would get the fully functional version. If they include a half a**, crippled replica in the default offer many unsuspecting users would just think that Ubuntu is so crappy that even VLC stops working. I can imagine some new user just switched from Windows complaining "I used to be able to play anything in Windows with VLC, but in Ubuntu it doesn't work, so I am moving back to Windows"

---

### Post by hzFVOW00pw on 2011-11-19
> **beew said:**
> I have to say I completely disagree with those who think VLC would be a good default player. Not that they will consider it, but if it does become the default player that would be a disaster,--for VLC.  Look, one of the best features of VLC is that it can play anything that you throw at it, that is because of its codecs. If it is included as the default they would have to strip the codecs and replace it with a crippled version. Why would I want that?

 VLC is one of those things that if you can't include it properly then it is better not to offer it at all, let the users  download it from ppas so they would get the fully functional version. If they include a half a**, crippled replica in the default offer many unsuspecting users would just think that Ubuntu is so crappy that even VLC stops working. I can imagine some new user just switched from Windows complaining "I used to be able to play anything in Windows with VLC, but in Ubuntu it doesn't work, so I am moving back to Windows"

Don't worry, VLC will never be the default player. It doesn't even have a library.

---

### Post by tartalo on 2011-11-19
> **aura7 said:**
> I am still waiting for a media player as good as iTunes in windows. Hope Apple starts making iTunes for linux too...

It's iTunes fault that many developers now confuse media library and playlist, that includes Banshee and Rhythmbox. Anyone who uses a music player in Linux for anything else than listening full albums of Justin Bierber is either using Foobar2000 via Wine or has programmed her own MPD client.

---

### Post by Dale61 on 2011-11-20
When I first started using Ubuntu, Dapper (6.06) was the latest release, and Rhythmbox was the default.  I eventually found Songbird, and I used that as my player of choice for some time.

Then, the developers of Songbird sold out to M$, so I reverted back to Rhythmbox while I tried others in a bid to find something I liked.  I found Banshee and used that regularly.

In the last week / 10 days, Banshee started to freeze, so I decided to find something else.  I came across gmusicbrowser, and that is now my player of choice.  It can be found in the Software Centre.

I did give VLC a go as a music player, but I found I had to import my library each and every time, then it would play the same tracks (I like to shuffle my music) every time.

---

### Post by LinuxFan999 on 2011-11-20
> **shuttleworthwannabe said:**
> I also read this elsewhere; so no more banshee--but I just hope RB turns out to be more than just a player--Amarok type player.
I heard that Tomboy and Mono will be removed too.
Ubuntu will finally be a Mono-free OS.

---

### Post by julianloui on 2012-02-16
Hi,

I've been able to use Banshee successfully only once, probably on Ubuntu 8.04.  Ever since then, Banshee invariably quits after after it's selected to play (a WAV file) and the cursor dances for a short while on the screen.  This happens with Ubuntu 10.04 and 11.10 also.  I must be missing some plugins? On the other hand, Movie Player has always been reliable.

I wish my computer had a Linux-compatible card or wireless adapter. Any advice or help will be much appreciated.  

Julian

---

### Post by mörgæs on 2012-02-17
> **julianloui said:**
> 
I wish my computer had a Linux-compatible card or wireless adapter. Any advice or help will be much appreciated.  



Best is to post a question in one of the support fora, not the cafe. Give as many hardware details as possible. 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

