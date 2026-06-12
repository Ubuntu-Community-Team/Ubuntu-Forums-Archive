---
title: "Automatically unlock encrypted HDD"
date: 2013-09-09
forum: Security
---

### Post by Zukaro on 2013-09-09
I was wondering how to automatically mount my encrypted HDD.  I'm using Ubuntu 13.04 and my machine has an encrypted SSD (which is what it boots from) and then an encrypted 1TB HDD for storage.  Basically I want to unlock both drives when entering my password to boot the machine (I have automatic login enabled as I'm the only user of this machine and the initial decryption acts as a login, so I'd rather not have to login twice as it doesn't really make sense).  Currently I've set it up so that when I click on the encrypted HDD it unlocks without asking for a password (the password is in the keyring which has no password as it'll always ask for a password if using automatic login) but I want it to unlock the drive automatically.  Although this isn't much of an issue if it were just photos or documents I'm storing in there, I use the drive to store my Steam games as well (as the SSD is tiny), and if I open Steam but forget to unlock the drive it (obviously) wont display any of my games.  Basically it's just an extra step which should be automated considering my setup.  I'll also be storing other programs in there eventually.

I'm not sure how to do this though.  I've looked in the disk management section and it's set to automatically unlock as well as automatically mount it, but it doesn't seem to actually do that.

---

### Post by |{urse on 2013-09-09
Someone asked this a while ago [http://ubuntuforums.org/showthread.php?t=1129621](http://ubuntuforums.org/showthread.php?t=1129621) his solution makes no sense to me but maybe it will help you. Please let me know!

"[COLOR=#000000]edit: Nevermind; I figured it out myself. After I couldn't get the partition to mount I created a keyfile from /dev/urandom and then used the cryptsetup luksAddKey command to create a second password for the partition using the keyfile I generated. I then referenced the keyfile in /etc/crypttab and it works just fine now. Yay."

[/COLOR]

---

### Post by Zukaro on 2013-09-09
I can't make sense of that.  ;^;
But thanks anyways.

---

