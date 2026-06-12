---
title: "Cannot Unlock From Lock Screen"
date: 2012-02-02
forum: Security
---

### Post by aceofalltrades on 2012-02-02
I have added the following line to /etc/pam.d/common-auth 
auth required pam_tally.so onerr=fail deny=3 unlock_time=99999

Once the screen locks you cannot unlock it.  If i comment out the line in the common-auth file, the unlock works just fine.  I need the line to deny the login attempts to 3 so this is kind of an issue for me.  

If i change it to 
auth required pam_tally.so onerr=succeeds deny=3 unlock_time=99999

The unlock works fine.  I'm not sure what is causing the error with the deny=fail.  How can debug this so i can look through the logs.

This is what i'm seeing in the auth.log file.
Feb  2 09:05:54 UbuntuTest gnome-screensaver-dialog: pam_tally(gnome-screensaver:auth): Error opening /var/log/faillog for update
Feb  2 09:05:57 UbuntuTest gnome-keyring-daemon[1165]: couldn't initialize slot with master password: The password or PIN is incorrect
Feb  2 09:05:57 UbuntuTest gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Feb  2 09:05:59 UbuntuTest gnome-screensaver-dialog: pam_tally(gnome-screensaver:auth): Error opening /var/log/faillog for update

If i mess with teh /var/log/faillog file it completely locks out logins from lock screen or the switch user interface.








Shawn

---

