---
title: "CD/DVD Creator"
date: 2012-11-02
forum: Virtualisation
---

### Post by oldefoxx on 2012-11-02
I just found a conflict between CD/DVD Creator and Oracle VirtualBox.  If VirtualBox takes the CD/DVD Drive and reallocates it to a client for its use, then you stick a DVD or CD into the drive, CD/DVD Creator snatches it away and treats it like Ubuntu is in charge, which technically it is, but not while it is allocated to the client.

I don't even know how you uninstall CD/DVD Creator and put it back later.  I did find that if the CD or DVD is non-blank, you can go under Devices/Storage and have VirtualBox get it back for the client's use.  But if it is blank, you have to go back under Ubuntu and close down CD/DVD Creator first, since it want to know what to do with the blank disk.

---

### Post by oldos2er on 2012-11-02
Moved to Virtualisation.

---

