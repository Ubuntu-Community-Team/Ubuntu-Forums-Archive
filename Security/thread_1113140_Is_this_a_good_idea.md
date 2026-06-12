---
title: "Is this a good idea?"
date: 2009-04-01
forum: Security
---

### Post by JFASI on 2009-04-01
We're putting together an Ubuntu lab, and there just has to be a better way of keeping many computers in package-sync than manually installing every single application by hand on every single machine. They all mount their /home folder via NFS, and passwords and logins are moderated by yp/NIS. Is it a good idea to export /bin and /sbin via NFS with only root having write access? 

If not, is there a better way to manage a lab?

---

### Post by bodhi.zazen on 2009-04-01
IMO I would set up a local repository to reduce bandwidth and update the boxes with a cron job.

You can also look at LTSP

The edubuntu documentation will walk you through it.

[https://help.ubuntu.com/community/EdubuntuFAQ](https://help.ubuntu.com/community/EdubuntuFAQ)

---

### Post by HermanAB on 2009-04-01
You could use a NFS mounted root, but setting it up is a PITA.  Parallel SSH or update scripts are easier.
[http://www.theether.org/pssh/](http://www.theether.org/pssh/)

---

### Post by hyper_ch on 2009-04-01
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

