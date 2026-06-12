---
title: "sudoers problem help"
date: 2009-10-03
forum: Security
---

### Post by jarrah-95 on 2009-10-03
i have addded this code at the end of my sudoers file but only the update manager part of this code works
```

jarrah jarrah-laptop=(ALL)NOPASSWD:/usr/bin/apt-get
jarrah jarrah-laptop=(ALL)NOPASSWD:/usr/bin/update-manager
jarrah jarrah-laptop=(ALL)NOPASSWD:/usr/bin/gnome-app-install

```
what can i do to fix this and make it work

---

### Post by Lars Noodén on 2009-10-03
I haven't tracked down what the problem is but I've run into the same myself.  Somehow sudo on ubuntu does not figure out the host name properly.  Since this is a locally mounted drive, I presume, and not a networked share, I propose replacing it with these two changes:

```

%jarrah ALL=(ALL)NOPASSWD:/usr/bin/apt-get
%jarrah ALL=(ALL)NOPASSWD:/usr/bin/update-manager
%jarrah ALL=(ALL)NOPASSWD:/usr/bin/gnome-app-install

```

The % is a petty detail, but it is good practice to assign privileges to groups, even if that group only has one user.  It scales better and is much easier to test if you have to help more than one account.

It may be a good idea not to allow anyone to install arbitrary programs without adding the password.  

```

%jarrah ALL=(ALL)PASSWD:/usr/bin/apt-get
%jarrah ALL=(ALL)NOPASSWD:/usr/bin/update-manager
%jarrah ALL=(ALL)PASSWD:/usr/bin/gnome-app-install

```

---

### Post by jarrah-95 on 2009-10-03
i have done that first addition but not the second as i want this for ease of use not realy security and i am the only one who can use my account as when i shut the lid of my laptop it locks and when im not using it i do that
eather way its still not working for gnome-app-installer
thanks

---

### Post by Lars Noodén on 2009-10-04
Here's the configuration I have used myself to run gnome-app-install without a password.  I'm in the group admin:

```

%admin ALL=(ALL) NOPASSWD: /usr/bin/gnome-app-install

```

If you still have problems, you can see the error messages if you use the shell.  Open two terminal windows.  Use your favorite editor (e.g. pico or nano), I happen to use vi for sysadmin work.

In one window:
[indent]
# make a backup
sudo cp /etc/sudoers /etc/sudoers.orig
# try your experiments, save, but don't quit till you're done for the day
sudo vi /etc/sudoers
# restore if the above failed
sudo cp /etc/sudoers.orig /etc/sudoers
[/indent]

In the other window:
[indent]
# clear sudo timestamp for a fresh start
sudo -K
# see if the new config file works
sudo gnome-app-install
[/indent]

---

