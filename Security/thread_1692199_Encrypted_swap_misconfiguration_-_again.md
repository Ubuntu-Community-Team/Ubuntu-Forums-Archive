---
title: "Encrypted swap misconfiguration - again"
date: 2011-02-21
forum: Security
---

### Post by jaykubun on 2011-02-21
Hello fellow (k)ubuntu users!

I am not sure if I choose the right forum for my question this time. First attempt to get this solved i started on the [URL="http://ubuntuforums.org/showthread.php?t=1688113"]
"Installation & Upgrades"
[/URL] Forum. So this is basically a repost.

I configured an encrypted swap during the installation process of my kubuntu maverick using the manual install CD. I do not use LVM. This worked fine but I made the mistake of assigning a password to the encrypted swap. I would like to change this in favor for a random key. I tried to change /etc/crypttab in the following way:

old /etc/crypttab looked like this: 
```

sda7_crypt UUID=23df4831-fb6d-4183-8d28-dd46664bcfbe none luks,swap
```

new:
```

sda7_crypt UUID=23df4831-fb6d-4183-8d28-dd46664bcfbe /dev/urandom swap
```

Now the system still asks for a password for sda7_crypt at startup, but does not recognize the old password. It seems that the swap gets a random key and works fine anyway, so I really want to remove only the question for the PW at boot time.
This is not a big issue, but it is annoying. When the system is up I can do swapoff and swapon without problems and no password is needed. 

Directly after boot swap works:

```
cat /proc/swaps
 Filename                                Type            Size    Used    Priority
 /dev/dm-1                               partition       5890044 0       -1
```

then I do "sudo swapoff -a" and get

```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
```

and finally after "sudo swapon -a"

```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       5890044 0       -1
```

So this problem seems to be located in the startup process. What do i have to change in order to have random encrypted swap already during boot time without questions for a password?

Thanks all!

---

### Post by jaykubun on 2011-02-22
Solved the problem by typing this into my shell:

```
sudo dpkg-reconfigure linux-image-2.6.35-25-generic
```

now it works

---

