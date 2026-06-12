---
title: "ubuntu one sync of unmounted truecrypte container"
date: 2013-06-21
forum: Ubuntu One (CLOSED)
---

### Post by ubto66 on 2013-06-21
ubuntu 12.04
ubuntu one 
Remark: Unless ubuntu one sells data on files on ubuntu one, then I would want to know why ubuntu one has not made ubuntu one encryption optional? Is it a technical issue?
On another forum, I was told, that if you make a 1gb truecrypt container and you put it into the dropbox sync file location. And you only connect to dropbox, when the truecrypt container is unmounted, then when you sync the unmounted truecrypt file/container with dropbox, then dropbox will only, and only have to, sync parts of the unmounted truecrypt file that have been modified. That can be done because the unmounted truecrypt file is not one big file, but is made of lots of smaller blocks. Dropbox can identify this, and only sync block changes. That is very much more effective, than having to upload the whole truecrypt file by every modification in the truecrypt container/file.
My question is, can ubuntu one manage to make this sync only modifications in the unmounted truecrypt file?
Thanks.

---

### Post by Irihapeti on 2013-06-21
I think you would either have to experiment, perhaps with a smaller truecrypt container, or ask the Ubuntu One devs directly. There's a "contact us" form on the Ubuntu One website.

Another option for encryption is encfs, available in the repositories. This creates individual files instead of a single container and the filenames are encrypted as well.

---

