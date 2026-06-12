---
title: "Audio Player that can &quot;cue tracks&quot;"
date: 2009-12-12
forum: Ubuntu Studio
---

### Post by beastrace91 on 2009-12-12
Howdy All,

I work for a small theatre company and my boss would like to move away from using CDs to play our audio from and move to a computer/MP3 player. I suggested my netbook

What I am looking for is an audio play that has a feature to "cue up" (get it ready to play but have it paused) the following track when the previous on ends (instead of playing straight through like they all do by default).

I was poking around the settings in Rhythmbox but did not see a setting like this - anyone have any ideas if it has it or maybe another audio player that has this feature?

Thanks,
~Jeff

---

### Post by kmac on 2009-12-12
Amarok has this feature. Right click on the song previous to your break and there will be an option..


```
$ sudo apt-get install amarok
```

---

### Post by Stochastic on 2009-12-12
You could also use a more production-oriented player like Mixxx, IDJC, or Rivendell (that may be overkill, but it certainly has that ability).

---

### Post by beastrace91 on 2009-12-12
Thanks for the suggestions all, I'll give those a try and see which I like best.

~Jeff

---

### Post by beastrace91 on 2009-12-12
Wow. None of the above do what I am looking for/need them to do :(

Amarok "queues" up the next track (as opposed to cueing which is different/what I need) - basically it just tells the player which track to play next. So it doesn't stop on the in-between :-/

The other ones suggested where a bit overkill for what I need - and I could not find the cueing feature I need in either of them :(

~Jeff

---

### Post by seeker5528 on 2009-12-12
I think a lot of players have an enqueue option, whether you have the option to enqueue files on the context menu when you right click in the file manger is another question.

There is a Nautilus script [here]( http://linux.softpedia.com/get/Multimedia/Audio/Enqueue-in-Audacious-37529.shtml) to provide support to enqueue files in Audacious from Nautilus, I would expect in seeing how it is done you could adapt it to other players easily enough.

Don't know what players might have an option to enqueue to a queue instead of a playlist, or failing that have an option to limit the playlist to X number of entries so previously played stuff would get pushed out as new stuff was enqueued it's not something I've had a reason to look for.

Also the players themselves, when you browse for files to add to the playlist, may have the option to enqueue the files if you right click a selected group of files in the file selector. If you are at the computer adding files to the play list it should be easy enough to remove stuff that has already been played.

I haven't really looked at the MPD stuff (Music Player Daemon), but it has several clients and one of those may fit your needs.

I don't know what the difference between cueing and queueing is, they sound the same to me. ;)

OK, re-reading the thread I think I might see what you mean. In Amarok, if you right click a track in the playlist one of the options is to stop playing when the track ends. Then when you want to start playing again you could double click the track in the playlist where you want it to start playing again.

Later, Seeker

---

### Post by beastrace91 on 2009-12-13
> **seeker5528 said:**
> if you right click a track in the playlist one of the options is to stop playing when the track ends. Then when you want to start playing again you could double click the track in the playlist where you want it to start playing again.

Ahh yes - I had noticed this feature. Its not ideal but it will work somewhat. I'm just trying to limit my mouse clicks/movements because during a show I'd be running it off a netbook with just a tiny touch pad to navigate while trying to run a slew of microphones at the same time xD

~Jeff

---

### Post by addeboy on 2010-01-19
If you haven't found yet a solution in this month, maybe Audacious will suit your needs. It has 2 options: "No Playlist Advance (Ctrl+N)" and "Stop After Current Song (Ctrl+M)" which I think are what you need.

---

### Post by beastrace91 on 2010-01-19
> **addeboy said:**
> If you haven't found yet a solution in this month, maybe Audacious will suit your needs. It has 2 options: "No Playlist Advance (Ctrl+N)" and "Stop After Current Song (Ctrl+M)" which I think are what you need.

I'll have to give that a try.

Thanks Much,
~Jeff

---

