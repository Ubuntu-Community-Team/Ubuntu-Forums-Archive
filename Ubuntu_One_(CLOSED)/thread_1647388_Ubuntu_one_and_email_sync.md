---
title: "Ubuntu one and email sync"
date: 2010-12-17
forum: Ubuntu One (CLOSED)
---

### Post by Me Mechant on 2010-12-17
Hi,

I'm using ubuntu one for about 4 month now and i must say that it becomes better every day! Good job everyone who works on it!

I was wondering if it was possible to do a back up of my email via ubuntu one. I'm using evolution and i don't really know which files to add to the synchronization process to be able to retrieve my email if my computer explode.

Thanks for the help!

---

### Post by duanedesign on 2010-12-18
What I like to do is on Fridays, when I make my backups, I do my evolution backup by going to File --> Backup Evolution Settings. When it asks what folder you would like to save the .tar.gz you could select your Ubuntu One folder.

---

### Post by Me Mechant on 2010-12-18
Thank Duanedesign!

A perfect answer as usual!

---

### Post by mrnettles on 2011-07-21
Does that actually back up the email messages or just the settings?

---

### Post by duanedesign on 2011-07-22
> **mrnettles said:**
> Does that actually back up the email messages or just the settings?

it backs up everything, including messages.

---

### Post by mrnettles on 2011-07-31
Thanks.

---

### Post by tellapu on 2012-06-15
Thanks syntaxer!

After ending process ubuntuone-syncdaemon in the system monitor the following worked in Ubuntu 12.04 AMD64:

> In **~/.config/ubuntuone** there is a file **syncdaemon.conf**.
Just add the following code at the beginning of the file (above [bandwidth_throttling]):
     Code:
     [__main__] root_dir = ~/new/folder 
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

