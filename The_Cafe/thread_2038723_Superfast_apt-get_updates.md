---
title: "Superfast apt-get updates?"
date: 2012-08-07
forum: The Cafe
---

### Post by vasa1 on 2012-08-07
I've complained [previously]("http://askubuntu.com/questions/127522/why-are-my-apt-get-update-fetches-so-large/136777#136777") about the size of apt-get updates (~6 MB) and the time it took (~ 3 min). A few others had the same experience.

Today, I ran apt-get update twice a few hours apart. Both times the size was less than 1 MB just like how it was before Precise came along.

(Just to be clear, I'm talking about the data downloaded during apt-get update and **not** apt-get upgrade.)

Anyone else?

---

### Post by shubham1 on 2012-08-07
> **vasa1 said:**
> I've complained [previously]("http://askubuntu.com/questions/127522/why-are-my-apt-get-update-fetches-so-large/136777#136777") about the size of apt-get updates (~6 MB) and the time it took (~ 3 min). A few others had the same experience.

Today, I ran apt-get update twice a few hours apart. Both times the size was less than 1 MB just like how it was before Precise came along.

(Just to be clear, I'm talking about the data downloaded during apt-get update and **not** apt-get upgrade.)

Anyone else?
ok this is normal for me it takes even more time

---

### Post by Jakin on 2012-08-07
In all the times i have used Ubuntu (or its variants), it never took more than 2mins (absolute tops) to update the cache. I wouldnt considered to have many repos, but its somewhere around 30ish sources.

I don't have a fast connection either. Also i clear that cache often..

---

### Post by vexorian on 2012-08-07
> **vasa1 said:**
> I've complained [previously]("http://askubuntu.com/questions/127522/why-are-my-apt-get-update-fetches-so-large/136777#136777") about the size of apt-get updates (~6 MB) and the time it took (~ 3 min). A few others had the same experience.

Today, I ran apt-get update twice a few hours apart. Both times the size was less than 1 MB just like how it was before Precise came along.

(Just to be clear, I'm talking about the data downloaded during apt-get update and **not** apt-get upgrade.)

Anyone else?
It downloads the headers first. If there was no change in the repository's list in comparison to the list apt already has, then it does not download the new list. When you do apt-get update frequently, there is a good chance many lists will not need to be downloaded.

---

### Post by philinux on 2012-08-07
15 seconds to update the cache.

I guess this will vary considerably due to ISP and ubuntu's servers.

---

### Post by vasa1 on 2012-08-07
The interesting thing for me is that until yesterday, ever since I moved to 12.04, data was > 6 MB. Today, it's been less than 1 MB.

---

### Post by vasa1 on 2012-08-07
See this: [https://bugs.launchpad.net/launchpad/+bug/1001780](https://bugs.launchpad.net/launchpad/+bug/1001780)

Comment #17: "The internal mirror script has been fixed to not clobber the timestamps for old files, so this should no longer be a big problem."

And the next entry:

affects:	 apt (Ubuntu) &#8594; ubuntu
Changed in ubuntu:
status:	 Confirmed &#8594; Fix Released

---

