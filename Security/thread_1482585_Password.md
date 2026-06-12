---
title: "Password"
date: 2010-05-13
forum: Security
---

### Post by popppppz on 2010-05-13
Hopefully someone can help me.  I installed fprint (fingerprint reader), I later removed it. Now my password is not accepted for anything, such as logging, or installing new programs.  So I rebooted in recovery and changed the password, it accepted it and I rebooted back to the desktop, but it still says incorrect password when I try to install software or access system settings.  I added 2 lines to the pam.d file when I installed fprint, 

auth sufficient pam_fprint.so
auth required pam_unix.so nullok_secure

I believe these lines might be forcing a fingerprint instead of a password, but I cant edit the file to delete these lines, and I cant reinstall the fprint software without a password.

---

### Post by wojox on 2010-05-13
Boot back into recovery mode and use nano.

---

### Post by arkham on 2010-05-13
If you can boot into single user or recovery mode to remove the required line in the pam.d file, that would be the quickest route to getting things back to normal.  Just edit the file from your favorite editor on the command line (you may have to mount the filesystem) and then reboot.

---

### Post by popppppz on 2010-05-14
thanks for the help guys, whats nano mode and also whats the command to edit the file in recovery mode?

---

### Post by popppppz on 2010-05-14
ok i just figured out how to use nano in terminal. it says it saved it but when i open pam.d the lines are still there even though i removed them and saved them using nano

---

### Post by popppppz on 2010-05-14
thanks guys Nano fixed it i didnt know i had to save it like this /etc/pam.d/common-auth      i was just saving it common-auth anyways thank you, this issue is resolved

---

