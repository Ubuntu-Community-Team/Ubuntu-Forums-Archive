---
title: "Can't get ossec to install"
date: 2009-02-28
forum: Security
---

### Post by joshh88 on 2009-02-28
I tried following the sticky on installation, but whenever i get to ./install.sh it says I must be in root. I have the latest version of ossec installed and I tried using their instructions which is extracting and then running ./install.sh, but when I run in terminal I select english and the terminal closes. This is really making me made that I cant get this to install.

---

### Post by bodhi.zazen on 2009-02-28
You have to run those command as root.

You can either 

```
sudo -i
```

This gives you a root shell.

The other option is to use sudo

sudo ./install.sh

---

### Post by joshh88 on 2009-02-28
still no such luck 
Error Making os_xml
make: *** [all] Error 1

 Error 0x5.
 Building error. Unable to finish the installation

---

### Post by bodhi.zazen on 2009-02-28
I have not seen that error so unless someone with more experience with ossec is able to advise you I suggest you file a but report with ossec (as it a 3rd party application).

---

