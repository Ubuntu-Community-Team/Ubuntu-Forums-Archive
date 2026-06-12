---
title: "Unknown files in 18.04.2 LTS"
date: 2019-04-11
forum: Security
---

### Post by cam17 on 2019-04-11
In my /tmp directory have the below files. I would like to know what the **ssh-etc** file and the 
**config-err-etc. This occurred on a new install of 18.04.2 LTS with no other software.**

```
-rw------- 1 mac mac 0 Apr 10 17:34 config-err-DzuNzQ-rw------- 1 mac mac 0 Apr 11 15:39 config-err-egnXJT
-rw------- 1 mac mac 0 Apr 11 15:53 config-err-ok0JlX
drwx------ 2 mac mac 4096 Apr 11 15:53 ssh-A3sUNneh42ws
drwx------ 3 root root 4096 Apr 10 17:34 systemd-private-c8b20496070343ac9968e03a35074577-bolt.service-Mgs9Wh
drwx------ 3 root root 4096 Apr 10 17:34 systemd-private-c8b20496070343ac9968e03a35074577-colord.service-CCqmfj
drwx------ 3 root root 4096 Apr 10 17:35 systemd-private-c8b20496070343ac9968e03a35074577-fwupd.service-m9LEVi
drwx------ 3 root root 4096 Apr 10 17:34 systemd-private-c8b20496070343ac9968e03a35074577-rtkit-daemon.service-guQiGC
drwx------ 3 root root 4096 Apr 10 17:34 systemd-private-c8b20496070343ac9968e03a35074577-systemd-resolved.service-CSvmLj
drwx------ 3 root root 4096 Apr 10 17:34 systemd-private-c8b20496070343ac9968e03a35074577-systemd-timesyncd.service-ajnGud
```

---

### Post by DuckHook on 2019-04-11
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. Also, please refrain from unusual styles and fonts because these are hard to read on some computers.

---

### Post by uRock on 2019-04-14
The config error file looks to be a blank text file.  Ran Bleachbit and it is gone.  My primary machine has been installed for about 9 months and that file is not there. Here's the output of** ls** on that folder in a VM before and after running Bleachbit.  Personally, I don't worry about this file.

```
iennor@iennor-VirtualBox:/tmp$ ls -ail
total 60
917505 drwxrwxrwt 14 root   root   4096 Apr 14 13:24 .
     2 drwxr-xr-x 24 root   root   4096 Apr 14 13:22 ..
918339 -rw-------  1 iennor iennor    0 Apr 14 13:10 config-err-9gLzSJ
917543 drwxrwxrwt  2 root   root   4096 Apr 14 13:09 .font-unix
917536 drwxrwxrwt  2 root   root   4096 Apr 14 13:10 .ICE-unix
918342 drwx------  2 iennor iennor 4096 Apr 14 13:10 ssh-************
919964 drwx------  3 root   root   4096 Apr 14 13:22 systemd-private-************-bolt.service-9mLNIh
918336 drwx------  3 root   root   4096 Apr 14 13:10 systemd-private-************-colord.service-ctxh08
919966 drwx------  3 root   root   4096 Apr 14 13:22 systemd-private-************-fwupd.service-2q5i9J
918057 drwx------  3 root   root   4096 Apr 14 13:10 systemd-private-************-rtkit-daemon.service-ENujBQ
917616 drwx------  3 root   root   4096 Apr 14 13:17 systemd-private-************-systemd-resolved.service-QmgEeZ
917614 drwx------  3 root   root   4096 Apr 14 13:17 systemd-private-************-systemd-timesyncd.service-Qq3ZOh
917612 drwxrwxrwt  2 root   root   4096 Apr 14 13:09 .Test-unix
917684 -r--r--r--  1 gdm    gdm      11 Apr 14 13:10 .X1024-lock
917522 drwxrwxrwt  2 root   root   4096 Apr 14 13:10 .X11-unix
917542 drwxrwxrwt  2 root   root   4096 Apr 14 13:09 .XIM-unix
``````

iennor@iennor-VirtualBox:/tmp$ ls -ail
total 60
917505 drwxrwxrwt 14 root   root   4096 Apr 14 13:27 .
     2 drwxr-xr-x 24 root   root   4096 Apr 14 13:22 ..
917543 drwxrwxrwt  2 root   root   4096 Apr 14 13:09 .font-unix
917536 drwxrwxrwt  2 root   root   4096 Apr 14 13:10 .ICE-unix
918342 drwx------  2 iennor iennor 4096 Apr 14 13:10 ssh-************
919964 drwx------  3 root   root   4096 Apr 14 13:22 systemd-private-************-bolt.service-9mLNIh
918336 drwx------  3 root   root   4096 Apr 14 13:10 systemd-private-************-colord.service-ctxh08
919966 drwx------  3 root   root   4096 Apr 14 13:22 systemd-private-************-fwupd.service-2q5i9J
918057 drwx------  3 root   root   4096 Apr 14 13:10 systemd-private-************-rtkit-daemon.service-ENujBQ
917616 drwx------  3 root   root   4096 Apr 14 13:17 systemd-private-************-systemd-resolved.service-QmgEeZ
917614 drwx------  3 root   root   4096 Apr 14 13:17 systemd-private-************-systemd-timesyncd.service-Qq3ZOh
917612 drwxrwxrwt  2 root   root   4096 Apr 14 13:09 .Test-unix
917684 -r--r--r--  1 gdm    gdm      11 Apr 14 13:10 .X1024-lock
917522 drwxrwxrwt  2 root   root   4096 Apr 14 13:10 .X11-unix
917542 drwxrwxrwt  2 root   root   4096 Apr 14 13:09 .XIM-unix

```

---

### Post by cam17 on 2019-04-16
Can you tell me what the ssh-xxx file is used for? I have not installed open-ssh.   I am concerned about the config-err because this is a fresh install with no updates or installed applications.

---

