---
title: "PWDIR not found please help"
date: 2009-01-31
forum: Server Platforms
---

### Post by sfuller on 2009-01-31
first iwhat to say that for all you help! i folower Dr.Small post and it help a lot put when i run this command
sudo dpkg-statoverride --force --update --add root sasl 755 /var/spool/postfix/var/run/saslauthd
i get directory no such file or directory if i make it it tell me
force will be ignored and no matter what it do when i start or restart saslauthd iget /ect/default/saslauthd:8:PWDIR: not found
here is my /ect/default/saslauthd
START=yes
PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd" and i followed this example [http://ubuntuforums.org/showthread.php?t=990582](http://ubuntuforums.org/showthread.php?t=990582)

---

### Post by Dr Small on 2009-01-31
Are you running Debian or Ubuntu ... and if so, what version? When I setup SASL with Postfix on Debian, I had to do some tinkering to get the thing to work properly, because some stuff was different.

---

### Post by sfuller on 2009-02-01
i am running ubuntu 8.10 am i would like to thank you for youre help so far an help would be great even if it i have to change OS or versions i just need a mail server that users can log using MS mail clients

---

