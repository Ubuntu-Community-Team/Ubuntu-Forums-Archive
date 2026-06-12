---
title: "Is sources.list processed from top to bottom? Trouble with AU repository"
date: 2007-07-27
forum: Repositories &amp; Backports
---

### Post by OzzyFrank on 2007-07-27
Hi. For the last few days I've had lots of problems getting many programs through Synaptic, and tonight while trying to get Xfce into Ubuntu I've found the culprit is **[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted**. I copied and pasted the lines and got rid of the "au" but still had this error, which perplexed me as I had just added the official Ubuntu ports. I then thought that perhaps it's not even reading what I just added, so commented out the original AU ones and sure enough all works fine. So I suppose I have 2 questions:

Is sources.list processed in order, and somehow Synaptic overlooks what follows if there is an error? Isn't it supposed to look through all the links provided and just go with what works and ignore the others?

And what's going on with the Aussie archives??

Oops, that was 3 questions, hehe.

---

### Post by mrfreddy on 2007-07-27
Take a gander here:
[http://ubuntuforums.org/showthread.php?t=509805]("http://ubuntuforums.org/showthread.php?t=509805")

---

