---
title: "FFMPEG Default Settings"
date: 2008-07-28
forum: Ubuntu Studio
---

### Post by hackerseraph on 2008-07-28
Any way to adjust ffmpeg's default settings so that when you use it in the terminal you wont have 64 bit audio as the defualt and you wont also have to type long strings to convert audio?

---

### Post by FakeOutdoorsman on 2008-07-28
You could edit the source code, but who wants to do that?  I use scripts.  Here's a very basic example:
```
#!/bin/bash
# Encoding Script
# Usage: ./encode.sh input.avi output.mp4
ffmpeg -i $1 -vcodec libx264 $2
```
Make a file named encode.sh and dump that into it.  Then make it executable:
```
chmod +x encode.sh
```
Now run it:
```
./encode.sh input.avi output.mp4
```
Alternatively, I guess you could also use a bash alias.  Edit ~/.bashrc and add:
```
alias convert='ffmpeg -i $1 -vn $2'
```
Now reload your .bashrc:
```
source ~/.bashrc
```
Now run your new command:
```
convert inputfile.avi outputfile.mp3
```
I'm not sure if using an alias like a script is problematic or not.

---

