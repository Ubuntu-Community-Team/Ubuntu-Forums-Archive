---
title: "Strange looking guest user acounts."
date: 2012-10-29
forum: Security
---

### Post by pcs305 on 2012-10-29
Hi,

I've notice some strange guest user accounts being created on my system.
Ubuntu server 12.04 with KDE and XCFE.

Is this normal or malicious? I did not see this on 10.04 install.

This is what I see in my /var/log/auth.log file (there are several guest- accounts created like this in the auth,log file):
```

2012-10-03T17:03:32.877728-05:00 sysk42 groupadd[7977]: group added to /etc/group: name=guest-Jskm4r, GID=145
2012-10-03T17:03:32.926936-05:00 sysk42 groupadd[7977]: group added to /etc/gshadow: name=guest-Jskm4r
2012-10-03T17:03:32.927346-05:00 sysk42 groupadd[7977]: new group: name=guest-Jskm4r, GID=145
2012-10-03T17:03:32.932680-05:00 sysk42 useradd[7981]: new user: name=guest-Jskm4r, UID=133, GID=145, home=/, shell=/bin/bash
2012-10-03T17:03:33.080154-05:00 sysk42 usermod[7986]: change user 'guest-Jskm4r' password
2012-10-03T17:03:33.230395-05:00 sysk42 chage[7991]: changed password expiry for guest-Jskm4r
2012-10-03T17:03:33.299158-05:00 sysk42 chfn[7994]: changed user 'guest-Jskm4r' information
2012-10-03T17:03:33.326112-05:00 sysk42 usermod[8002]: change user 'guest-Jskm4r' home from '/' to '/tmp/guest-Jskm4r'
2012-10-03T17:03:33.393153-05:00 sysk42 su[8007]: Successful su for guest-Jskm4r by root
2012-10-03T17:03:33.393171-05:00 sysk42 su[8007]: + ??? root:guest-Jskm4r
2012-10-03T17:03:33.393910-05:00 sysk42 su[8007]: pam_unix(su:session): session opened for user guest-Jskm4r by (uid=0)
2012-10-03T17:03:33.420572-05:00 sysk42 su[8007]: pam_unix(su:session): session closed for user guest-Jskm4r
2012-10-03T17:03:33.560436-05:00 sysk42 lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-Jskm4r by (uid=0)
2012-10-03T17:03:49.714155-05:00 sysk42 lightdm: pam_unix(lightdm-autologin:session): session closed for user guest-Jskm4r
2012-10-03T17:03:50.440291-05:00 sysk42 userdel[8449]: delete user 'guest-Jskm4r'
2012-10-03T17:03:50.440578-05:00 sysk42 userdel[8449]: removed group 'guest-Jskm4r' owned by 'guest-Jskm4r'
```

---

### Post by cryptotheslow on 2012-10-29
I believe that happens when someone logs into the desktop environment using the "Guest" account. The username generated is apparently randomised with that additional 6 character string appended.

Have a look in /etc/passwd and you should find the entry for it there.

For example on my 12.04 install I have this:
```

guest-IYHmKO:x:115:125:Guest,,,:/tmp/guest-IYHmKO:/bin/bash

```

Note the home dir is within /tmp so will not survive a reboot.

Your log looks slightly stange in that the guest user seems to be created, logged in then immediately removed. Is your KDE or XFCE environment set to automatically log in?

---

### Post by cryptotheslow on 2012-10-29
OK - I just tested a Guest login (into Unity) and these auth.log entries appear:

```

Oct 29 16:15:00 ubulaptop1204 lightdm: pam_unix(lightdm:session): session closed for user lightdm
Oct 29 16:15:01 ubulaptop1204 groupadd[2932]: group added to /etc/group: name=guest-epF0wf, GID=128
Oct 29 16:15:01 ubulaptop1204 groupadd[2932]: group added to /etc/gshadow: name=guest-epF0wf
Oct 29 16:15:01 ubulaptop1204 groupadd[2932]: new group: name=guest-epF0wf, GID=128
Oct 29 16:15:01 ubulaptop1204 useradd[2936]: new user: name=guest-epF0wf, UID=118, GID=128, home=/, shell=/bin/bash
Oct 29 16:15:01 ubulaptop1204 usermod[2941]: change user 'guest-epF0wf' password
Oct 29 16:15:02 ubulaptop1204 chage[2946]: changed password expiry for guest-epF0wf
Oct 29 16:15:02 ubulaptop1204 chfn[2949]: changed user 'guest-epF0wf' information
Oct 29 16:15:02 ubulaptop1204 usermod[2957]: change user 'guest-epF0wf' home from '/' to '/tmp/guest-epF0wf'
Oct 29 16:15:02 ubulaptop1204 su[2962]: Successful su for guest-epF0wf by root
Oct 29 16:15:02 ubulaptop1204 su[2962]: + ??? root:guest-epF0wf
Oct 29 16:15:02 ubulaptop1204 su[2962]: pam_unix(su:session): session opened for user guest-epF0wf by (uid=0)
Oct 29 16:15:02 ubulaptop1204 su[2962]: pam_unix(su:session): session closed for user guest-epF0wf
Oct 29 16:15:02 ubulaptop1204 lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-epF0wf by (uid=0)
Oct 29 16:15:02 ubulaptop1204 lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
.
.
Oct 29 16:17:09 ubulaptop1204 lightdm: pam_unix(lightdm-autologin:session): session closed for user guest-epF0wf
Oct 29 16:17:09 ubulaptop1204 userdel[3435]: delete user 'guest-epF0wf'
Oct 29 16:17:09 ubulaptop1204 userdel[3435]: removed group 'guest-epF0wf' owned by 'guest-epF0wf'

```

Note I stayed logged in for 2 minutes or so - which the timing of the removal of the random guest username coincides with. No entry remains in /etc/passwd for this one, so I think the one that does still exist in my /etc/passwd must have been a session that crashed or exited uncleanly.

All in all, this appears to be the way that the LightDM session manager handles Guest sessions. Ubuntu 10.04 used GDM session manager - probably why you are seeing a difference in the log entries.

---

### Post by samiux on 2012-10-29
> **pcs305 said:**
> Hi,

I've notice some strange guest user accounts being created on my system.
Ubuntu server 12.04 with KDE and XCFE.

Is this normal or malicious? I did not see this on 10.04 install.

This is what I see in my /var/log/auth.log file (there are several guest- accounts created like this in the auth,log file):
```

2012-10-03T17:03:32.877728-05:00 sysk42 groupadd[7977]: group added to /etc/group: name=guest-Jskm4r, GID=145
2012-10-03T17:03:32.926936-05:00 sysk42 groupadd[7977]: group added to /etc/gshadow: name=guest-Jskm4r
2012-10-03T17:03:32.927346-05:00 sysk42 groupadd[7977]: new group: name=guest-Jskm4r, GID=145
2012-10-03T17:03:32.932680-05:00 sysk42 useradd[7981]: new user: name=guest-Jskm4r, UID=133, GID=145, home=/, shell=/bin/bash
2012-10-03T17:03:33.080154-05:00 sysk42 usermod[7986]: change user 'guest-Jskm4r' password
2012-10-03T17:03:33.230395-05:00 sysk42 chage[7991]: changed password expiry for guest-Jskm4r
2012-10-03T17:03:33.299158-05:00 sysk42 chfn[7994]: changed user 'guest-Jskm4r' information
2012-10-03T17:03:33.326112-05:00 sysk42 usermod[8002]: change user 'guest-Jskm4r' home from '/' to '/tmp/guest-Jskm4r'
2012-10-03T17:03:33.393153-05:00 sysk42 su[8007]: Successful su for guest-Jskm4r by root
2012-10-03T17:03:33.393171-05:00 sysk42 su[8007]: + ??? root:guest-Jskm4r
2012-10-03T17:03:33.393910-05:00 sysk42 su[8007]: pam_unix(su:session): session opened for user guest-Jskm4r by (uid=0)
2012-10-03T17:03:33.420572-05:00 sysk42 su[8007]: pam_unix(su:session): session closed for user guest-Jskm4r
2012-10-03T17:03:33.560436-05:00 sysk42 lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-Jskm4r by (uid=0)
2012-10-03T17:03:49.714155-05:00 sysk42 lightdm: pam_unix(lightdm-autologin:session): session closed for user guest-Jskm4r
2012-10-03T17:03:50.440291-05:00 sysk42 userdel[8449]: delete user 'guest-Jskm4r'
2012-10-03T17:03:50.440578-05:00 sysk42 userdel[8449]: removed group 'guest-Jskm4r' owned by 'guest-Jskm4r'
```

I would suggest you to check what serivce is running as GID=145 and according to the log, your box looks like it is compromised.

Samiux

---

### Post by pcs305 on 2012-10-29
I think I have found my "hacker"!

After upgrading from 10.04 to 12.04 the guest account was activated.

My 11 yo son figured this out and was using my machine to play games when his computer confiscated. 

Thanks for the help!

---

### Post by cryptotheslow on 2012-10-29
Brilliant - never underestimate the kids' abilities :D

---

