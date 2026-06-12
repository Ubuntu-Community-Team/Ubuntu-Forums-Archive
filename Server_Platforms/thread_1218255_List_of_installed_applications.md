---
title: "List of installed applications"
date: 2009-07-20
forum: Server Platforms
---

### Post by fafifurnir on 2009-07-20
Hello to all,

I have a pc running Ubuntu server 7.10.

there is a command (from shell command line) to retrieve the list of installed applications?

For the running service I know atop, sysv-rc-conf, etc., but for applications ?

Regards

---

### Post by amauk on 2009-07-20
```
dpkg --get-selections
```will list all packages installed via apt

---

### Post by shizzy-t on 2009-07-20
dpkg -l

---

### Post by juancarlospaco on 2009-07-20
dpkg -l > MyApplications.txt

---

### Post by slakkie on 2009-07-20
> **amauk said:**
> ```
dpkg --get-selections
```will list all packages installed via apt

Use this one.

If you redirect that output to a file you can go to a different box and install the same packages on that one by doing:

```

sudo dpkg --set-selections < file.name
sudo apt-get dselect-upgrade

```

ALthough dpkg will also be helpful, but then use this command:

```

dpkg -l | grep "^ii"

```

---

