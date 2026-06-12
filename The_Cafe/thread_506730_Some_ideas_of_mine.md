---
title: "Some ideas of mine"
date: 2007-07-22
forum: The Cafe
---

### Post by Christophe Vanlancker on 2007-07-22
I'm very happy about the way Ubuntu is evolving these years and specially lookup for the next release of Gutsy.

However I still have some ideas in mind of which I'm not sure if they have already been issued or considered.


**1- MP3 to OGG app that would convert all your music if desired.**
Here's the idea: if you live in a country where it's illegal to have mp3 used in linux, why can't we give the user the option to easily convert their music files into the open format?
I'm not sure if having this capability is legally al right or if having an app that's installed by default who can understand the mp3 format in any way is breaking the law.

**2- Better IDV-Tag management in our media players like Rhythmbox**
How can it be that when I edit the tags in any mp3 song that only the media player I used to edit it is the only one who remembers the changes instead of writing it along with the file?
This gives me major headaches when having to listen to my music in other music players.
I know there are things like EasyTag to manipulate the IDV settings within the music files, but please! Isn't it time to incorporate these feature into our music players?
The idea is to write the changes once, and view the songs correctly no matter which music player you use. It can't be that difficult?

**3- More info about support for different mp3 players**
Now for those people who use Ipods in linux, I think it must have happened at least once that the ipods library suddenly becomes corrupted for some mysterious reason. Now I know that not everything can work with a new update for the firmware (which you shouldn't be doing anyway when using solely linux to put songs on it) but the media player like say Rhythmbox could at least warn you about the possible *risks* that you take as a newbie.

**4- Smart technology within Rhythmbox**
For those who use iTunes, I guess they are aware of the *consolidate* option in the menu, which organises your music within folders nicely named after the artist and album. Not only are they organized in the iTunes folder, but it gives you some backup feeling and capabilities. I think Rhythmbox is mature enough to have this feature and others in it.
You know the moodbar in Amarok? Why not doing something similar? Or have a special function that selects similar songs based on the "mood" or genre of the songs? That would be cool to use in parties!

**5- Smart auto-partitioning**
Instead of having everything under the root partition /, why not make the /home directory exterior to the / partition?  That way if someone screws up something or got too experimental on their system, they can always reinstall the system back without losing potentially important files?

---

### Post by ddrichardson on 2007-07-22
Some good ideas - try posting them [here]("https://wiki.ubuntu.com/IdeaPool").

---

### Post by guitarmaniac on 2007-07-22
Yeah, those are some good ideas, not really new, but definitely need attention.
Rhythmbox is far too under featured to be the default player for ubuntu.

---

### Post by bonzodog on 2007-07-22
> **Christophe Vanlancker said:**
> 
**1- MP3 to OGG app that would convert all your music if desired.**
Here's the idea: if you live in a country where it's illegal to have mp3 used in linux, why can't we give the user the option to easily convert their music files into the open format?
I'm not sure if having this capability is legally al right or if having an app that's installed by default who can understand the mp3 format in any way is breaking the law.

Mp3 and ogg are both what we call lossy formats. To move from one to the other actually makes things worse, as the track would lose even more quality. No, you *have* to encode to ogg as the initial format, otherwise this would have been done years ago.

> [i]**2- Better IDV-Tag management in our media players like Rhythmbox**
How can it be that when I edit the tags in any mp3 song that only the media player I used to edit it is the only one who remembers the changes instead of writing it along with the file?
This gives me major headaches when having to listen to my music in other music players.
I know there are things like EasyTag to manipulate the IDV settings within the music files, but please! Isn't it time to incorporate these feature into our music players?
The idea is to write the changes once, and view the songs correctly no matter which music player you use. It can't be that difficult?[/i]
Look at some other players - Rhythmbox is not one of the best players around, and is missing a lot of good features, such as you describe. Most of us use Amarok (KDE based player, with FULL tag editing abilities), or Quod Libet/Ex falso (Ex falso is possibly one of the best tag editors I know of - it recognises, and stores, all known types of format -- you get it with the Quod Libet Player). Rhythmbox is only included because the gnome developers decided to make it their player of choice. Other popular choices are bmpx/audacious (winamp look-alike, can use all winamp themes), mpd with a front end like sonata, and Exaile(a lot like quod libet).

> [i]**3- More info about support for different mp3 players**
Now for those people who use Ipods in linux, I think it must have happened at least once that the ipods library suddenly becomes corrupted for some mysterious reason. Now I know that not everything can work with a new update for the firmware (which you shouldn't be doing anyway when using solely linux to put songs on it) but the media player like say Rhythmbox could at least warn you about the possible *risks* that you take as a newbie.[/i]
Um, possibly, but The IPod feature is being worked on for Rhythmbox. It takes time to develop features like this when you are reverse engineering closed code.

> [i]**4- Smart technology within Rhythmbox**
For those who use iTunes, I guess they are aware of the *consolidate* option in the menu, which organises your music within folders nicely named after the artist and album. Not only are they organized in the iTunes folder, but it gives you some backup feeling and capabilities. I think Rhythmbox is mature enough to have this feature and others in it.
You know the moodbar in Amarok? Why not doing something similar? Or have a special function that selects similar songs based on the "mood" or genre of the songs? That would be cool to use in parties![/i]
Again, this is down to the gnome/rhythmbox developers, nothing to do with Ubuntu. I would seriously get yourself another player.

> [i]**5- Smart auto-partitioning**
Instead of having everything under the root partition /, why not make the /home directory exterior to the / partition?  That way if someone screws up something or got too experimental on their system, they can always reinstall the system back without losing potentially important files?[/i]
Those of us that are technically minded are already puzzled as to why Ubuntu does not create a /home partition at install. Most of us that know a fair bit about Linux and partitioning use manual  set-up to create a /home partition. This bug has been pointed out already in Launchpad, and was asked for 2 years ago.

---

### Post by ddrichardson on 2007-07-22
> **bonzodog said:**
> Those of us that are technically minded are already puzzled as to why Ubuntu does not create a /home partition at install. Most of us that know a fair bit about Linux and partitioning use manual  set-up to create a /home partition. This bug has been pointed out already in Launchpad, and was asked for 2 years ago.

Actually, whilst I agree and use a seperate /home partition myself, I can see both sides of the argument on this one. The thing is that a lot of problems that new users run into are related to settings within their own home directories (remember how many non-unix types don't know about hidden files) and coming from a Windows philosophy of reinstall-when-broke, a persistent home directory wont solve these issues. Anything that makes a new user transition from "I was experimenting and messed up" to "Ubuntu just doesn't work" may be counter productive. Just my £0.05...

---

### Post by Christophe Vanlancker on 2007-07-22
> **ddrichardson said:**
> Some good ideas - try posting them [here]("https://wiki.ubuntu.com/IdeaPool").

Thanks! I'll keep in mind the other posts that have answerd to this to keep the ideas relevant to the ubuntu team.

---

### Post by Christophe Vanlancker on 2007-07-22
> **bonzodog said:**
> Mp3 and ogg are both what we call lossy formats. To move from one to the other actually makes things worse, as the track would lose even more quality. No, you *have* to encode to ogg as the initial format, otherwise this would have been done years ago.


Look at some other players - Rhythmbox is not one of the best players around, and is missing a lot of good features, such as you describe. Most of us use Amarok (KDE based player, with FULL tag editing abilities), or Quod Libet/Ex falso (Ex falso is possibly one of the best tag editors I know of - it recognises, and stores, all known types of format -- you get it with the Quod Libet Player). Rhythmbox is only included because the gnome developers decided to make it their player of choice. Other popular choices are bmpx/audacious (winamp look-alike, can use all winamp themes), mpd with a front end like sonata, and Exaile(a lot like quod libet).


Um, possibly, but The IPod feature is being worked on for Rhythmbox. It takes time to develop features like this when you are reverse engineering closed code.


Again, this is down to the gnome/rhythmbox developers, nothing to do with Ubuntu. I would seriously get yourself another player.


Those of us that are technically minded are already puzzled as to why Ubuntu does not create a /home partition at install. Most of us that know a fair bit about Linux and partitioning use manual  set-up to create a /home partition. This bug has been pointed out already in Launchpad, and was asked for 2 years ago.

1-  I forgot about that issue... so yeah, there isn't really a solution to this. :(

2-  True, but I feel that this should have been integrated way back because it's such a logical and basic thing to have and be able to do.

3-  Sure, I can understand that. It's not easy to reverse engineer closed source stuff. But I wanted to point out that normal users don't know about these issues. Hence the user should be at all time aware of the compatibility layer of Rhythmbox with their model of ipod and current firmware version.  Right now, Rhythmbox doesn't tell you anything. 

4-  We'll just have to wait.... just reformated my Ubuntu box with a separate partition... reinstalled the system and I was happy that it remembered all my desktop settings. :)

---

