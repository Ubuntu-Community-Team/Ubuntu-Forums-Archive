---
title: "How to reinstall Ubuntu and link it to the same 20 GB folder made for it on D drive?"
date: 2013-05-14
forum: Ubuntu Application Development
---

### Post by someshangale on 2013-05-14
Hi!
This is my first query i am putting on forum.I am a new user of ubuntu.Lastly i installed Ubuntu 12.04 LTS on my PC on D drive.It was working ok with some minor problems.Later when my windows crashed I called my system administrator who was unaware of Ubuntu OS.He format the C drive where Windows was installed but this also led to removal of my Ubuntu since there is a boot file of ubuntu on C drive.But since basic ubuntu was installed on D drive i still have the 20 GB folder named ubuntu intact but can't access it since it is in some diffrent format.
I didn't took back-up of the Os in Deja-u hence i want to know whether i can access the document in that 20 GB folder without installing ubuntu ?If yes,How?If not then whether i can access it after installing ubuntu? If yes how? Can i make that [COLOR=#ff0000]UBUNTU[/COLOR] [COLOR=#ff0000]folder[/COLOR] the [COLOR=#0000cd]default UBUNTU[/COLOR] folder again? how?

Please revert back with solution since i am having some important data in it.

Regards
Somesh

---

### Post by TheFu on 2013-05-14
Ok, so it sounds like you did a Wubi install?  Please confirm this.  Wubi is not supported in the current Ubuntu, so you have an older version - hopefully 12.04.  All of your questions here should state clearly that you are using Wubi - this is very important to getting good help.

I don't know that this will work, but I suspect it will.  I would:
* rename the current d:/Ubuntu folder to d:/Ubuntu.good
* Get the exact same installer that you used the first time ... the same Ubuntu release.
* Install Ubuntu using that installer. Install into d:/Ubuntu
* Rename d:/Ubuntu into d:/ubuntu.new
* Rename d:/Ubuntu.good into d:/Ubuntu 
Boot.

See if that works. BTW, I would backup both installations - that is both the *.good and *.new at the appropriate time - PRIOR to doing anything risky.

I would strongly recommend getting onto 12.04 is you are running something else.  Then plan to move onto 14.04 when that becomes available. If you've decided to keep using Ubuntu by April of 2014, then it is time to move to a dual-boot configuration and drop the Wubi. ;)

Good luck!

---

### Post by someshangale on 2013-05-16
Dear TheFu,
Thanks for the reply.

yes i was using Ububtu 12.04 LTS and did a WUBI installation.

I will try the trick you mentioned .lets hope that it work.

---

### Post by someshangale on 2013-06-18
Dear TheFu,
 Thanks for the solution.It worked.

---

