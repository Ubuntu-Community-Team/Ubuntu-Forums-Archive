---
title: "[SOLVED] Script fails with LVM"
date: 2007-09-06
forum: Ubuntuzilla
---

### Post by omahn on 2007-09-06
I just discovered ubuntuzilla after speaking to some colleagues who highly recommended the script for installing newer versions Firefox and Thunderbird.  Unfortunately it fails to complete on my systems.

I think the issue lies with my use of LVM and the output of df -k. Here's the error:

```
Backing up old Firefox preferences

Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1032, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 219, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 246, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 503, in install
    self.backupProfile()
  File "/usr/local/bin/ubuntuzilla.py", line 639, in backupProfile
    self.checkDiskSpaceForBackup("~/.mozilla")
  File "/usr/local/bin/ubuntuzilla.py", line 359, in checkDiskSpaceForBackup
    availableForBackup = int(self.util.getSystemOutput(executionstring="df -k "+target+" | grep '/dev' |awk '{print $4}'"))

```

I'm using LVM on my systems and I can see that df -k returns a two line entry, see below:

```
pre500@jumpjet:~$ df -k
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/mapper/sdaVG-root
                     206424760  85494788 118836084  42% /
varrun                 1037472       156   1037316   1% /var/run
varlock                1037472         0   1037472   0% /var/lock
procbususb             1037472        84   1037388   1% /proc/bus/usb
udev                   1037472        84   1037388   1% /dev
devshm                 1037472         0   1037472   0% /dev/shm
/dev/sda1               124427     50737     73690  41% /boot
```

Could this be the issue? I suspect the blank line is causing some issue here:
```

pre500@jumpjet:~$ df -k | grep '/dev' |awk '{print $4}'

1037388
1037472
73690
```

Any ideas?

Thanks.

---

### Post by nanotube on 2007-09-06
hi
that was some good troubleshooting it may be indeed what's causing the problem.
is your ~/.mozilla folder located in /dev/mapper/sdaVG-root ? 
what's your output of:
```
df -k ~/.mozilla | grep '/dev' |awk '{print $4}'
```
and
```
df -k ~/.mozilla
```

don't worry, i'll try to get this working for you :)

---

### Post by omahn on 2007-09-06
> **nanotube said:**
> 
what's your output of:
```
df -k ~/.mozilla | grep '/dev' |awk '{print $4}'
```
and
```
df -k ~/.mozilla
```

```

pre500@jumpjet:~$ df -k ~/.mozilla | grep '/dev' |awk '{print $4}'

pre500@jumpjet:~$ df -k ~/.mozilla
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/mapper/sdaVG-root
                     206424760  85614588 118716284  42% /
pre500@jumpjet:~$ 
```

On my system this command gives the desired output..

```
pre500@jumpjet:~$ df -k ~/.mozilla | grep '[0-9]%' | awk '{print $3}'
118716284
pre500@jumpjet:~$ 
```

Unfortunately this would be non functional on systems that produce the df output on 1 line as the awk command would print one column too early as the device is included in column 0... 

> **nanotube said:**
> 
don't worry, i'll try to get this working for you :)

Good stuff. :-)

---

### Post by omahn on 2007-09-06
This *appears* to work for me... YMMV:

```
pre500@jumpjet:~$ df -k ~/.mozilla | grep '[0-9]%' | awk '{ NN = NF - 2; print $NN }'
118714832
pre500@jumpjet:~$
```

I believe it will work on non LVM systems too as it's reading from the last column backwards.

---

### Post by nanotube on 2007-09-06
> **omahn said:**
> This *appears* to work for me... YMMV:

```
pre500@jumpjet:~$ df -k ~/.mozilla | grep '[0-9]%' | awk '{ NN = NF - 2; print $NN }'
118714832
pre500@jumpjet:~$
```

I believe it will work on non LVM systems too as it's reading from the last column backwards.

hey
an ingenious solution! :) i will stick that into ubuntuzilla for the next release. 

in the meantime, you can just edit that line in ubuntuzilla.py, to reflect the new approach you have devised, so that you can get it to install for you. 

thanks! :)

---

### Post by omahn on 2007-09-07
> **nanotube said:**
> hey
an ingenious solution! :) i will stick that into ubuntuzilla for the next release. 
in the meantime, you can just edit that line in ubuntuzilla.py, to reflect the new approach you have devised, so that you can get it to install for you. 
thanks! :)

Cool, works perfectly now!

---

### Post by nanotube on 2007-09-08
> **omahn said:**
> Cool, works perfectly now!

thanks for fixing the bug! :) i'll be sure to credit you in the cvs changelogs. :)

---

