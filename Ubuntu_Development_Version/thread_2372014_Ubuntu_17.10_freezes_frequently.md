---
title: "Ubuntu 17.10 freezes frequently"
date: 2017-09-20
forum: Ubuntu Development Version
---

### Post by kagashe on 2017-09-20
I had installed Ubuntu 17.10 on a spare partition and updating it daily. If I use Firefox (or Epiphany) for browsing the system freezes after a few minutes. It does not respond to any key presses like Ctrl Alt F1 or Ctrl Alt Del.

My Leptop is Lenovo-G50-45 which has AMD chip. I do not use any proprietary driver. Memory is 2GB (1712 MB is available) and 1024 MB swap partition.

There is PgDn/SysRq key on extreme right. Fn+SysRq also does not work. I am shutting down by long pressing the power key.

I would like to submit a Bug Report but could not find any logs of previous boots. I understand I have to configure journalctl for this (how?)

Kamalakar

---

### Post by ventrical on 2017-09-20
> **kagashe said:**
> I had installed Ubuntu 17.10 on a spare partition and updating it daily. If I use Firefox (or Epiphany) for browsing the system freezes after a few minutes. It does not respond to any key presses like Ctrl Alt F1 or Ctrl Alt Del.

My Leptop is Lenovo-G50-45 which has AMD chip. I do not use any proprietary driver. Memory is 2GB (1712 MB is available) and 1024 MB swap partition.

There is PgDn/SysRq key on extreme right. Fn+SysRq also does not work. I am shutting down by long pressing the power key.

I would like to submit a Bug Report but could not find any logs of previous boots. I understand I have to configure journalctl for this (how?)

Kamalakar

There seems to be something wrong in the number you mention with memory resources. Also swap should be at least 2GB. I am assuming it is a hardware freeze due to a resource  problem. Most laptops now  the have 2GB or less will not work  very well with 17.10 . Are you using SSD drive?

Regards..


Regards..

---

### Post by cariboo on 2017-09-20
Create a bug against the kernel eg:

```
ubuntu-bug linux
```

I have frequent lockups on my Toshiba laptop during the early part of development, it didn't stop until the 4.12 kernel was released.

---

### Post by flocculant on 2017-09-20
> **kagashe said:**
> ...

I would like to submit a Bug Report but could not find any logs of previous boots. I understand I have to configure journalctl for this (how?)

Kamalakar

```
sudo mkdir -p /var/log/journal
```

should start persistent journalctl logs.

```
journalctl --list-boots
``` does exactly what you'd expect it to do

More information [here]("https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs"), check the Past Boots section.

---

### Post by kagashe on 2017-09-21
> **ventrical said:**
> There seems to be something wrong in the number you mention with memory resources. Also swap should be at least 2GB. I am assuming it is a hardware freeze due to a resource  problem. Most laptops now  the have 2GB or less will not work  very well with 17.10 . Are you using SSD drive?

Regards..


Regards..
When I installed Ubuntu 17.10 it used existing swap partition and was working well. Meanwhile I broke my Debian install while changing the repos from stable to testing and reinstalled Debian. Debian install probably altered the UUID of swap partition and Ubuntu 17.10 stopped using it.

I came to know that Ubuntu 17.10 could use swapfile and created it just now:
```
sudo fallocate -l 1G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo swapon --show

```

I hope it was hardware freeze and should work ok now.

I have added swapfile to /etc/fstab
```
sudo cp /etc/fstab /etc/fstab.bak
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

```

Kamalakar

---

