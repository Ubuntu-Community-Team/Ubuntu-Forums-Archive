---
title: "[Request] gksu 1.2.5"
date: 2005-05-28
forum: Ubuntu Backports
---

### Post by McQuaid on 2005-05-28
In this [thread](http://www.ubuntuforums.org/showthread.php?t=36945) over in breezy dev forum some users were talking about gksu's latest version 'greying out' the background when a user launches something that needs gksu.  I have this on my sid box and it's kinda nice.  I guess it basically emphasized the point that the user could not launch anything else when a gksu gui prompt was present.  

Not a big thing on my wishlist for backports so if it gives you any headaches don't worry about it.

---

### Post by Technoviking on 2005-06-02
Could not get it to compile from the source from breezy.

Sorry,
Mike

---

### Post by jdong on 2005-06-02
Ok, it's compiling OK after I removed the 06_translations.patch.

I'm surprised Ubuntu folks haven't seen this problem yet.

---

### Post by Technoviking on 2005-06-02
[QUOTE=jdong]Ok, it's compiling OK after I removed the 06_translations.patch.

I'm surprised Ubuntu folks haven't seen this problem yet.[/QUOTE]
Looked at doing that, but did not want to remove any the Ubuntu folks work :).

Mike

---

### Post by jdong on 2005-06-02
It was designed against 1.2.4... the patch clearly reveals that. In fact, some of the translations no longer exist!

I'm sure the maintainer will realized that soon, fix it, and upload a new revision. Meanwhile, the current Breezy gksu has been uploaded to the master mirror.

---

### Post by Slo Mo Snail on 2005-06-02
Done the same for ppc and uploaded to staging ;)

---

### Post by infinito on 2005-06-03
Fade out of screen doesn't happen here, using 1.2.5. from backports.

---

### Post by McQuaid on 2005-06-03
Yes it seems I was in error thinking this was a new feature of 1.2.5.  It is actually in the changlog of 1.2.4.
[http://people.debian.org/~kov/gksu/gksu1.2/ChangeLog](http://people.debian.org/~kov/gksu/gksu1.2/ChangeLog) 

So, I'm not sure why this does not work in the ubuntu build, maybe someone else can shed light on this.

---

