---
title: "Which DE/WM are we testing with Ubuntu in 18.04 development cycle in U+1?"
date: 2017-10-26
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-10-26
Whatever Ubuntu derivative we use with the bionic/devel repos, the lsb-release would show only, 

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu Bionic Beaver (development branch)"

```

It is what we'd see, even if we don't use any official (Ubuntu + official DE) derivative, for example a WM like Openbox. Do we test Ubuntu in the U+1  section only with the an official DE or also with any DE/WM available in the Ubuntu repos?

---

### Post by dino99 on 2017-10-26
At least with everything found in 'main', and the community, as usual, will do the extra testing  :P

---

### Post by vasa1 on 2017-10-26
I would think the DE/WM combos tested should only be the ones used by the official flavors because such feedback would be relevant to the final releases.

---

### Post by slickymaster on 2017-10-26
> **vasa1 said:**
> I would think the DE/WM combos tested should only be the ones used by the official flavors because such feedback would be relevant to the final releases.

This ^^^

---

### Post by Chanath on 2017-10-26
> **vasa1 said:**
> I would think the DE/WM combos tested should only be the ones used by the official flavors because such feedback would be relevant to the final releases.

Do you think the devs would come here to check how we are faring with the DE/WM combos or whatever else we are testing? I heard many a time that, they don't come here, and if we want to convey something to them, we have to file a bug report. Maybe, we discuss the problems here, if and when they happen, and one of us might file that bug.

---

### Post by flocculant on 2017-10-26
> **Chanath said:**
> Do you think the devs would come here to check how we are faring with the DE/WM combos or whatever else we are testing? I heard many a time that, they don't come here, and if we want to convey something to them, we have to file a bug report. Maybe, we discuss the problems here, if and when they happen, and one of us might file that bug.

The way is see this is: I found an issue - I'll report it - if it languishes I can find someone who knows what's up and point it out to them. It works. [lpbug]792085[/lpbug] reported in June 2011, I found someone in irc this year, few days later a patched kernel, a test or two, and fix released. 

The other way: someone finds an issue - doesn't bother reporting it - a few people chat about it in circles somewhere else - doesn't get fixed. They won't fix it without a bug - no paper trail to follow for the fix. Talk to someone about the issue - they'll ask you to report it.

In addition - if you know the upstream - link that to what you might've reported on launchpad.

---

### Post by Frogs Hair on 2017-10-26
Cariboo adressed this already. This would apply to other community maintained projects as well.
[https://ubuntuforums.org/showthread.php?t=2374905&page=2](https://ubuntuforums.org/showthread.php?t=2374905&page=2)





> Unity will still be supported until 2021 in the LTS versions, so any questions and bugs can be asked/reported in General Help. Starting with Bionic, unity is no longer in the main repositories, as it has been moved to the universe, where it can be maintained by the Ubuntu community. Bug reports and question can still be posted in the U+1 development forum, but any other discussions will be moved to the Chat Forums.




Thread Closed

---

### Post by cariboo on 2017-10-26
> **Chanath said:**
> Do you think the devs would come here to check how we are faring with the DE/WM combos or whatever else we are testing? I heard many a time that, they don't come here, and if we want to convey something to them, we have to file a bug report. Maybe, we discuss the problems here, if and when they happen, and one of us might file that bug.

This sub-forum is for reporting problems, and if you have a solution, post it. If no one comes up with a solution create a bug report.

If you are here just for conversation and not to help, you are in the wrong sub-forum. Any off-topic threads will either be closed, or moved to the chat areas of the Forums.

---

