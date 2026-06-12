---
title: "Witch antivitus scanner ?"
date: 2015-01-27
forum: Security
---

### Post by guldberg72 on 2015-01-27
Hello.
I am hosting a server with ubuntu 14.04 lts headless. The server is hosting a Wordpress blog and a Cloud storage service. 
my users is using linux, mac and windows. i was wondering what the best antivirus would be to scan my system for viruses so if oneof my clients is downloading a infected file wont spread to all of his or her's computers ?

---

### Post by lukeiamyourfather on 2015-01-27
The de facto antivirus on Linux is ClamAV. It can be run as a command when you want or it can be run as a daemon. The daemon is much faster as it can use multiple processor cores while scanning and the command uses only one processor core. I wasn't able to get it running as a daemon on Ubuntu 14.04 LTS due to some problems with AppArmor (apparently a long standing bug) but the command ran just fine.

---

