---
title: "Ubuntu one doesn't sync my Documents folder. Other folders work fine."
date: 2012-03-24
forum: Ubuntu One (CLOSED)
---

### Post by Chiel92 on 2012-03-24
Hi,
I want to synchronise my Documents folder which is in my home directory. However that doesnt work.
When I press rightmouse button on the folder and select "Synchronise on Ubuntu one", it just doesnt do anything. I don't see "Stop synchronising" as with other folders.
Any ideas?

(I run ubuntu 10.04)

---

### Post by Chiel92 on 2012-03-29
Bump.
Maybe I should mention that the Documents folder is on a different partition.
In /etc/fstab I added entries such that my Documents are binded in my home folder.
I do the same for many folders. However only the Documents folder fails to upload on ubuntu one, the others work fine. 
So I guess this shouldn't make I difference. Just in case...

---

### Post by duanedesign on 2012-04-06
Could you run this command from a Terminal:

```
u1sdtool --list-folders
```

You should see the folders you have selected to sync and Subscribed=True. If you do not see the folder try restarting the syncdaemon and see if that helps.
```

u1sdtool -q

u1sdtool -c
```

---

### Post by Chiel92 on 2012-04-06
Thanks for your reply!
When I enter
```
u1sdtool --list-folders
```

I get a list with entries.
One of these entries is:
```
  id=b3fa058a-5cfa-41ff-aeac-e57f4fb8a437 subscribed= path=/home/user/Documents

```As you see, the folder is in the list, but the subscription seems to be unset?

---

