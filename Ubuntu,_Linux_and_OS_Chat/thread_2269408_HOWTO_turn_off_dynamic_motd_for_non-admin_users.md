---
title: "HOWTO: turn off dynamic motd for non-admin users"
date: 2015-03-15
forum: Ubuntu, Linux and OS Chat
---

### Post by divestoclimb on 2015-03-15
I found this old, unsolved thread on the forum with the same question I had, so since I found the answer I figured I'd post it here.
[Set motd to display update message only for admin]("http://ubuntuforums.org/showthread.php?t=1487243")

The problem is that the dynamic motd contains information that's mostly only of interest to admins who can update packages or reboot the system, and on a server like I'm running, people like my Mom don't need to be confused by this stuff (she logs in occasionally with a script that opens a reverse SSH tunnel). I wanted to turn this off for her.

The solution is to add a line to /etc/pam.d/sshd above the "session ... pam_motd.so" lines. The modified portion of the file is:
```

# Print the message of the day upon successful login.
# This includes a dynamically generated part from /run/motd.dynamic
# and a static (admin-editable) part from /etc/motd.
session    [default=1 success=ignore] pam_succeed_if.so quiet user ingroup sudo
session    optional     pam_motd.so  motd=/run/motd.dynamic noupdate
session    optional     pam_motd.so # [1]

```

If the pam_succeed_if.so check fails (the user is not in group sudo), the "1" action causes PAM to skip the next module. See [http://www.linux-pam.org/Linux-PAM-html/sag-configuration-file.html](http://www.linux-pam.org/Linux-PAM-html/sag-configuration-file.html) and [http://www.linux-pam.org/Linux-PAM-html/sag-pam_succeed_if.html](http://www.linux-pam.org/Linux-PAM-html/sag-pam_succeed_if.html)

This could also be added to /etc/pam.d/login if desired.

---

### Post by tgalati4 on 2015-03-15
Perhaps change it to a static message:

"No MOTD for you!"
                          --MOTU

---

