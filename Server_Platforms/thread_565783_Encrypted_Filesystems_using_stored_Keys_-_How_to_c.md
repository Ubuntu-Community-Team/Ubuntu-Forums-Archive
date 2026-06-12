---
title: "Encrypted Filesystems using stored Keys - How to change to passphrase entry?"
date: 2007-10-02
forum: Server Platforms
---

### Post by steve987 on 2007-10-02
Hello Community :-),

after trying Ubuntu for a while I jumped now into (not that) cold water and banned windows-xp from my harddrive.

I've succesfully setup encrypted partitions using the [How to Setup Completely Encrypted System - Ubuntu Feisty]("https://help.ubuntu.com/community/EncryptedFilesystemHowto8") on my IBM T41.

I've encrypted: /root, /swap and of course /home.
As mentioned in the howto, the unlock-keys for /swap and /home are stored on the /root partition in /etc/keys/home.key.

I feel uncomfortable with this setup now and would like to change it, so that I need to enter an additional passphrase to open my encrypted /home-partition, mainly because of two reasons:

1) If somebody sees my /etc/keys/home.key (maybe because of an intrusion via the web?) my encrypted data is totally open.

2) How can I unencrypt my /home-partition when my /root-partition is damaged or the home.key-file is corrupt?

QUESTION:

What do I need to do, to use a passphrase for my /root-partition instead of a key stored on another partition?
Of course I don't want to reformat my whole partition ... :-)

regards from berlin

- Stev E.

---

