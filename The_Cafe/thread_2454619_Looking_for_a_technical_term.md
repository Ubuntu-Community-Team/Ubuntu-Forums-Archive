---
title: "Looking for a technical term"
date: 2020-12-03
forum: The Cafe
---

### Post by satimis on 2020-12-03
Hi all,

I'm looking a technical term for searching new hosting companies.

I'm currently subscribing WordPress hosting with unlimited storage and unlimited websites.  The current plan shall expire on March, 2021.  At time of subscribing I was NOT aware the hosting company imposing a limit on the number of files upload.

What is the technical term for limit on "number of files upload"?  Is it data cap restriction/limit ?  I need this technical term in searching.

Please advise.  Thanks

Regards

---

### Post by wildmanne39 on 2020-12-03
*Thread moved to **The Cafe for a more appropriate fit**.*

---

### Post by TheFu on 2020-12-03
Did it just run out of inodes on the file system?
Or do you think they actually setup a quota?

---

### Post by satimis on 2020-12-03
> **TheFu said:**
> Did it just run out of inodes on the file system?
Or do you think they actually setup a quota?
My current hosting company set up a quota even though I'm subscribing plan of unlimited storage.

Regards

---

### Post by sdsurfer on 2020-12-03
With the help of[ this article]("https://www.techradar.com/web-hosting/the-hidden-limits-of-unlimited-web-hosting") (see "Technical" section) it looks like a search for "hosting unlimited inodes" might be of some help, which alludes to what TheFu is suggesting. From that section:

*"The inode is a good place to start. An inode is an entry in a file  system index which stores the details of a file or directory. A web host  might say it offers unlimited storage, but it'll almost certainly  restrict the total number of inodes you can use, effectively setting a  maximum number of files."*

They also discuss a lot of other items hidden in the marketing term "unlimited." Pretty through article.

---

