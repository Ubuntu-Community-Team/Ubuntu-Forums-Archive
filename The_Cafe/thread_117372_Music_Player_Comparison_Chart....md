---
title: "Music Player Comparison Chart... ?"
date: 2006-01-14
forum: The Cafe
---

### Post by aysiu on 2006-01-14
Does anyone know of a chart or site that compares all the major Linux music players out there? I already did [this Google search](http://www.google.com/search?hl=en&q=comparison+rhythmbox+juk+amarok+noatun+beep+xmms&btnG=Google+Search) and not much popped up.

I'd be interested in seeing something that had a list of features and checkboxes for which players had which features. Stuff that I've been thinking about...

[i]Inline tag editing
Ability to rate songs
Ability to sort songs by various criteria
Play counts
Global keyboard shortcuts for song navigation
Scanning / library methods
Native desktop
Ability to rescan manually
Playlist capabilities
iPod / MP3 player integration[/i]

So far I'm in a toss-up between XMMS, JuK, Rhythmbox, and AmaroK. 

I like the stability of **XMMS**. I'm in a bit of a love-hate relationship with libraries and scanning. I like that you don't have to wait for a rescan when you pop up XMMS, but I don't like that you need to manually add songs each time you get new ones. And XMMS doesn't have global keyboard shortcuts, as far as I know.

**JuK** I like. It's simple and fast (at scanning, at navigating). Unfortunately, it's a bit too barebones. You can't rate songs. And lately, for some strange reason, it freezes up Gnome and XFCE (but not KDE, its native environment).

**Rhythmbox** is my current choice. I like its general stability. Its inability to refresh songs automatically and edit ID3 tags inline kind of annoy me, but it's mapped to my global keyboard shortcuts, and it lets me rate songs.

**AmaroK** is obviously the most fully featured music player, but for some strange reason it's extremely unresponsive on my computer. If I use a keyboard shortcut to move to the next song, it takes literally two seconds for AmaroK to move to the next song. Maybe it's because I have over 8000 songs, but JuK and Rhythmbox seem to be able to handle the large music collection just fine. Other than that, it's tough to beat AmaroK--smart playlists, lyrics fetching, play counts, yada yada yada.

What do you use, and why? Oh, and if you know of a comparison chart or are interested in making one, please let me know.

---

### Post by UbuWu on 2006-01-14
Amarok and totem

Comparison of a lot of media players (not only for linux):
[http://en.wikipedia.org/wiki/Comparison_of_media_players](http://en.wikipedia.org/wiki/Comparison_of_media_players)

---

### Post by aysiu on 2006-01-14
[QUOTE=UbuWu]Amarok and totem[/quote] *Totem*. I forgot Totem. Whoops. I can't believe I gave up Totem's spot for LSongs. Oh, well.

> 
Comparison of a lot of media players (not only for linux):
[http://en.wikipedia.org/wiki/Comparison_of_media_players](http://en.wikipedia.org/wiki/Comparison_of_media_players) I think that chart's a good start. I'm looking for something that's focused more on *features* than platform support (what tags does it support, what operating systems, what file types). Thanks, though.

---

### Post by super on 2006-01-14
rhythmbox
totem
xmms
bmp
vlc
eclair

are all installed on my box currently. and i use all except b,p on a regular basis.

---

### Post by majikstreet on 2006-01-14
I haven't voted because I switch from player to player a lot. I use XMMS and Beep-Media-Player a lot now, but I LOVE rhythmbox, but I broke it trying to upgrade it... so.....

---

### Post by bored2k on 2006-01-14
QuodLibet

---

### Post by ember on 2006-01-14
It's QuodLibet for me, too. And Totem-Xine for some unruly Audio-CDs. Yet I'll be willing to contribute to a comparison chart. Yet not today - sometimes even computer people have to sleep ;)

---

### Post by aysiu on 2006-01-14
I've never even *heard* of Quodlibet, but two responses already cited it... I'm going to give that a try!

**Edit**: No joy. Quodlibet doesn't do global keyboard shortcuts.

---

### Post by Sheinar on 2006-01-14
I use Beep Media Player mostly. Never could stomach using Rythmbox.

---

### Post by drizek on 2006-01-14
the same thing happens with me with amarok. i think it is just a bug, not a performance problem. i only noticed it in the latest release, it worked fine before. either way, it really isnt a problem for me.

---

### Post by Azion on 2006-01-14
i've only been using XMMS lately, first one I used

---

### Post by MetalMusicAddict on 2006-01-14
Im rather unsatisfied with the state of audio players for linux so I switch alot trying to find one that suits me best. So far Muine works very much like I listen to music. Album based. I am **VERY** much looking forward to [Songbird]("http://www.songbirdnest.com/"). Go to the link. It looks really promising.

[IMG]http://www.songbirdnest.com/files/images/library_context_menu.thumbnail.png[/IMG]
[BIG]("http://www.songbirdnest.com/files/images/library_context_menu.png")

I kinda wonder about the lack of visualizations. *Looks* like AmaroK has some but needs libvisual. Doesnt look to be in the repos.

---

### Post by Kerberos on 2006-01-14
[QUOTE=aysiu]*Totem*. I forgot Totem. Whoops. I can't believe I gave up Totem's spot for LSongs. Oh, well.
[/QUOTE]
Wow!  Totem actually opens something! :D

---

### Post by potrick on 2006-01-16
Noticed lsongs on the list...has anyone gotten this to work in Ubuntu? Just wondering.

---

### Post by BoyOfDestiny on 2006-01-16
I also use uade (has plugins for xmms and beep) thought I'd mention it.

[http://zakalwe.virtuaalipalvelin.net/uade/](http://zakalwe.virtuaalipalvelin.net/uade/)

I'm just hoping gstreamer will add support for nsf's and spc's (there was a gstreamer .8 plugin, but looks like it's abandoned). In the meantime I've been using audio overload... it's not gpl, although some parts are lgpl... 

At least the gstreamer SID plugin they have is useable (tested it in rythm box). :)

---

### Post by Jay_Dogg on 2006-01-16
Quod Libet, it's got everything I need.

---

### Post by doclivingston on 2006-01-16
[QUOTE=BoyOfDestiny]I also use uade (has plugins for xmms and beep) thought I'd mention it.

[http://zakalwe.virtuaalipalvelin.net/uade/](http://zakalwe.virtuaalipalvelin.net/uade/)

I'm just hoping gstreamer will add support for nsf's and spc's (there was a gstreamer .8 plugin, but looks like it's abandoned). In the meantime I've been using audio overload... it's not gpl, although some parts are lgpl... [/QUOTE]

There was actually a discussion about this ~4 weeks ago in the gstreamer IRC channel.

The problem is that gsteamer is stream based, and the was that uade work doesn't fit with that. uade isn't a decoder library or anything, it emulates the amiga applications, and it only works with xmms due to a lot of hacks. Unless version two (which was only released the other week) changes that, it would be a fairly huge effort to make a gstreamer plugin.

---

### Post by frodon on 2006-01-16
Don't forget muine, it's really nice ;) : [http://muine.gooeylinux.org/](http://muine.gooeylinux.org/)

---

### Post by Ampersand on 2006-01-16
I'm between XMMS and BMP. XMMS has more plugins available from the repositories, but BMP has better Japanese text support. I use Alsaplayer if I just want tom just play through a directory of music.

Not a player in itself, but I also use JGay for selecting a few hours of music to go on my mp3 player.

---

### Post by Spie on 2006-01-16
Take a look at Banshee. It's really nice. Ripping, tag editor, CD writing, audioscrobbler support, rate songs, play counts, very good iPod support, etc etc. And all in a gnome-like environment.
Mono based, and it is in rapid development.

---

### Post by Wolki on 2006-01-16
> **frodon]Don't forget muine, it's really nice  said:**
> http://muine.gooeylinux.org/[/url]

I second that. Though I use Aamarok too, as it's alarm clock plugin works ^^;;

Good news for Muine fans, btw: [http://www.tenslashsix.com/?p=104](http://www.tenslashsix.com/?p=104)

---

### Post by psychicdragon on 2006-01-16
I use Quod Libet. The album list mode is nice.

I used to be quite happy with Muine, it's probably got the best interface of any music player I've seen, but it fails to fully load my music library. For some reason it ignores over half of my Ween albums, that just won't do.

---

### Post by PuNGS on 2006-01-16
amaroK works perfectly for me, so I'm sticking with it.

---

### Post by Pancetilla on 2006-01-16
I'm using ogg123 :oops:

---

### Post by mips on 2006-01-16
Sorry, about to go slightly off topic. In windows I really love winamp and would like to see xmms catch up to winamp. I like the integrated ripper and whish xmms could do the same. I need a good ripper that offers the different VBR quality levels although I find VBR standard sufficient for my PC listening.

---

### Post by aysiu on 2006-01-16
I don't think that's off-topic at all.
Well, after trying Muine and Quodlibet, I'm sticking with Rhythmbox for now.

**Main things I dig about Rhythmbox:**

Doesn't crash my Gnome or XFCE (unlike JuK). Something weird happens where all of a sudden none of my keyboard keys work, my right-click doesn't work (left-click works fine), and I can't left-click on the Gnome foot menu anymore.

Has ratings and playcounts (unlike JuK) and the playcounts count by the end of the song being reached, not the beginning (unlike AmaroK)

Includes Genres in the library listing (unlike Quodlibet)

Uses the multimedia keys defined in *System > Preferences > Keyboard Shortcuts.* I searched all around these forums to see if there was a solution to getting these keys to work with other players, but I found nothing. (Unlike Quodlibet, XMMS, Beep, Muine)

Doesn't take forever to load my 8500+ songs music collection (unlike Quodlibet)

**Main things I hate about Rhythmbox**:

I have to use EasyTag (i.e., a separate application) to retag songs, and Rhythmbox doesn't necessarily recognize all tag changes (particularly genre changes), even if I change both ID3v1 and ID3v2 tags. So I end up having to manually edit the ~/.gnome2/rhythmbox/rhythmboxdb.xml file.

There's no "delete song" option. I can delete it from the library, but I actually have to track down the file in the folder to delete the song. So when I detect duplicates, it's an extra few steps to flush them out.

The way to rescan the library is to "add" the folder that's already been added... weird, and that folder takes a long time to load up (not the refreshing, just the loading, as I have all 8500+ files in one folder... no subfolders).

So, for now, I'm sticking with Rhythmbox.

---

### Post by frodon on 2006-01-17
Wow, i really agree with you aysiu, i like muine but i'm also stick with rythmbox. I think the next release of ryhmbox will be really great if developers improve the behaviour about tags and song removing.

Who use banshee here ?

---

### Post by mcduck on 2006-01-17
I think that MPD should be in the list too :D

That's what I'm using most of the time. Amarok and XMMS are both nice too.

---

### Post by Galoot on 2006-01-17
I generally use xmms, but only because I have limited space and only load a few hundred songs from my collection to the hard drive at a time.

The day I get a more modern PC (or at least a hard drive larger than 8GB) is the day I'll start looking into something with more features.

+bookmarks thread+

---

### Post by NiceGuy on 2006-01-17
I use muine because its simple and works! My only grips are that it cant play wma's (so I have to convert them which is a pain!). BMPx looks like it has lots of potential but is VERY unstable at the moment.

---

### Post by malmjako on 2006-01-18
For streamed music I use gxine (mostly together with streamtuner).

---

### Post by george_apan on 2006-01-18
As far as I know there is no linux player that supports what I consider the bare essentials for a music player. These are:

1. at least mp3, vorbis, flac support
2. gapless playback for lame mp3s and everything else
3. APEv2 tags in mp3s
4. replaygain support for any supported filetype (that includes replaygain info in APEv2 tags in mp3s)
5. a fast loading database.

Therefore I'm stuck with using foobar2000 with wine. So it's "Other" for me.

---

### Post by exchequer598 on 2007-10-25
I used AmaroK, but then I switched to Exaile. I love AmaroK, but couldn't live with a KDE app on GNOME! Exaile's got a long way to go, though!

---

