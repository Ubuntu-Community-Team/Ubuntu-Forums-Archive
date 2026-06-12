---
title: "Ubuntu peppered with holes? No kernel update available?"
date: 2011-03-05
forum: Security
---

### Post by Hector23 on 2011-03-05
"Nine vulnerabilities allow attackers to gain root privilege and 14 lead to denial of service."

"Upgrade packages include Ubuntu 10.04 LTS:

    * linux-image-2.6.35-25-generic 2.6.35-25.44~lucid1"

[http://www.zdnet.com.au/ubuntu-peppered-with-holes-339310663.htm](http://www.zdnet.com.au/ubuntu-peppered-with-holes-339310663.htm)

More on the saem subject here. always at ZDnet:

<http://www.zdnet.com/blog/open-source/ubuntu-security-holes-found-holes-fixed/8402>

This was online yesterday night and I still have no kernel update available.

uname -r
2.6.32-29-generic

What is one supposed to do about all those warnings?

---

### Post by wojox on 2011-03-05
Are you sure? Run in a terminal:

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

Then reboot your computer regardless and check your kernel version again.

---

### Post by Hector23 on 2011-03-05
> **wojox said:**
> Are you sure? Run in a terminal:

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

Then reboot your computer regardless and check your kernel version again.

Nothing to upgrade. Maybe you have lucid-proposed enabled?

I continued this discussion on a thread that was already opened at:

[http://ubuntuforums.org/showthread.php?p=10526399](http://ubuntuforums.org/showthread.php?p=10526399)

Google didn't provide a link to this page when I searched.

---

