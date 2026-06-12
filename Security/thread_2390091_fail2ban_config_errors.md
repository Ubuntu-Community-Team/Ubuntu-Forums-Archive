---
title: "fail2ban config errors"
date: 2018-04-25
forum: Security
---

### Post by sniper8752 on 2018-04-25
I am using fail2ban.  I run ```
sudo fail2ban-client -d
``` and the first two lines are the following: ```
WARNING Wrong value for 'maxretry' in 'sshd'. Using default one: 'None'
WARNING Wrong value for 'bantime' in 'sshd'. Using default one: 'None'
```.  I did some research, and this can be caused if there are comments on the same line.  I went through my jail.conf file, and one of the settings had a comment on the same line, so I moved it to the line below.  I ran the command again, and it is returning this same error.

---

### Post by TheFu on 2018-04-25
Probably need to show the output from **fail2ban-client -d** to get any help.

---

