---
title: "Ninan install issue"
date: 2011-01-10
forum: Server Platforms
---

### Post by thebeev on 2011-01-10
Hello all,

I can't get ninan to come up in my browser, browsing to server ip:9090/ninan  with no luck.  Followed the instructions on the ninan site about making the following files executable.

[LIST]
[*] ninancore.sh
[*] ninanstop.sh
[*] createMYSQLDB.sh
[*] upgradeninan.sh
[/LIST]
then finally run the following command

```
nohup ./ninancore.sh &
```I ended up installing OpenJDK.  Should I be using Sun's version of Java instead?

Running the following...

Ubuntu Server 10.04LTS x64 - 2.6.32-24-server

```
user@NAS:/home/ninan-2.1.0$ java -version

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu1~10.04.1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)
```Would appreciate any help on this.

---

