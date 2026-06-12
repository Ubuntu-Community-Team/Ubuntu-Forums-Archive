---
title: "LKL Linux KeyLogger vs. logkeys"
date: 2010-12-18
forum: Security
---

### Post by correnticalde on 2010-12-18
*Business case is*: install a key logging utility on Ubuntu 10.04 (Lucid Lynx).

*Solution*: Trying to address the business case I stumbled upon two different key logging utilities: LKL Linux KeyLogger and logkeys. Based upon my humble experience first one does not matches expectations, while the second one does it in full.

*Scope of the article*: share the experience with others which might have a similar business case.

*Assumption*: the lab system has an italian keyboard layout.


**FIRST TRY**: LKL Linux KeyLogger

[http://blog.theunical.com/ubuntu/linux-keylogger-in-ubuntu/](http://blog.theunical.com/ubuntu/linux-keylogger-in-ubuntu/)

- How to install?
 [http://sourceforge.net/projects/lkl/](http://sourceforge.net/projects/lkl/)
 ./confiure
 make
 sudo make install

- How to use?
 sudo lkl -l -k /home/XYZ/Downloads/lkl/keymaps/it_km -o /home/XYZ/loggy.log
 (apparently seems ok)

- now it has to start automatically at any reboot
 cd /etc/init.d
 sudo vi rc.local
 add at the bottom "/usr/local/bin/lkl -l -k /home/XYZ/Downloads/lkl/keymaps/it_km -o /home/XYZ/loggy.log &"
 (it starts but in the loggy.log file there is only garbage, I tried to remove the two keyboard mapping it_UP e it_ALT, but no way it does not log anything meaningful)


**SECOND TRY**: logkeys

[http://code.google.com/p/logkeys/](http://code.google.com/p/logkeys/)

- How to install?
  gunzip logkeys-0.1.1a.tar.gz 
  tar xvf logkeys-0.1.1a.tar 
  cd logkeys-0.1.1a/
  cd build/
  ../configure
 ('sudo apt-get install build-essential' if previous command fails)
  make
  sudo make install

- it is important to have the correct map file so download the it.map file from their website

- How to use?
 sudo logkeys -s -m /home/XYZ/Downloads/de.map -o /home/XYZ/loggy.log
 sudo logkeys -k

- now it has to start automatically at boot time
  cd /etc/init.d
  sudo vi rc.local
  add at the bottom "/usr/local/bin/logkeys -s -m /home/XYZ/Downloads/de.map -o /home/XYZ/loggy.log &"
 (it starts and the loggy.log file is human readable, mission accomplished)


**CONCLUSION**
IMHO logkeys rules! ;o)

Cheers,

Fabrizio

---

### Post by und3rtug4 on 2013-01-25
logkeys is a nice tool indeed!

---

### Post by howefield on 2013-01-25
Old thread closed.

---

