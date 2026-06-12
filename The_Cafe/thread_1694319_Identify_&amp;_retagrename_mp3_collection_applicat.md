---
title: "Identify &amp; retag/rename mp3 collection application?"
date: 2011-02-24
forum: The Cafe
---

### Post by mips on 2011-02-24
I've been wanting to identify & retag my mp3 music collection which is in total chaos.

I need an application that will:
1. Identify the song as osme have no details whatsoever, based on a online database of sorts. I suspect it will have to do some form of comparison of the content.
2. Retag/rename all songs in the format of Artist-Album-Song.
3. The processed files must be stored in a new folder/location.

Anybody go any suggestions for something that can do the job well?

I know of a few windows apps like MediaMonkey etc but would prefer a linux tool.

PS. I though about posting this in the Multimedia & Video forum but dunno if it's the best place for it. So mods if you think this is in the wrong place feel free to move it.

---

### Post by lykeion on 2011-02-24
EasyTag is an excellent tag editor. Install it via Ubuntu Software Center. It uses online CD database services musicbrainz and freedb. If you'll spend 30 minutes with it to learn how to rename files, fill tags, etc you'll find it will get your job done.

---

### Post by mips on 2011-02-24
> **lykeion said:**
> EasyTag is an excellent tag editor. Install it via Ubuntu Software Center. It uses online CD database services musicbrainz and freedb. If you'll spend 30 minutes with it to learn how to rename files, fill tags, etc you'll find it will get your job done.

Does EasyTag have a acoustic fingerprints database like MusicBrainz Picard?

I have installed Cowbell, EasyTag, MusicBrainz Picard so far but just want to find out which will be the best for the job.

I have some really obscure music in my collection, african, arabic, bulgarian, french etc so I'm not that optimistic. Hence the acoustic fingerprint requirement.

Thanks for your help.

---

### Post by lykeion on 2011-02-24
No, I don't think EasyTag does that. And regarding best tool for the job, why don't you try them and see for yourself which one is best for you?

---

### Post by mips on 2011-02-24
> **lykeion said:**
> And regarding best tool for the job, why don't you try them and see for yourself which one is best for you?

I'll try it out shortly, busy making a backup of my music collection first just in case ;)

Thanks, appreciate your help.

---

### Post by nilarimogard on 2011-02-24
I would recommend [Puddletag]("http://www.webupd8.org/2011/01/puddletag-awesome-mp3tag-like-editor.html"). It can automatically fill id3 tags via Amazon or MusicBrainz, get cover art and lots more. I find it to be the best mp3tag alternative for Linux (but better).

---

### Post by mips on 2011-02-24
I'm busy running MusicBrainz Picard.

How would I change the following,
```
$if2(%albumartist%,%artist%)/%album%/$num(%tracknumber%,2) %title%
```

in order to get the output folders & files as,

/Artist-Album/Artist-Album-Trackname.mp3

---

### Post by mips on 2011-02-24
I've decided not to use separate folders.

This does what I need
```
%artist%-%album%-%title%
```

---

### Post by Chronon on 2011-02-24
> **mips said:**
> I'm busy running MusicBrainz Picard.

How would I change the following,
```
$if2(%albumartist%,%artist%)/%album%/$num(%tracknumber%,2) %title%
```

in order to get the output folders & files as,

/Artist-Album/Artist-Album-Trackname.mp3

This would just be:
```
%artist%-%album%/%artist%-%album%-%title%
```

---

