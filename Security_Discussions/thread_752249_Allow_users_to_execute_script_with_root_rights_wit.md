---
title: "Allow users to execute script with root rights without allowing reading/writing"
date: 2008-04-11
forum: Security Discussions
---

### Post by Kypara on 2008-04-11
I would want to allow my users to only run script without asking root password at /usr/local/bin/c_mount which requires root privileges to execute (mounts my encrypted fs). When using visudo to allow passwordless sudo there, it also allows reading/writing the script file and letting them to run commands with root privileges without typing root password with sudo nano c_mount.

/etc/sudoers
bill   ALL = (ALL) NOPASSWD /usr/local/bin/c_mount-sda7

I would only want them to run the script without other access to it.

---

### Post by cdenley on 2008-04-11
Seems to work fine after adding a colon. Does bill belong to the admin group? If so, maybe it is working correctly, but his password was entered for sudo in the last 15 minutes.

```

test ALL = (ALL) NOPASSWD:/opt/test

```

```

test@ubuntu:~$ sudo /opt/test
test
test@ubuntu:~$ sudo echo test
[sudo] password for test: 
Sorry, user test is not allowed to execute '/bin/echo test' as root on ubuntu.
test@ubuntu:~$ sudo nano /opt/test
[sudo] password for test: 
Sorry, user test is not allowed to execute '/usr/bin/nano /opt/test' as root on ubuntu.

```

---

### Post by Kypara on 2008-04-12
Woops, it worked as desired after revoking bill's administrative rights... At least following comrades will know how to allow only executing files for desktop users. (didn't find any resources myself) :oops:

Allowing non-admin users to execute scripts etc. without allowing modification/reading:

```
sudo chmod 111 /.../yourscripthere (allow everybody to only execute the script)
sudo visudo (opens /etc/sudoers for editing)
``` 

And replace username with user name/groups/aliases:
```
username ALL = (ALL) NOPASSWD: /.../yourscripthere
```

---

