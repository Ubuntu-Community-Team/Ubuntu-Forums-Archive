---
title: "Run a Terminal Command with pause and resume"
date: 2011-05-17
forum: Server Platforms
---

### Post by grants on 2011-05-17
I need to run a script that I build to build a word list. Essentially what it does is run through a base list and expands that into billions of words. This way I can keep a small dictionary file and a script to expand it into a larger file (about 500 gigs). 

This script should take anywhere from 12-14 days to run and on my last day the power went out at my house. Is there anyway I can run this again with a fail over system?

I know a battery back up is an ideal addition to my home server but if the power is out for an hour it wouldn't have made a difference. Also if I had the ability to pause the script do a reboot and resume it again that would be amazing. 

Any help would be great.

---

### Post by DaithiF on 2011-05-17
without knowing more about the script its hard to offer concrete suggestions.  can you post the script?

but as a general comment, something that runs for 12-14 days needs a redesign!  the raw time to write 500gb of data to disk should be of the order of ~4 hours.  So it sounds like whatever algorithm you are using to construct the permutations is pretty inefficient if its adding another 308 hours on top of that!

secondly, could you not split up the output into many separate (and smaller) files, then combine them into a single file at the end.  So that at least if the process fails you can pick it up from where you left off rather than from the beginning.

---

### Post by grants on 2011-05-17
> **DaithiF said:**
> could you not split up the output into many separate (and smaller) files, then combine them into a single file at the end.  So that at least if the process fails you can pick it up from where you left off rather than from the beginning.

Thats what I'm working on now. 

I have one script that reads lines of a file and adds 0-9 and the end and also adds 0-9 to the end of those results. 

(this essentially turns a 5 line file into 605 lines)

This is done with a shell script to read the lines of the file and print the line through a loop using an array as a list of different characters to add at the end of the line. No memory space needed for this besides writing to the disk and the size of the array.  

Next I'm adding special characters. Multiplying the number of lines now by 33. 

First step is done. The special characters is where I had a power outage and causing this to be redone. If I split into multiple files then I need to do the first step over again. This is probably what I'll do since the first part only took 10 hours. 


There is probably a more efficient way do this but I think I'm restricted by system performance. I'm using an old AMD dual core socket 939. Which is pretty old. Has 2 gigs of ram and a pretty slow hard drive. I think a 5400 RPM drive (not sure)

At the end the two scripts combined will transform a dictionary word list of 300k words into a 1,197,900,000 word list however my base word list is much larger then 300k.

---

### Post by grants on 2011-05-17
If I do start all over I'd like to send the results into a zipped file at the same time so I don't have to consume such a large amount of disk space. End results were calculated to be about 500 gigs. Compression ratio has been greater then 90% with word lists in the past. So I'm sure you can see the need to have these compressed. 

I usually use tar -czvf to compress them.

---

### Post by DaithiF on 2011-05-17
can you show how you are appending the 0, 00, etc. values to the lines?  10 hours still seems way too long, a noddy test on my machine of 20 lines expanding out to 2220 and  extrapolated to a 300k source suggests a runtime of approx 45mins.

for compressing, you can pipe the output to gzip to compress it on the fly, e.g.:

```
yourscript | gzip > output.gz

```
since you're only generating one file theres no need to put it in a tar archive.

---

### Post by grants on 2011-05-17
```
while read line; do
yr=(195 196 197 198 199 200 201 202)
chr=(0 1 2 3 4 5 6 7 8 9)

echo "$line"

for n1 in "${chr[@]}"; do
echo "$line$n1"
for n2 in "${chr[@]}"; do
echo "$line$n1$n2"
done
done

for y1 in "${yr[@]}"; do
for v1 in "${chr[@]}"; do

echo "$line$y1$v1"

done
done
done

```

Like I said, I have a slow computer, I'm sure this would be alot faster in c or c++ but the code is pretty simple so I can't imagine there would be a much faster way to do this. I honestly think its my drive that is slowing everything up. 

I'm in the process of just splitting into 10 different files to make it easier. Thanks for the gzip code.

---

