---
title: "Script to check the integrity of /boot?"
date: 2012-06-26
forum: Security
---

### Post by Stonecold1995 on 2012-06-26
I have three partitions on my disk, two of them are encrypted (/ and /home) and the third isn't (/boot).  To prevent attacks that involve modifying files in /boot, I'd like a script that resides on / that can check the integrity of /boot at each boot and either warn me and allow me to choose whether to continue boot, or halt boot and immediately unmount / (preferably the former).  I could easily make a script that simply checks the MD5sums when I log in, but the problem with that is that starting at login would defeat the purpose of stopping the computer from booting up with a compromised /boot partition.

I saw a script that could do this kind of thing on a Wiki about Arch Linux, but it was a bit too complicated to understand.  Where can I find a script that can do this?

Also, how would I get passed permission issues (files like vmlinuz-3.2.0-25-generic are read-protected), or would the script be run as root automatically?

---

### Post by Cheesemill on 2012-06-26
Just use the script that's mentioned on the Arch Wiki here:
[https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS#Securing_the_unencrypted_boot_partition](https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS#Securing_the_unencrypted_boot_partition)

The script can be downloaded here:
[ftp://ftp.heise.de/pub/ct/listings/1203-146.zip](ftp://ftp.heise.de/pub/ct/listings/1203-146.zip)

I've used it myself and it's easy enough to install. First  copy chkboot.sh and chkboot_user to /usr/local/bin, you can do this by opening nautilus as root by doing:
```
gksudo nautilus
```and then dragging the files into /usr/local/bin from the file roller window.
Then make them executable by doing:
```
sudo chmod a+x /usr/local/bin/chkboot*
```Add chkboot.sh to rc.local:
```
echo "/usr/local/bin/chkboot.sh &" | sudo tee /etc/rc.local
```and then run 'gnome-session-properties' and add an entry for /usr/local/bin/chkboot_user.sh

---

### Post by Stonecold1995 on 2012-06-26
> **Cheesemill said:**
> Just use the script that's mentioned on the Arch Wiki here:
[https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS#Securing_the_unencrypted_boot_partition](https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS#Securing_the_unencrypted_boot_partition)

The script can be downloaded here:
[ftp://ftp.heise.de/pub/ct/listings/1203-146.zip](ftp://ftp.heise.de/pub/ct/listings/1203-146.zip)

I've used it myself and it's easy enough to install. First  copy chkboot.sh and chkboot_user to /usr/local/bin, you can do this by opening nautilus as root by doing:
```
gksudo nautilus
```and then dragging the files into /usr/local/bin from the file roller window.
Then make them executable by doing:
```
sudo chmod a+x /usr/local/bin/chkboot*
```Add chkboot.sh to rc.local:
```
echo "/usr/local/bin/chkboot.sh &" | sudo tee /etc/rc.local
```and then run 'gnome-session-properties' and add an entry for /usr/local/bin/chkboot_user.sh

Should I set chkboot_user.sh to "run on startup" or "run on pre-KDE startup"?

Also, how do I check to see if it's working (aside from making potentially dangerous changes to files in /boot)?

---

### Post by Hungry Man on 2012-06-26
Are you going to use a script to check the integrity of the script that checks the integrity of the /boot too?

---

### Post by Cheesemill on 2012-06-27
> **Hungry Man said:**
> Are you going to use a script to check the integrity of the script that checks the integrity of the /boot too?
And why would you need to do that?

---

### Post by Cheesemill on 2012-06-27
> **Stonecold1995 said:**
> Should I set chkboot_user.sh to "run on startup" or "run on pre-KDE startup"?

Also, how do I check to see if it's working (aside from making potentially dangerous changes to files in /boot)?
Set it to run on startup, it needs to run after KDE has started.

You can try just altering the timestamp on a file rather than making any changes to the data it contains, for example:
```
sudo update-grub
```
should be enough to trigger the script.

---

### Post by Stonecold1995 on 2012-06-27
> **Hungry Man said:**
> Are you going to use a script to check the integrity of the script that checks the integrity of the /boot too?
Yes, and one that checks the integrity of *it*, and another to detect ITS integrity, etc.  I'll do this over and over (scripts checking scripts checking scripts) until my entire 700+ GB hard disk is full. :p

Actually, I'd have no need to do that because the only thing that can be modified by an attacker is /boot, which doesn't hold the integrity-verifying script.  If an attacker is already able to modify the script, that means he already has access to /, which means I'm pretty much screwed (well, actually I have a separate encryption key for /home, but / still has some sensitive data).

---

### Post by Stonecold1995 on 2012-06-27
> **Cheesemill said:**
> Set it to run on startup, it needs to run after KDE has started.

You can try just altering the timestamp on a file rather than making any changes to the data it contains, for example:
```
sudo update-grub
```
should be enough to trigger the script.
I tried that.  Nothing happened.

---

### Post by Cheesemill on 2012-06-27
Just a thought, you're using KDE aren't you.

The chkboot_user.sh script uses zenity to display information to the user.
Zenity is an application that diplays pop-ups using GTK, it probably won't be installed with Kubuntu.

Try running the script from a terminal and see if it gives you any error mesages:
```
/usr/local/bin/chkboot_user.sh
```

---

### Post by Cheesemill on 2012-06-27
I've just installed the script on my machine and it works perfectly, issuing a 'sudo update-grub' and then rebooting triggers a warning pop-up.

I'm pretty sure you're just missing zenity.

---

### Post by Stonecold1995 on 2012-06-27
> **Cheesemill said:**
> Just a thought, you're using KDE aren't you.

The chkboot_user.sh script uses zenity to display information to the user.
Zenity is an application that diplays pop-ups using GTK, it probably won't be installed with Kubuntu.

Try running the script from a terminal and see if it gives you any error mesages:
```
/usr/local/bin/chkboot_user.sh
```
I am using KDE, although I do have Zenity installed.  Also, I do you mean chkboot_user.sh is suppose to be in /usr/local/bin?  I thought it was suppose to be in /usr/local/bin/chkboot (I thought the instructions meant to copy the whole chkboot directory to /usr/local/bin instead of the individual files).  I'm moving them out of that directory right now to see if that works.

EDIT: Okay so I moved the scripts out of the directory.  I ran "/usr/local/bin/chkboot_user.sh", but there were no error messages.  It just silently ran as if I just typed "test".

---

### Post by Cheesemill on 2012-06-27
> **Stonecold1995 said:**
> I am using KDE, although I do have Zenity installed.  Also, I do you mean chkboot_user.sh is suppose to be in /usr/local/bin?  I thought it was suppose to be in /usr/local/bin/chkboot (I thought the instructions meant to copy the whole chkboot directory to /usr/local/bin instead of the individual files).  I'm moving them out of that directory right now to see if that works.

EDIT: Okay so I moved the scripts out of the directory.  I ran "/usr/local/bin/chkboot_user.sh", but there were no error messages.  It just silently ran as if I just typed "test".

Both chkboot.sh and chkboot_user.sh are both supposed to live in /usr/local/bin

You could put them anywhere you want as long as they are executable and you call them both by their full path (obviously don't put them in /boot).

chkboot.sh needs to be called by the root user every time you boot, which is why you call it from /etc/rc.local (You need to add the entry in rc.local before 'exit 0').

My /etc/rc.local looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/local/bin/chkboot.sh &

exit 0
```
This is the script that does all of the work, calculating checksums, comparing file sizes and inode numbers etc...
If it notices any discrepancies then it creates the file /var/chkboot/bootfiles-diff

When you run /usr/local/bin/chkboot_user.sh (add it to your user startup applications), it looks for the /var/chkboot/bootfiles-diff file. If it exists then it fires up a zenity dialog box prompting you to accept the changes.

---

### Post by Stonecold1995 on 2012-06-27
I found the problem.  In chkboot.sh, there was the this:
```
# the boot device - check "mount" for /boot
bdev=/dev/sda1
bdisk=/dev/sda
bdir=/boot
chkdir="/var/chkboot"
```
But for me, the device with / is sdb (not sda), and the partition is sdb5 (not sda1).  The partition sdb1 is /boot.  I changed it to:
```
# the boot device - check "mount" for /boot
bdev=/dev/sdb5
bdisk=/dev/sdb
bdir=/boot
chkdir="/var/chkboot"
```
And now it's working!  Thank you!

---

### Post by Cheesemill on 2012-06-27
I thought I'd mentioned about the hard-coded variables earlier.

I definitely composed the message, I just must not have clicked on 'post' before I closed my browser.

Oops :)

---

