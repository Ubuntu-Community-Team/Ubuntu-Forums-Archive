---
title: "What is the best way to use UbuntuOne for backups?"
date: 2009-10-14
forum: Ubuntu One (CLOSED)
---

### Post by omegamormegil on 2009-10-14
As Symlinks aren't supported (yet), what is the best way of backing up all my stuff?  I have a pretty complex organizational structure for my Documents, and I'd like them all backed up.  I don't want to just create a copy of everything in the UbuntuOne folder.  I want them backed up in place.  What is the best solution for this?  Hardlinks?  

What are the rest of you doing to accomplish this?

---

### Post by joshuahoover on 2009-10-15
> **omegamormegil said:**
> As Symlinks aren't supported (yet), what is the best way of backing up all my stuff?  I have a pretty complex organizational structure for my Documents, and I'd like them all backed up.  I don't want to just create a copy of everything in the UbuntuOne folder.  I want them backed up in place.  What is the best solution for this?  Hardlinks?  

What are the rest of you doing to accomplish this?

Right now there isn't a very good way to do this. We have it on our roadmap to allow users to select any folder to sync with Ubuntu One rather than force you to put everything into ~/Ubuntu One. This is something we're (currently) planning on doing for Lucid and we'll release in our beta PPA as the feature is built.

Thank you,

Joshua

---

### Post by cevans on 2009-10-30
> **omegamormegil said:**
> As Symlinks aren't supported (yet), what is the best way of backing up all my stuff?  I have a pretty complex organizational structure for my Documents, and I'd like them all backed up.  I don't want to just create a copy of everything in the UbuntuOne folder.  I want them backed up in place.  What is the best solution for this?  Hardlinks?  

What are the rest of you doing to accomplish this?

cp -rla should work, creating a hard-linked recursive copy, but it certainly isn't ideal.

---

### Post by superfoor on 2009-10-30
Just a show of hands how many people here noticed the problem after messing with the bandwidth limiter. After trying to slow mine down i started getting the error where it wouldnt connect so i went back in and just checked the bandwidth limiter checkbox leaving the numbers where they were and now I'm back up.

---

