---
title: "Semi-Sudo User Configuration"
date: 2010-08-03
forum: Security
---

### Post by btrichardson on 2010-08-03
Hello All,

I need to configure an installation of Ubuntu 10.04 Desktop such that I have semi-sudo privileges. I need to be able to do everything a sudo user can do except for muck with the sudoers file or the log files.

Can someone suggest a way to do this?

--
Thanks!
Bryan

---

### Post by Bachstelze on 2010-08-03
> **btrichardson said:**
> Hello All,

I need to configure an installation of Ubuntu 10.04 Desktop such that I have semi-sudo privileges. I need to be able to do everything a sudo user can do except for muck with the sudoers file or the log files.

Can someone suggest a way to do this?

--
Thanks!
Bryan

Not possible.  The user can just do [font=monospace]sudo -i[/font] and be indistinguishable from another sudoer, or root himself.  It only makes sense to allow a very limited set of actions to be done as root, not allow everything except a limited set.

---

### Post by Agent ME on 2010-08-03
I think a good idea would be only allowing the apt-get and synaptic programs for the "semi-sudo user". The user would be able to muck up the system if they really wanted to (by installing lots of extra stuff, especially packages that install system services, or by removing necessary packages) but they shouldn't be able to cover up their tracks or access other users' files.

---

### Post by bodhi.zazen on 2010-08-03
You need to generate a list of commands you wish to allow and then configure sudo

See: [http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)

for details.

You may also wish to look at apparmor. You could configure a profile for a shell an allow everything then restrict access to a few files.

---

