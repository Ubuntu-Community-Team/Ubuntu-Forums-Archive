---
title: "Possible fix to much Cinelerra Buginess"
date: 2008-05-11
forum: Ubuntu Studio
---

### Post by kayosiii on 2008-05-11
I noticed that the most recent Cinelerra Build for ubuntu comes with an option to run as superuser - well this option seemed to fix a lot of problems for me. However I believe the same affect can be achieved a lot more conveniently by making cinelerra a member of the audio group...

Anyways if you want to test try
the following command in a command prompt and let me know if Cinelerra gets any more stable for you...

sudo chown root.audio /usr/bin/cinelerra

---

### Post by dperfors on 2008-05-13
For me it still doesn't work after changing the group, it starts up, but doesn't responce...

---

### Post by kayosiii on 2008-05-13
are you running the regular or studio version of ubuntu?
also what if you try 
running sudo cinelerra from command line

---

### Post by cotcot on 2008-05-13
I am running cinelerra on 64 bit. No crashes. No need to run as user. (compiled it myself from svn).

---

### Post by dperfors on 2008-05-14
> **kayosiii said:**
> are you running the regular or studio version of ubuntu?I use the regular version, but I use the Realtime version of the kernel...
> **kayosiii said:**
> what if you try running sudo cinelerra from command lineI didn't check that, but I used the "Cinelerra hi-pr (only admin)" menu item and that works.

---

### Post by daverich on 2008-05-14
If you get fed up give Kdenlive a go from the Hardy Repos.

It's MUCH better than the old version, I actually managed to finish a project with it.

Kind regards

Dave Rich

---

