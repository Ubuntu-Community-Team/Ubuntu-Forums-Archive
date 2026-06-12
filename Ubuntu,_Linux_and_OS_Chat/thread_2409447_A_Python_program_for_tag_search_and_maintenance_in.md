---
title: "A Python program for tag search and maintenance in file names"
date: 2019-01-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Halbarad on 2019-01-02
Hi, I don't really know if this is the right subforum for my message.

I have been using for several years a Python program I wrote and refined in time for searching and maintaining tags within file names. The program is called "qtag". It searches for filenames containing words or word beginnings (tags) or not containing certain tags. For example, "qtag liv mp4" would find "Pink Floyd Live.mp4", "PinkFloydLive.mp4" and "Lively.Jack.mp4", but not "Deliverance.mp4" (because "liv" is not at the beginning of a word, it's not a tag). A colon before a tag means "not" -- "qtag liv :Jack mp4" (not Jack) would not find "LivelyJack.mp4" but would find the other two files. You can have as many tags as you like, in any order. Adding "-w" writes links to the found files into a working directory and opens it with the default file manager. There are more options for mass tagging and untagging, appending more links to the working directory, case sensitive search etc. etc. One can use wild characters and regex expressions and so, also strings that are not at the beginning of a word can be searched for.

All that qtag does can be done with other commands, esp. with find... exec, but qtag is much easier to use for purposes related to tag management. 

Several people asked me a copy of the program and suggested I should share it. I have the python3 file (some 500 lines of code) and a manual. I have attached the files to this message. If this is not the right forum for submitting programs, just tell me. To run the program, after decompressing it, change its properties accordingly (right click file name "qtag", Permissions, set Execute to "Anyone" -- if you can use "chmod" you don't need explanations). To run it: from Terminal, "python3 [path]qtag" or just "qtag" if you put the file in a directory included in your path (echo $PATH). Both program and manual can be read with a text editor. That's it.

---

### Post by TheFu on 2019-01-03
And gitlab or github aren't options because?  Those are the most commonly used sites to share code, build a community, gain help and feedback about the program.  

Did you use Linux extended user attributes (part of Linux file systems) for the tag storage? [http://www.linux-mag.com/id/8741/](http://www.linux-mag.com/id/8741/)  When the file is moved/copied, the xattrs go with it, provided the target file system supports xattrs.  Sorta like how adding metadata to photos with exif is better than entering all that data into some proprietary photo library tool (cough, Adobe) never to be available again.

Hopefully, some use of locate/updatedb was leveraged.

A script around those to tools/techniques is definitely a good step.

---

