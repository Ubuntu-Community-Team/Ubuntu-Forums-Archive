---
title: "Vmware-Workstation 6.5"
date: 2010-01-20
forum: Virtualisation
---

### Post by Drenriza on 2010-01-20
I have been trying to install vmware from a bundle onto my linux/ubuntu 9.10 machine without luck.

Under the installation when it reaches configuration it just stops their. If i abort the installation and try again, it just get stuck at configuration again.

Anyone know this problem?
Kind Regards

---

### Post by fjgaude on 2010-01-20
From what I've learned 9.10 has issues with how it handled networks. WS 7.0, Player 3.0 have been updated to handle 9.10... Server has not!

---

### Post by Drenriza on 2010-01-20
but im using a workstation, arnt that driffent from a vm-ware server?

---

### Post by fjgaude on 2010-01-20
Yes, WS 6.5 and not 7.0... I believe, and somebody correct me if I'm wrong, you need to upgrade to get WS to work with 9.10.

---

### Post by darco on 2010-01-20
Post the output of the install log or from the terminal...

---

### Post by Drenriza on 2010-01-21
its when i try to install the vm-ware player 2.5.3 then it just freezes under the configuration process. cant you somehow exclude that from the installation process in the bundle?

---

### Post by Drenriza on 2010-01-21
Installing VMware Player 2.5.3
    Configuring...Traceback (most recent call last):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 73, in emit
    if self.shouldRollover(record):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 146, in shouldRollover
    msg = "%s\n" % self.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 630, in format
    return fmt.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 421, in format
    s = self._fmt % record.__dict__
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 28: ordinal not in range(128)
Traceback (most recent call last):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 73, in emit
    if self.shouldRollover(record):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 146, in shouldRollover
    msg = "%s\n" % self.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 630, in format
    return fmt.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 421, in format
    s = self._fmt % record.__dict__
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 11: ordinal not in range(128)
Traceback (most recent call last):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 73, in emit
    if self.shouldRollover(record):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 146, in shouldRollover
    msg = "%s\n" % self.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 630, in format
    return fmt.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 421, in format
    s = self._fmt % record.__dict__
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 62: ordinal not in range(128)
Traceback (most recent call last):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 73, in emit
    if self.shouldRollover(record):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 146, in shouldRollover
    msg = "%s\n" % self.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 630, in format
    return fmt.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 421, in format
    s = self._fmt % record.__dict__
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 67: ordinal not in range(128)
Traceback (most recent call last):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 73, in emit
    if self.shouldRollover(record):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 146, in shouldRollover
    msg = "%s\n" % self.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 630, in format
    return fmt.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 421, in format
    s = self._fmt % record.__dict__
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 52: ordinal not in range(128)
Traceback (most recent call last):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 73, in emit
    if self.shouldRollover(record):
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/handlers.py", line 146, in shouldRollover
    msg = "%s\n" % self.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 630, in format
    return fmt.format(record)
  File "/tmp/vmis.R459pu/install/vmware-installer/python/lib/logging/__init__.py", line 421, in format
    s = self._fmt % record.__dict__
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 55: ordinal not in range(128)

---

### Post by fjgaude on 2010-01-21
Pray, do download the free Player 3.0, it works with 9.10.

---

### Post by Drenriza on 2010-01-21
i found a saloution at
[http://linux.aldeby.org/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html](http://linux.aldeby.org/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html)

Thanks for your time everybody :KS

---

### Post by fjgaude on 2010-01-22
Yes, that solution is simply too much work for one who doesn't truly need a Server. Player 3.0 works with 9.10 without hassle. Thanks for the link!

---

