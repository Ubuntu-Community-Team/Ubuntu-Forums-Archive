---
title: "How to delete OS upgrade?"
date: 2019-12-17
forum: Ubuntu/Debian BASED
---

### Post by alvinrr on 2019-12-17
How to delete this POP OS upgrade on my Ubuntu 18.4? I remember installing Pop OS for my shell theme and icons.
please see attached image.

---

### Post by deadflowr on 2019-12-17
*Thread moved to **Ubuntu/Debian BASED***

Pop OS is it's own operating system based Ubuntu.

But for what it's worth, you can try changing the upgrade setting in software sources (also known as Software and Updates.
In Software and Updates go to the updates tab section and go to the Notify me of new version and toggle the bar to Never.

If that doesn't work, try editing the release-upgrade file in /etc/update-manager/release-upgrade and try changing the Prompt= to never
See: [https://www.howtoforge.com/tutorial/ubuntu-lts-update-dist-upgrade/]("https://www.howtoforge.com/tutorial/ubuntu-lts-update-dist-upgrade/")

---

### Post by alvinrr on 2019-12-17
Hello, that doesn't work, I wanted it to be deleted permanently and not just stop it from prompting.

---

### Post by alvinrr on 2019-12-21
Does that mean that Pop OS is installed in my computer as well?

---

### Post by Frogs Hair on 2019-12-21
Post the output of the following command. Pop OS and Ubuntu are different operating systems though Pop is Ubuntu based. Are you running a system 76 computer ? If so the new default would be Pop OS and that would explain the upgrade offer. 

```
lsb_release -a 
```

---

### Post by alvinrr on 2019-12-21
No, my previous OS is Windows 7, I just switched to Ubuntu this past week.

alvin@alvin:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic

---

### Post by Frogs Hair on 2019-12-21
Where did you download the Ubuntu ISO from ?

---

### Post by guiverc on 2019-12-21
It could you've added a Pop_OS PPA to your system (after a theme or something minor) which has caused pollution to your packages.

Apt tools upgrade by versions; and Pop/Mint/etc intentionally put higher version numbers on their packages so their packages replace Ubuntu ones for their users, which can create problems like what you've noticed plus potentially worse down the road when it's release-upgrade time (ie. when you want to release-upgrade to 20.04).

As written (the limited details) we cannot know what you did due to lack of detail.

---

### Post by alvinrr on 2019-12-21
Thanks for the answers guys, I have found an article thread with similar problem, I followed the steps he did and the POP_OS upgrade is now gone, and this is now Solved.
[https://askubuntu.com/questions/1188605/why-is-my-ubuntu-18-04-distribution-asking-me-to-upgrade-to-pop-os-19-10](https://askubuntu.com/questions/1188605/why-is-my-ubuntu-18-04-distribution-asking-me-to-upgrade-to-pop-os-19-10)

---

