---
title: "new"
date: 2013-08-01
forum: Server Platforms
---

### Post by zalta1980 on 2013-08-01
I have a Ubuntu 12.04 Server Edition in production with Citadel as mail  server. It runs well with heavy traffic so I am afraid to mess with it.  However, there's an annoying bug in the Citadel version that comes on  12.04: The "Delete" button in web mail doesn't delete messages but only  hides them until you refresh. On the Citadel version coming with 13.04  this is fixed. I would really like to be able to upgrade Citadel, but  when I try I run into dependency problems and it won't install. I was  wondering if anyone here could help me find a way to get a newer version  of Citadel installed on 12.04 that doesn't include building it on the  server something I would rather not do on this particular system.

---

### Post by sudodus on 2013-08-01
Welcome to the Ubuntu Forums :-)

Did you try upgrading Ubuntu Server in two steps (via 12.10)?

But be sure to have a good backup before starting the upgrading process, because it is risky, and with two steps the risks are higher.

---

### Post by CharlesA on 2013-08-01
As this is a production server, I would strongly recommend against upgrading the entire OS from an LTS to a regular release just for one application.

It would probably be a better idea (even if it's more complicated), to install Citadel from their website, so you have the latest version.
[http://www.citadel.org/doku.php/doku.php?id=installation:start](http://www.citadel.org/doku.php/doku.php?id=installation:start)

---

### Post by sudodus on 2013-08-01
> **CharlesA said:**
> As this is a production server, I would strongly recommend against upgrading the entire OS from an LTS to a regular release just for one application.

It would probably be a better idea (even if it's more complicated), to install Citadel from their website, so you have the latest version.
[http://www.citadel.org/doku.php/doku.php?id=installation:start](http://www.citadel.org/doku.php/doku.php?id=installation:start)

+1

After thinking only a few seconds, I have to agree. Stay with the LTS version if possible because of the general stability of LTS versions.

---

### Post by Irihapeti on 2013-08-16
To those who replied to this thread:

This thread has been closed because the OP came back and included spam links in the first post. These have been removed.

However, the first post was a direct copy/paste from [http://ubuntuforums.org/showthread.php?t=2163488](http://ubuntuforums.org/showthread.php?t=2163488)

Since that post is still unanswered, please would you give your help there.

---

