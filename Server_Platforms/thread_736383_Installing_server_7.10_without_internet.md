---
title: "Installing server 7.10 without internet"
date: 2008-03-26
forum: Server Platforms
---

### Post by Armaron on 2008-03-26
I'm trying to install Ubuntu Server Gutsy 7.10. But for some reason it stops at 21% completed. It sais it is trying to get libc6-udeb. But never finishes. Any ideas on what I need to do?

---

### Post by ryth on 2008-03-26
Sounds like your disc might be corrupted.  Always a good idea to run the checksum on your image when you DL it, and then to run the disk check option when you first boot from it.  Is it possible for you to run the disk check and see what that comes up with?

*i should note that i'm not 100% sure that the server version disc has the disc-check option.

---

### Post by twright on 2008-03-26
make sure that you do not try to configure the internet connection (after it prompts you after DHCP fails)

if you try to set it up manually it will think you are connected and attempt to get files of the internet

---

