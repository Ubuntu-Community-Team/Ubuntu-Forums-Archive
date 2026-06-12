---
title: "Please help me to understand my rkhunter results."
date: 2017-04-20
forum: Security
---

### Post by Bobby_James on 2017-04-20
I have - like many people - rkhunter results that I am finding hard to interpret. 

I hope that some kind person with experience of this program can spent a couple of minutes assessing my output. Do I have anything to worry about?

```
07:55:31]   Checking for passwd file changes                [ Warning ]
[07:55:31] Warning: User 'postfix' has been added to the passwd file.
[07:55:31]   Checking for group file changes                 [ Warning ]
[07:55:31] Warning: Group 'postfix' has been added to the group file.
[07:55:31] Warning: Group 'postdrop' has been added to the group file.

```

This is the main section that I don't understand. Why would a user be added to the passwd file?

```
[07:58:31]   /usr/sbin/adduser                               [ Warning ]
[07:58:31] Warning: The command '/usr/sbin/adduser' has been replaced by a script: /usr/sbin/adduser: a /usr/bin/perl script, ASCII text executable
[07:58:36]   /usr/bin/ldd                                    [ Warning ]
[07:58:36] Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script, ASCII text executable
[07:58:40]   /usr/bin/lwp-request                            [ Warning ]
[07:58:40] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable
[07:58:45]   /bin/egrep                                      [ Warning ]
[07:58:45] Warning: The command '/bin/egrep' has been replaced by a script: /bin/egrep: POSIX shell script, ASCII text executable
[07:58:45]   /bin/fgrep                                      [ Warning ]
[07:58:45] Warning: The command '/bin/fgrep' has been replaced by a script: /bin/fgrep: POSIX shell script, ASCII text executable
[07:58:48]   /bin/which                                      [ Warning ]
[07:58:48] Warning: The command '/bin/which' has been replaced by a script: /bin/which: POSIX shell script, ASCII text executable
```

I have seen reports online that some of these e.g adduser, which, and ldd should be scripts but I don't know about the rest. Are they all OK?

```
08:03:31] Warning: Process '/sbin/wpa_supplicant' (PID 1152) is listening on the network.
[08:03:31] Warning: Process '/sbin/wpa_supplicant' (PID 1152) is listening on the network.
[08:03:31] Warning: Process '/sbin/dhclient' (PID 1397) is listening on the network.

```

I assume these programs should be listening. Yes?

```
[08:03:36]   Checking /dev for suspicious file types         [ Warning ]
[08:03:36] Warning: Suspicious file types found in /dev:

```

I have read that this is a false positive. Correct?

Many thanks!

---

### Post by deadflowr on 2017-04-20
Did you run
```
sudo rkhunter --propupd
```
first?

---

### Post by Bobby_James on 2017-04-20
Yes, I did run --propupd first.

---

### Post by Habitual on 2017-04-20
[To avoid these warnings,]("https://help.ubuntu.com/community/RKhunter")

---

