---
title: "howto give permission to folder that root created?"
date: 2008-07-24
forum: Security
---

### Post by adhg on 2008-07-24
Hi all,

I (mistakenly) added a file to my folder with root permission. Now, when I try to access it (through my account 'adriana') I get an error message that I have no permission.

this is how it looks:

drwxr-xr-x  7 root      root       4096 2008-07-23 15:31 fileA
drwxr-xr-x  7 adriana   adriana    4096 2007-12-05 23:05 fileB

so for fileB - I'm good, I have access but for fileA - err.

I initially thought that this is only an issue of the properties (drwxr...) but it's the same for fileA and fileB.

So...how do I give permission to adriana (and other users) to fileA?

thanks

---

### Post by unutbu on 2008-07-24
```
sudo chown -R adriana:adriana fileA
```
This will make adriana the owner of the fileA directory, as well as the owner of all files within the directory fileA.

---

