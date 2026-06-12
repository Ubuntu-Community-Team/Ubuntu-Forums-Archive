---
title: "should commands have fixed position arguments or options?"
date: 2019-07-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-07-16
i wrote a little script in Python.  it calculates hash checksums of files but limits itself to a specified maximum number of bytes.  it has 2 arguments:  which algorithm to use and what maximum size to read for the checksum.  after that is any number of file names.  if no names, it will read STDIN.  if the file name is - it will read STDIN.  if - is given 2 or more times it outputs an error message and quits without reading any files.

eventually, i will make it available under an MIT-like license.  but i am wondering if it is preferred to have options like -a for algorithm and -s for size.  since both are required, i just made them positional in version 0.0.1.

what are your preferences?

i needed this script last month when i was looking for a file to find what i had originally named it.  it was one of thousands that had the same size on several multi-terabyte disks.  i needed to match it by checksum.  but this was so slow because each file is a gigabyte in size and checksumming the whole file was all i could do.

---

### Post by TheFu on 2019-07-17
Use getopts().  This is a solved problem.

---

### Post by Skaperen on 2019-07-17
my question is *not how* to code options, it is *whether* to have them or not.  and what people's *preferences* are for things that are *not optional* in this command.

---

### Post by TheFu on 2019-07-17
Positional options that can be badly interpreted usually end badly.  If a short option prevents that, I'd go that way.  The input file is traditionally the last argument. 

I bet you'd get more responses with a few examples, less words.

---

### Post by Skaperen on 2019-07-18
compute and show the md5 hash of the first 4 megabytes of files foo and bar```
hash-size md5 4m foo bar
```
compute and show the sha256 hash of the first megabyte of the file xyzzy```
hash-size sha256 1m xyzzy
```

---

### Post by TheFu on 2019-07-18
```
$ hash-size sha256 1m 8m
```
Which is the file?  The code can't guess 100% correct every time.  
If you want to support both, perhaps a -p option for  --positional could be used?

---

### Post by Skaperen on 2019-07-18
it would be documented as positional: hash-size <algorithm>  <size>   [<files> ...]

if no files, it reads stdin, as most commands doing reading do. if the file name is '-', it reads stdin at that point in the list of files.  but, only one '-' is allowed.

remembering positional arguments for a positonal command is (IMHO) no harder that remembering -a for algorithm and -s for size.  but there are positional commands in Unix/Linux/Ubuntu, such as [FONT=courier new]chmod[/FONT] (also has options for optional uses).

---

### Post by SeijiSensei on 2019-07-19
For programs with only a few options, positional would be my choice. Something like rsync has dozens of options and so it has lots of long-form --option alternatives.

I'm not sure why I'd want to limit the hash to only the first N bytes. By default, I'd want it to hash the entire file(s). So I might make that a long-form option:

```
hash-size md5 foo bar --length=4m
```

---

### Post by Skaperen on 2019-07-19
the regular commands can do the whole file.  but i have been thinking that a way to do the whole file might be convenient.  i might do -s and --size with default to full file.  this program supports all the hashes available in Python's *hashlib* module.

the reason i wanted to has just part of a file a few weeks ago was that i was looking for a file with the same contents as one i had already.  i just didn't know its name.  i wanted its name and date.  so i had to just do md5 of whole files.  unfortunately, lots of these files were exactly the same size, 1073741824 each (they were all splits of one very massive file).  hashing just the first 4k would probably have found just the one, though if there was more than one match of just 4k then a whole file hash of just those would narrow it down.

i'm also testing out various pieces of code to build a program that scans through a file system, or rule-defined portions, and hard links identical files together to reduce space utilization (the rules to make sure files that should not be linked are not linked).  partial hashing could speed this up.  if a partial hash matches, then a full hash can be done.

---

