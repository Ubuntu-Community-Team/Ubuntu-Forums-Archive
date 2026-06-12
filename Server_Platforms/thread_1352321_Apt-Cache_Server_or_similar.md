---
title: "Apt-Cache Server or similar?"
date: 2009-12-11
forum: Server Platforms
---

### Post by nbotticelli on 2009-12-11
A few years ago I set up an apt-cache server for a summer camp where students built their own computers from kits and installed Edubuntu. This saved on bandwidth and made the updating and configuration of the student's computers very efficient.

Currently I am in the process of setting up Ubuntu on netbooks for our sixth grade students and would like to set up another apt-cache server to save on bandwidth/time too.

I've forgotten how I set this up originally and was wondering if anyone had any up to date tutorials on how to do this.

I also seem to remember that there were a few similar ways to set this up with different software packages but I forget what they were and what the pros/cons are.

It's going to be set up on an older rather limited box but this shouldn't be too much of an issue as it worked fine before.

I plan on using Ubuntu server without any graphical front end too.

Thanks for any help!

---

### Post by nbotticelli on 2009-12-11
Okay, so it looks like I am looking for apt-cacher not apt-cache. I'm also finding apt-cacher-ng which looks a bit newer.

---

### Post by i.r.id10t on 2009-12-11
You actually want apt-mirror

---

### Post by munky99999 on 2009-12-11
I use apt-cacher which works fine. There's a bit of a bug with the one in karmic and older. In some translation files which dont exist show up as error. Which if you used a normal repo would just give back a blank page. The version in lucid lynx is 1 version newer but not the latest one which debian unstable has.


apt-cacher-ng is a rewrite of the current one. Havent tried it because the current apt-cacher works fine. It's not a fork of the original afaik. Also -ng is meant to be streamlined for performance but the machine I use it on has plenty of resources.

---

