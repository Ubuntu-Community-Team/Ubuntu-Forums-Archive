---
title: "Quitting Banshee: the reasons why"
date: 2011-07-27
forum: The Cafe
---

### Post by lads on 2011-07-27
Dear all, this message was originally submitted to the Banshee forum, where it's publication has not been accepted. I believe it is important to register user experience with software as an indispensable path to improve it.

> Dear Banshee fellowship,

I've upgraded to Ubuntu 11.04 two months ago and have been using Banshee since. I'm giving it up and going back to Rhythmbox. Here I lay the problems that lead me to do so, may it help improve Banshee in the future.

**First 5 seconds of the track are not audible**

This happened the first time I used Banshee and it repeated many times during the first week of use. When you click play on some file the time starts increasing but the sound only comes at about 5 seconds into the track, missing these first moments of music. With time it became less and less frequent; I have no idea what may be causing this.

**Tracks on disconnected hard drives**

I have music files spread across several hard drives and operating systems, that I use at work and at home. When inadvertently a file from a disconnected hard drive is brought on play Banshee doesn't play any music but it doesn't emit an error message either, it's up to you to figure out what's wrong. Rhymthbox simply hides files in its playlist that are not available at the moment; when a remote hard drive is re-connected it automatically re-lists any files that may be stored there. Also, if Rhymthbox can't read a file for some reason it emits an error message (usually not very helpful but at least you know something's wrong).

**Duplicate file names**

After about one month of usage Banshee started listing some files in duplicate. It took me quite a while to understand what is causing this: sometimes Ubuntu fails to unmout remote hard drives leaving unused directories at /media. When this happens Ubuntu remounts the drive the next time with a “_” sufix to its name, e.g. “myDrive_”. The result: Banshee double lists files at “myDrive” and “myDrive_”. At this time some tracks are now listed in triplicate and the playlist has now dozens of thousands of files. This is the main reason why I'm quitting Banshee, since there's no easy way to simply clean these duplicates. This was never a problem with Rhythmbox, perhaps because it never lists files in drives it can't access.

**Play stops unexpectedly**

This has become quite frequent, and may be a consequence of the duplicate and triplicate listing, though it happens with radios too. Banshee simply stops playing at the end of some random track without any error message; imagine there is a 10 track LP, you start playing the first track and it goes down to the 7th or 8th and then simply stops. Though with files you can restart the playing, with radios this usually requires a restart to Banshee.

Visually Banshee is surely an improvement over Rhythmbox, but it still has a few degrees to climb before reaching the same level of maturity.

Best. 

---

### Post by Steeperton on 2011-07-27
My main problem with Banshee was that .ogg files skipped 3 or 4 times per song.

Like you, I've gone back to rhythmbox.

---

### Post by Aquix on 2011-07-27
It's not a big move to be honest, and be prepared to make it more often. And like with all linux software you go into your software center, download a few at the time, test them out, and remove the ones you don't like. And remember that it's no crime to use more than one program for music. I use both vlc and gnome-mplayer for videos and podcasts. After that you keep your eye on the buntu blogs for new players and releases. 

Your right about user response but rants in the banshee forums is not the way to do it. It's not that your opinion doesn't matter or that they ignore you in any way but that it's a waste of time for both writer and reader. Post short posts with questions about how to solve your problem, and if stuck join their irc chat room and ask there. Another method is to search through their bug list. And remember that on many projects people are using their spare time on it since that's the nature of free open source programs. 

And test out clementine, it's the best music player to date in my humble view. :D

---

### Post by mpiter on 2011-07-27
> **lads said:**
> ...Banshee simply stops playing at the end of some random track without any error message...

When a program does something wrong without error messages, check [COLOR="Olive"]$(HOME)/.xsession-errors[/COLOR].  This files keeps track of the error messages produced by the programs launched from a dock, a menu, or at startup.

---

### Post by zekopeko on 2011-07-27
> **lads said:**
> Dear all, this message was originally submitted to the Banshee forum, where it's publication has not been accepted.

Banshee doesn't have a forum but a mailing list. I'll have to see some proof of your statement that Banshee developers censored your opinion.

---

### Post by del_diablo on 2011-07-27
> **mpiter said:**
> When a program does something wrong without error messages, check [COLOR="Olive"]$(HOME)/.xsession-errors[/COLOR].  This files keeps track of the error messages produced by the programs launched from a dock, a menu, or at startup.

That is irrelevant for a desktop user.

---

### Post by mpiter on 2011-07-27
> **del_diablo said:**
> That is irrelevant for a desktop user.

I do not understand. I use Gnome 2 (Ubuntu Classic in Natty) with Compiz and Emerald, and my [COLOR="Green"].xsession-errors[/COLOR] is filled as it used to be.  Am I not a desktop user?  If not, what is a desktop user?

---

### Post by Nightstrike2009 on 2011-07-27
I too went back to rhythmbox after using Banshee for ages. The reason being Banshee and Easytag (Mp3 ID3 tagger) are both fine on my desktop but fail to "Fit to screen" on my netbook, I am unsure why but suspect being mono based to be at fault.

---

### Post by Bertrand_Lorentz on 2011-07-27
The original message was posted on the forum interface of our mailing-list :
[http://banshee.fm/support/forum/](http://banshee.fm/support/forum/)

Messages posted there have to be manually moderated before they are sent to the mailing-list, which creates a delay. But I think they are visible immediately through the forum interface.

---

### Post by BrokenKingpin on 2011-07-27
My main issue with Banshee is that is slow and bloated. For a music player it should not take so long to load initially. I have been using Banshee for about a year now, and have always advocated for it, but I think I am going to switch to something else. There are plenty of music players that have a similar feature set, but don't take 7 days to startup.

---

### Post by mpiter on 2011-07-27
> **BrokenKingpin said:**
> ...I have been using Banshee for about a year now, and have always advocated for it, but I think I am going to switch to something else...

I tried this afternoon Guayadeque following several people pieces of advise. It crashed every 10 minutes on my system setup, but many people claim to have it stable on their computer.  Give it a try because it can manage a huge music database and is beautifully connected to Internet.

---

### Post by BudBear on 2011-07-27
initially i liked Banshee. nice interface, worked well with a limited local library. then when i tried to connect to a smb library it would just lock up.  it seemed to have a problem with a particularly large mp3 file. not sure why, but i went back to rhythmbox, simply because it works with my music library and also my iphone, sort of.  but that may change soon anyway.  that is to say,  either it working or me having an iphone.

---

### Post by medic2000 on 2011-07-27
I don't even consider using Banshee for it is Mono. Plus i suggest ncmpc++ to everyone who finds jukeboxes very slow and bloated.

---

### Post by Syndicalist on 2011-07-28
Rhythmbox is the superior music player and jukebox.

---

### Post by lads on 2011-07-28
> **Aquix said:**
> And test out clementine, it's the best music player to date in my humble view. :D

Been using Clementine since yesterday, certainly better than Banshee. Stable and easy to use; graphically it isn't spectacular, but hey, it is a music player :)

---

### Post by Syndicalist on 2011-07-29
Bansheee tries to be/do too much. I almost think they have become a better video player than music player now.....at least its good for video that uses surround sound, though VLC is also good. Rhythmbox is just more user friendly and coherent.

I like Exhaile for lite weight, but I still prefer Rhythmbox over anything else.

---

### Post by aeiah on 2011-07-29
> **medic2000 said:**
> I don't even consider using Banshee for it is Mono. Plus i suggest ncmpc++ to everyone who finds jukeboxes very slow and bloated.

i suggest everyone checks out gmpc, which runs on the mpd backend like ncmpc++ but won't scare everyone away, since its a desktop application and not an ncurses terminal app :P

---

### Post by lads on 2011-08-09
I'm quitting Clementine after it started to list tracks in duplicates, triplicates and even quadruplicates. I haven't managed to find why this is happening, there hasn't been any shutdown event leading to drive names changing since I started using it.

Back to good old Rhythmbox. Will try GMPC.

From the feedback in this thread it seems obvious Banshee has some ground to cover before reaching the maturity of other media players.

Thanks for all the suggestions. Best regards.

---

### Post by hakermania on 2011-08-09
I don't use banshee either, it takes approximately 10 seconds to load and it is far too heavy generally, although I didn't have any of the problems mentioned to the first post!
I prefer Clementine!

---

### Post by mpiter on 2011-08-09
> **lads said:**
> From the feedback in this thread it seems obvious Banshee has some ground to cover before reaching the maturity of other media players.

Do not only rely on other people's experience.  I have tried most media players discussed here and some others too. Banshee is my favorite one.  Not that it is absolutely the best, but I have not found anything that I dislike in it, it is highly stable on my computer configuration, I have never met a problem in a couple of months, and its interface seems natural to me.  I did not like the way clementine managed the CD covers.  I did not succeed in making Guayadeque run more than 10 minutes without crash, I do not like the VLC interface...  So if Banshee seems nice to you, give it a try because many things depend on personal tase.

---

### Post by johnnybgoode83 on 2011-08-09
Banshee is an excellent music manager but for one rather major issue for me.  The memory and CPU it uses is way too high and so that is the first application I remove when doing a clean install for someone.  Personally, I prefer Rhythmbox for updating my music device because it is really simple and straight forward - highlight the songs or album you want to add and drag it to the device and job done.
 
I also use Guayadeque for all other music related activities such as fetching album art and tagging.  It is a trully excellent player for managing large collections without using too much memory and CPU.  It is also a pretty full featured music manager while staying relatively lightweight.

---

### Post by BrokenKingpin on 2011-08-09
> **medic2000 said:**
> I don't even consider using Banshee for it is Mono. Plus i suggest ncmpc++ to everyone who finds jukeboxes very slow and bloated.
What is wrong with Mono? It is a fantastic development platform. Is it just because it was originally a Microsoft standard? I will never understand the Mono hate. I can understand if you just don't like the app, but not even trying because of Mono... take off your foil hat.

---

### Post by trinux_bc on 2011-08-09
I switched to Guayadeque a couple months ago, it's been completely stable and feels really light weight on my system. Banshee felt clunky, like I was always waiting for it, and that's just not something I'm willing to put up with in a music player.

trinux_bc

---

### Post by BrokenKingpin on 2011-08-10
What ever happened to XMMS? It was a light and simple music player, but I think I don't think it is actively maintained anymore.

---

### Post by medic2000 on 2011-08-10
> **BrokenKingpin said:**
> What is wrong with Mono? It is a fantastic development platform. Is it just because it was originally a Microsoft standard? I will never understand the Mono hate. I can understand if you just don't like the app, but not even trying because of Mono... take off your foil hat.

Why not? Should i like it? Plus i don't like the application too.

---

### Post by medic2000 on 2011-08-10
Tried and loved Gmpc by the way! It is very light and offers many features.
[http://gmpc.wikia.com/wiki/Gnome_Music_Player_Client](http://gmpc.wikia.com/wiki/Gnome_Music_Player_Client)

---

### Post by mpiter on 2011-08-10
> **BrokenKingpin said:**
> What ever happened to XMMS? It was a light and simple music player, but I think I don't think it is actively maintained anymore.

XMMS was discontinued because it was considered as poorly written and difficult to maintain.  It led to a few forks.  One of them is Audacious and I think it is presently maintained.  There was also XMMS2, but I have not followed at all that fork.  I have no idea what has become of it.

---

### Post by PC_load_letter on 2011-08-10
> **Aquix said:**
> 
And test out clementine, it's the best music player to date in my humble view. :D

^ this! There is also Guayadeque, Exaile, and the community maintained Songbird.

---

### Post by forrestcupp on 2011-08-10
> **lads said:**
> Dear all, this message was originally submitted to the Banshee forum, where it's publication has not been accepted. I believe it is important to register user experience with software as an indispensable path to improve it.

If they really did censor you, it's probably because you started it off telling them that you're dropping them and going back to Rhythmbox. If you really want something fixed, you don't begin your request by trashing them and telling them you're going to use a better program.

---

### Post by BrokenKingpin on 2011-08-11
> **medic2000 said:**
> Why not? Should i like it? Plus i don't like the application too.
You shouldn't judge an application before even trying it just because it was written in a certain language. Banshee sucks because it was poorly written (IMO), not because it was developed in Mono. There are loads of quality application written in .Net/Mono, so I don't understand what people have against it (and being a MS technology is a **** poor reason).

---

### Post by fqowehf on 2011-08-11
Mono "IS" very buggy and since banshee was made on its interface and compilers, use Rhythmbox since it wasnt and is less buggy and better.

The Developers of Mono really need to learn that linux apps should NOT be made in C# since its taken over by microsoft and who knows what they Mono did to port it, and what will it do to you system stability.

---

### Post by zekopeko on 2011-08-11
> **NullCity said:**
> Mono "IS" very buggy and since banshee was made on its interface and compilers, use Rhythmbox since it wasnt and is less buggy and better.

The Developers of Mono really need to learn that linux apps should NOT be made in C# since its taken over by microsoft and who knows what they Mono did to port it, and what will it do to you system stability.

Now you are just bashing without any arguments to support it. Mono actually has commercial sponsors so people are getting paid to work on it. Not to mention that there are commercial applications built on top of it for which people pay good money.

---

### Post by medic2000 on 2011-08-11
> **BrokenKingpin said:**
> You shouldn't judge an application before even trying it just because it was written in a certain language. Banshee sucks because it was poorly written (IMO), not because it was developed in Mono. There are loads of quality application written in .Net/Mono, so I don't understand what people have against it (and being a MS technology is a **** poor reason).

No you misunderstood me. I have tried Banshee. In fact i've tried many audio players written for Linux. These include: 

Banshee, BMP, XMSS, Audacious, Rhythmbox, Exaile, Gmusicbrowser, Guayadeque, Quod Libet, Songbird, AlsaPlayer, Audacious, Amarok, Sonata, GMPC and Ncmpc++(the last three is MPD clients). And maybe some others too.
I have used them for a while. To really see if they are suitable for me.

As for Mono, it is not **** reason. I think it taints the GNU and Linux. I have nothing against MS and its tech. I don't bash any company. But i just don't like them. Their attitude is always insidious for me. Ok companies is for making money but this kind of greedines. What did they when the singer Amy Winehouse died? Do you know? In 24 hours after death they post a message to twitter:

"Remember Amy Winehouse by downloading the ground-breaking 'Back to Black' over at Zune"

This is just nowadays. Look at the history of company.

I don't like these kind of things. They are rich beyond dream. Yet still trying to make more profit by using a girl's death? Serious MS? Are you worshipping money? 

Give something to humanity. Give something to computer world. Make your Office format open or work with LibreOffice developer to create a world-wide standart format. Support Hardware Vendors for Linux drivers too. Make your Bootloader recognize Linux.

No they never will. Maybe will but if only it is profitable for them. We are talking about that kind of company here.

Maybe this is just fine with you. Of course it can be. People have different ideas, different point of views. But you can not tell me that i have **** poor reason to not like Mono. Plus there are very good alternatives for me.

I personally came to Linux to be free. And after this why should i relinquish my freedom again?

---

### Post by zekopeko on 2011-08-11
> **medic2000 said:**
> <snip>

You are being irrational and emotional. You do have crappy reasons to dislike Mono. You are generalizing Microsoft based on one person's bad judgment.

---

### Post by medic2000 on 2011-08-11
> **zekopeko said:**
> You are being irrational and emotional. You do have crappy reasons to dislike Mono. You are generalizing Microsoft based on one persons bad judgment.

We are talking about software here and you are criticizing me? In this forum we have people like that? I don't need your prejudice. Your answering type is pure "crap". Learn to respect people's thoughts. Come with your arguments. Don't troll. 

Also read the lines about "...history" in my post.

Irrational? Yeah? Maybe you shouldn't use Linux at all because it is very "irrational". People worked hard to create a distro which is free. They worked for free? Oh very "irrational!". Ahh never mind they are crap people.

---

### Post by zekopeko on 2011-08-11
> **medic2000 said:**
> We are talking about software here and you are criticizing me? In this forum we have people like that? I don't need your prejudice. Your answering type is pure "crap". Learn to respect people's thoughts. Come with your arguments. Don't troll.

Also read the lines about "...history" in my post.

> Irrational? Yeah? Maybe you shouldn't use Linux at all because it is very "irrational". People worked hard to create a distro which is free. They worked for free? Oh very "irrational!". Ahh never mind they are crap people.

So let me get this straight: you are saying I'm prejudiced while accusing Mono, a Free software project, of being "tainted" simply because it is built on an specification from Microsoft, completely ignoring the fact that it is an independent project from any sort of Microsoft control.

I urge you to go and look up the dictionary definition of prejudice because you are drenched in it.

---

### Post by Ric_NYC on 2011-08-11
"Bashing Banshee"....


:P

---

### Post by Ichtyandr on 2011-08-11
> **lads said:**
> Been using Clementine since yesterday, certainly better than Banshee. Stable and easy to use; graphically it isn't spectacular, but hey, it is a music player :)

I also prefer clementine especially on kubuntu. Otherwise audacious is my favorite on (x)ubuntu, reminds good old winamp

---

### Post by BrokenKingpin on 2011-08-12
> **NullCity said:**
> Mono "IS" very buggy and since banshee was made on its interface and compilers, use Rhythmbox since it wasnt and is less buggy and better.

The Developers of Mono really need to learn that linux apps should NOT be made in C# since its taken over by microsoft and who knows what they Mono did to port it, and what will it do to you system stability.
This is a joke right? If not you have no idea what Mono is, or how software development works in general (I hope to god you are not a software developer).

---

### Post by Erik1984 on 2011-08-12
> **Ichtyandr said:**
> I also prefer clementine especially on kubuntu. Otherwise audacious is my favorite on (x)ubuntu, reminds good old winamp

I like Audacious but not the Winamp 2.x interface, it's much better with GTK-interface IMO.

---

### Post by em3raldxiii on 2011-08-12
Interesting that the OP mentioned duplicate entries in Banshee (and other apps) but not in Rhythmbox ... I have suffered from the entry duplication issue in Rhythmbox!  It's not too difficult to remedy (remove the cache file in ~/.local/share/rythmbox/) which will cause Rhythmbox to rescan the directories, and this may also be the same for other players.

For spontaneous playlists, and for doubleclick-playing, I use VLC.  I like it because it's fast, quite light weight, and it plays everything.  Their menus took me a little bit of getting used to (they are somehow just a little bit different from what I have become accustomed to).

Finally:  To all those who are arguing about opinions other than what the OP posted about (MONO, C#, Microsoft, censorship): please be courteous and don't hyjack these threads with personal attacks, etc.  It's counterproductive and distracts from the original topic.

---

### Post by BobMarleyy on 2011-08-13
I also tried Banshee for too long. I thought it would work properly, because it is shipped with the new Ubuntu 11.04. Unfortunately, Banshee sometimes just quits (for me only when playing internet radio). It indeed appears to be more heavy to run.

Another funny issue is that there is no easy-to-use lyrics plugin. Those that run with Banshee, are worthless, since they cannot read songs from internet radio. (This is no problem in Rhythmbox). Does anyone have some advice for me on using lyrics in Banshee?

To conclude, I do not like to be the exception ;) and I also switched back to Rhythmbox. This raises the question: Why did they ship the new Ubuntu with Banshee? I never had so much trouble with an auto-installed Ubuntu app before. This indicates that usually Ubuntu rocks, but what is going on what Banshee!

Banshee bashing, woohoo :D

---

### Post by mpiter on 2011-08-13
> **BobMarleyy said:**
> I also tried Banshee for too long. I thought it would work properly, because it is shipped with the new Ubuntu 11.04. Unfortunately, Banshee sometimes just quits (for me only when playing internet radio). It indeed appears to be more heavy to run.

Stability and trustworthiness was obviously the least of Canonical's concern for Ubuntu 11.04. They just wanted to provide Unity at all cost, including a system that did not work. In 23 years of Linux-based system use, I have never seen something as bad as Ubuntu 11.04.

> To conclude, I do not like to be the exception ;) and I also switched back to Rhythmbox. This raises the question: Why did they ship the new Ubuntu with Banshee? I never had so much trouble with an auto-installed Ubuntu app before. This indicates that usually Ubuntu rocks, but what is going on what Banshee!

Banshee bashing, woohoo :D

Many applications are less stable in Ubuntu 11.04 than in previous versions.  This is not just Banshee.  I prefer Banshee over Rhythmbox because I like its search engine and the way it manages CD covers.  I do not listen to radio, that is maybe why I have no problems with that software.

Have you tried [COLOR="Green"]Guayadeque[/COLOR]?  I have not succeed in making it stable on my computer, but many users did and it is beautifully linked to the Internet.  Maybe you will like it.

---

### Post by Ichtyandr on 2011-08-13
> **Euroman said:**
> I like Audacious but not the Winamp 2.x interface, it's much better with GTK-interface IMO.

absolutely, it does not integrate into sound menu or provide status icon, but otherwise it is pretty much perfect

---

### Post by dh04000 on 2011-08-13
Why do people feel the need to tell us when they stop using an application?

Its not a breakup, feel free to tell the other party by text, and leave us out of it.

---

### Post by lads on 2011-10-28
> **dh04000 said:**
> Why do people feel the need to tell us when they stop using an application?

Indeed this wouldn't have been a subject for the Ubuntu fora in the first place. Normally I would just report my misfortunes to the Banshee dev team and that was it. But it happens that my story wasn't accepted there. From this thread we also learn that Banshee is still a green piece of software that most folk find a few points behind their music players of choice.

So here's the relevance for this community: why has an immature piece of software whose dev team isn't very open to the community being included in an Ubuntu release?

---

### Post by Docaltmed on 2011-10-28
> **lads said:**
> 

So here's the relevance for this community: why has an immature piece of software whose dev team isn't very open to the community being included in an Ubuntu release?

Your question is based on faulty premises. Banshee is not immature -- it's been under development since at least 8.04, perhaps before then. And its developers are very responsive. Every question/problem/bug I have discussed with them over the years has been addressed very rapidly. 

Just because someone wrote a snarky note and nobody responded with the correct kowtow is not a reason to dismiss an application.

---

### Post by lads on 2011-10-28
> **Docaltmed said:**
> Just because someone wrote a snarky note and nobody responded with the correct kowtow is not a reason to dismiss an application.

Just to make it clear, the problem wasn't that no one responded, the message simply wasn't accepted. While it isn't flattering I don't think it is offensive in any way. If users can't report bugs and their difficulties how is the software supposed to mature?

---

### Post by prudra on 2011-10-28
I am also one who has left banshee in favour of rhythmbox on my debian squeeze laptop, though the package is still there. I remember there was some problem which led me to this step. As long as I had debian lenny I used only banshee. I have not checked banshee on my ubuntu-10.04 netbook.

---

### Post by prudra on 2011-10-28
> **dh04000 said:**
> Why do people feel the need to tell us when they stop using an application?

Its not a breakup, feel free to tell the other party by text, and leave us out of it.

This is cafe, that's why.

---

### Post by krapp on 2011-10-28
While you guys are at it, quit the whole iTunes clone thing. It's an evil, evil model for media, and your RAM will hate you for it. File manager + playlists are the way to go. I use moc for music.

---

### Post by K-Ghidorah on 2011-10-28
I went the other way around - I dropped Rhythmbox in favor of Banshee a  number of months ago, simply because there were a number of my music  files that Rhythmbox failed to read, not to mention the fact that it  wouldn't play nice with my iPod.  

> **krapp said:**
> While you guys are at it, quit the whole iTunes clone thing. It's an evil, evil model for media, and your RAM will hate you for it. File manager + playlists are the way to go. I use moc for music.

I actually like the interface and it works for me.  I guess that makes me evil too :twisted:

---

### Post by krapp on 2011-10-28
Well when your vindictive RAM slits your throat in the night, don't say I didn't tell you so.

---

### Post by Copper Bezel on 2011-10-28
Yeah, but *all* of the RAM in my computer already *exists* for my convenience. If it's *slightly more* convenient to use slightly more of it at a time, I'm very likely to do.

There are light jukeboxes, too, you know. BeatBox, for instance. If you were using graphical apps, there's no reason any particular jukebox would have to be heavier than any particular standalone music player + a file manager, since it's just the music player with a stripped-down file manager worked in....

---

### Post by 3Miro on 2011-10-28
To add to the problems with Banshee. I have a Ssytem76 laptop and I have Ubuntu 11.10 installed, I had some trouble figuring out Banshee, so I deleted it. After reading this thread, I decided to give it another try on my multi-boot desktop. 

I installed the latest banshee under Arch and I noticed that for some reason it ignores video files without extensions. I have a folder where I keep music that needs sorting, I added that folder to Banshee and I can see the .mp3 and .mpg files, but I cannot see the several video files that come without an extension. Under Linux, the DE doesn't rely on extensions to know the type of file, I can just click on the files with Thunar or Nautilus or Dolphin and the default medial player would pop up, however, Banshee seems to rely on file extensions. I tried to manually add the files to Banshee, but it will only let me add files with a media extension ... is this made for Windows or what?

I liked Rhythmbox, but it cannot play videos. I really couldn't figure out Amarok (and I was a KDE user for years), somehow I can never figure out how to play anything in that interface. I like the idea of Banshee playing both Audio and Video files, but I guess I can't figure that one out either. I liked Kaffaine, but since I moved to GTK DE I stay away from QT apps. The best media management program that I know of, is a simple file manager for sorting folders and a simple and fast player ... i.e. Thunar + Parole. I bet I can find and play my music faster than you can find and play yours with any of the fancy players.

---

### Post by krapp on 2011-10-28
> **3Miro said:**
> The best media management program that I know of, is a simple file manager for sorting folders and a simple and fast player ... i.e. Thunar + Parole. I bet I can find and play my music faster than you can find and play yours with any of the fancy players.

Ha! GUI? What do you need the GUI for when you have like 4 fine console players to choose from!

---

### Post by 3Miro on 2011-10-28
> **krapp said:**
> Ha! GUI? What do you need the GUI for when you have like 4 fine console players to choose from!

I computer has three mods of operation: two hands on the keyboard (console is the best here), one hand on he keyboard and one hand on the mouse (probably the most flexible interface, look at electronic sports), one hand one the mouse one hand on my beer. In the last mode, Thunar + Parole works best for me and it is the most appropriate mode for listening to music.

What I am trying to say is: GUI = the best beer interface.

---

### Post by krapp on 2011-10-28
Two words: beer helmet.

---

### Post by lads on 2011-12-23
Well, it seems I'm not the only one quitting Banshee. According to [ILoveUbuntu.net]("http://iloveubuntu.net/rhythmbox-has-landed-default-media-player-ubuntu-1204-lts") it won't be the default player in beta 1 of the next Ubuntu release:

> The latest updates bring Rhythmbox as the default media player in Ubuntu 12.04 and remove Gbrainy and Tomboy.

This approach has been sketched at UDS-P (and is now available as a blueprint on launchpad) and has as a main goal the use of the lightweight GTK+3 Rhythmbox by default until Precise BETA 1, when the developers will review the status of GTK+3 Banshee (at the moment is a GTK+2 application) and will choose Precise's default media player.

Merry Christmas and all that.

---

### Post by sunfromhere on 2011-12-23
I also find Banshee too big for what I need it for: playing music. Currently, I'm looking for a minimal player in which I can just add a folder and have it played. I see some of you mentioned a couple, but is there any that could replace Banshee in the volume panel?

---

### Post by lads on 2011-12-27
> **sunfromhere said:**
> I also find Banshee too big for what I need it for: playing music. Currently, I'm looking for a minimal player in which I can just add a folder and have it played. I see some of you mentioned a couple, but is there any that could replace Banshee in the volume panel?

If you install Rhythmbox you'll get a new set of mini controls added to the volume control.

---

### Post by d3v1150m471c on 2011-12-27
~/Music/artist/album/song.mp3
~/Music/artist/album/another_song.mp3

Simple organization

```

#!/bin/bash
if [[ $(id -u) == 0 ]]; then
    echo 'cannot use as root'
    exit 1
fi
cd /path/to/Music
while true;do
    while true;do
        read -p '>>> ' SONG
        X=`find -L -iname *.mp3 | grep -i "$SONG" | head -1`
        [[ $(echo X$X) == X ]] && X=`find -L -iname *.ogg | grep -i "$SONG" | head -1`
        cvlc "$X" --play-and-exit >/dev/null 2>&1
    done
done

```

:-)

---

### Post by lads on 2012-01-06
So it seems that the main motivation for Banshee to be dropped from Ubuntu 12.04 was lack of GTK3 support. But it turns out the community itself was very keen on the change, about [70% of approval in this poll]("http://www.omgubuntu.co.uk/2011/11/banshee-tomboy-and-mono-dropped-from-ubuntu-12-04-cd/").

Also interesting that in a message from the Canonical folk to the Ubuntu Desktop Mailing list part of the usability problems are acknowledged:

> 3. Stability in core function. Banshee has many features, though the
general impression is that it has stability issues with frequent crashes
and hangs needing force quits. RB is known to be quite stable.

Nice to see Ubuntu getting better.

---

### Post by mpiter on 2012-01-06
> **lads said:**
> So it seems that the main motivation for Banshee to be dropped from Ubuntu 12.04 was lack of GTK3 support. But it turns out the community itself was very keen on the change, about [70% of approval in this poll]("http://www.omgubuntu.co.uk/2011/11/banshee-tomboy-and-mono-dropped-from-ubuntu-12-04-cd/").

The poll did not address Banshee but the set Mono, Banshee, and Tomboy.  I bet many people just answered against Mono.  Furthermore, the answer choices were biased toward "Yes, it was a good move".  The only available options to say "No" were either being shocked by the decision or being inconsolable.  Why not include something such as "No, I do not think it is a wise move?"  In other words, the 70 % are meaningless as far as Banshee is concerned.

> Nice to see Ubuntu getting better.

I think the last good Ubuntu version was 10.10.

---

### Post by lads on 2012-01-13
> **mpiter said:**
> In other words, the 70 % are meaningless as far as Banshee is concerned.

True, but note that Rhythmbox [is indeed the most popular]("http://www.omgubuntu.co.uk/2010/10/which-would-you-choose-as-default-banshee-or-rhythmbox-poll/") of the two media players.

---

### Post by mpiter on 2012-01-13
> **lads said:**
> True, but note that Rhythmbox [is indeed the most popular]("http://www.omgubuntu.co.uk/2010/10/which-would-you-choose-as-default-banshee-or-rhythmbox-poll/") of the two media players.

Right.  Good poll.  I saw in forums that many people reproach Banshee to be heavy and unstable.  I have not met problems yet with it.

---

### Post by coldjeanz on 2012-01-14
I'm a new user but after using audio enhancers for my other music players the sound quality coming out of Banshee sounds awful. Does anyone know if there is a plugin out there that improves sound quality?

---

### Post by Docaltmed on 2012-01-14
> **coldjeanz said:**
> I'm a new user but after using audio enhancers for my other music players the sound quality coming out of Banshee sounds awful. Does anyone know if there is a plugin out there that improves sound quality?

Go to View > Equalizer.

Adjust sound to heart's content. There are a number of presets there as well.

---

### Post by coldjeanz on 2012-01-15
> **Docaltmed said:**
> Go to View > Equalizer.

Adjust sound to heart's content. There are a number of presets there as well.

Thanks. Using the "Laptop" preset worked great.

---

### Post by ex_isp on 2012-04-21
I've been running v12 (Lisa) for a short while now and have had few problems.  Main one is with Banshee.  It will inevitably lock (while continuing to play) and permanently deny me access to any other controls leaving me no choice but to do a hard power off.

Today, I also removed Banshee and am instead using  my long time friend Rhythmbox as it does not, and has never given me any issues.

---

### Post by tmaranets on 2012-04-21
A few times, when i play music on Banshee, I get some errors(which I don't like).For me Banshee has been a trouble a few times. I still use it sometimes(when I am on Ubuntu and I want to listen music), but I think I will use Itunes for the time being.

---

### Post by MisterGaribaldi on 2012-04-21
[img]http://img.photobucket.com/albums/v607/JaviFL/ThreadNecromancy.jpg[/img]

---

### Post by CharlesA on 2012-04-21
> **MisterGaribaldi said:**
> [img]http://img.photobucket.com/albums/v607/JaviFL/ThreadNecromancy.jpg[/img]
Back to sleep it goes..

---

