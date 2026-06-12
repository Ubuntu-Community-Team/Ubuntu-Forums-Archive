---
title: "Password-protected SD Cards"
date: 2009-02-10
forum: Security
---

### Post by RMOP on 2009-02-10
I have SD cards on my Nokia phones. Password is enabled. If I move an SD card to another Nokia phone, I'm prompted for the PW. If I insert the same SD card in either a Windows or Ubuntu PC, I'm greeted with, metaphorically, a blank stare. No PW prompt, can't see the media. Nothing. I have to REMOVE PW protection on the Nokia BEFORE transferring the card to my Ubuntu eeePC. And then re-enable it when I return the card to the Nokia. A nag.

I'd like a feaure/utility in Ubuntu that recognizes an SD card as PW protected and prompts for the PW. Am I asking too much?? Or is this a limitation imposed by the Nokia PW scheme itself. I'd really like to PW protect the SD card on my Ubuntu machine, and let it be interchangeable with those on my Nokia phones.

---

### Post by donkyhotay on 2009-02-10
ALthough I've never used it myself it sounds like your phone uses it's own encryption scheme. Unless nokia creates a linux app to decrypt their encryption system I don't think it can be done.

---

### Post by roboknight on 2011-12-14
There isn't any encryption scheme.  The card simply doesn't respond when locked.  Windows/Linux/OSX appear to have no tools to really deal with a password locked SDCard.  It is simply a matter of being able to send the password to the card (SDCard CMD42).  It is a little more involved, but basically, that is what it comes down to.  There may be an ioctl in the Linux MMC driver, but I haven't seen any tools lately that will issue SDCard commands to the device.  It may not even be possible to send the commands through a USB card reader.  Most card readers have limited functionality, (i.e. read/write cards), but when it comes to doing anything else... nothing.  That could be the main issue.  At any rate, you need a laptop/reader that supports the SDCard interface to be able to get Linux to access it.  If you can read the CID of the card, you should be able to send the password command or write software to allow that to happen.  Standard SDCard readers WILL NOT suffice (i.e. the ones you get in Best Buy/Walmart/Target/NewEgg).  Laptops with the readers built in typically have a real SDCard interface.

---

### Post by nothingspecial on 2011-12-14
[[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]](http://imageshack.us/photo/my-images/696/necrov.png/)

---

