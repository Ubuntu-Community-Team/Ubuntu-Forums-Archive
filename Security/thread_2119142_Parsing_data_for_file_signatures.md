---
title: "Parsing data for file signatures"
date: 2013-02-23
forum: Security
---

### Post by duke.tim on 2013-02-23
I'm wondering if there is a way to parse through an unidentified file to identify file signatures, especially if it appears to contain multiple files.

For example a picture embedded within a document. Or spliting an image file for example 'foo.png' with another file 'music.mp4'




The purpose is partly to learn how to manually look/script a way of detecting content where it doesn't belong (Since malware will hide it'self within another file this could be useful). I tried using the ```
file
``` command but it only returns the first thing it finds, and the -k option doesn't seem to solve the problem.

I was thinking as an example for finding an mp4 within the png file (which wouldn't open since the mp4 in it would corrupt it) using grep with some sort of signature 

So if the signature is 'ftup' and the file called merged.corruption

```
grep 'ftyp' merged.corruption
```

would return a match if the signature is detected.

I found some signatures on google here.

[http://www.garykessler.net/library/file_sigs.html](http://www.garykessler.net/library/file_sigs.html)
[http://en.wikipedia.org/wiki/List_of_file_signatures](http://en.wikipedia.org/wiki/List_of_file_signatures)

Is there a better or easier way?
Can this be done with the file command?
Is there any considerations I should keep in mind if using grep or file, like binary and ASCII data within the same file?

---

### Post by duke.tim on 2013-02-23
Sorry for the double post, I believe I only hit the submit button once.

---

### Post by lisati on 2013-02-23
> **duke.tim said:**
> Sorry for the double post, I believe I only hit the submit button once.

Closed..... :D

---

