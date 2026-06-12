---
title: "Breezy/Hoary Backports"
date: 2005-09-10
forum: Ubuntu Backports
---

### Post by Emerzen on 2005-09-10
Hi all,

I just upgraded to Breezy Preview release and all went well.  I know Breezy has no official Backports yet.  I was wondering if I can simply add the hoary backport addresses to synaptic w/o any harm (keeping 'hoary' in the name instead of breezy)?  Will that "break my Ubuntu?"

-Thanks

---

### Post by jdong on 2005-09-10
It won't do much, but it won't do any harm either. All of hoary-backports packages (official and unofficial, staging and stable) register as older than Breezy, so APT would never select any of these packages.


Breezy-backports will be open when Breezy+1 is launched. Keep your eyes peeled :)

---

### Post by Toddy on 2005-09-10
I temporarily add backports to my sources.list to pick-off a few key files needed for Breezy (w32codecs for example).  I've noticed that when doing so, I get notified about a package "gnome-btdownload" (0.0.20-1~5.04ubp1).  I've simply ignored this file, and it goes away when I remove backports from my Breezy sources.list.  So the statement of "APT would never select any of these packages" isn't quite true.

---

### Post by jdong on 2005-09-10
Fine, I retract and qualify that statement!

After a conversation on #ubuntu-devel, I was informed that Breezy would likely get this update.

Also, gnome-btdownload is python based and compatible with Hoary and Breezy.

---

### Post by XDevHald on 2005-09-10
[QUOTE=jdong]Fine, I retract and qualify that statement!

After a conversation on #ubuntu-devel, I was informed that Breezy would likely get this update.

Also, gnome-btdownload is python based and compatible with Hoary and Breezy.[/QUOTE]
 Yeah, I got that update much earlier today and figured it was :)

P.S We need an update for the connection because of timeouts (Is annoyed by this action) It really feels like cable has tunred into dialup :p I've also rebooted my router and the problem still persists.

---

### Post by Emerzen on 2005-09-10
Thanks for the replies, I'll give it a go.

---

