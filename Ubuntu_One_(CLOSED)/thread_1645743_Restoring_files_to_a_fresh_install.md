---
title: "Restoring files to a fresh install"
date: 2010-12-15
forum: Ubuntu One (CLOSED)
---

### Post by scooby359 on 2010-12-15
I'm using Ubuntu One for both access to my files from various computers, but also as a lazy way of backing up my files. 

I can't get my head round what happens if I delete a file off my computer, or if I had to wipe my computer and do a fresh install - will UO just restore the files off the cloud server or will it think I've purposefully deleted them and wipe the copies saved to the cloud?


I've looked through old posts and can't see anything that specifically answers this query. Thanks for any help anyone can give.


Chris

---

### Post by duanedesign on 2010-12-18
The file sync works both ways. You delete a file off the server, it gets deleted from your computers. You delete a file from one of the computers connected to Ubuntu One and that file gets removed from the server and your other computers.

If your computer had a catastrophic failure, and could not start up, Ubuntu One would not be able to communicate with the server so there would be no chance that it could delete your files. You would just buy a new computer and add it to your Ubuntu One account. However if you accidentally delete a folder or something along those lines where the OS, and Ubuntu One, are still functional you run the risk of the files being deleted.

---

