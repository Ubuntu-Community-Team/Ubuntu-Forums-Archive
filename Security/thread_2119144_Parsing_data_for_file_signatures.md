---
title: "Parsing data for file signatures"
date: 2013-02-23
forum: Security
---

### Post by duke.tim on 2013-02-23
I'm wondering if there is a way to parse through an unidentified file to identify file signatures, especially if it appears to contain multiple files.

For example a picture embedded within a document. Or spliting an image file for example foo.png with another file music.mp4




The purpose is partly to learn how to manually look/script a way of detecting content where it doesn't belong (much like what malware does). I tried using the ```
file
``` command but it only returns the first thing it finds, and the -k option doesn't seem to solve the problem.

I was thinking for finding an mp4 within the png file (which wouldn't open since the mp4 in it would corrupt it) using grep with some sort of signature 

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

### Post by Ms. Daisy on 2013-02-23
You could look at [Scalpel]("http://www.digitalforensicssolutions.com/Scalpel/") to carve the file into pieces. Perhaps you can automate it by comparing the carved files to known signatures and return matches if they don't match the original filetype.

---

### Post by sudodus on 2013-02-23
***PhotoRec*** is a tool to recover lost files. When the file system or partition table is destroyed, and the data is still lying on the disk or flash pendrive, it is possible to find it and recover it using typical signatures in various file types. The name indicates, that it was originally designed to recover photo files (for example jpeg files). But now it is developed into a general recovery tool.

Maybe it can also help you looking for 'files in files'.

---

### Post by duke.tim on 2013-02-23
Scalpel looks like it is perfect for the job!

Now to only figure out how to find and add specific signatures.

Thank you Ms. Daisy



sudodus I'll be sure to take a look at PhotoRec.

---

### Post by Ms. Daisy on 2013-02-23
> The purpose is partly to learn how to manually look/script a way of detecting content where it doesn't belong (much like what malware does). For this purpose I'd recommend that you identify known filetypes and perhaps calls to urls. In other words, a Word document that makes a call to _http;//somebadsite.c0m/nasty.exe_ would be an interesting find but may not contain a signature for embedded filetypes. You might be able to script that by looking for [http://*.*](http://*.*) strings, but I'm not sure how you would eliminate false positives like a document with a harmless link in the body.

---

### Post by unspawn on 2013-02-24
...I suggest you add looking into *statistical analysis* to the above suggestions. Finding changes in entropy might come in handy in cases w/o available signature or as second opinion method.

---

### Post by duke.tim on 2013-03-01
Looking for URL's is a good idea, It would b fairly simple to find them using the "strings" command, but it would need a list to determine if the url is a bad one. Maybe resolving the domain name and comparing the result to networks that are known to send out malware (or more statistically likely to send out malware) would help identify potentially harmful addresses.

Unspawn I will most certainly also need to look into statistical analysis. 
I wonder if similar types of malware have similar values of entropy, and if the entropy of of normal files will show a significant difference.
Sounds like a great experiment to try out!

---

