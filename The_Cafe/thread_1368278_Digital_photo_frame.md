---
title: "Digital photo frame"
date: 2009-12-30
forum: The Cafe
---

### Post by Jimmey on 2009-12-30
My girlfriend has just been given a digital photoframe for Christmas, and it's essentially a no-brand, no-frills job. 

One of the features that we were really looking for was the ability to play back the photos randomly, which this frame doesn't seem to have, so I ask, is it either

A. Possible that I can somehow edit the device firmware to allow random playback?

or

B. Possible that I can manually re-shuffle the files on the USB stick that we have to they're essentially played in random order anyway?

Thanks

---

### Post by ceramicm on 2009-12-30
I have an idea about B.

Have you looked at a program like pyRenamer? It allows you to mass rename files, and can attach a random number to the new file name. For example, a file called "New Year's 2009 001.JPG" might be renamed to "813465.JPG" and "New Year's 2009 002.JPG" to "162540.JPG", and so on, for all your files. Then, assuming your frame displays pictures in order by filename, your pictures would display in a random order, although it would be the same random order until you renamed them again.

No idea about A., sorry. It sounds...difficult.

---

### Post by Xbehave on 2009-12-30
I think this should shuffle the files (will expand the file names every time, so probably not perfect for a long term solution
```
for file in *; do mv $file $RANDOM-$file; done
```

got to go eat, but if nobody fixes it before i get back i'll try and add cutting so that you don't end up with stupidly long filenames

edit: or you could just remove the original completly and go with
```
for file in *; do mv $file $RANDOM.JPG; done
```

---

