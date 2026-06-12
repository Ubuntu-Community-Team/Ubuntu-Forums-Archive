---
title: "Is anyone else tired of the broken repositories?"
date: 2006-08-03
forum: Repositories &amp; Backports
---

### Post by greenstar on 2006-08-03
****This is not a thread to troubleshoot or fix anything, so don't ask.****

Recent weeks have shown the Ubuntu repositories to be less than reliable. What gives? I've worked around or through other obstacles I've encountered as an Ubuntu user. This is *the* deal-breaker of deal-breakers. Without the repositories, Ubuntu is like a fish out of water.

So I'd like to know what's really going on. And why it hasn't been corrected yet.

If anyone has any _real_ knowledge of what's going on, please post here. 
[B]
Please keep opinions, guesses & speculation to yourself. This thread is here to help us find the root of the problem. [/B]**Responses should be relevant to the problem.**

I didn't post this or word it to exclude anyone, but rather to keep the drone of irrelevant & unhelpful posts at bay so that the actual situation may be examined as best as possible and without distraction. No offense is meant to anyone, and none should be taken.

Let's get this out in the open,
Greenstar

Edit:
If you are having repository problems, please post _only_ the following:
(To find this info, in a terminal do: sudo gedit /etc/apt/sources.list and look for a line that looks like: **deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted**) 
     1. Which country's repos you're using. (This is the two letter country code in the above line, immediately before .archive.ubuntu.com)
     2. Whether you're using http or ftp for the official repos. (This is just after "deb" in the example line.)
   3. Official Ubuntu repositories only, others are not part of this discussion.

So a helpful response would look something like this:

I use the US repos: us
I use http

or

I use the austrian repos: at
I use ftp

---

### Post by Panik on 2006-08-03
Sorry (Would Delete but don't know how.

---

### Post by greenstar on 2006-08-03
OK, guess I wasn't clear enough... **PLEASE don't post error messages and the like here, there are plenty of other posts around with that info.**

This is for collection of data related to the problem, not discussion of it's symptoms.

Thanks,
Greenstar

---

### Post by greenstar on 2006-08-03
I'll start with my info.

I have removed the country code from my repo lines, so I have:
deb [ftp://archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") dapper main restricted

I use ftp

Greenstar

---

### Post by greenstar on 2006-08-03
No worries, Panik. You can edit by clicking the red scissors at the bottom of your post. Replacing the error messages you posted with the info requested would be great and help further the effort to fix this.

Thanks,
Greenstar

---

### Post by coltey on 2006-08-03
I'm hitting the US and have tried both http and ftp:
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

---

