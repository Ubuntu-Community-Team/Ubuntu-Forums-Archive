---
title: "Segmentation Fault when exiting from su"
date: 2018-08-20
forum: Server Platforms
---

### Post by donald-flissinger on 2018-08-20
Hi,

Strange segmentation fault when exiting from su,

I'm on:
root@ubuntu-server:/home/donald# uname -a
Linux ubuntu-server.flissinger.local 4.4.0-133-generic #159-Ubuntu SMP Fri Aug 10 07:31:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

root@ubuntu-server:/home/donald# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.5 LTS"


dmesg gives:

[389161.916804] traps: su[64329] general protection ip:7f7295ad1cc0 sp:7fffb5301370 error:0 in libc-2.23.so[7f7295a83000+1c0000]
[389358.155893] traps: su[102473] general protection ip:7f8916169cc0 sp:7ffdd9b10250 error:0 in libc-2.23.so[7f891611b000+1c0000]
[389374.965757] traps: su[102987] general protection ip:7fcb59daacc0 sp:7ffd571f9f90 error:0 in libc-2.23.so[7fcb59d5c000+1c0000]
[390430.144714] traps: su[103041] general protection ip:7fa4b84facc0 sp:7fff7021ec10 error:0 in libc-2.23.so[7fa4b84ac000+1c0000]
[390451.290534] traps: su[108098] general protection ip:7fb296340cc0 sp:7ffd000b78f0 error:0 in libc-2.23.so[7fb2962f2000+1c0000]


root@ubuntu-server:/home/donald# exit
exit
Segmentation fault (core dumped)
donald@ubuntu-server:~$

How to debug?

Best Regards,
Donald.

edit:

Just upgraded to 18.04 LTS via do-release-upgrade but the error still persists, anyone?

---

### Post by T.J. on 2018-08-25
If I had to guess based on your post, your upgrade was not entirely clean and you have some stale libraries that are causing linking issues.   It would probably be wise to backup your important data on another drive and then do a clean install, formatting over the existing one.

---

### Post by donald-flissinger on 2018-09-01
Thanks for your reply, I had this error before the upgrade too, what does Ubuntu run when exiting from su?

---

