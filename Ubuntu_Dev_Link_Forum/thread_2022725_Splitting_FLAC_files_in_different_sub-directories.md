---
title: "Splitting FLAC files in different sub-directories"
date: 2012-07-11
forum: Ubuntu Dev Link Forum
---

### Post by hihihi100 on 2012-07-11
TO ADMINS: Sorry I created this thread in the devel section, please move it to "encoding and programming language" (dont remember the exact name)... thx

Hi there:

I have 33 sub-directories with 33 flac files and their respective cue files. I have found some code to split it:

[https://bbs.archlinux.org/viewtopic.php?id=75774](https://bbs.archlinux.org/viewtopic.php?id=75774)

That works well for each of the sub-directories, but I was wondering if, instead of going one sub-directory by one, there is an automated way of doing it (for example, a script that searches for all FLAC and CUE files inside the directory that contains the 33 sub-directories).

Also, for the same script:

I'd rather have the output in the same sub-directory, not in a newly created "split" sub-directory, as it happens with this code (notice the "mkdir split" lines in each of the audio formats. I have tried with removing that line, but then the script gives error. What else do I have to edit to achieve this?

Please compare:

original:

```
    *.flac*)
        mkdir split
        shnsplit -d split -f *.cue -o "flac flac -V --best -o %f -" *.flac -t "%n %p - %t"
        rm -f split/00*pregap*
        cuetag.sh *.cue split/*.flac
        exit
```

will this one work?

```
    *.flac*)
        shnsplit -d -f *.cue -o "flac flac -V --best -o %f -" *.flac -t "%n %p - %t"
        rm -f split/00*pregap*
        cuetag.sh *.cue split/*.flac
        exit
```

I dont know which "split" are the ones that make reference to the directory and what others, if any, are needed to perform the action of split. I got rid of one, but I dont have a clue. Help appreciated

---

