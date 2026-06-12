---
title: "Automounting a crypted device not working, manually works"
date: 2020-12-16
forum: Security
---

### Post by heikki-kniivila on 2020-12-16
Hi.
I have this script at /root/cryptoskripta.sh
[INDENT]#!/bin/bash


ask_for_password () {
    cryptkey="Unlocking the disk $cryptsource ($crypttarget)\nEnter passphrase: "
    if [ -x /bin/plymouth ] && plymouth --ping; then
        cryptkeyscript="plymouth ask-for-password --prompt"
        cryptkey=$(printf "$cryptkey")
    else
        cryptkeyscript="/lib/cryptsetup/askpass"
    fi
    $cryptkeyscript "$cryptkey"
}


device=$(echo $1 | cut -d: -f1)
filepath=$(echo $1 | cut -d: -f2)


# Ask for password if device doesn't exist
if [ ! -b $device ]; then
    ask_for_password
    exit
fi


mkdir /tmp/auto_unlocker
mount $device /tmp/auto_unlocker


# Again ask for password if device exist but file doesn't exist
if [ ! -e /tmp/auto_unlocker$filepath ]; then
    ask_for_password
else
    cat /tmp/auto_unlocker$filepath
fi


umount /tmp/auto_unlocker
[/INDENT]

foud it there:  [https://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition](https://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition)

But the problem is that the mount isn't done automatically at boot.

if i do systemctl start [email]systemd-cryptsetup@chome.servic[/email]e
it will give me an error arguing that the file /filu does not exist:
a paste: [https://pastebin.ubuntu.com/p/hrD8hhFzVq/](https://pastebin.ubuntu.com/p/hrD8hhFzVq/)

runing the command
cryptdisks_start chome
works anyhow.

So i can manually mount the device but not automatically on boot.

this is my /etc/crypttab:
chome UUID=763ccc90-something/dev/disk/by-uuid/e32fd99e-something1:/filu luks,keyscript=/root/cryptoskripta.sh
(replaced something there)

Any hint??

---

### Post by llamabr on 2020-12-16
Could you just add it to an autostart file? What WM/DE are you using? Or you could autostart it from cron with something like:

> @reboot  /path/to/shell.script

right in your crontab file

---

