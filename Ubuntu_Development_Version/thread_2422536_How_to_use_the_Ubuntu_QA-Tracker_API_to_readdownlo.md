---
title: "How to use the Ubuntu QA-Tracker API to read/download tests for a testcase/milestone"
date: 2019-07-09
forum: Ubuntu Development Version
---

### Post by guiverc on 2019-07-09
I want to download my QA-testing results (particularly comments, but bug numbers would be great too), but have had no luck trying to use the example code found on [http://iso.qa.ubuntu.com/qatracker/api](http://iso.qa.ubuntu.com/qatracker/api)  (or the code it points to found at [https://code.launchpad.net/~ubuntu-qa-website-devel/ubuntu-qa-website/python-qatracker](https://code.launchpad.net/~ubuntu-qa-website-devel/ubuntu-qa-website/python-qatracker)).

As I don't code in python, it's possible it could be something simple, but I get either errors or no results. *This is very vague sorry, but I'm not the the machine where I tried so I don't have access to the actual errors currently, but what I tried was pretty much only what I downloaded, first being the iso.qa example & second being the launchpad code*

Does anyone have a simple script *that they can provide to me* that will download a users (ie. mine) QA-tests recorded for a testcase (eg. Lubuntu 19.10 all, or just 'live session' tests).  I only want to read data so I don't need authentication, and I'm hoping to get it in a series of small text files, OR a large text file I can `grep` to extract what I need.

(an example of what I want; earlier today I had a repeat of a bug I'd tagged a couple of weeks ago, so would have loved to grep this file using a few words to find the lp.bug.report to re-tag for the current test. Another desired use is to see which boxes I've tested with recently so I can easily rotate the hardware I use etc)

---

### Post by guiverc on 2020-01-26
bump....

I also want to continue 20.04 testing using a box; which is ~setup for a re-try of a 18.04.4 install that failed last time, but I can't remember which install failed... I'd like to search my prior qa-test for tests I did to hopefully find it..

---

### Post by guiverc on 2020-06-11
bump.

would be nice if I could work out how to use this...

 I've discovered an issue with groovy ISOs no longer booting on some BIOS machines ([https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1883040](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1883040) impacting *ubuntu, xubuntu, ubuntu-studio, kubuntu, lubuntu* maybe others), and it'd be nice to get a list of my 47 *groovy* recorded tests so I can see a list of dates I used those boxes] impacted by that bug...  (ie. dump my results to a file & *grep* the results since I record boxes with the same strings in comments..)

---

### Post by guiverc on 2020-11-27
bump.

---

### Post by guiverc on 2020-12-15
*bump*

---

