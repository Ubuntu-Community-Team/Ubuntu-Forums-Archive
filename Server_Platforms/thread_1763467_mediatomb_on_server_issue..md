---
title: "mediatomb on server issue."
date: 2011-05-20
forum: Server Platforms
---

### Post by mnknight on 2011-05-20
I have given up on trying to get mediatomb to work, so i want to completely remove it from the server, but bits and pieces are left behind even after i have purged them.
Can still access mediatomb by the webpage, any ideas on how to completely remove this 100%?

any help would be great.

---

### Post by arrrghhh on 2011-05-20
aptitude purge didn't get it?

Perhaps their site gives you a rundown on what's installed - did you install it from the repo's?

---

### Post by mnknight on 2011-05-20
nope purge didn't work and i installed it with apptitude! just want it gone, samba works well enough for my purposes, and i was just playing around when i installed mediatomb and need it gone.

thanks for replying

---

### Post by arrrghhh on 2011-05-20
Did you remove all three packages?

```
mediatomb
mediatomb-common
mediatomb-daemon
```

[This page](http://mediatomb.cc/pages/download#debian_ubuntu) might also help - it lists a few directories used by mediatomb... not sure if it's exhaustive or not tho.

---

### Post by mnknight on 2011-05-20
yes all three have been purged but still have issue where the server package left crap behind. thanks for the reply

---

