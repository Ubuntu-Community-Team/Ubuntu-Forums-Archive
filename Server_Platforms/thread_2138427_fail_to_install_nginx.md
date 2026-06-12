---
title: "fail to install nginx"
date: 2013-04-24
forum: Server Platforms
---

### Post by dienz on 2013-04-24
Hi all,

I've just try to install nginx in my ubuntu server from the shell :aing@server:/home/aing# sudo apt-get install nginx
But the result is like this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.38.46) but 3.2.0.40.48 is to be installed
                 Depends: linux-headers-generic (= 3.2.0.38.46) but 3.2.0.40.48 is to be installed
 nginx : Depends: nginx-full but it is not going to be installed or
                  nginx-light but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Then I try to fix it with : aing@server:/home/aing#sudo apt-get -f install and the result is:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic
The following packages will be upgraded:
  linux-generic
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,722 B of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.38.46); however:
  Version of linux-image-generic on system is 3.2.0.40.48.
 linux-generic depends on linux-headers-generic (= 3.2.0.38.46); however:
  Version of linux-headers-generic on system is 3.2.0.40.48.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Please, help me what to do then, and thanks before

---

### Post by CharlesA on 2013-04-24
That [issue]("http://ubuntuforums.org/showthread.php?t=2137125") seems to be [popping up]("http://askubuntu.com/questions/283244/apt-get-upgrade-failing-due-to-dependency-issue") a lot.

So far I have not found a fix for it. I guess you could try booting into the previous kernel and purging linux-generic and then reinstalling it. You could even try that while running on the current kernel, but I don't know if it will work or not.

```
sudo apt-get purge linux-generic
```

---

### Post by dienz on 2013-04-24
> **CharlesA said:**
> That [issue]("http://ubuntuforums.org/showthread.php?t=2137125") seems to be [popping up]("http://askubuntu.com/questions/283244/apt-get-upgrade-failing-due-to-dependency-issue") a lot.

So far I have not found a fix for it. I guess you could try booting into the previous kernel and purging linux-generic and then reinstalling it. You could even try that while running on the current kernel, but I don't know if it will work or not.

```
sudo apt-get purge linux-generic
```

Thank you for your respon. Really appreciate it.
I'd found a solution [here]("http://ubuntuforums.org/showthread.php?t=2134500") ,well, it's not the same but quite similiar.

```
dpkg --remove linux-generic
``` and then following by
```
apt-get install linux-generic
```

After all, when running apt-get -f install it returns with no errors.
FYI, this problem comes up since /boot directory is full, and when it comes to install a program or update the system, voila, errors occur.

---

### Post by CharlesA on 2013-04-24
Glad you were able to get it sorted. Thanks for posting the solution too!

---

