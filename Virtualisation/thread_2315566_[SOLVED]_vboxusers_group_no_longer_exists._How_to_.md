---
title: "[SOLVED] vboxusers group no longer exists. How to add it back?"
date: 2016-02-29
forum: Virtualisation
---

### Post by KenUBF on 2016-02-29
Hi all. I am trying to get my USB device working with Virtualbox on Ubuntu 14.04 with the latest version of Virtualbox. I have intalled the Extension pack and the guest additions CD in the virtual machine I want to enable USB support for. I had issues with this a week ago and I forgot I had to add my user name to the vboxuers group. So I did that and I was able to use my gps on another VM. I am trying to use a USB device with another VM so I checked to see if I was still listed in the vboxers users group and for some strange reason, I get output that tells me there does not exist a vboxusers group. Previously, I used the following command to add myself to the vboxusers group:   [php]sudo adduser [ USERNAME ] vboxusers[/php]  This is the output when I tried to add myself again to see if it would fix the issue a second time:  [php]The group `vboxusers' does not exist.[/php]  How do I add this group back?  Thanks in advance.

---

### Post by MAFoElffen on 2016-02-29
As requested:
```

sudo groupadd vboxusers
sudo usermod -aG vboxusers userName

```

---

### Post by KenUBF on 2016-03-02
This worked. Thank you so much!

---

