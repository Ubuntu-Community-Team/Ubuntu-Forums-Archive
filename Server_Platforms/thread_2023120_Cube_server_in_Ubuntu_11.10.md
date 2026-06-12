---
title: "Cube server in Ubuntu 11.10"
date: 2012-07-12
forum: Server Platforms
---

### Post by Nerdishman on 2012-07-12
I wanted to get a basic (original cube, NOT Cube 2) cube server on Ubuntu Server 11.10. I downloaded the unix bianaries but when I run it, it says "Error while loading shared libraries: libstdc++.so.5: cannot open shared oblect file: no such file or directory". Is there a way i can run the server?

EDIT:I submitted this to Server but this would be better in Gaming and Leisure

---

### Post by Ji Ruo on 2012-07-12
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libstdc++5

```

in a terminal ;)

---

