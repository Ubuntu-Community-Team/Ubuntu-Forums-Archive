---
title: "apt-get broken after installation of sox14.3"
date: 2011-03-14
forum: Server Platforms
---

### Post by marue on 2011-03-14
After installing sox-14.3, an audio commandline tool, i constantly get the following message when i try to use apt-get: 
```
apt-get: symbol lookup error: /usr/lib/libstdc++.so.6: undefined symbol: _ZNSt7num_getIcSt19istreambuf_iteratorIcSt11char_traitsIcEEE2idE, version GLIBCXX_3.4
```Is there a way to remove and reinstall apt-get or /usr/lib/libstdc++.so.6 on Ubuntu 8.04?

edit:
I have now figured out that apt-get breaks as soon as i install libstdc++6, when i remove libstdc++6 everything runs fine. After  "sudo apt-get install libstdc++6" libstdc++6 gets installed, afterwards each call of apt-get results in the error above.

---

