---
title: "Keyboard layout"
date: 2007-02-03
forum: Server Platforms
---

### Post by druhboruch on 2007-02-03
How to change keboard layout from French to English?
It is a server, there is no X installed...

---

### Post by Brazen on 2007-02-04
```
sudo dpkg-reconfigure console-data
```

---

### Post by druhboruch on 2007-02-04
Thanks.

---

### Post by MasterOfMuppets on 2007-02-11
When I try this it says:
Package `console-data' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: console-data is not installed

:(

---

### Post by psi36 on 2007-02-26
Same problem: I used the automatic keyboard recognition during install, but apperently now I've got the wrong keyboard lay-out selected. Also running server, so no X.

And console-data is not installed. Or at least that's what it says when I do ```
sudo dpkg-reconfigure console-data
```

This is quite anoying. Luckily I use ssh most of the time, so then it's no problem, but it would be nice to have the correct keyboard layout when I do use the server directly.

---

