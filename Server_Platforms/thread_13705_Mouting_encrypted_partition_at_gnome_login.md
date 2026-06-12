---
title: "Mouting encrypted partition at gnome login?"
date: 2005-02-02
forum: Server Platforms
---

### Post by ember on 2005-02-02
Hi,

I've googled around a bit and read some howtos, yet I did not suceed in mounting an encrypted partition at gnome login instead of bootup time.

To be more detailed:
- I set up an encrypted partition, namely /dev/hda7 following the dm-crypt How-To on the Ubuntu Wiki, it is linked to /home/ember/Crypt
- At the moment I am required to enter the password everytime I reboot the machine (which happens at least once a day because it's barebone I use both at home and in my office). That works quite well (only the fact that I have no chance to retype my password is a bit annoying)
- What I would like to have is the possibility to mount the Partition only when I log into Gnome (or alternatively have just a link to a script on my desktop, which does that) and be prompted for password when I mount the partition.
- If I try to do that with noauto in /etc/fstab (see below), I'll still get a password request at bootup, though the partition will not be mounted:

/dev/mapper/crypt       /home/ember/Crypt       ext3    noauto,defaults 0      1

Does anyone have a solution for that problem or a link where I can look up additional information on dm-crypt setup?

Best,
Ember

---

### Post by michux on 2006-05-30
You can write a simple shell script like this:

```
sudo cryptsetup luksOpen /dev/hda7 encrypted
sudo mount /dev/mapper/crypt /home/ember/Crypt
```

And save it as file ~/bin/mount_encrypted.sh

If you want to have a desktop entry you can just make a shortcut to both files. Just edit ~/Desktop/mount_encrypted and put there something like:

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=~/bin/mount_encrypted.sh
TryExec=
X-GNOME-DocPath=
Terminal=true
Name[pl_PL]=Mount encrypted
GenericName[pl_PL]=
Comment[pl_PL]=
Name=Mount encrypted
GenericName=
Comment=

```

And then an unmount script would be something like:

```
sudo umount /home/ember/Crypt
sudo cryptsetup luksClose /dev/mapper/crypt
```

---

### Post by seldon77 on 2006-06-16
The technique described is a good idea... but in practice, I don't think it works too well (you need to be root, etc).

one other method to mount the encrypted partition at boot is described in the Encrypted Partition Howto#3.

---

### Post by seldon77 on 2006-11-01
hope this helps someone...

after hours of head scratching, trying to get an encrypted partition mounted by an ordinary user at gnome login (on Edgy), I added this to my startup programs (system/preferences/sessions):

gnome-terminal -e "pmount /dev/hdb3"

with /dev/hdb3 being my encrypted partition.

---

### Post by seldon77 on 2006-11-03
note - dapper popped up a password in gnome boot if there is an encrypted hdd, but edgy doesn't any more for some reason !?

Re: the above, I forgot you also need the name of the encrypted drive (ie. /dev/hda3) listed in /etc/pmount.allow, or it wont open it.

---

