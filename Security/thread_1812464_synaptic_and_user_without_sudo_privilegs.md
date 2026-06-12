---
title: "synaptic and user without sudo privilegs"
date: 2011-07-26
forum: Security
---

### Post by otto67at on 2011-07-26
I am using Ubuntu Maverick
What I am trying is the following: I have a user named administrator is in the admin group and has sudo rights, and one user named handler in group handler without sudo rights.
In Softwarecenter and many other tools it works perfectly.
When I am logged into user handler, Softwarecenter ask me for the password of user administrator. Only sudo, gksu and therefore synaptic asks me for the password of user handler and as a result, does not work.
I don't want, that the regular user can make system-things with HIS password, he has to know the password of administrator do do this.
In Debian I have 2 Passwords. Thats good, but it is possible for user root to interactively log in. This is better in Ubuntu but there I have only one password and thats bad.
Is there any way to tell sudo to run as user administrator when handler calls ist? How does Softwarecenter do this?
Is there any sollution to prevent the regular user to do system administration as long as he don't know a second password?

A whole thanks ia, BigOtto :)

---

### Post by bodhi.zazen on 2011-07-26
See : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

as well as man sudoers

---

### Post by otto67at on 2011-07-26
Ok, in the meantime this sites I know inside out :) this are the first sites you get searching with google.
"Users don't have to remember an extra password (i.e. the root password), which they are likely to forget" is exactly this, i DON'T want :)
Has anyone another suggestion?
I would like to have 2 passwords without an interactive root-login, that would be my favorite solution :)

edit:  Is there a possibility to give a password to the user root without permitting interactive login?

edit2: yes, i give him the shell /dev/null, i'll try this, maybe this is my solution :)

edit3: my sollution is now:
usermod -s /dev/null -p xxx root
and
Defaults:handler timestamp_timeout=0, runaspw
%admin ALL=(ALL) ALL
handler host=(root) /usr/sbin/synaptic

What do you think about this, is this acceptable secure? Is it possible to endanger a root account with password but without usable shell?
Of course a local user with adequate knowledge can change this using a lifefilesystem, but I am shure, he has not :) but is there a danger from the internet? The computer is accessible via ssh.

BigTHX

---

