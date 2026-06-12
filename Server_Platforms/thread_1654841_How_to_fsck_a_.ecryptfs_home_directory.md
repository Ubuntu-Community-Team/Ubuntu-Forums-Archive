---
title: "How to fsck a .ecryptfs home directory?"
date: 2010-12-28
forum: Server Platforms
---

### Post by genti on 2010-12-28
The battery of my UPS is shot and the computer was on when I lost power a couple of times ...
The computer starts fine and I can use it almost normally but I cannot delete some files in my home directory.

First part of the attachment has the weird permissions.

When I do a rm (sudo or not does not matter) I get:
**#rm: cannot remove `File1': Operation not permitted**

I tried adding acl permissions but that did not get me anywhere.
I tried deleting it via inode number and I was not able to:

#ls -li

# find . -inum 20922369 -exec rm -i {} \;
#find: `./File4': Input/output error
**#rm: remove weird file `./File1'? y**
#rm: cannot remove `./File1': Operation not permitted

#/home/user/.Private on /home/user type ecryptfs 

Fsck on an unmounted partition where the whole /home is mounted shows no problems so the issue is within the ecryptfs.

How can I run a fsck? Or to find what encrypted filename belongs to the corrupted files and delete them?

Most likely there are other corrupt files somewhere so does anyone have a suggestion

Thank you!

---

