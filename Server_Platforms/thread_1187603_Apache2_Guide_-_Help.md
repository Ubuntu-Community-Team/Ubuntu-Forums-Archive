---
title: "Apache2 Guide - Help"
date: 2009-06-14
forum: Server Platforms
---

### Post by lmlypfan on 2009-06-14
I'm trying to share my music library with friends via Apache2. 
Its taken me a while to even get the basics down, and was wondering if anyone on here could recommend a good intro guide to Apache2.

I'm running a headless ubuntu 9.04 server. I have a RAID5 config with mdadm.

I was able to get Apache to list my music directories and files by creating a symbolic link in the /var/www directory.

Here is my current issue. 

When i browse to a directory in firefox and try and save a complete folder w/ "save link as", the directory name is always something goofy, and does not save the directory and files. It just saves an html file.

Say i was trying to save the directory Phish_Hampton_2009, the file name it tries to save is something like "8aVrsrJ1.html.part"

Anyone ideas?

sincerely,

Knewb

---

### Post by mlinux on 2009-06-14
Try brows to the file in that directory and do a save as. You can't do a save link as cos you are doing a directory browsing!

---

### Post by lmlypfan on 2009-06-14
I can save the individual files, no problem. I would like to save my friends the hassle of having to grab each and every individual file though.
I also don't want to have to zip entire sets (concerts) of FLACs.

I've browsed other peoples directories and been able to download a whole folders contents. It must be a setting somewhere.

---

### Post by dfreer on 2009-06-14
Hmmm, from my understanding you can't use "Save Link As..." to download a directory. I'd expect that is actually saving the HTML contents of that page instead of the files contained within.

I would suggest either manually compressing the folder and downloading that (would be quicker anyways), or creating a PHP script to do this on the fly. If it's just music, you might want to look into Icecast or Firefly/mt-daapd to serve music.

EDIT: Didn't see the above. I haven't heard of a way to have apache serve directories as files other than using PHP.

---

