---
title: "Rhythmbox Roadmap"
date: 2008-06-02
forum: The Cafe
---

### Post by b3n87 on 2008-06-02
Hi guys

I must admit, I've grown to like Rhythmbox, i never used to like it but I do now.

Anyway I was just wondering, does anyone know what they have in mind for new features in rhythmbox, I cant find anything.

On a second note, what would you like to be added to Rhythmbox if it was up to you?

But more im more curious on my first point, anyone know whats to come?

---

### Post by swoll1980 on 2008-06-02
Equalizer, I want it. I don't know if it's coming, or not

---

### Post by b3n87 on 2008-06-02
yeah my friend wants that badly to. hes a recent ubuntu convert and was surprised that it didnt have one.

your sig quote is classic btw

---

### Post by RiceMonster on 2008-06-02
> **swoll1980 said:**
> Equalizer, I want it. I don't know if it's coming, or not

Agreed. If an audio player has no equalizer, I immediatly uninstall it. I also had problems editing tags in Rhythembox. Untill both those problems don't exist, I won't use it.

---

### Post by swoll1980 on 2008-06-02
> **b3n87 said:**
> 

your sig quote is classic btw

Yeah. W is quite the character.

---

### Post by swoll1980 on 2008-06-02
> **RiceMonster said:**
> Agreed. If an audio player has no equalizer, I immediatly uninstall it. I also had problems editing tags in Rhythembox. Untill both those problems don't exist, I won't use it.

Yeah I use Exaile. It's a nice GTK music player with an eq

---

### Post by banjobacon on 2008-06-02
Someone developed a Rhythmbox equalizer plugin, but I'm not sure if it works. [http://cs.helsinki.fi/u/ttokalli/rb-plugins/](http://cs.helsinki.fi/u/ttokalli/rb-plugins/)

---

### Post by geoken on 2008-06-02
Just tried the plugin, it works but it's not ideal.

To access it you need to go to plug ins > equalizer > configure, there's no panel or menu shortcut for it. Also, the changes aren't live. You need to make changes, then disable and re enable the plugin. Also, the disable-re enable cycle will make the current track restart.

---

### Post by banjobacon on 2008-06-02
> **geoken said:**
> Just tried the plugin, it works but it's not ideal.

To access it you need to go to plug ins > equalizer > configure, there's no panel or menu shortcut for it. Also, the changes aren't live. You need to make changes, then disable and re enable the plugin. Also, the disable-re enable cycle will make the current track restart.

No wonder it never worked for me. I didn't bother dis-/re-enabling. The  again, I don't really use equalizers, so I didn't really care much. This seems to be an important feature for many people, though, so maybe someone with know-how and free time will spot this plugin and contribute to it. Maybe bugzilla will draw more attention to it.

---

### Post by banjobacon on 2008-06-02
I guess one feature I'd like to Rhythmbox is better tagging fuctionality. I currently use Ex Falso for tagging/remaning, but I'd prefer to just use Rhythmbox, if they could duplicate the functionality in a sane interface.

---

### Post by geoken on 2008-06-02
I found this on launchpad [https://code.launchpad.net/~jmillikin/rhythmbox/equalizer-plugin]("https://code.launchpad.net/~jmillikin/rhythmbox/equalizer-plugin")

I'm in the same boat as you though, I've never really thought twice about an equalizer.

---

### Post by pt123 on 2008-06-02
There was plans to add glitz features i.e. coverflow. There was a page detailing it (don't have the link to it).

Other ideas included adding tags like how you tag mail in Gmail. I.e. you can have multiple tags for a song. There by building more complex smart playlists.

---

### Post by hanzomon4 on 2008-06-03
Why is everything audio related painfully difficult on linux, like getting an eq or god forbid listening to more then one thing at a time?

---

### Post by swoll1980 on 2008-06-03
If you want an eq use Exaile as far as listening to more than one thing at a time I've done it a few times on accident, and it worked fine, though I don't know why someone would choose to hear several things at the same time.(I get enough of that from the kids)  That's the great thing about people, they are a unique in there own way.

---

### Post by grossaffe on 2008-06-03
one feature i'd like is for it to not crash when i plug in my mp3 player.

---

### Post by AmishFury on 2008-06-03
proper replaygain support... if exaile's playlist sorting wasn't so [hurrrr] and if it didn't slow down anytime i try to do anything with my 4000+ track playlist i'd be using it purely on proper replaygain options (ability to choose between album or track gain, preamp gain, gain adjustment for files without replaygain tags... rhythmbox only has a hidden checkbox but it handles my library and sorts my playlist properly)

---

### Post by muep on 2008-06-03
The developers of Rhythmbox have said that there is no intention of getting an equalizer into Rhythmbox. Instead, if an equalizer is needed, it would be much more efficient to make it a Pulseaudio plugin, so that every player wouldn't need to duplicate the effort.

Rhythmbox is meant for searching and playing music, not fine-tuning your audio system.

---

### Post by 50words on 2008-06-03
> **muep said:**
> The developers of Rhythmbox have said that there is no intention of getting an equalizer into Rhythmbox. Instead, if an equalizer is needed, it would be much more efficient to make it a Pulseaudio plugin, so that every player wouldn't need to duplicate the effort.

Rhythmbox is meant for searching and playing music, not fine-tuning your audio system.

Good point.

---

### Post by geoken on 2008-06-03
> **muep said:**
> 

Rhythmbox is meant for searching and playing music, not fine-tuning your audio system.

While I never wanted an equalizer, I can understand where those people are coming from and I think you've mis-characterized them with the above comment.

It isn't about wanting the audio player to fine tune the audio system. It's about wanting song by song control over how music sounds. I have some songs/DJ sets where the bass is simply too heavy and I get a much better listening experience turning that songs bass down. The very next song could be the opposite, with highs that are too high. I don't think they care how it's being done (ie. equalizer built into app, or app leveraging some system wide equalizer by having the ability to control it). All they really want is for the audio player to have control over equalization on some level because it's unlikely that a system wide equalizer will have the ability to remember equalizer settings for a specific song and mod the equalizer when said song is playing.

---

### Post by banjobacon on 2008-06-03
> **AmishFury said:**
> proper replaygain support... 

How do you set replaygain values? On Windows, I'd use foobar2000, but I haven't found a comparably simple solution for Ubuntu.

---

### Post by AmishFury on 2008-06-03
> **banjobacon said:**
> How do you set replaygain values? On Windows, I'd use foobar2000, but I haven't found a comparably simple solution for Ubuntu.

exaile has full replay gain options
audacious has full replay gain controls
rhythmbox is an on/off checkbox you can get to with gconf-editor (i assume it uses track gain)


it's all about the player you use

---

### Post by banjobacon on 2008-06-04
> **AmishFury said:**
> exaile has full replay gain options


How do I *set* replaygain values in Exaile? In foobar2000, there was an option in the context menu: I'd select songs, right click, click "Set Album Gain" or something like that, and the program would calculate the values and write them in the tags. I don't see anything in Exaile or Rhythmbox that does this; as far as I can tell, they only *read* replaygain tags.

---

### Post by pt123 on 2008-06-04
me to have been wondering how to do this

---

### Post by quinnten83 on 2008-06-04
i would like the coverflow plugin to work right and better playlist handling.

---

### Post by AmishFury on 2008-06-04
no idea how one would set replaygain values in linux... i do all my ripping and encoding in windows

---

### Post by Larir on 2008-06-04
Random by album not just by song (selects a random album, plays all the songs on it and randomly selects the next album).

I guess that's all. That's the only feature I'd rather use Amarok for :D

Hmm, otherwise I think Rhythmbox is quite good for me. I don't have an mp3 player so don't know how those things work with the box. It's good for playing anything I have... oggs, mp3s, etc.

Ya, I think random by the album should make me happy. Maybe I should ask for it...!!!

Oh yeah, the cover plugin ***** up sometimes and brings the wrong cover for an album...

**edit:** Thought of another thing... A choice for when you press the X to close the application it won't close but minimize it to the systray. I know it's not much 'cause you can just click the tray icon anyway, but at first I didn't know such a thing was possible and would always accidentally close the box when I was supposed to minimize it... Just something for the people that're used to winamp I guess.

---

### Post by pt123 on 2008-06-05
I did a fewe searches you can do replaygain by using a package called mp3gain
This article has instructions on how to use it
[http://www.linux.com/articles/59957](http://www.linux.com/articles/59957)

---

### Post by af20001 on 2008-06-05
If you encode to FLAC, you can use the built-in metaflac tools to set replay gain.

On an album by album basis you can run:

metaflac --add-replay-gain *.flac

within the folder containing the album.

If you want to apply it to your whole collection, this should work:

ls $dir/*.flac >/dev/null 2>&1 && metaflac --add-replay-gain $dir/*.flac

VorbisGain is also available for running against .ogg files.

Both metaflac and VorbisGain do not change the actual audio files, they just insert tags containing the volume adjustment levels.

---

### Post by banjobacon on 2008-06-05
> **pt123 said:**
> I did a fewe searches you can do replaygain by using a package called mp3gain
This article has instructions on how to use it
[http://www.linux.com/articles/59957](http://www.linux.com/articles/59957)

MP3gain write ape tags rather than id3v2 tags, which can cause some confusion in some mp3 players, apparently. I was playing around with it last night, and it seems to work well, otherwise. 

I also read that LAME does some sort of replaygain analysis, but I'm confused as to whether it writes the tags in such a way that players can use them to apply the proper gain.

---

### Post by knavarathna92 on 2008-06-05
support for video podcasts and music videos.  I realize that rythymbox is an audio player but If it's also intended for management of some music players, I would like to manage it in one application.  Currently I have to use Rythymbox for audio, Gpodder for podcast syncing, GTKpod for music videos and Gpixpod for photos.  Rythymbox is nice, it just needs to grasp the more advanced needs of it's users.:)

---

### Post by quinnten83 on 2008-06-05
> **knavarathna92 said:**
> Rythymbox is nice, it just needs to grasp the more advanced needs of it's users.:)

It's a gnome application they don't do advanced!!!

---

### Post by banjobacon on 2008-06-06
> **pt123 said:**
> I did a fewe searches you can do replaygain by using a package called mp3gain
This article has instructions on how to use it
[http://www.linux.com/articles/59957](http://www.linux.com/articles/59957)

So, I've decided to go with mp3gain. Can someone who is bash literate tell me what the command given in the article will do?

```
 find . -name *mp3 -exec mp3gain -a -k {} \; 
```

Will this command: (1) go through my collection of mp3s of albums, kept in separate folders, and analyze each album separately; or (2) analyze all the mp3s it finds as one huge album?

EDIT: I decided to test it out on a small collection of albums. The command gets mp3gain to analyze files one by one (not what I want), not as albums (what I do want).

---

