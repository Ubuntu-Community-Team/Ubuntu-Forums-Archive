---
title: "Wacky Grub/UUID issue."
date: 2010-12-16
forum: Server Platforms
---

### Post by Tralce on 2010-12-16
So how do I tell grub to stop trying to boot based on UUIDs? I've been dealing with this for about two years now. I have this one system, a PowerEdge 1550, that for some reason WILL NOT boot using a UUID, and will only boot if I edit the first entry in grub, remove everything to do with UUIDs (completely delete the search line, replace root=uuid=[uuid] with root=/dev/sda1). I can't seem to make these settings stick and now with 10.10 there's no longer a menu.lst to edit. 

So, in short, I need grub to stop trying to boot based on a UUID. Absolute paths, baby. That's what I need.

---

### Post by Elfy on 2010-12-16
This might help - [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


> #GRUB_DISABLE_LINUX_UUID="true"

    * Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
    *

      A bug currently requires true be placed within quotation marks for this option, when uncommented, to take effect. Quotation marks currently are not the default and the user must add them.

---

### Post by Tralce on 2010-12-16
Ah, perfect. Worked like a charm. Thanks for the amazingly fast reply.

---

### Post by Elfy on 2010-12-16
Just happened to be passing :)

---

