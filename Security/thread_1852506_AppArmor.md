---
title: "AppArmor"
date: 2011-09-30
forum: Security
---

### Post by Merisi on 2011-09-30
Where do I download AppArmor?  If you get it to start with where do I find it?  I've been reading this thread [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906) and have been getting very confused.

---

### Post by sanderd17 on 2011-09-30
apparmor is installed by default on Ubuntu. You just don't get a settings manager.

It is used to limit powers of applications. Maybe you find something useful in this links: [https://wiki.archlinux.org/index.php/AppArmor#Links](https://wiki.archlinux.org/index.php/AppArmor#Links)

---

### Post by Merisi on 2011-09-30
I just entered 

[FONT=Times New Roman]sudo apt-get install apparmor-profiles[/FONT]
into terminal and something happened but I'm not sure what.

---

### Post by Rubi1200 on 2011-09-30
Thread moved to Security Discussions.

Merisi,
the best way to begin understanding AppArmor is to read the documentation.

sanderd17 already posted a link that has useful information.

If you want to try testing AppArmor, I recommend using a separate test partition or virtual machine so that if something goes wrong you can always start afresh.

---

### Post by sanderd17 on 2011-09-30
That sets some settings for certain apps, nothing else.

AppArmor really is a powerful but complex tool. You can also create profiles by letting it learn from the app. You work with the app, AppArmor registers everything and in the created profile, it gives access to anything you need for the app, but blocks all other things.

I do not know how to do it, I only read that.

If you are a regular desktop user, you don't really need that (it protects against attacks from the inside, a desktop user needs to be protected against attacks from the outside).

---

### Post by Merisi on 2011-09-30
> **sanderd17 said:**
> That sets some settings for certain apps, nothing else.

AppArmor really is a powerful but complex tool. You can also create profiles by letting it learn from the app. You work with the app, AppArmor registers everything and in the created profile, it gives access to anything you need for the app, but blocks all other things.

I do not know how to do it, I only read that.

If you are a regular desktop user, you don't really need that (it protects against attacks from the inside, a desktop user needs to be protected against attacks from the outside).

I think I'm just going to leave this one alone for now as it just seems to complicated for me.

---

### Post by Dangertux on 2011-09-30
It's not really all that bad you just have to spend a little bit of time reading about the syntax for profiles

You may wish to read [this]("http://www.google.com/url?sa=t&rct=j&q=novell%2Bapparmor%2Bguide&source=web&cd=1&ved=0CB0QFjAA&url=http%3A%2F%2Fwww.novell.com%2Fdocumentation%2Fapparmor%2Fpdfdoc%2Fapparmor2_admin%2Fapparmor2_admin.pdf&ei=m9iFTuPCGc2ztwfthrFJ&usg=AFQjCNFkVnHk6ViSUyW50JkgTE8ZoCXvAA&sig2=nif3PPXwNpSFup3B-u5YGA&cad=rja")  (pdf) and[ this ]("http://www.google.com/url?sa=t&rct=j&q=novell%2Bapparmor%2Bguide&source=web&cd=2&ved=0CCUQFjAB&url=http%3A%2F%2Fwww.novell.com%2Fdocumentation%2Fapparmor%2Fpdfdoc%2Fbook_opensuse_aaquick21_start%2Fbook_opensuse_aaquick21_start.pdf&ei=m9iFTuPCGc2ztwfthrFJ&usg=AFQjCNGK7XJUm7-fdSHWQDPPApOSXJMORQ&sig2=8beThEy8MWZZe9V46RLtnw&cad=rja")(pdf) it's very enlightening when it comes to writing your own profiles. The second one will be more useful for you since the first is more directly related to OpenSuse

---

