---
title: "OSX Folder Actions in Ubuntu?"
date: 2007-08-06
forum: The Cafe
---

### Post by sicofante on 2007-08-06
I've stumbled upon this tonight:

[http://www.simplehelp.net/2007/01/30/folder-actions-for-os-x-explained-with-real-world-examples/](http://www.simplehelp.net/2007/01/30/folder-actions-for-os-x-explained-with-real-world-examples/)

I don't know if something similar exists in Ubuntu. I find it a great idea.

---

### Post by Nikron on 2007-08-06
> **sicofante said:**
> I've stumbled upon this tonight:

[http://www.simplehelp.net/2007/01/30/folder-actions-for-os-x-explained-with-real-world-examples/](http://www.simplehelp.net/2007/01/30/folder-actions-for-os-x-explained-with-real-world-examples/)

I don't know if something similar exists in Ubuntu. I find it a great idea.

Yeah, it'd be fairly simple with either ionotify or periodic scanning with cron.

---

### Post by vexorian on 2007-08-06
heh probably the first thing from OSx I heard and like, this sounds very useful, hope either gnome or KDE clones that...

---

### Post by sicofante on 2007-08-07
> **Nikron said:**
> Yeah, it'd be fairly simple with either ionotify or periodic scanning with cron.
You mean easy for a developer o easy for an end user? Can you elaborate?

---

### Post by juxtaposed on 2007-08-07
Wow, one thing that I have never seen before and I find really cool and useful.

---

### Post by a12ctic on 2007-08-07
It'd be pretty easy to do probably, ive had folders like that where i just use a batch script to convert them all.

---

### Post by stmiller on 2007-08-07
Nautilus scripting is the closest thing I can think of.

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by vexorian on 2007-08-07
> **sicofante said:**
> You mean easy for a developer o easy for an end user? Can you elaborate?
Well, the method described in that blog is not specially easy to use or understand.

---

### Post by Nikron on 2007-08-07
> **sicofante said:**
> You mean easy for a developer o easy for an end user? Can you elaborate?

Dunno if you call a simple bash script a developr or user level.  Either way, with something like inotify-tools you can set up a simple bash script for "folder options"

---

### Post by 23meg on 2007-08-07
I put together a script that utilized [fileschanged]("http://fileschanged.sourceforge.net/") a while ago to accomplish this. It did work, but not consistently enough for casual use; I needed to have a way of controlling multiple instances of fileschanged reliably.

Fileschanged is probably not the best choice if this is to be implemented into a DE though; working with FAM / gamin / inotify directly would be the way to go.

---

### Post by bikeboy on 2007-08-07
Hmm, maybe somebody who understands the system a bit could blueprint this for Gutsy+1?

---

### Post by vexorian on 2007-08-08
> **bikeboy said:**
> Hmm, maybe somebody who understands the system a bit could blueprint this for Gutsy+1?
it looks more something gnome should try in nautilus, so I am kind of thinking this would be good as a topaz brainstorm.

---

### Post by FuturePilot on 2007-08-08
This sounds like a pretty handy thing to have.

---

### Post by sicofante on 2007-08-08
How about using this?

[http://oss.sgi.com/projects/fam/faq.html#what_is_fam](http://oss.sgi.com/projects/fam/faq.html#what_is_fam)

They say Nautilus already uses it, so knowing when a directory/folder has received a new file should be already built into Nautilus. Adding a script to that event should be quite easy.

---

