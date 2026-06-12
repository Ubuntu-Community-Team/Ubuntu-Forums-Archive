---
title: "Evolution Contacts not working."
date: 2010-01-14
forum: Ubuntu One (CLOSED)
---

### Post by Captain Rotundo on 2010-01-14
I installed the evolution-couchdb package, when I start evolution I can see the couchdb book, but my contacts (really just one at this point) don't show up.
When started from the shell evolution spits this error:

(evolution:30238): evolution-addressbook-WARNING **: error loading addressbook : e_book_new: no factories available for URI `couchdb://127.0.0.1'

---

### Post by rodrigo_ on 2010-01-15
> **Captain Rotundo said:**
> 
(evolution:30238): evolution-addressbook-WARNING **: error loading addressbook : e_book_new: no factories available for URI `couchdb://127.0.0.1'
It looks to me as if you don't have evolution-couchdb installed, so can you check it please?

---

### Post by user1397 on 2010-01-23
> **rodrigo_ said:**
> It looks to me as if you don't have evolution-couchdb installed, so can you check it please?
you can do that easily btw by typing ```
apt-cache search evolution-couchdb
```in a terminal

---

### Post by hhlp on 2010-01-25
follow this instruction it work for me :

[https://wiki.ubuntu.com/UbuntuOne/Tutorials/Contacts](https://wiki.ubuntu.com/UbuntuOne/Tutorials/Contacts)

---

### Post by duanedesign on 2010-01-27
@Captain Rotundo
Did the advice that was suggested help, is this still an issue for you? Hopefully you got it worked out, otherwise drop a post and we will see if we cant get you fixed up.

---

