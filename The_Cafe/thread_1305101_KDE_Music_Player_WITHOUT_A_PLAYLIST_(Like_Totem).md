---
title: "KDE Music Player WITHOUT A PLAYLIST (Like Totem)"
date: 2009-10-29
forum: The Cafe
---

### Post by coldReactive on 2009-10-29
I just want to know if there is a media player (like totem) for kde that does not have a playlist system? I'm getting annoyed when I have to click on a playlist item to play that track, when I could just open the file and have it play automatically and stuff. It also has to be able to repeat the media file over and over again.

This means:

-- No Rhythmbox,
-- No Amarok,
-- No XMMS2 (XMMS has this feature, but isn't in the repos anymore.)
-- etc.

If totem had a kde port, I would be glad. It has to be kde-based or cross-DE.

---

### Post by xuCGC002 on 2009-10-29
Dragon Player? :confused:

---

### Post by doorknob60 on 2009-10-29
VLC, not a KDE program but it's Qt so it looks and works fine.

---

### Post by RiceMonster on 2009-10-29
kmplayer

---

### Post by hoppipolla on 2009-10-29
Amarok I... oh ._.

lol


Juk! And!... oh :(

This is tough! lol


Just use something that is designed for video like Dragon or SMPlayer, or a more lightweight Mplayer frontend.

---

### Post by SuperSonic4 on 2009-10-29
VLC is my favourite, I just drag and drop it although it does use a playlist system

---

### Post by coldReactive on 2009-10-29
Results:

VLC - No Repeat Option (I know this by heart)
Dragon Player - No repeat option
KMPlayer - added a file to playlist, play button wouldn't play. (OGG File.), since it adds files to playlists, it auto-fails.

---

### Post by hoppipolla on 2009-10-29
> **coldReactive said:**
> Results:

VLC - No Repeat Option (I know this by heart)
Dragon Player - No repeat option
KMPlayer - added a file to playlist, play button wouldn't play. (OGG File.), since it adds files to playlists, it auto-fails.

I dunno man, just use Amarok 2.2 and remove the playlist. lol

Failing that, XMMS would do the trick even though it's old. So would some random XMMS2 frontend or an Mplayer frontend that is more focused on music :)

---

### Post by coldReactive on 2009-10-29
> **hoppipolla said:**
> I dunno man, just use Amarok 2.2 and remove the playlist. lol

Failing that, XMMS would do the trick even though it's old. So would some random XMMS2 frontend or an Mplayer frontend that is more focused on music :)

Removing the playlist doesn't allow me to choose a new track to play. The music player has to play the file I open, amarok doesn't do this.

Guess I'll just switch back to Ubuntu, again. -_- I was looking forward to KDE too.

---

### Post by hoppipolla on 2009-10-29
> **coldReactive said:**
> Removing the playlist doesn't allow me to choose a new track to play. The music player has to play the file I open, amarok doesn't do this.

Guess I'll just switch back to Ubuntu, again. -_- I was looking forward to KDE too.

aww nooooo! lol

KDEEEE!

Oh I dunno maaaan... what about this - [http://wiki.xmms2.xmms.se/wiki/Client:Promoe](http://wiki.xmms2.xmms.se/wiki/Client:Promoe)

---

### Post by coldReactive on 2009-10-29
> **hoppipolla said:**
> aww nooooo! lol

KDEEEE!

Oh I dunno maaaan... what about this - [http://wiki.xmms2.xmms.se/wiki/Client:Promoe](http://wiki.xmms2.xmms.se/wiki/Client:Promoe)

*has to compile* :|

Sorry, but no.

---

### Post by Falc7 on 2009-10-29
whats bad about using a gnome native application in KDE?

---

### Post by koleoptero on 2009-10-29
> **coldReactive said:**
> Results:

VLC - No Repeat Option (I know this by heart)

Do you? Click on the playlist button, click the repeat button to repeat 1 or all (whatever you wish), close the playlist window, start opening files.

Screenshot attached.

---

### Post by coldReactive on 2009-10-29
> **koleoptero said:**
> Do you? Click on the playlist button, click the repeat button to repeat 1 or all (whatever you wish), close the playlist window, start opening files.

Screenshot attached.

It still fails because it adds files to the playlist.

---

### Post by Xbehave on 2009-10-29
amarok -l, --load                Load URLs, replacing current playlist
amarok --queue                   Queue URLs after the currently playing track

---

### Post by koleoptero on 2009-10-29
> **coldReactive said:**
> It still fails because it adds files to the playlist.

Actually it only adds one, then replaces it with the next, so it's not like using the playlist at all. You just have to allow only one instance of it.

---

### Post by hoppipolla on 2009-10-29
one of these solutions just HAS to work lol

---

### Post by coldReactive on 2009-10-29
> **koleoptero said:**
> Actually it only adds one, then replaces it with the next, so it's not like using the playlist at all. You just have to allow only one instance of it.

The problem with VLC is that I might use it for DVDs, but that doesn't work, I have to use xine for DVDs.

---

### Post by dragos240 on 2009-10-29
> **coldReactive said:**
> Results:

VLC - No Repeat Option (I know this by heart)
Dragon Player - No repeat option
KMPlayer - added a file to playlist, play button wouldn't play. (OGG File.), since it adds files to playlists, it auto-fails.

VLC does have a repeat option! Go in the playlist, click on the song, and push loop once.

---

### Post by hoppipolla on 2009-10-29
I use quite a few Gnome apps in KDE anyway, like Pidgin, Filezilla, Chrome, Firefox and Nicotine. It's not the end of the world, I quite like them! :)

---

### Post by coldReactive on 2009-10-29
> **hoppipolla said:**
> I use quite a few Gnome apps in KDE anyway, like Pidgin, Filezilla, Chrome, Firefox and Nicotine. It's not the end of the world, I quite like them! :)

Pidgin and Firefox are not GNOME, nor is Chrome.

---

### Post by hoppipolla on 2009-10-29
> **coldReactive said:**
> Pidgin and Firefox are not GNOME, nor is Chrome.

lol you know what I mean, GTK apps.


EDIT -- and blah blah Firefox is XUL or some such, who cares I use Chrome anyway xD

---

### Post by samjh on 2009-10-29
smplayer
- written in Qt, so good in KDE
- has repeat function
- not dependant on a playlist

BTW, what's so bad about playlists?  Totem uses playlists too: when you open a file, it is automatically added into an empty playlist.

---

### Post by dmizer on 2009-10-29
> **coldReactive said:**
> It still fails because it adds files to the playlist.

I'm not sure why this is a problem. VLC automatically adds the files to the playlist, so it works exactly the same way totem does. The only difference would be in how you select the repeat option.

Understanding why the above is a problem might help us come up with a possible solution.

---

### Post by coldReactive on 2009-10-29
totem replaces the entire playlist, when you open a new file, with the new file, then, it automatically plays the new file.

This is the functionality I want, along with the repeat function, and no visualizations.

---

### Post by hoppipolla on 2009-10-29
> **coldReactive said:**
> totem replaces the entire playlist, when you open a new file, with the new file, then, it automatically plays the new file.

This is the functionality I want, along with the repeat function, and no visualizations.

I just tried this in Dolphin out of curiosity. KMPlayer fired up like a shot and played the track with no issues. It even replaced the playlist.

You can also play it embedded with Dolphin.

---

### Post by coldReactive on 2009-10-29
Like I said KMPlayer didn't play when I hit the play button, nothing happened.

[strike]SMPlayer plays, no sound, and gives an error box asking what version of mplayer I'm using (but I can't change this later if I pick the wrong one.)[/strike]

nevermind, audio was somehow muted. Thanks for smplayer, now I can go back to KDE :3

---

### Post by samjh on 2009-10-29
...(retracted after edit)...

What distro are you using, by the way?

---

### Post by coldReactive on 2009-10-29
> **samjh said:**
> ...(retracted after edit)...

What distro are you using, by the way?

I'm about to switch back to kubuntu from ubuntu. I was using Kubuntu for a while, but had this media player annoyance I just couldn't get over.

---

### Post by hoppipolla on 2009-10-29
I'm glad SMPlayer works :)

It's a wicked player! Still strange that you had problems with KMPlayer, but oh well, if you've found a solution then cool :)

---

### Post by SuperSonic4 on 2009-10-30
> **hoppipolla said:**
> I just tried this in Dolphin out of curiosity. KMPlayer fired up like a shot and played the track with no issues. It even replaced the playlist.

You can also play it embedded with Dolphin.

Haha, I never knew that! Many thanks :popcorn:

---

### Post by chucky chuckaluck on 2009-10-30
you might find kaffeine totem-esque.

---

