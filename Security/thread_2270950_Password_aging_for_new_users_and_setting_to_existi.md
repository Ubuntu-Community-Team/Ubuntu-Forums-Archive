---
title: "Password aging for new users and setting to existing users"
date: 2015-03-26
forum: Security
---

### Post by smurphy_it on 2015-03-26
Good day.  I have an Ubuntu 12.04.4 LTS system I am attempting to setup password aging on.   I have set the max_pass_age = 60, and I have also set the inactivity = 30 days.  What I am attempting to do may be "breaking secuity".  As I would like anyone NOT using ssh-keys to be affected by password aging, and after 90 days are NOT able to login.  However, I would like anyone USING ssh-keys to "not be affected by the password aging".

Thus far, I'm not having much luck.  Here are the scenarios I have attempted thus far, and their outcomes.  

1) If "usePAM no" is set in /etc/ssh/sshd_config and date passed your inactivity timer, you can still login (and forced to change your password) when connecting via ssh using a password (so basically inactivity is ignored).  Password ageing restrictions NOT affecting client logging in via ssh keys.  

2) If "usePAM yes" in /etc/ssh/sshd_config and date has passed your inactivity timer the account is "expired" and the user's connection is dropped when connecting via ssh (password).. indicating their account is expired and to contact a system admin (inactivity honoured).  The password ageing also affects ssh keys, so once the inactivity date has passed, the account is locked out via passwords and ssh keys.

I did see mention to setting the "ChallengeResponseAuthenication yes/no".  However, this has a negative security implication as well.  If ChallengeResponseAuthenication yes is set in the /etc/ssh/sshd_config file, then any time an user attempts to connect to the server via ssh (and the account is locked) it displays on the screen the account is locked.

Any suggestions on working around this issue ?

---

