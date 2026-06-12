---
title: "Ubuntu/Git Related Question"
date: 2012-01-19
forum: Server Platforms
---

### Post by extjspoker on 2012-01-19
Hi everyone,

I just recently purchased my first ever VPS, and I'm super stoked about it. :)

I have Ubuntu 10.10 64 bit running with no problems along with git version 1.7.1. I am able to push to the remote repository from my local box and I have a post-receive hook that then does a git checkout -f which pushes simply the files to my DocumentRoot for that particular project. Now is where the trouble comes in.

The file permissions for the files that get pushed to DocumentRoot are (-r--------) where I'd like them to be 0774 or something as they are web documents...

Any ideas? Thanks in advance!

---

