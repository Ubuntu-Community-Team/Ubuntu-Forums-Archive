---
title: "Back up software from the repos?"
date: 2010-11-02
forum: Security
---

### Post by dogdo on 2010-11-02
I need a program that can be configured to detect new/updated files in my home directory and make a copy off these files to a truecrpyt encrypted external hard drive. Does such a program exist in the repos-and a good one too if possible-i dont want my drive becoming corrupted or the program missing files to copy etc

---

### Post by CharlesA on 2010-11-02
Check out rsync.

---

### Post by dogdo on 2010-11-02
> **CharlesA said:**
> Check out rsync.

Odd i seem to have that program already installed-when i click remove in software centre  a message pops up saying that doing this will remove updates for the ubuntu standard system set...wtf? 

and i need a program for local access back up, not one done from another machine...

---

### Post by CharlesA on 2010-11-02
rsync is installed by default. It can do local or remote backups.

Try reading the manual:

```
man rsync
```

---

### Post by HermanAB on 2010-11-04
Howdy,

Newcomers always look for 'backup software'.  That is probably a Windows thing.  Old timers use tar and rsync.  These two programs are extremely simple to use.  There are GUIs for them, but those typically just makes it more difficult rather than easier.  So read the rsync man page.  It is a better kind of copy and the usage is a one liner.

If your backup program is not a one liner, then you are doing it wrong.

---

