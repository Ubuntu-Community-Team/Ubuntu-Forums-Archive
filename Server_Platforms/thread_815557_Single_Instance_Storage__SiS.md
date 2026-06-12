---
title: "Single Instance Storage / SiS"
date: 2008-06-01
forum: Server Platforms
---

### Post by amdman on 2008-06-01
Guys,
     Did a search (here and Google) didn't find much on it.  Any plans to put single instance storage (SiS) into either Ubuntu Server or a linux server at all?

Reason for this, I have a file server at home that's been linux forever (it's gone through it's changes, Slackware - reiserfs/Redhat 9 - reiserfs/CentOS - ext3/ and now Ubuntu 8.04 - ext3)  Over the years I have amassed a large number of files that are exactly the same in different directories.  They are buried pretty deep so going through by hand would be ridiculous.  I notice Windows Home Server offers a this single instance storage thing that converts multiple files to pointers of one file.

Got anything to help me out?

Thanks,
AmdMAN

---

### Post by windependence on 2008-06-02
Well I don't think there is anything like it, but you have a few options. You could go to freshmeat and look for something similar, or you write your own script to parse the directories and do the same thing using symlinks. I'm also pretty sure someone has script out there for finding duplicate files and then you could just delete the multiple copies.

BTW, I have the same problem, but I'm too lazy to fix it!

-Tim

---

### Post by quelx on 2008-06-02
This claims to create symlinks of your duplicate files 

[http://pmatch.rubyforge.org/](http://pmatch.rubyforge.org/)

> You can use it to generate commands that need both filenames - for example to replace duplicate files with symlinks:

pmatch tmp -c"rm #{d} && ln -s #{o.fullpath} #{d}"

Instead of using #{o} I have used #{o.fullpath} to return full path to the filename instead of relative one. #{o} by default (the same for #{d}) will return a path to the file relative to the path you have provided while running pmatch. That could cause symlinks to be generated as broken - full path will fix that problem.

---

