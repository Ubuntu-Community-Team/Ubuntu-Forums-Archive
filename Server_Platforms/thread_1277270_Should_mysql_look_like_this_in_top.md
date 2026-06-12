---
title: "Should mysql look like this in top?"
date: 2009-09-28
forum: Server Platforms
---

### Post by CzarAlex on 2009-09-28
I've been having a problem with my server locking up after a week or so. The logs (that I looked at) didn't appear to offer anything helpful, but I've noticed that restarting mysql every so often seems to remedy the problem. I checked top and saw this:

[img]http://www.czaralex.com/images/top.png[/img]

Now, I'm not the most experienced user, by any means..but after such a short uptime should it be using 12% of my memory? When I restart the mysql server, it doesn't seem to reset that usage. The largest db I have is a wordpress blog db weighing in at 518kb.

Thoughts?

---

### Post by superc0w on 2009-10-10
Yeah doesn't seem like a mysql issue.  My mysql instance is running at about 4% without any load so if you're making reads and writes in a prod environment that's definitely not out of range.  You don't have a lot of free memory which is the first thing I'm noticing.  Can you set up your top output to post the top offenders of memory? I think the '>' char let's you scroll through.

---

