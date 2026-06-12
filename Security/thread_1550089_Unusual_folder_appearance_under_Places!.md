---
title: "Unusual folder appearance under Places!"
date: 2010-08-10
forum: Security
---

### Post by Manyette on 2010-08-10
I'm not sure this is the correct place for this post, but since it involves a keyring, I'm making my best guess.  Feel free to move it if I am in error.

I have had a "tmp" directory appear under Places in the first grouping which contains "Home", "Deaktop", "Documents", etc.  When I open this folder I find the attached png file.

When I look for this folder I find it is owned by root, but it appears in what should be my home directories.  The only guess I have as to it's origin is that I recently formatted a USB stick as an encrypted device. I don't know if that is when it appeared or not.

Can anyone shed any light on what this folder is, and why it appears where it does?  Somehow it just doesn't seem a correct placement.  Thanks for any information/help.

---

### Post by FuturePilot on 2010-08-10
/tmp is a directory where temporary files and directories are stored. Usually they are not preserved over reboots. As to how it got under Places, the only way I can think of is if you accidentally bookmarked it. You can open Nautilus and under Bookmarks select Edit Bookmarks and you can remove it.

---

### Post by Manyette on 2010-08-10
> **FuturePilot said:**
> /tmp is a directory where temporary files and directories are stored. Usually they are not preserved over reboots. As to how it got under Places, the only way I can think of is if you accidentally bookmarked it. You can open Nautilus and under Bookmarks select Edit Bookmarks and you can remove it.

Thank you very much.  You were of course correct, although how I managed to bookmark it totally escapes me.  Somehow, I just didn't connect it with the system's tmp folder.  I guess because of where it appeared.  Once again I've missed the glaringly obvious!  Again, many thanks.

---

### Post by FuturePilot on 2010-08-10
You're welcome :)

---

