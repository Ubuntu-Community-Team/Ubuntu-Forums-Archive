---
title: "Twitter account hacked, how to track down source?"
date: 2011-09-18
forum: The Cafe
---

### Post by mikeym on 2011-09-18
Hi,

Does anyone have any idea how to track down the source of a twitter hack? I apparently "made" a post last night saying:

"How to make money working from home. http://is.gd/XXXXXX"

It happened within 3 mins of a friend making an identical post, and my machines were off at the time, so I'm guessing it's from their machine (mac) which I suppose I might have logged onto at some point. Changed my password and setup HTTPS by default as per twitter security page advice and I've not made another post while my friend has.

Is there a way of telling which application or IP made a specific twitter port?

---

### Post by Shpongle on 2011-09-18
you were probably XSS , did you click any links before it happened ?

---

### Post by Dangertux on 2011-09-18
The source was quite likely you're browser or your friends. 

Twitter has been known for a variety of XSS vulns in the past. Note you don't have to click a link neccessarily but usually you do. As far as where did you find the xss'ed conten, it is a great big Internet who knows

Running noscript will help, alot.

---

### Post by Lampi on 2011-09-18
@mikeym, [follow the twitter howto]("http://support.twitter.com/groups/33-report-a-violation") for compromised accounts. Only twitter has the resources to track it.

---

### Post by mikeym on 2011-09-19
Thanks for the help.

I seem to have sorted my problem though my friend still has a problem. I've reported it to twitter so maybe they'll get somewhere with it.

---

### Post by SavageWolf on 2011-09-19
What "additional applications" do you have enabled? They would be a good place to start.

---

