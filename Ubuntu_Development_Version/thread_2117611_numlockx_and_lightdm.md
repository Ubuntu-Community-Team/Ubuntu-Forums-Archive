---
title: "numlockx and lightdm"
date: 2013-02-19
forum: Ubuntu Development Version
---

### Post by stinkeye on 2013-02-19
In quantal I could enable numlock at the greeter by
```
gksudo gedit /etc/lightdm/lightdm.conf
```

and add

```
greeter-setup-script=/usr/bin/numlockx on
```
When doing this in Raring,
the initial boot to the greeter works and numlock is enabled
but when I logout all I get is a black screen with an x cursor.
numlockx is installed.
Anyone know if there is a bug for this?

---

### Post by brainwash on 2013-02-19
You might want to take a look at this bug report:

[https://bugs.launchpad.net/lightdm/+bug/1128474](https://bugs.launchpad.net/lightdm/+bug/1128474)

---

### Post by stinkeye on 2013-02-19
> **brainwash said:**
> You might want to take a look at this bug report:

[https://bugs.launchpad.net/lightdm/+bug/1128474](https://bugs.launchpad.net/lightdm/+bug/1128474)
Thanks, looks like the same bug and added to it.

---

### Post by brainwash on 2013-02-19
Can anyone else confirm this bug? Here are the different script parameters which may be affected:
```
# display-setup-script = Script to run when starting a greeter session (runs as root)
# greeter-setup-script = Script to run when starting a greeter (runs as root)
# session-setup-script = Script to run when starting a user session (runs as root)
# session-cleanup-script = Script to run when quitting a user session (runs as root)
```

---

### Post by pqwoerituytrueiwoq on 2013-03-08
[s]anyone have a fix for this? the bug report says fix commited, but the issue is still present for me[/s] - fixed in proposed 1.5.1-0ubuntu1
```
~$ apt-cache policy lightdm
lightdm:
  Installed: 1.4.0-0ubuntu5
  Candidate: 1.4.0-0ubuntu5
  Version table:
 *** 1.4.0-0ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/main amd64 Packages
        100 /var/lib/dpkg/status
```

```
~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
#greeter-setup-script = sh -c 'numlockx on;ogg123 /usr/share/sounds/ubuntu/stereo/system-ready.ogg 2> /dev/null &'
#session-cleanup-script = /usr/local/bin/session-cleanup-script
#session-setup-script = sh -c 'ogg123 /usr/share/sounds/ubuntu/stereo/desktop-login.ogg &'
```

```
~$ cat /usr/local/bin/session-cleanup-script
#!/bin/bash
ogg123 /usr/share/sounds/ubuntu/stereo/desktop-logout.ogg &
#echo "`date`" > /var/log/xfce-logout-script
pid="`pgrep -f gmusicbrowser | head -1`"
#echo "pid = $pid" >> /var/log/xfce-logout-script
if [ "0$pid" -gt "0" ]; then
    user=$(ps aux | awk '{print $1" "$2}' | grep $pid | awk '{print $1}')
#    echo "user = $user" >> /var/log/xfce-logout-script
    sudo -u $user gmusicbrowser -cmd Quit
fi
```

---

