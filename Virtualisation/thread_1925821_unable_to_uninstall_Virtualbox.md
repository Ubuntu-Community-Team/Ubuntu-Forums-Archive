---
title: "unable to uninstall Virtualbox"
date: 2012-02-15
forum: Virtualisation
---

### Post by fidelandche on 2012-02-15
Hi all,

I installed VirtualBox from Oracles site, had a play with AmigaOS 4.1, however did not find AmgiaOS much good, so I want to remove Virtualbox as I will not use it again, when I have tried the following code from virtualbox;

```
sudo ./VirtualBox.run uninstall
```

```
./VirtualBox.run uninstall

```

```
/opt/VirtualBox/uninstall.sh
```

I am unable to uninstall virtualbox, here is the output from the terminal on those codes,

andyandmillie@andyandmillie-Satellite-L300:~$ sudo ./VirtualBox.run uninstall
[sudo] password for andyandmillie: 
sudo: ./VirtualBox.run: command not found
andyandmillie@andyandmillie-Satellite-L300:~$ ./VirtualBox.run uninstall
bash: ./VirtualBox.run: No such file or directory
andyandmillie@andyandmillie-Satellite-L300:~$ /opt/VirtualBox/uninstall.sh
bash: /opt/VirtualBox/uninstall.sh: No such file or directory
andyandmillie@andyandmillie-Satellite-L300:~$ 


Any ideas?

---

### Post by CharlesA on 2012-02-15
That is only to uninstall the guest additions.

You'd just need to purge virtualbox to remove it.

```
sudo apt-get purge virtualbox-4.1
```

---

### Post by rburkartjo on 2012-06-03
note as easy as it looks note error message


Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-4.1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 126 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 267289 files and directories currently installed.)
Removing virtualbox-4.1 ...
dpkg: error processing virtualbox-4.1 (--purge):
 subprocess installed pre-removal script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 virtualbox-4.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by CharlesA on 2012-06-03
> **rburkartjo said:**
> note as easy as it looks note error message


Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-4.1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 126 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 267289 files and directories currently installed.)
Removing virtualbox-4.1 ...
dpkg: error processing virtualbox-4.1 (--purge):
 subprocess installed pre-removal script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 virtualbox-4.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
ray@ray-GC660AA-ABA-SR5123WM:~$
Glad you found a fix to your problem. :)

[http://ubuntuforums.org/showthread.php?t=1994697](http://ubuntuforums.org/showthread.php?t=1994697)

Wonder why the kernel modules didn't unload automagically..

---

