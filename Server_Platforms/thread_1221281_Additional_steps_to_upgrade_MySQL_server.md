---
title: "Additional steps to upgrade MySQL server?"
date: 2009-07-23
forum: Server Platforms
---

### Post by wesg on 2009-07-23
I'm running Ubuntu 9.04 CLI and need to upgrade MySQL from 5.0.45 to 5.1.x. I ran the command sudo apt-get install mysql-server and it appeared to download and install the package properly, however if I connect to the server with the terminal or Webmin, I see 5.0.45. 

What am I missing to use the updated version?

---

### Post by wesg on 2009-07-23
Solved it myself. Just made the command 

```
sudo apt-get install mysql-server-5.1
```

---

