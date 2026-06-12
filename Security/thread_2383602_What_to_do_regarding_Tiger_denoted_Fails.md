---
title: "What to do regarding Tiger denoted Fails"
date: 2018-01-27
forum: Security
---

### Post by smith73 on 2018-01-27
I ran Tiger on a newly installed Ubuntu-Mate 16.04.3 and it found the following Fails:    ```
 # Checking network configuration The system is not protected against Syn flooding attacks The system is not configured to log suspicious (martian)  packets
 # Checking md5sums of installed files Installed file `/boot/vmlinuz-4.10.0-28-generic' checksum differs from installed package 'linux-image-4.10.0-28-generic'.      Installed file `/usr/lib/python3/dist-packages/cupshelpers/__pycache__/__init__.cpython-35.pyc'  checksum differs from installed package 'python3-cupshelpers'.       Installed file `/usr/lib/python3/dist-packages/cupshelpers/__pycache__/config.cpython-35.pyc'   checksum differs from installed package 'python3-cupshelpers'.       Installed file `/usr/lib/python3/dist-packages/cupshelpers/__pycache__/cupshelpers.cpython-35.pyc'  checksum differs from installed package 'python3-cupshelpers'.      Installed file `/usr/lib/python3/dist-packages/cupshelpers/__pycache__/installdriver.cpython-35.pyc'   checksum differs from installed package 'python3-cupshelpers'.      Installed file `/usr/lib/python3/dist-packages/cupshelpers/__pycache__/openprinting.cpython-35.pyc'   checksum differs from installed package 'python3-cupshelpers'.      Installed file `/usr/lib/python3/dist-packages/cupshelpers/__pycache__/ppds.cpython-35.pyc'           checksum differs from installed package 'python3-cupshelpers'.       Installed file  `/usr/lib/python3/dist-packages/cupshelpers/__pycache__/xmldriverprefs.cpython-35.pyc'  checksum differs from installed package 'python3-cupshelpers'.    
 # Checking device permissions... /dev/fuse has world permissions /dev/kmsg has world permissions /dev/rfkill has world permissions    # Checking for existence of log files... Log file /var/log/btmp permission should be 660  Log file /var/log/messages does not exist    # Checking sshd_config configuration files... Cannot find a configuration file for SSH.   # Performing common access checks for root... There is no /etc/ftpusers file.    # Checking ntpd configuration... Remote NTP Server(s) must be specified! 
```     All ports are closed at this PC. What can be done about these fails?    Thanks

---

