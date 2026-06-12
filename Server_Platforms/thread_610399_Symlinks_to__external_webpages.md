---
title: "Symlinks to  external webpages"
date: 2007-11-11
forum: Server Platforms
---

### Post by Nulifier on 2007-11-11
I was trying to create a webserver (apache, fully working) and I ran into a problem.

I was trying to create several RSS feeds but the problem is that I want to have one link for people to use to get them
ie. [www.mypage.com/rss.xml](www.mypage.com/rss.xml)
and then have them not care how it is being generated as this will change in the future

Currently I am getting them off a external web page but I am using a cron script that runs every 15 mins and jsut uses wget to download them and then I have a symlink (ie. rss.xml) to the file that I downloaded.

I was wondering if I could just create a symlink (or something like it) that I could just link to the file directly

I tried creating a symlink using a url but it is a broken link

Any help would be apreciated

---

