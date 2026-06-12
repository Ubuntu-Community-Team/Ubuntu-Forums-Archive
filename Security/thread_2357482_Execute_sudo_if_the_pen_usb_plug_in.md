---
title: "Execute sudo if the pen usb plug in"
date: 2017-04-02
forum: Security
---

### Post by sed_faster on 2017-04-02
Hello folks,

In last days I was this idea. "It is possible create a pen usb which I use to plug on usb my ubuntu server and only the times which this usb plug I will use sudo?" This usb will be "usb key master"
Do you understand the idea? My level English it is not very good!

Thanks

---

### Post by TheFu on 2017-04-03
Perhaps making your login password require 2FA would be sufficient? Then whenever sudo is needed, you'd need 
a) something you know - a passphrase
b) something you have - a 2FA device

There are a few of these devices made. Yubikey, smartcards, OnlyKey are just a few. They are $10-$50.  smartcards have been around the longest, but due to many different standards, they are not universal.  Yubikey implements 4 different standards - each with different pros/cons.  OnlyKey is like a yubikey, but with 6 different groupings and some interesting other capabilities for destroying under distress, or plausible deniability and safe codes.  Of course, off of this assumes an owner has setup these things and understands their usage.

Just requiring a single device to access sudo isn't 2FA.  I've known people to place GPG keys on USB storage and require that to be used to unlock their GPG or ssh-keys. If you login to a normal user account, but not the account with sudo capabilities, this could be an added security layer to require an **su -** to a different userid when sudo is desired.

Sorry I don't have the total answer to the question.

---

