---
title: "Simple scan does not detect hp officejet pro 8710"
date: 2017-08-06
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-08-06
Installed and running Ubuntu 17.10.  Scanner not working.  'Output of apt-cache policy libsane-hpaio sane-utilslibsane-hpaio:'

```
 apt-cache policy libsane-hpaio sane-utilslibsane-hpaio:
libsane-hpaio:
  Installed: 3.17.6+repack0-2build1
  Candidate: 3.17.6+repack0-2build1
  Version table:
 *** 3.17.6+repack0-2build1 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status
N: Unable to locate package sane-utilslibsane-hpaio:
```

Pinter does print in Libreoffice.

Henry

---

### Post by howefield on 2017-08-06
Post moved to own thread and to the "*Ubuntu Development Version*" forum.

---

### Post by vocx on 2017-08-06
> **Hewjr100 said:**
> Installed and running Ubuntu 17.10.  Scanner not working.  'Output of apt-cache policy libsane-hpaio sane-utilslibsane-hpaio:'

```
 apt-cache policy libsane-hpaio sane-utilslibsane-hpaio:
libsane-hpaio:
  Installed: 3.17.6+repack0-2build1
  Candidate: 3.17.6+repack0-2build1
  Version table:
 *** 3.17.6+repack0-2build1 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status
N: Unable to locate package sane-utilslibsane-hpaio:
```

Pinter does print in Libreoffice.

Henry

How did you install your printer? The proper way to get HP printers working is to use HPLIP. See here [https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post13658387](https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post13658387)

Your HP OfficeJet Pro 8710 seems to be supported, according to the HP website [http://hplipopensource.com/hplip-web/models/officejet/hp_officejet_pro_8710.html](http://hplipopensource.com/hplip-web/models/officejet/hp_officejet_pro_8710.html)

According to that website, you need HPLIP version 3.16.5. I am running Ubuntu 16.04 so my HPLIP version is a bit older, 3.16.3. If I wanted to use your printer I'd have to install a newer HPLIP from the HP website. Since you just upgraded to 17.10, I imagine that your version of HPLIP is sufficient, check with "apt policy hplip".
```

hplip:
  **Installed: 3.16.3+repack0-1**
  Candidate: 3.16.3+repack0-1
  Version table:
 *** 3.16.3+repack0-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```
If it's not installed, install it, and then run the setup with the printer on and connected to the computer, or to your local network.
```

sudo apt install hplip
hp-setup

```

Wait. Did you say you are running 17.10? This version of Ubuntu has not launched officially. It will appear at the end of October 2017. Be careful with using development versions because the packages included there may not be working correctly. If this is really your wish, carry on with care. Otherwise, I would stick to 17.04.

---

### Post by Hewjr100 on 2017-08-06
Dual booting Windows 10 & Ubuntu 17.10  for testing purposes.  I don't need to print in ubuntu, just trying to get it working and post fix.

Henry

---

