---
title: "An odd issue."
date: 2009-01-18
forum: System76 Support
---

### Post by xakh on 2009-01-18
Every time I run Update Manager and need to install something, it gives me this weird error.
It says that the cache file is corrupted. I'm not at all sure what this means. Someone help? Next time I do an update, and the error appears, I'll screenshot it.

---

### Post by mgol on 2009-01-18
Try this:
[http://ubuntuforums.org/showpost.php?p=6528443&postcount=11](http://ubuntuforums.org/showpost.php?p=6528443&postcount=11)
These folders contain cache files for what's inside repositories. Maybe it'll help...

---

### Post by xakh on 2009-01-18
> **mgol said:**
> Try this:
[http://ubuntuforums.org/showpost.php?p=6528443&postcount=11](http://ubuntuforums.org/showpost.php?p=6528443&postcount=11)
These folders contain cache files for what's inside repositories. Maybe it'll help...

Hmm. I hope this isn't one of those rm-rf things that kills my machine. I'm going to do it, but if I have to factory restore, I'll be sad.
EDIT: I did it, and it said the first one didn't exist, and the second one didn't wanna be removed, even with sudo, which is weird.

---

### Post by thomasaaron on 2009-01-18
try running 

```
sudo apt-get clean
sudo apt-get check
sudo apt-get install -f
```

---

### Post by mgol on 2009-01-18
> **xakh said:**
> Hmm. I hope this isn't one of those rm-rf things that kills my machine.
You could look into the whole thread I linked to and You would see that this has already helped somebody - if it were a threat somebody would quickly delete my post, and certainly wouldn't thank me for that one. ;)

> **xakh said:**
> EDIT: I did it, and it said the first one didn't exist, and the second one didn't wanna be removed, even with sudo, which is weird.
The partial folder might not exist, that's not weird. And as for the second error - what exactly was it? Maybe just an information refusing to delete some directories, which is actually correct if You didn't (and You shouldn't in this case!) give a "-f" option to "rm" command.

Anyway, I suppose that if You write it, the update-manager error didn't disappear?

---

### Post by xakh on 2009-01-18
> **mgol said:**
> You could look into the whole thread I linked to and You would see that this has already helped somebody - if it were a threat somebody would quickly delete my post, and certainly wouldn't thank me for that one. ;)


The partial folder might not exist, that's not weird. And as for the second error - what exactly was it? Maybe just an information refusing to delete some directories, which is actually correct if You didn't (and You shouldn't in this case!) give a "-f" option to "rm" command.

Anyway, I suppose that if You write it, the update-manager error didn't disappear?

I didn't put a -f, but it just said "Is a directory"
Btw, I don't know if the error's happening, every time I actually get an update. I haven't seen an update yet. It doesn't really do anything, it just pops up a dialog box, I dun like that.

---

### Post by mgol on 2009-01-18
It's normal, as I said in the cited post. rm invoked without -f option omits directories and I want it to omit them. It prints warnings that it didn't delete them, but it's ok. If it actually deleted those directories, updates-managing programs would complain and You'd have to recreate them. So maybe the problem is gone.

But please do execute also commands that thomasaaron posted, they can repair a problem if my solution didn't work.

---

