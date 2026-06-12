---
title: "tar backup on tape"
date: 2008-12-17
forum: Server Platforms
---

### Post by Koybe on 2008-12-17
Hello,

I'm trying to use tar to backup folders on a tape.

I'm using ```
tar -cf /dev/st0 Myfiles
```Everything is going fine, then I try to read the tape :```
tarr -tf /dev/st0
```.... well perfect.

then I try to restore:```
tar -xf /dev/st0 "MyFile" -C /restore_directory
``` The tape is running for some time, like it's looking or the file, everything complete sucessfuly... but i got nothing in my restore directory. 

Any clue?

---

### Post by ikonia on 2008-12-17
your not using the auto-rewind device, try doing an mt -f /dev/st0 rewind first

---

### Post by Koybe on 2008-12-21
Thank you for your reply. I tried but it didn't help.

Any other ideas?

---

### Post by Koybe on 2008-12-21
OK, I found it. -C seems to be an invalid otion with tape. Not using it result in extracting to current directory.

Thanks anyway!

---

