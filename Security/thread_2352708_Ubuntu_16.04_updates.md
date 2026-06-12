---
title: "Ubuntu 16.04 updates"
date: 2017-02-14
forum: Security
---

### Post by cam17 on 2017-02-14
I have three Ubuntu 16.04 workstations and all on the same network. 1 of my Ubuntu 16.04 worstations seesm to get updates almost every day yet I have another that when I open Ubuntu update software says there are no updates since Nov-2016. It is currently Feb-2017. After several tries it finally found updates.

Is there a method I can test connectivity to the update server? I suspect possible filtering of my Ubuntu updates.

---

### Post by CharlesA on 2017-02-15
You can always run this in the terminal..

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Also keep in mind that different machines may have different packages installed and not everything is updated all the time.

---

### Post by ian-weisser on 2017-02-16
'apt update/upgrade' will always present the latest updates.
The GUI's Software Update, however, uses [Phased Updates]("https://wiki.ubuntu.com/PhasedUpdates"), which may delay updates a few days.

Days, not months.
What do you mean by 'filtered'?

---

