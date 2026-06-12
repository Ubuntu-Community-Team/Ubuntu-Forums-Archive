---
title: "facepalm"
date: 2010-09-18
forum: The Cafe
---

### Post by Goolie on 2010-09-18
So, I've been studying from a book about linux command lines, and it supposed to help you out with your Linux+ certification.  Well, I'm going along, learning about chmod, chown, ls, cd, mkdir, recursive, text filters, oh it was just exciting.

Until I rebooted my PC and got a good ol' 

"There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256).

So, I'm all like. . hrm?  And my GUI won't load.

So, I head over to the forums like a good kid and search.  I see a bunch of responses and one of them mentions the /tmp folder.  Hrm. . .

So I jump over to the terminal (as that's the only way I can log in to the system) and that works.

Turns out this damned book decided throwing

LOG IN TO ROOT AND DO THIS:

```
chmod -R ugo-rwx /tmp
```
Touche, little book of learning.  You got me.

Fixed the permissions, but I kind of feel silly for doing this.  Why would they even put that in this damned book? haha, if I didn't have at least a slight clue about what happened, i'd be pissed!

:facepalm:

---

### Post by ubunterooster on 2010-09-18
I really hoped you contacted the author/publisher. This could cause a lawsuit in many cases if it happened to the wrong person. I hope they fix the error for later publications

---

### Post by red_Marvin on 2010-09-18
It might be a typo, or it might be a tough love way of teaching you not to enter commands that you haven't analyzed. It is pretty benign, I mean it could have been a command that overwrites the kernel and whatnot - so I would not attribute it to malice, for that reason, and for the fact that it is in a book, where the author is easily traced.
I actually think it's good that it was put there, now you'll pay more attention. (:

---

### Post by Goolie on 2010-09-19
I didn't think it was malicious, and I don't know if they intended it to be so, I mean, I *did* get the thorough learning of permissions and what not with this experience.  So the curveball just might be a little twist.  A twist down a path of learning!  I'll toss them an e-mail, just to see a response.

---

### Post by ubunterooster on 2010-09-19
Excellent. Just give us the response, if you wish.

---

### Post by Goolie on 2010-09-19
> **ubunterooster said:**
> Excellent. Just give us the response, if you wish.

wilco!  i'll ask them if they can post their response here!

:)

---

