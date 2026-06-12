---
title: "ilegitimate &quot;su: Authentication Failure&quot; returned from root&amp;password."
date: 2007-10-20
forum: Testimonials &amp; Experiences
---

### Post by Siljrath on 2007-10-20
this happened on my dad's PC which i installed via wubi, studio ubuntu.  the password for both my user and for root.
i thought i must have just forgotten them since it was such a long time from when i had installed til when i actually got around to logging in (a microsoft keyboard wasnt playing nice n not being "on" for when i needed to press down to select ubuntu from the boot options), and i thought this more likely because it's my dad's computer, so i thought i must have made up a different password specially for this case.

so i thought nothing more of it... just my memory failure i thought.


...

until just a moment ago, on my own studio ubuntu (7.04 feisty fawn) installed from cd, doing the same thing!  except this time my user password and name are reccognised.

how come i keep getting "Authentication Failure" in the terminal, and basically the same on the login screen?

i am now 100% certain i am entering the correct password....

is there somethign simple i am missing?

is ther something i need to be doing differently in ubuntu?

have i actually gone delusional?

---

### Post by muffinhead on 2007-10-23
I'm getting the same thing when trying to log on as root. Searching the forum now to see if I can find anything. If I do find anything I'll let you know.

I really need to login as root since I can only install the newest Nvidia driver for linux as root and without the X-Server running.:(

---

### Post by muffinhead on 2007-10-23
Solved My problem. Logging in as root is not advised and is disabled by default.

Instead use sudo -i

I think this is called a fakeroot or something.:)

Oh crap I accidentally double posted instead of editing, can a mod merge my posts or is it no big deal?

---

