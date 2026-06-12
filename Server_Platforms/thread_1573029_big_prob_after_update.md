---
title: "big prob after update"
date: 2010-09-12
forum: Server Platforms
---

### Post by dustdevels on 2010-09-12
i am running ubuntu server with kubuntu desktop 10.04 i attempted to up date and it errored out so i went back and tryed to update again but this time it said it was already installed so i closed everything out restarted and when it boots back up its tellin me sound has been removed and my keyboard and mouse will not work after booting into kubuntu i have keyboard function intill boot i dont wanna reinstall and loose all the work ive done can anybody give me an idea of what to do

---

### Post by kimberlite on 2010-09-12
Start your machine in recovery mode and choose netroot terminal. In terminal window:

```
apt-get update && apt-get upgrade
```

To fix broken dependencies, you can try the following:
```
apt-get install -f
```

If it is not enough to start your GUI than you can reinstall kde-desktop:

```
apt-get install kde kubuntu-desktop
```

---

### Post by dustdevels on 2010-09-12
apearently the update messed up mysql something fierce tells me i need to do the dpkg which seems to be freezing also it says mysql is inconsistant wont let me remove it and then try it fresh tells me to reinstall it so the dpkg is attemting yet again to install im beginning to think im gonna have to reinstall :cry: i hope not

---

