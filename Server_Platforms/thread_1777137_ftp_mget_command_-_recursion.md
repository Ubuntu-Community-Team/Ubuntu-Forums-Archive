---
title: "ftp mget command - recursion?"
date: 2011-06-07
forum: Server Platforms
---

### Post by Phil Stone on 2011-06-07
Just introduced myself to ftp. I am transferring some non-sensitive files to/from my personal ftp site. I can't seem to find a recursion option with mget in ftp to make a local copy of my site. Basically I have tried ```
 mget -rf *
mget --recursive *
mget -recursive * 
``` which result in all files in / being dl but does not traverse down the file tree. 

Currently no directories exist in my local directory. So I also tried with a directory created with the same name as a remote directory. But mget doesn't appear able to open remote directories anyway as response 550 unable to open file is returned.

---

