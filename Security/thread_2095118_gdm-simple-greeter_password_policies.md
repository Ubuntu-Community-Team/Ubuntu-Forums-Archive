---
title: "gdm-simple-greeter password policies"
date: 2012-12-15
forum: Security
---

### Post by jdgregson on 2012-12-15
Hello. I am not sure if these would be pam settings or gdm-simple-greeter settings, but I would like to edit the password policies on the lock screen. What I would like to do is set the system to automatically run a script if somebody incorrectly guesses the password on the lock screen three times. This script could then do other things, like send a notification of some sort, then shut the system down. Is is possible to configure gdm-simple-greeter to do that? If not, are there alternate lock screens which could do that?

---

### Post by jdgregson on 2012-12-16
I figured out a not-too-simple way to do it myself. I'll post it here in case anybody in the future wants to do the same thing. Using this method, the system will begin to shutdown 0-15 seconds after the user enters the Nth wrong guess, and the account will be locked out during that time. It has three parts.


Part one:

Place this line in the /etc/pam.d/common-auth file, BEFORE everything else. It most likely won't work if you append it to the end of the file.
```

auth required pam_tally.so onerr=fail deny=3 unlock_time=20 file=/tmp/passwordfail

```

Things that you may want to change:
deny=3 means that it will shutdown after three guesses



Part two:

Save this script in a file, make it executable, and place it in the system path. I called it check-logins and places it in /bin
```

#!/bin/bash

# jdgregson

USER=foo
FILE=/tmp/passwordfail
MAX_GUESSES=3

COUNT=$(pam_tally --file $FILE --user $USER | cut -d")" -f 2 | cut -d"s" -f 2 | cut -d" " -f 2)
if [ "$COUNT" -gt "$MAX_GUESSES" ]; then
  # max guesses exceeded
  shutdown now
fi

```


Things that you may want to change:
USER=foo sets the user which this lock is active for. This code only checks one user, rather than every user on the system.
MAX_GUESSES=3 sets the number of wrong guesses to shut down after. It should be the same number as it is in step one.
Place other commands which you may want to run before the "shutdown now" line.


Part thee:

Place this line at the end of /etc/crontab. It will run the script from step two every fifteen seconds, which just checks if the user has exceeded their maximum password guess limit, and shuts down the system if they have.
```

*  *  * * * root  /bin/check-logins; sleep 15; /bin/check-logins; sleep 15; /bin/check-logins; sleep 15; /bin/check-logins; sleep 15;

```

Things that you may want to change:
/bin/check-logins should be the path to the script that you saved from step two.

---

