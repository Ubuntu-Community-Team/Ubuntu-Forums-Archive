---
title: "Zero Day Flaw"
date: 2016-01-22
forum: Security
---

### Post by naresh6 on 2016-01-22
Hello All,

how we can fix the Zero Day Flaw.

server version "

3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
"Ubuntu 14.04.2 LTS"



inputs please.

Thanks.

---

### Post by maglin2 on 2016-01-22
Is this what you mean?

[http://www.ubuntu.com/usn/usn-2870-1/](http://www.ubuntu.com/usn/usn-2870-1/)

---

### Post by naresh6 on 2016-01-22
yes,

[http://www.zdnet.com/article/new-zero-day-flaw-hits-millions-of-linux-servers-also-affects-most-android-devices/](http://www.zdnet.com/article/new-zero-day-flaw-hits-millions-of-linux-servers-also-affects-most-android-devices/)
 
CVE-2016-0728

---

### Post by maglin2 on 2016-01-22
I don't understand your problem. I don't run 14.04. or ubuntu server, but isn't the solution just, as usual, this
[https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades)
as advised in the link I posted above?

---

### Post by ajgreeny on 2016-01-22
> **maglin2 said:**
> I don't understand your problem. I don't run 14.04. or ubuntu server, but isn't the solution just, as usual, this
[https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades)
as advised in the link I posted above?

^^^+1
How come you are still using kernel 3.13.0-48 when the rest of us are now using 3.13.0-76.

I can not remember when the 48 version was released but it was some while ago so you should certainly upgrade your kernel with commands ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by deadflowr on 2016-01-22
Indeed, running the 3.13.0-48 kernel probably has quite a few more issues and security holes than just the latest one.

---

### Post by naresh6 on 2016-01-23
Thanks everyone for inputs..

---

### Post by Graham1 on 2016-01-23
Hi All

I am running Ubuntu 14.04.3 with the 3.19.0-47 kernel. So, if I downgrade to the 3.13.0-76 kernel, this will fix the issue. Won't this then open up a ton of previous vulnerabilities? Does this vulnerability mainly affect public computers (inc. servers) and not personal computers? I am the only person that uses my computer, so should I be safe? (no need to downgrade).

:)

---

### Post by ajgreeny on 2016-01-23
If you're already using the 3.19.0-47 kernel, and as that is the latest of the 3.19.0- series I don't think you need to worry.

The problem naresh6 has is that he is using kernel 3.13.0-48 has been upgraded several times and he should now be running 3.13.0-76.

---

### Post by deadflowr on 2016-01-23
^^Yep, 3.19 kernel series is patched just like the 3.13 kernel
(and the 3.16 kernel and the 4.2 kernel)
Here's the USN for the 3.19 used in 14.04:
[http://www.ubuntu.com/usn/usn-2871-2/](http://www.ubuntu.com/usn/usn-2871-2/)

Do Not downgrade the kernel.
Unneeded and potentially disastrous.

---

### Post by Graham1 on 2016-01-23
> **deadflowr said:**
> ^^Yep, 3.19 kernel series is patched just like the 3.13 kernel
(and the 3.16 kernel and the 4.2 kernel)
Here's the USN for the 3.19 used in 14.04:
[http://www.ubuntu.com/usn/usn-2871-2/](http://www.ubuntu.com/usn/usn-2871-2/)

Do Not downgrade the kernel.
Unneeded and potentially disastrous.

Hi deadflowr

Thanks for your reply. Are you sure "USN-2871-2" is linked to the "USN-2870-1" vulnerability? I'm not likely to downgrade the kernel manually (wouldn't know what to do) but just wanted to be sure (peace of mind).

@ajgreeny: Thanks for your reply also.

:)

---

### Post by maglin2 on 2016-01-23
Scroll to the bottom of the page and you should see the same CVE Ref in both cases.

---

### Post by deadflowr on 2016-01-23
> **Graham1 said:**
> Hi deadflowr

Thanks for your reply. Are you sure "USN-2871-2" is linked to the "USN-2870-1" vulnerability? I'm not likely to downgrade the kernel manually (wouldn't know what to do) but just wanted to be sure (peace of mind).

@ajgreeny: Thanks for your reply also.

:)
Yes it the same bug.
One affects 14.04 with the 3.13 kernel, and the other affects 14.04 with the 3.19 (aka: the lts-vivid) kernel.

They release a different security notice for every different kernel affected.
So there are actually a few others notices, but those aren't related to yours.

---

### Post by Graham1 on 2016-01-24
Thanks for confirming maglin2 and deadflowr. Much appreciated.

:)

---

### Post by naresh6 on 2016-01-25
i used below [COLOR=#000000]commands and try to upgrade, but kernel version not changed,  [/COLOR]
 
sudo apt-get update
sudo apt-get dist-upgrade

here the output

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@aws-unixeng-test2:~# apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
root@aws-unixeng-test2:~# cat /etc/os-release
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
root@aws-unixeng-test2:~# uname -a
Linux aws-unixeng-test2 3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
root@aws-unixeng-test2:~#
```

---

### Post by deadflowr on 2016-01-25
Your running kernel won't get updated until you reboot.

Look in the boot directory to see what the latest kernel is
```
ls /boot
```
run
```
sudo update-grub
```
this will ensure the bootloader sees and uses the newest kernel listed.
and reboot, if you are able to.

---

