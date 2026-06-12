---
title: "I hate Real-Player."
date: 2009-01-17
forum: The Cafe
---

### Post by scragar on 2009-01-17
I'm sorry if this doesn't belong here, or on these forums at all, but the real player forums won't let me post a new thread, so I'm going to ask my question and rant here.

OK, so I got given a video, it was a real media video, so I downloaded and installed real player(via the .bin on their site) since VLC wouldn't work. This is possibly the stupidest thing I have ever done to any of my machines, before now anything I have done that has caused harm has resulted in my learning something, real media is just plain annoying.

OK, long story short I want to install ALL of realplayer's annoying little bits, I want to remove it from my menu's(I use XFCE, so no menu editor of that kind), I want to change all my mp3 and avi icons back to the defaults, instead of the stupid real player icon, I want to stop it being the default for various media formats(I have fixed a few, but it's still default for so much). So that's the question, how do I uninstall the whole thing? I've already deleted it's entry in /opt but that's about it. Anyone got any clues on where to start for cleaning things up? Or should I just give up and reinstall(I have a list of everything installed, so I think I could reinstall in an hour or so...)?

---

### Post by BGFG on 2009-01-17
```

sudo apt-get purge realplayer* 

```

I learnt my lesson with Real'anything' in windows. if it's realmedia i can do without it.

---

### Post by cardinals_fan on 2009-01-17
> **scragar said:**
> 
OK, long story short I want to install ALL of realplayer's annoying little bits, I want to remove it from my menu's(I use XFCE, so no menu editor of that kind), I want to change all my mp3 and avi icons back to the defaults, instead of the stupid real player icon, I want to stop it being the default for various media formats(I have fixed a few, but it's still default for so much). So that's the question, how do I uninstall the whole thing? I've already deleted it's entry in /opt but that's about it. Anyone got any clues on where to start for cleaning things up? Or should I just give up and reinstall(I have a list of everything installed, so I think I could reinstall in an hour or so...)?
[http://ubuntuforums.org/showpost.php?p=4760919&postcount=5](http://ubuntuforums.org/showpost.php?p=4760919&postcount=5)

---

### Post by Montblanc_Kupo on 2009-01-17
Sorry I can't help with the file association problem... I know in Ubuntu with GDM you can just right click on a file and tell it what you want it to open with by default.

For future reference though, MPlayer does a great job opening realplayer files without the horror of dealing with the actual realplayer.

---

### Post by scragar on 2009-01-17
> **cardinals_fan said:**
> [http://ubuntuforums.org/showpost.php?p=4760919&postcount=5](http://ubuntuforums.org/showpost.php?p=4760919&postcount=5)

Thank you so much, you've saved me a reinstall.

---

### Post by cardinals_fan on 2009-01-17
> **scragar said:**
> Thank you so much, you've saved me a reinstall.
No problem.  That search box is ridiculously handy :D

---

### Post by scragar on 2009-01-17
> **Montblanc_Kupo said:**
> Sorry I can't help with the file association problem... I know in Ubuntu with GDM you can just right click on a file and tell it what you want it to open with by default.

For future reference though, MPlayer does a great job opening realplayer files without the horror of dealing with the actual realplayer.

I have used Mplayer before for real media files, it took some effort to get it set up though, I thought installing real would save me time, I was really wrong about that.

You can do the same thing to change the default in XFCE as well, it's just that I hate the idea of doing it for every single file format to restore it to what I want: mp3, mp4, mkv, avi, ogg, ogv, ogm, wav, flac... Total pain in the rear end.

---

### Post by scragar on 2009-01-17
> **cardinals_fan said:**
> No problem.  That search box is ridiculously handy :D

It's 2am in the morning and I've been playing about with it for the better part of an hour, forgive me for being a bit slow on the uptake. I did try a google search, and got about 300 tutorials for how to do the same thing to windows, and a ton of guides telling you to just delete the folder in /opt when I added 'linux' as a search term, I never thought to search these forums using the search box here.

---

### Post by speedwell68 on 2009-01-17
Never had a problem with Realplayer, it installed fine on my PC using the *.deb file from their website.  No problems with file associations, I believe it asks you about that in the install.  I use it to listen to he BBC Worldservice News feeds.  One of those great bits of software that just works.

---

### Post by richg on 2009-01-17
I love real player. Works fine for me.

Rich

---

### Post by linux_nc on 2009-01-17
it works fine for me for real media

---

### Post by vishzilla on 2009-01-17
People still use Real-Player?

---

### Post by hanzomon4 on 2009-01-17
> **vishzilla said:**
> People still use Real-Player?

Fo ReaL!!

---

### Post by mrgnash on 2009-01-18
It's a useless piece of junk that hasn't worked any of the times I have tried it, so I hate it too. Mplayer is the be-all and end-all of media players.

---

### Post by schauerlich on 2009-01-18
Buffering...

---

### Post by hoopz23 on 2009-01-18
yeah i gave up on real player after it screwed up my computer back in the day.

---

### Post by RiceMonster on 2009-01-18
I remember when real player changed all my icons too. That was annoying. I can't figure out why anyone would want to use it anyway. There really isn't anything good about it.

---

### Post by Polygon on 2009-01-19
vlc-1.0.0-git can play real media/real audio files. so soon the need for real player will disappear =)

---

### Post by RiceMonster on 2009-01-19
Mplayer plays them just fine already. I think it's a little harder to do it in Ubuntu though.

---

### Post by uberdonkey5 on 2009-01-19
Real Player has always been super with me. Never had my icons change?! My icons are whatever I select them to be in preferences?! The real player media format is also likely to be around for a long while. For me it starts quickly and plays things perfectly. I'd love to be more of a purist and just use mplayer, but to be honest I'm a vlc/rythmbox/realplayer person.

---

### Post by ssj4Gogeta on 2009-01-19
> **scragar said:**
> OK, long story short I want to install ALL of realplayer's annoying little bits, I want to remove it from my menu's(I use XFCE, so no menu editor of that kind), I want to change all my mp3 and avi icons back to the defaults, instead of the stupid real player icon, I want to stop it being the default for various media formats(I have fixed a few, but it's still default for so much). So that's the question, how do I uninstall the whole thing? I've already deleted it's entry in /opt but that's about it. Anyone got any clues on where to start for cleaning things up? Or should I just give up and reinstall(I have a list of everything installed, so I think I could reinstall in an hour or so...)?

<sarcastic comment>
Double click on "add/remove progs", find the entry for Real Player, click on "remove".
</sarcastic comment>:P:P:P

no offense:)

---

### Post by Skripka on 2009-01-19
> **vishzilla said:**
> People still use Real-Player?

No Kidding.:confused::confused::confused:

---

### Post by scragar on 2009-01-19
Real player on it's own isn't that bad, I might actually still have it installed, if it didn't take liberties with my system, I never wanted it to assign itself the default player for everything, or to change my icons, I just wanted something that would play real media files when I wanted it to.

That's the big problem with real if you ask me, they think too highly of themselves, not content with identifing themselves as having the "best" media player they enfoce it on other people.

What happened to those good old days when installing a program would not change all your settings to what the program developers think you should have. It shows a complete lack of trust and respect for the program users, and honestly, when Real can't even get the player up to scratch with VLC in terms of lightweight and functional I have to complain.
(What is with real media having two playlists, one the real playlist, and the other being a secret one which works only when you open something from file, I can't add anything to the second playlist because of the way it works, if I want to build a new playlist I can't unless I delete the current one, and built the new one there, then double click the first item in it so it knows what to start playing, talk about counter intuitive)

---

### Post by wmcbrine on 2009-01-19
Real Player: Over a decade of suck, and still going. It's amazing.

---

### Post by hanzomon4 on 2009-01-19
The OSX version sucks less but I never use it.... Real is like the popup spam of the media world.

---

### Post by eragon100 on 2009-01-19
I use realplayer, but only for real media files.
It works fine for me: installed with the .deb package, and the file
assiocations are only set to real player for... real media files!
Everything else remains VLC :popcorn:

Some Naruto episodes on narutochaos.com are in real media format, so I need to have it installed.

---

### Post by bash on 2009-01-19
I remember RealPlayer from my Windows days. Was version 3 or 4 the first time I saw it. And with every version it seemed to get more bloated, naggy and annoing. Sadly a lot of computers that you have to use (Uni, school, internet cafe, ...) come with it as the default video player. 

Although they seem to have gotten better since version 10, for me it's still: If it says Real, I stay real far away from it.

> **EDavidBurg said:**
> Buffering...

At least in Windows I was happy when I finally got to the feared buffering .... Before I just had to click myself through 2 wizards, deny for the n-th time 3 memberships offers and try to convince RealPlayer that I did NOT (shocker eh?) want to sign up for a realmedia or whatever it is called account.

---

