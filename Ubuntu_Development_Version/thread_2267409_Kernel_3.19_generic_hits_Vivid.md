---
title: "Kernel 3.19 generic hits Vivid"
date: 2015-03-01
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-03-01
So I just installed the 3.19.0-7-generic kernel in Vivid 15.04 and the good thing is that it didn't want to remove all of the previous kernels.

/etc/kernel/postinst.d/apt-auto-removal is allowing me to keep both the previous and this new kernel.

```
cavsfan@cavsfan-MS-7529:~$ uname -a
Linux cavsfan-MS-7529 3.19.0-7-generic #7-Ubuntu SMP Thu Feb 26 20:19:34 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

I guess this will be faster performance wise and better overall?

---

### Post by zika on 2015-03-01
> **Cavsfan said:**
> So **I just installed** the 3.19.0-7-generic kernel in Vivid 15.04 and the good thing is that it didn't want to remove all of the previous kernels.Why would it remove anything if You've just installed it manually? ;) Did You do it manually or it came to Your install automatically?

---

### Post by Cavsfan on 2015-03-01
> **zika said:**
> Why would it remove anything if You've just installed it manually? ;) Did You do it manually or it came to Your install automatically?

I got it through manual updating. **sudo apt-get update && sudo apt-get dist-upgrade**

[http://ubuntuforums.org/showthread.php?t=2251168&p=13225832#post13225832](http://ubuntuforums.org/showthread.php?t=2251168&p=13225832#post13225832)

[http://ubuntuforums.org/showthread.php?t=2251168&page=2&p=13235656#post13235656](http://ubuntuforums.org/showthread.php?t=2251168&page=2&p=13235656#post13235656)

---

### Post by Mateusz Stachowski on 2015-03-01
In my case it wants to remove the previous kernel which was installed through regular updates with Synaptic. But only it's extra package.

> $ sudo apt-get autoremove Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Nast&#281;puj&#261;ce pakiety zostan&#261; USUNI&#280;TE:
  linux-image-extra-3.18.0-13-generic
0 aktualizowanych, 0 nowo instalowanych, 1 usuwanych i 0 nieaktualizowanych.
Po tej operacji zostanie zwolnione 157 MB miejsca na dysku.

It wanted to do the same thing previously to the 3.18.0-12 kernel.

---

### Post by Cavsfan on 2015-03-01
> **Mateusz Stachowski said:**
> In my case it wants to remove the previous kernel which was installed through regular updates with Synaptic. But only it's extra package.

> $ sudo apt-get autoremove Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Nast&#281;puj&#261;ce pakiety zostan&#261; USUNI&#280;TE:
  linux-image-extra-3.18.0-13-generic
0 aktualizowanych, 0 nowo instalowanych, 1 usuwanych i 0 nieaktualizowanych.
Po tej operacji zostanie zwolnione 157 MB miejsca na dysku.

It wanted to do the same thing previously to the 3.18.0-12 kernel.

My system did not want to remove any parts of the 3.18.0-13-generic. Which made me think the problem is fixed.

But that is exactly what my Vivid and Trusty systems have been doing. 
It would just request to autoremove one part of the kernel but I went ahead and removed the rest of the kernel manually.

E.g **sudo apt-get purge linux-headers-3.18.0-12 linux-headers-3.18.0-12-generic linux-image-3.18.0-12-generic linux-image-extra-3.18.0-12-generic **

I hope that it does not ask to remove the 3.18.0-13 kernel in the future. But now that I see I'm not the only one experiencing this it may be a huge problem.
I guess you are supposed to have 2 kernels, one for backup but until today that has not happened.
Even though the autoremove file created when a new kernel is added has the previous 2 kernels listed so they would stay.

---

### Post by Mateusz Stachowski on 2015-03-01
Yes you should have two kernels, one for backup. This is how it supposed to work but I never had it working or at least I don't remember a time when it actually worked that way. It either wants to remove all kernels, only extras part of the kernel or simply it doesn't list any kernels to be autoremoved so you have GB of wasted hard drive space and eventually you can't boot your system.

Also that autoremove for kernels is only one big ugly hack so it's no wonder it doesn't work like it supposed to do.

Also the autoremove thing omits the kernels that you installed manually.

---

### Post by craig10x on 2015-03-01
Is 3.19 kernel available on the daily builds yet?  Just curious ;)

---

### Post by PaulW2U on 2015-03-01
> **craig10x said:**
> Is 3.19 kernel available on the daily builds yet?  Just curious ;)

Yes, I tested today's Xubuntu daily builds earlier.

---

### Post by Cavsfan on 2015-03-01
My Precise 12.04 install works correctly keeping 2 kernels, but the autoremove doesn't propose to remove all of the parts of the 3rd kernel back. 
It only wants to remove 2 of the 3 parts that need removed.

I have always kept track of the kernels on each system on a text file and manually remove the 3rd one back after a reboot when a new one gets installed.
This was the last kernel I deleted on Precise: **sudo apt-get purge linux-headers-3.2.0-75 linux-headers-3.2.0-75-generic linux-image-3.2.0-75-generic**.
I still have the **3.2.0-76-generic** and running the **3.2.0-77-generic** kernel.

At some point they had added 2 extra files to the kernel files.
At that time the autoremove worked correctly wanting to remove 5 kernel files. Then something happened and now the autoremoval of kernels is broken.

On Vivid for example a kernel would get installed in the updates lets say the **3.18.0-13-generic** for example. Requiring a reboot of course.
But prior to rebooting the /etc/apt/apt.conf.d/01autoremove-kernels file would be correct listing the 2 most recently installed kernels **3.18.0-12-generic** and **3.18.0-13-generic**.

Upon rebooting autoremove would want to remove the one prior which would leave one kernel.
This /etc/apt/apt.conf.d/01autoremove-kernels file at that time would contain the **3.18.0-11-generic** and **3.18.0-13-generic**
Not mentioning the previous kernel so autoremove thought it should remove it so I manually deleted it. Every time a kernel was removed a reboot was required, which seemed unusual.

Then I would look at the /etc/apt/apt.conf.d/01autoremove-kernels file and it would be back to listing the **3.18.0-12-generic** and **3.18.0-13-generic** kernels.

That is what is broken. ;)

---

### Post by craig10x on 2015-03-01
@Paul: Thanks...i wanted to check out the 15.04 live session when 3.19 kernel arrived...appreciate it :smile:
Always loved your Fred Flintstone avatar, by the way ;)

---

### Post by ventrical on 2015-03-01
It installed here with no problems, no offer to remove.

```

sudo apt-get dist-upgrade

```

---

### Post by Cavsfan on 2015-03-02
> **ventrical said:**
> It installed here with no problems, no offer to remove.

```

sudo apt-get dist-upgrade

```

Have you been able to keep 2 kernels before this upgrade to the 3.19 kernel from the official repositories?
My system is still not asking to remove the previous 3.18 kernel either.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep -e "linux-generic" -e "linux-header" -e "linux-image"
ii  linux-generic                                        3.19.0.7.6                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.18.0-13                              3.18.0-13.14                               all          Header files related to Linux kernel version 3.18.0
ii  linux-headers-3.18.0-13-generic                      3.18.0-13.14                               amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-7                               3.19.0-7.7                                 all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-7-generic                       3.19.0-7.7                                 amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.19.0.7.6                                 amd64        Generic Linux kernel headers
ii  linux-image-3.18.0-13-generic                        3.18.0-13.14                               amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-7-generic                         3.19.0-7.7                                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.18.0-13-generic                  3.18.0-13.14                               amd64        Linux kernel extra modules for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-7-generic                   3.19.0-7.7                                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                                  3.19.0.7.6                                 amd64        Generic Linux kernel image

```

---

### Post by jerrylamos on 2015-03-02
> **Cavsfan said:**
> Have you been able to keep 2 kernels before this upgrade to the 3.19 kernel from the official repositories?
My system is still not asking to remove the previous 3.18 kernel either.
My experience over the years since Dapper Drake Beta ubuntu update & upgrade leaves the previous linux image.

Achtung - in rare cases the new linux-image doesn't work and I have to boot the previous image to get running.  This is a Development forum and the new linux image may be screwed up for your hardware.

If and only if the new image works, I do a 
ls /boot then a 
sudo synaptic (if it's not installed do a sudo apt-get install synaptic)
search on linux-image-3
then choose to remove old image(s) completely.

Saves a bunch of clutter on the partition.

---

### Post by Cavsfan on 2015-03-02
> **jerrylamos said:**
> My experience over the years since Dapper Drake Beta ubuntu update & upgrade leaves the previous linux image.

Achtung - in rare cases the new linux-image doesn't work and I have to boot the previous image to get running.  This is a Development forum and the new linux image may be screwed up for your hardware.

If and only if the new image works, I do a 
ls /boot then a 
sudo synaptic (if it's not installed do a sudo apt-get install synaptic)
search on linux-image-3
then choose to remove old image(s) completely.

Saves a bunch of clutter on the partition.

Jerry, did you read this post? I know it's sort of long but it explains the problem pretty well. 
This started happening to me in Trusty and has been continuing ever since.

[http://ubuntuforums.org/showthread.php?t=2267409&p=13237558#post13237558](http://ubuntuforums.org/showthread.php?t=2267409&p=13237558#post13237558)

---

### Post by craig10x on 2015-03-02
Running today's daily build of 15.04 on live session...3.19 kernel running smooth and stable on my intel (sandybridge) toshiba laptop 17" (which is my desktop...lol) :D
I wanted to see how it runs on my hardware, since this will be the release kernel and i planned on upgrading my 14.10 to 15.04 after it is released...

---

### Post by ventrical on 2015-03-02
> **Cavsfan said:**
> Have you been able to keep 2 kernels before this upgrade to the 3.19 kernel from the official repositories?
My system is still not asking to remove the previous 3.18 kernel either.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep -e "linux-generic" -e "linux-header" -e "linux-image"
ii  linux-generic                                        3.19.0.7.6                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.18.0-13                              3.18.0-13.14                               all          Header files related to Linux kernel version 3.18.0
ii  linux-headers-3.18.0-13-generic                      3.18.0-13.14                               amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-7                               3.19.0-7.7                                 all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-7-generic                       3.19.0-7.7                                 amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.19.0.7.6                                 amd64        Generic Linux kernel headers
ii  linux-image-3.18.0-13-generic                        3.18.0-13.14                               amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-7-generic                         3.19.0-7.7                                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.18.0-13-generic                  3.18.0-13.14                               amd64        Linux kernel extra modules for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-7-generic                   3.19.0-7.7                                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                                  3.19.0.7.6                                 amd64        Generic Linux kernel image

```

Has worked well here.

```

ventrical@ventrical-MS-7798:~$ dpkg -l | grep -e "linux-generic" -e "linux-header" -e "linux-image"
ii  linux-generic                                         3.19.0.7.6                                  amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.15.0-1                                3.15.0-1.5                                  all          Header files related to Linux kernel version 3.15.0
ii  linux-headers-3.15.0-1-generic                        3.15.0-1.5                                  amd64        Linux kernel headers for version 3.15.0 on 64 bit x86 SMP
ii  linux-headers-3.15.0-2                                3.15.0-2.6                                  all          Header files related to Linux kernel version 3.15.0
ii  linux-headers-3.15.0-2-generic                        3.15.0-2.6                                  amd64        Linux kernel headers for version 3.15.0 on 64 bit x86 SMP
ii  linux-headers-3.15.0-3                                3.15.0-3.7                                  all          Header files related to Linux kernel version 3.15.0
ii  linux-headers-3.15.0-3-generic                        3.15.0-3.7                                  amd64        Linux kernel headers for version 3.15.0 on 64 bit x86 SMP
ii  linux-headers-3.15.0-4                                3.15.0-4.9                                  all          Header files related to Linux kernel version 3.15.0
ii  linux-headers-3.15.0-4-generic                        3.15.0-4.9                                  amd64        Linux kernel headers for version 3.15.0 on 64 bit x86 SMP
ii  linux-headers-3.15.0-5                                3.15.0-5.10                                 all          Header files related to Linux kernel version 3.15.0
ii  linux-headers-3.15.0-5-generic                        3.15.0-5.10                                 amd64        Linux kernel headers for version 3.15.0 on 64 bit x86 SMP
ii  linux-headers-3.15.0-6                                3.15.0-6.11                                 all          Header files related to Linux kernel version 3.15.0
ii  linux-headers-3.15.0-6-generic                        3.15.0-6.11                                 amd64        Linux kernel headers for version 3.15.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-10                               3.16.0-10.15                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-10-generic                       3.16.0-10.15                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-11                               3.16.0-11.16                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-11-generic                       3.16.0-11.16                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-16                               3.16.0-16.22                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-16-generic                       3.16.0-16.22                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-17                               3.16.0-17.23                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-17-generic                       3.16.0-17.23                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-18                               3.16.0-18.25                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-18-generic                       3.16.0-18.25                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-21                               3.16.0-21.28                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-21-generic                       3.16.0-21.28                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-22                               3.16.0-22.29                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-22-generic                       3.16.0-22.29                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-23                               3.16.0-23.31                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-23-generic                       3.16.0-23.31                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-24                               3.16.0-24.32                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-24-generic                       3.16.0-24.32                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-25                               3.16.0-25.33                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-25-generic                       3.16.0-25.33                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-28                               3.16.0-28.38                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-28-generic                       3.16.0-28.38                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-3                                3.16.0-3.8                                  all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-3-generic                        3.16.0-3.8                                  amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-9                                3.16.0-9.14                                 all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-9-generic                        3.16.0-9.14                                 amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.18.0-11                               3.18.0-11.12                                all          Header files related to Linux kernel version 3.18.0
ii  linux-headers-3.18.0-11-generic                       3.18.0-11.12                                amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-3.18.0-13                               3.18.0-13.14                                all          Header files related to Linux kernel version 3.18.0
ii  linux-headers-3.18.0-13-generic                       3.18.0-13.14                                amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-3.18.0-8                                3.18.0-8.9                                  all          Header files related to Linux kernel version 3.18.0
ii  linux-headers-3.18.0-8-generic                        3.18.0-8.9                                  amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-3.18.0-9                                3.18.0-9.10                                 all          Header files related to Linux kernel version 3.18.0
ii  linux-headers-3.18.0-9-generic                        3.18.0-9.10                                 amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-7                                3.19.0-7.7                                  all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-7-generic                        3.19.0-7.7                                  amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-4.0.0-040000rc1                         4.0.0-040000rc1.201502222235                all          Header files related to Linux kernel version 4.0.0
ii  linux-headers-4.0.0-040000rc1-generic                 4.0.0-040000rc1.201502222235                amd64        Linux kernel headers for version 4.0.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.19.0.7.6                                  amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.15.0-1-generic                          3.15.0-1.5                                  amd64        Linux kernel image for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-3.15.0-2-generic                          3.15.0-2.6                                  amd64        Linux kernel image for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-3.15.0-3-generic                          3.15.0-3.7                                  amd64        Linux kernel image for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-3.15.0-4-generic                          3.15.0-4.9                                  amd64        Linux kernel image for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-3.15.0-5-generic                          3.15.0-5.10                                 amd64        Linux kernel image for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-3.15.0-6-generic                          3.15.0-6.11                                 amd64        Linux kernel image for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-10-generic                         3.16.0-10.15                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-11-generic                         3.16.0-11.16                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-16-generic                         3.16.0-16.22                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-17-generic                         3.16.0-17.23                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-18-generic                         3.16.0-18.25                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-21-generic                         3.16.0-21.28                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-22-generic                         3.16.0-22.29                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-23-generic                         3.16.0-23.31                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-24-generic                         3.16.0-24.32                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-25-generic                         3.16.0-25.33                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-28-generic                         3.16.0-28.38                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-3-generic                          3.16.0-3.8                                  amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-9-generic                          3.16.0-9.14                                 amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.18.0-11-generic                         3.18.0-11.12                                amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-3.18.0-13-generic                         3.18.0-13.14                                amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-3.18.0-8-generic                          3.18.0-8.9                                  amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-3.18.0-9-generic                          3.18.0-9.10                                 amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-7-generic                          3.19.0-7.7                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.0.0-040000rc1-generic                   4.0.0-040000rc1.201502222235                amd64        Linux kernel image for version 4.0.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.15.0-1-generic                    3.15.0-1.5                                  amd64        Linux kernel extra modules for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-extra-3.15.0-2-generic                    3.15.0-2.6                                  amd64        Linux kernel extra modules for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-extra-3.15.0-3-generic                    3.15.0-3.7                                  amd64        Linux kernel extra modules for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-extra-3.15.0-4-generic                    3.15.0-4.9                                  amd64        Linux kernel extra modules for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-extra-3.15.0-5-generic                    3.15.0-5.10                                 amd64        Linux kernel extra modules for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-extra-3.15.0-6-generic                    3.15.0-6.11                                 amd64        Linux kernel extra modules for version 3.15.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-10-generic                   3.16.0-10.15                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-11-generic                   3.16.0-11.16                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-16-generic                   3.16.0-16.22                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-17-generic                   3.16.0-17.23                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-18-generic                   3.16.0-18.25                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-21-generic                   3.16.0-21.28                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-22-generic                   3.16.0-22.29                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-23-generic                   3.16.0-23.31                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-24-generic                   3.16.0-24.32                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-25-generic                   3.16.0-25.33                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-28-generic                   3.16.0-28.38                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-3-generic                    3.16.0-3.8                                  amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-9-generic                    3.16.0-9.14                                 amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.18.0-11-generic                   3.18.0-11.12                                amd64        Linux kernel extra modules for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-extra-3.18.0-13-generic                   3.18.0-13.14                                amd64        Linux kernel extra modules for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-extra-3.18.0-8-generic                    3.18.0-8.9                                  amd64        Linux kernel extra modules for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-extra-3.18.0-9-generic                    3.18.0-9.10                                 amd64        Linux kernel extra modules for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-7-generic                    3.19.0-7.7                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.19.0.7.6                                  amd64        Generic Linux kernel image
ventrical

```

---

### Post by Cavsfan on 2015-03-03
@ventrical
That's good. Trusty doesn't though. Although I have never needed to use the previous kernel before. And don't really care if it does or if it doesn't.
I've booted into the previous kernel once just to verify that something was broke there too but even that was a wasted effort IMO.

So, you must have some spare disk space. You keep all previous kernels?

---

### Post by Cavsfan on 2015-03-06
Installed Vivid Mate beta1 yesterday since it's now a flavor and it didn't have the 3.19 kernel pre-installed. But it was there for a dist-upgrade.

---

