---
title: "Sudoers Query"
date: 2010-11-10
forum: Security
---

### Post by Skavenger0 on 2010-11-10
Ok Stupid question really but I'm having trouble find a solution.

I've got a script which is:

/home/Unlock.sh
```
#!/bin/sh
cd /media/"SafeStick Login"
sudo ./safestick
```

In my sudoers file I have:

```
Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%cdrom ALL=NOPASSWD: /home/Unlock.sh

```

For some reason when I run Unlock.sh I get asked for the sudo password.

If I run ```
sudo -l
```
```
User test may run the following commands on this host:
    (ALL) ALL
    (root) NOPASSWD: /home/Unlock.sh

```

Any ideas?

---

### Post by CharlesA on 2010-11-10
You get asked for it because it's running ./safestick with sudo. If you ran sudo ./Unlock.sh and removed sudo from inside the script, it shouldn't ask for the password.

---

### Post by Skavenger0 on 2010-11-10
Brilliant Cheers. I knew it was somthing stupid just couldnt see it

---

