---
title: "XMMS random play is not random [Solution]"
date: 2007-09-23
forum: The Cafe
---

### Post by Atreus12 on 2007-09-23
> 
randomm3u is a simple program to randomize Winamp style .m3u playlists. It goes to extreme lengths to ensure the randomization is truly random.


One of my complaints about audio players like XMMS is that the random playlist mode is not random. Some are better than others, but it seems like I keep hearing the same songs again and again.

So while google-ing I found this cool solution. As far as I know it only works with xmms (or similar) playlists. Make a backup of your playlist first.

[http://www.zincland.com/randomm3u/](http://www.zincland.com/randomm3u/)

Usage: 
./randomm3u   infile.m3u   outfile.m3u   [www.random.org](www.random.org)  [email]youremail@domain.com[/email]

Anyway, I thought it worked pretty well, so I figured I would post it up and maybe someone else will find it useful.

The program is open source too, released to public domain.

Edit:
Once you randomize your playlist, there is no need to use "random play" mode, just play from the top down. When you get to the bottom, rerandomize and start over.

---

### Post by picpak on 2007-09-23
That didn't work so good. In fact, there's two songs from the same artist (in some cases, three) throughout the entire list. Was that intentional?

---

### Post by Atreus12 on 2007-09-23
> **picpak said:**
> That didn't work so good. In fact, there's two songs from the same artist (in some cases, three) throughout the entire list. Was that intentional?

Yes and no. No it should not come out like that. Yes it keeps the two adjacent lines together. So if your playlist came out in pairs, you were not using an XMMS type playlist.
Look at the structure of a XMMS playlist:

```

#EXTM3U
#EXTINF:259,8 Artist - Song Title
/path/to/song/1
#EXTINF:277, Artist - Song TItle
/path/to/song/2
...

```

Thus, it keeps the lines together so nothing gets messed up. Every entry has two lines. The top line is info about the song, and the bottom line is the location of the song. Splitting these up would break your playlist.

**Edit: So if you simply ran a list of songs through (which were not in the above format) they will come out in pairs. If you run an XMMS playlist through, it will be completely random**

---

### Post by dmber on 2007-09-23
two songs from the same artist next to each other is still "random".  if you have ten tracks, at some point they will randomly play 1-10.

---

### Post by picpak on 2007-09-23
> **dmber said:**
> two songs from the same artist next to each other is still "random".  if you have ten tracks, at some point they will randomly play 1-10.

True, but I'd like to randomize it a bit more than that. ;)

---

