---
title: "Problems with permissions and shared folder in VirtualBox."
date: 2012-03-01
forum: Virtualisation
---

### Post by Rytron on 2012-03-01
Hi.

I am using Ubuntu 10.04 as my Host OS.
I have Xubuntu 11.10 as my Guest OS installed in VirtualBox.

I am having problems with permissions and the shared folder in VirtualBox. I can access it from within the guest OS but only with root. Even when I do that I cannot copy from the host onto my guest folder.

How do I fix this?

I setup the folder in Vbox settings with the folder-name 'Host-Share' (it links to my host Desktop directory).

I ran this command in Vbox:
```
sudo mount -t vboxsf Host-Share /home/cal/Desktop/Host-Share
```

---

