---
title: "ubuntu doesnt respect my file locks"
date: 2009-04-30
forum: Server Platforms
---

### Post by johnman145 on 2009-04-30
I made my own java server which creates a lock file to indicate the server is running. After the server is finished the lock if automatically released. This way i can restart a new server which will wait until the the other instance has finished by looking at the file-lock. 

The server is running on ports  < 1024 so i need to run it with sudo to be able to bind to the ports. The problem is that when i run a second instance... and close down the first one, the file-lock is acquired instantly while the first server is NOT finished. So it seems that even if i lock a file... i can still get a new file lock on it.

Is this a bug? A feature? or is this normal when running programs with sudo?

How can i create a file-lock (in java) which is enforced?

im running:
- Ubuntu server ED 8.04 LTS
- Java(TM) SE Runtime Environment (build 1.6.0_11-b03)
- Java HotSpot(TM) Client VM (build 11.0-b16, mixed mode, sharing)

(The locking mechanism works perfectly winXP sp3 btw)

---

### Post by johnman145 on 2009-05-01
I took me some time but i finally decided this can not be done with the normal java libs afaik. So i got rid of all filelocks and use sockets now. Since i got some problems in the past where the OS didn't free the used sockets it was not my first choice... but so far it is working perfectly, and better then the file-locking stuff. Im really surprised and annoyed by the fact java doesn't have an OS wide semaphore :@.

---

