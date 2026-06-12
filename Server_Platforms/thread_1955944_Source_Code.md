---
title: "Source Code"
date: 2012-04-10
forum: Server Platforms
---

### Post by mandza on 2012-04-10
Where i can download source code of ubuntu, server and desktop platform?
Thanks a lot for your answers.

---

### Post by nothingspecial on 2012-04-10
Each component package has it's source code available.

You can download it using ```
apt-get source <package-name>
```

---

### Post by MG&amp;TL on 2012-04-10
Ubuntu is maintained in lots of source *packages* where a server builds them into binaries for convenience.

If you want to see the source code (and packaging) of a particular package, you can use:

```
apt-get source <package>
```

Some packages, such as *ubuntu-restricted-extras* are not entirely open-source, there may be some binary in the source package, or it may download some external material when installing.

EDIT: beaten to it, as per usual. :P

---

### Post by mandza on 2012-04-11
Thanks a lot :)

---

