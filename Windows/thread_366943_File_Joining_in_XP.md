---
title: "File Joining in XP"
date: 2007-02-21
forum: Windows
---

### Post by insane_alien on 2007-02-21
I transfered a bunch of files (disk images specifically but its irrelevant) over to an XP computer, i couldn't fit them on my USB stick so i used the split command figuring that i would be able to join them on XP if i prodded around a bit. no such luck.

so, can i join the bits together or am i going to have to go and rethink?

---

### Post by erlyrisa on 2007-02-21
search for "joining files in xp"

---

### Post by M_the_C on 2007-02-22
> **erlyrisa said:**
> search for "joining files in xp"
That's not very helpful.

I don't know anything about it myself, but I found this web-site with a free open-ource program that works in Linux and Windows.

[Link.]("http://stahlforce.com/dev/index.php?tool=split&back=dev")

It may help.  Good Luck.

---

### Post by insane_alien on 2007-02-22
do you know if that program will work on already split files? i would give it a shot but i don't have the time just now. i'll have a go tomorrow if i'm concious.

---

### Post by erlyrisa on 2007-02-22
Another option , which would help you be more comfortable on windows is to install cygwin. It's a firaly concise subset of a typical Linux distro - that runs natively on windows.
Sorry about pionting out the obvious 'google search' - there are a whole bunch of file utilities on the net though finding one that doesn't include malware maybe a problem.

---

### Post by insane_alien on 2007-02-23
i  tried google but all i got was a bunch of pay to download ones.

i'm downloading the one linked and i'm going to try that out.h

---

### Post by erlyrisa on 2007-02-23
hmm , sorry to hear that.

-I thought of another option (If your the programing type)

Have you tried Powershell ? - I have only recently installed (and to tell you the truth, in this gui world haven't really used it)

I am pretty sure you could stream the two files as objects and just plainly append the ending object to the starting object. I wouldn't know the code - it wouldn't be more than a 1 liner - it's just learning it that is the hard part.

but seeing the power of powershell (by reading it's documentation) the command may actually be as easy as...

(get-item file1.txt) + (get-item file2.txt)

--yeah its wrong - maybe some-one else knows what the command may be?

---

### Post by chewearn on 2007-02-23
After using split command in linux, and moving the files to XP, have you tried the old fashion DOS copy command?

Example:
```
copy /b file1+file2+file3 combinedfile.iso
```

I tested it on a small 200kB jpg file, seems to work.

---

### Post by insane_alien on 2007-02-23
yeah, i've just realised how much i suck at DOS see for that command, would i have to go to the folder the files are in yeah? also, how do you do that in DOS i keep think cd but that doesn't work.

would the command be 

copy /b xaa+xab+xac image.iso 

or something else?

---

### Post by haricharan on 2007-02-23
you could try connecting the two computers through a crossover cable and setting static IP addresses for them and transfer the files....this might a naive suggestion....but worth doing if the two computers are nearby!!..

---

### Post by insane_alien on 2007-02-23
the separation of 34 miles poses a bit of a problem for your standard crossover cable. a LAN would be my preffered method for this but a sneakernet was more practical(higher bandwidth too). really should invest in an external HDD

---

### Post by haricharan on 2007-02-23
:roll: oops...sorry abt that....yeah an external HDD would be much easier.......

---

### Post by erlyrisa on 2007-02-23
> **insane_alien said:**
> yeah, i've just realised how much i suck at DOS see for that command, would i have to go to the folder the files are in yeah? also, how do you do that in DOS i keep think cd but that doesn't work.

would the command be 

copy /b xaa+xab+xac image.iso 

or something else?

I can't beleive that worked! - after ooh 15years another piece of DOS has been unravelled to me.!
(Though I still cant make a new directory as the current date!)

---

### Post by chewearn on 2007-02-24
Yeah, pretty must all old DOS commands still exist in XP.

1. Start -> Run -> cmd <enter> will open a terminal window.
2. Use cd to navigate to the folder where you files are.  Only thing to remember is back slash \ instead of forward / to delimit the folders/files; as in "c:\program files"; use double quotes if file name contains spaces.
3. Forward slash instead of dash for options.
4. Tab to autocomplete folder/file names, just like in linux.

copy /b xaa+xab+xac image.iso

is correct.

---

### Post by insane_alien on 2007-02-24
ahh MS uses 'chdir' instead of 'cd' damn their inefficient practises.

update: ok, its churning away now. probably take a couple of hours now.

update update: yay it worked! thanks guys. i just got shouted at for being a noob on proper windows forums as well. i love this place.

---

### Post by KittyChunk on 2007-09-01
Useful thread! This was most helpful in transferring the stupidly big BioShock demo over to my gaming PC :-)

---

### Post by oedenfield on 2007-12-06
for the record...

To add content from one file to another in PowerShell all you have to do is this:

add-content mergedFile.txt -value (get-content sourceFile.txt)

You could put multiple files in there or a path and *.* if needed.

---

