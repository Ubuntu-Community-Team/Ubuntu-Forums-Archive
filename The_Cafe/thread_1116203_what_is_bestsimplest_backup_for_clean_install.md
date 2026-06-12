---
title: "what is best/simplest backup for clean install ?"
date: 2009-04-04
forum: The Cafe
---

### Post by newbie2 on 2009-04-04
ok... there is soon a new version of ubuntu ... for someone who would do a pure clean install of the new ubuntu version on his/her comp , and with a extern harddrive or a USB stick ...what is the simplest/best method to do that with maintaining his/her 'old' settings? :?:

---

### Post by billgoldberg on 2009-04-04
> **newbie2 said:**
> ok... there is soon a new version of ubuntu ... for someone who would do a pure clean install of the new ubuntu version on his/her comp , and with a extern harddrive or a USB stick ...what is the simplest/best method to do that with maintaining his/her 'old' settings? :?:

Backing up /home and putting it back after install.

Never done that though, could give problems.

---

### Post by newbie2 on 2009-04-04
> **billgoldberg said:**
> Backing up /home and putting it back after install.

Never done that though, could give problems.
thanks for the reply dude ;) ... i see that you are flemish ... i just posted this coz of someone who has some problems with such a 'clean install' , more specificaly with his pidgin settings : [http://www.seniorennet.be/forum/viewtopic.php?t=108901](http://www.seniorennet.be/forum/viewtopic.php?t=108901)

---

### Post by SomeGuyDude on 2009-04-04
A good idea: put /home on its own partition. Then you can upgrade/reinstall/switch as many times as you want no problems.

---

### Post by beercz on 2009-04-04
> **billgoldberg said:**
> Backing up /home and putting it back after install.

Never done that though, could give problems.
I have done this a few times and it seems to work.

As SomeGuyDude said putting your /home directory on a separate partition is useful as you don't have to restore your data once you have done a fresh install, your /home data is left untouched (providing you read the screen very carefully, especially in the partitioning section of the installer).

Always a good idea - if not essential - to regularly backup your /home directory though.

I do mine automatically everyday using [http://rsnapshot.org]("http://rsnapshot.org/") as a cron job.

Good luck!

---

