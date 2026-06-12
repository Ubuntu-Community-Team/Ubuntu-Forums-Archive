---
title: "[SOLVED] Automaticly reboot remote machine"
date: 2008-08-28
forum: Server Platforms
---

### Post by zyberwoof on 2008-08-28
Using ssh, I am able to run a command automatically on a remote system with something like ```
ssh server1 'ifconfig'
```.  I run this as a user who is an admin on both machines.  I know if I manually ssh into the remote machine I can run ```
sudo shutdown -hP now
``` and then type my password when it prompts me to.  

Is there a way I can remotely shutdown that machine without needing to enter the "sudo" password?  If I need to store the password in my script or a text file I don't mind doing that, just as long as it can be automated.

I mainly just want to be able to go through a list of servers and run an administrative command on them one by one with a script.

---

### Post by cdenley on 2008-08-28
You can edit your sudoers file to allow certain commands to be run without a password.
```

export EDITOR=/usr/bin/nano
sudo -E visudo

```
Just add this line
```

%admin ALL = (ALL) NOPASSWD:/sbin/shutdown -hP now

```

---

### Post by zyberwoof on 2008-08-29
> **cdenley said:**
> You can edit your sudoers file to allow certain commands to be run without a password.
```

export EDITOR=/usr/bin/nano
sudo -E visudo

```
Just add this line
```

%admin ALL = (ALL) NOPASSWD:/sbin/shutdown -hP now

```

Thanks a lot.  That is exactly what I needed.  I never even knew of the visudo command.  This will help a lot.

---

