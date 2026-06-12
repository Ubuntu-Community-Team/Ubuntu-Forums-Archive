---
title: "Bazaar VS Hg VS Git"
date: 2009-11-27
forum: The Cafe
---

### Post by MaxIBoy on 2009-11-27
I would like opinions on what version control system I should use, please read on for the usage scenario.


Lately I have been contributing to a medium-smallish open-source project (total codebase size is something like 5 Mb of C files.) My preferred way of doing it is to have a local working copy with my own mad-scientist experiments in it, and every once in a while I submit something or other to merge. Also, whenever some major change happens in the master codebase, I will sync with it. However, syncing is a big hassle of diffing files manually and copying added functions into new files, etc. and that's really getting old.

I also have a home server, and I will update the files hosted there whenever I finish some feature or bugfix. I am usually on the same LAN as the server, but this is not always the case. I log into the server with SSH. The server has a dyndns domain name.

Lately I have decided that I need to start using a version control system. The main dev team uses SVN, but it's really not for me; in my usage scenario, it's severely lacking. I'd rather use a distributed system like Bazaar, Hg, or Git. Which one do you guys think will work best for my use? The features I want are: 
-The VCS I use should be able to support syncing the server over SSH.
-Ideally, it should make it easier to merge in changes from an SVN repo.
-Easy to use from the command line. GUI frontends are kinda "meh" for me.
-Easy to setup a website change viewer similar to ViewVC or Trac (optional but would be cool.)

Keep in mind, I neither have nor want write access to the main SVN repository.


If you know of another one besides Hg, Bzr, or Git, which would work well, could you also please suggest it?

---

### Post by phrostbyte on 2009-11-27
I'm a fan of Git. Git has very poor Windows support though.

---

### Post by MaxIBoy on 2009-11-27
> **phrostbyte said:**
> I'm a fan of Git. Git has very poor Windows support though.
Windows support is not an issue.

---

### Post by phrostbyte on 2009-11-27
Git is *fast*. I like the UI of gitweb too if you plan to have a web interface check that out.

---

