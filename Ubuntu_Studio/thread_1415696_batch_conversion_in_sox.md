---
title: "batch conversion in sox"
date: 2010-02-25
forum: Ubuntu Studio
---

### Post by rossco_50 on 2010-02-25
Hi,

Does anyone know how I could batch convert a directory full of 44.1Khz wav samples to 48khz wav using sox?

If I am in the directory and do 'sox *.wav *48.wav rate 48000' this converts all files to 48khz but puts them all in a single file. How can I get multiple output files? 

Thanks,

Ross

---

### Post by darsu on 2010-02-25
Something roughly like this: (try at your own risk, I'm not quite positive)

ls -1 *.wav | awk '{system("sox " $1 " " substr($1,1,index($1,".")-1) "48.wav rate 48000"); }'

Features:
* ls -1 lists one file per line
* | pipes the output of the command before it to the command after it
* awk is a programming language and the bit between the single quotes is an awk program that processes an input string (denoted by $1), constructing a sox command out of it.

(Oops, watch out, that doesn't work quite correctly with files that have more than one period in the name. Eg. foo.bar.wav would result in foo48.wav)

---

### Post by rossco_50 on 2010-02-27
Hi Darsu,

Thanks so much, that worked very well.

Sorry to be greedy, but could this command be made to put all new output files into a new folder?

Cheers,

Ross

---

### Post by darsu on 2010-02-27
If you modify the sox command string inside that mess to

"sox " $1 " **foo/**" substr($1,1,index($1,".")-1) "48.wav rate 48000"

the output should come out as foo/whatever48.wav.

---

### Post by rossco_50 on 2010-02-28
Thanks again.

However, inserting the directory name where you have suggested does not create the directory. I get an error:

sox FAIL formats: can't open output file ` 48khz/worm48.wav': No such file or directory 

If I create the folder manually first it works no problem. Should I be able to make the command create a folder?

Thanks,

Ross

---

### Post by darsu on 2010-02-28
The script indeed assumes the directory already exists.

---

