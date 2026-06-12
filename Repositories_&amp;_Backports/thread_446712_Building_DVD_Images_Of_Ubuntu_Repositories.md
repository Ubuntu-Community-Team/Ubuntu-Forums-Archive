---
title: "Building DVD Images Of Ubuntu Repositories"
date: 2007-05-17
forum: Repositories &amp; Backports
---

### Post by Sasan on 2007-05-17
I followed the Building DVD Images Of Ubuntu Repositories tutorial found on HowToForge's website.  I do apologize for downloading the repositories but I live in the boonies and don't have high speed.  The only place I have high speed is at work.  I am a newbie and am doing a lot of experimenting with Ubuntu, so I need to have the complete repositories easily accessible.  I am a power user with a programming degree, so when I really screw Ubuntu up I have to reinstall.

I got the main, multiverse, restricted, and universe repositories downloaded for both i386 and amd64 (of course the tutorial is geared toward i386 only).  When I issue the debpartial command, I am told that Packages.gz does not exist.  I checked under /home/sasan/ubuntu/dists/main/amd64-binary and Packages.gz is there.  I did tweak the command slightly as by default if no --arch is specified debpartial automatically looks for the i386-binary directory rather than adm64-binary directory.  Does anyone know why debpartial is telling me that the Packages.gz archive doesn't exist when in fact it does?  I've done some googling but haven't found anything on debpartial that is comprehensible by a newbie.

Thanks in advance.

---

