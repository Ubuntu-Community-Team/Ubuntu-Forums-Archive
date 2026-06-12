---
title: "mounting truecrypt as /home"
date: 2007-05-30
forum: Server Platforms
---

### Post by Xbehave on 2007-05-30
im trying to mount a truecrypt volume as my home. the problem is the permission on my home directory become 700 meaning that kdm complains it cant access some files
the permissions for the file are 777
the permissions for /home/juan are 777
but the permission for the mounted /home/juan are 700

also to unmount i have to drop to console
then i have to unmount -l and logout of the console then close the truecrypt file
i mount the file using truecrpyt -u -i as without -u it sets ownership to root and i cant access the folder atall 
if i mount before i login in kdm i get an access error on a . file
if i mount after, i cant launch any more programs
i have tried with both copied and empty folders and even tho a blank folder will be filled if its not a true crypt volume it still fails.

what can i do to make the permissions of the mounted file 777 (or whatever thy need to be) chmod doesn't do anything?

---

### Post by kalisto on 2007-05-31
Hi Juan you might want to take a look at this: [http://www.willempen.org/mount-user-permissions/](http://www.willempen.org/mount-user-permissions/)

I think this may be the touble your having.

---

