---
title: "FireFox 3 and Firefox 3.5 side by side?"
date: 2009-10-29
forum: Ubuntuzilla
---

### Post by shane2peru on 2009-10-29
I have the newest FF installed thanks to Ubuntuzilla, and I'm wondering if I can still run my old FF3.0 installation to test some html coding some times.  Is this possible?

Shane

---

### Post by grizato on 2009-10-29
Yes there is, I found out when I id a similar thing the other way round. First get Firefox-3.tar.gz of the mozilla website and run it from the uncompressed package.

Hope that's what you meant/wanted!:p

Karmic's Out!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by nanotube on 2009-10-29
> **shane2peru said:**
> I have the newest FF installed thanks to Ubuntuzilla, and I'm wondering if I can still run my old FF3.0 installation to test some html coding some times.  Is this possible?

Shane

Hey
yes, you can, you can run firefox.ubuntu, which will run the repos version of ff3.

however, first, quit ff3.5 if it is running (or run with -no-remote option), because it will otherwise detect a running firefox and simply spawn a new window of ff3.5, and second, create a separate profile, since there have been a bunch of changes in profile structure between ff3 and ff3.5, and you really shouldn't share the same profile between the two.

---

### Post by shane2peru on 2009-10-29
> **nanotube said:**
> Hey
yes, you can, you can run firefox.ubuntu, which will run the repos version of ff3.

however, first, quit ff3.5 if it is running (or run with -no-remote option), because it will otherwise detect a running firefox and simply spawn a new window of ff3.5, and second, create a separate profile, since there have been a bunch of changes in profile structure between ff3 and ff3.5, and you really shouldn't share the same profile between the two.

Thanks!  That worked like a charm!  I did have to close FF3.5 even with the -no-remote option I couldn't get them to run together.  That is ok, I just needed to open FF3.0 and run it to check some pages.  

Shane

---

### Post by nanotube on 2009-10-29
ok cool :) strange that no-remote didn't work... maybe both firefoxes have to run with -no-remote in order for it to work...

---

