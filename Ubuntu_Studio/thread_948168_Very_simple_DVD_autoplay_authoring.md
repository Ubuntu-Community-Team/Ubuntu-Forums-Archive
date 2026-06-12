---
title: "Very simple DVD autoplay authoring"
date: 2008-10-15
forum: Ubuntu Studio
---

### Post by pssturges on 2008-10-15
Hi,

I'm looking for a really simple way to author DVD's from a single MPEG file. No menus or re-encoding just autoplay. I'd like the output to be DVD folders rather than burning or ISO's. Probably prefer a command line solution, but GUI ok. 

Thanks in advance,
Phil

---

### Post by patrickballeux on 2008-10-15
If you don't want any dvd menu, just the bare bone movie there is a very simple way to do this:

Put your mpeg movie (already VOB compatible) in a folder, and create a subfolder named "dvd" that will contain the dvd content...

```

dvdauthor -o dvd *.vob
dvdauthor -o dvd -T

```

That's it! 

Any vob files will be included as chapter, and the next call with "-T" is to create the structure for the DVDs to find the files/movies...

All you have to do after is to burn the content of the folder "dvd" onto a DVD ...

For a complete solution that will transcode and create the final ISO, look for Devede.  It is a GUI, but is really efficient at creating DVDs from any videos.  It can even create basic menu which is more than enough if you need them...

Good luck!

---

### Post by pssturges on 2008-10-15
wow! That was quick! And exactly what I was looking for. I'll give it a go.

Many thanks
Phil

---

