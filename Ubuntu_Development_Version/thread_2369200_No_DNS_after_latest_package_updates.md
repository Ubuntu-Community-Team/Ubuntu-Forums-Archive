---
title: "No DNS after latest package updates"
date: 2017-08-19
forum: Ubuntu Development Version
---

### Post by darran-kelinske on 2017-08-19
I just updated to the latest packages on Artful 17.10 and now my DNS does not work. I have added individual entries in /etc/hosts as a workaround, but this is a major showstopper. Has anyone else experienced this with the latest packages?

Any ideas on getting things working again?

Thank you!

---

### Post by jarod1860 on 2017-08-22
same issue

---

### Post by harry332 on 2017-08-22
This could be the correct bug report to this one:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1712283](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1712283)

---

### Post by amano on 2017-08-22
Still happening? 

This upload by xnox might fix some network problems: [https://lists.ubuntu.com/archives/artful-changes/2017-August/008763.html](https://lists.ubuntu.com/archives/artful-changes/2017-August/008763.html)

---

### Post by Rustan on 2017-08-23
on Virtualbox systemd 234-2ubuntu8 work for me.

---

### Post by Irihapeti on 2017-08-23
I just updated my Vbox standard Ubuntu install. I'm still getting the no-dns bug.

I can work around it by running the command "sudo dhclient", which is how I manage to get the updates.

---

### Post by Irihapeti on 2017-08-24
Fixed by installing latest "current" image.

---

### Post by darran-kelinske on 2017-08-24
This didn't work for me. I'm still without internet aside from the hosts I manually added. Thank you all for responding! :)

---

### Post by darran-kelinske on 2017-08-29
I was able to resolve the issue by doing the following:

sudo ln -s /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf

---

### Post by bkinsey on 2017-10-15
thank you darran-kelinske, your solution worked for me also.

---

