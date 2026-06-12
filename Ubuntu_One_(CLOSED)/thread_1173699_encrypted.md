---
title: "encrypted?"
date: 2009-05-30
forum: Ubuntu One (CLOSED)
---

### Post by capput on 2009-05-30
I was looking at the dropbox website which claims that with dropbox "All data is transferred over SSL and encrypted with AES-256 before storage."  After looking I have not been able to find any information on the ubuntu one site and I am curious if there is any similar protection for information with ubuntu one?

---

### Post by kklimonda on 2009-05-30
I know that it is transferred over SSL to them, dunno if it's encrypted before stored.

---

### Post by jflaker on 2009-05-30
Just from a liability standpoint, I can't see it not being stored in encrypted format....the cost of One leak of customer files that contain sensitive info can spell disaster for Canonical

---

### Post by xdevnull on 2009-10-14
Any more on this yet?  I looked around and couldn't find anything.  Frankly, I'm not wild about storing unencrypted files on any corporation's server.

---

### Post by joshuahoover on 2009-10-15
> **xdevnull said:**
> Any more on this yet?  I looked around and couldn't find anything.  Frankly, I'm not wild about storing unencrypted files on any corporation's server.

My apologies for the confusion. We need to add this information, as it's pretty important to know. :) Currently the transport of data from your computer to the cloud is encrypted using SSL. We do not encrypt the files in storage. Our recommendation is for users to do this using something like Karmic's encrypted home folder or other similar solutions (True Crypt, etc.)

Thank you,

Joshua

---

