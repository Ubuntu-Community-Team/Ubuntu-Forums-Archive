---
title: "Strange machine state after udates - Ubuntu Mate 16.04"
date: 2016-04-15
forum: Virtualisation
---

### Post by bapoumba on 2016-04-15
Host is Mac OSX up to date, VirtualBox and guest additions up to date. Just installed Ubuntu mate 16.04 and ran the regular updates. I was doing other things waiting for the updates to run, so not sure when that happened but this is how I found the machine after a while. Has anyone ever seen that ? Restarted the machine and seems OK. 4GB mem, 3 CPU, 1 monitor, 128MB video mem, very strange. iso md5sum is correct.

---

### Post by slickymaster on 2016-04-15
The exact same thing happened to me yesterday bapoumba, with yesterday's Xubuntu Desktop amd64 image.

Didn't find anything relevant on the logs though.

---

### Post by bapoumba on 2016-04-15
Thanks slicky. What I read is : 0 application "cannot read word" system.
I did not find anything in the logs or online either, the upgrade seems to have run correctly, just ran a dist-upgrade to get the kernel packages. Video looks OK and resizing the guest window works so I'm not sure.

---

### Post by slickymaster on 2016-04-15
Because everything is working as expected after running the updates, I didn't pay much more attention to the issue.

---

### Post by bapoumba on 2016-04-15
Thanks slicky. What I read is : 0 application "cannot read word" system.
I did not find anything in the logs either, the upgrade seems to have run correctly, just ran a dist-upgrade to get the kernel packages. Video looks OK and resizing the guest window works so I'm not sure.

Maybe these ?
[https://www.virtualbox.org/ticket/13615](https://www.virtualbox.org/ticket/13615)
[https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1443853](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1443853)

---

### Post by slickymaster on 2016-04-15
> **bapoumba said:**
> Thanks slicky. What I read is : 0 application "cannot read word" system.
I did not find anything in the logs either, the upgrade seems to have run correctly, just ran a dist-upgrade to get the kernel packages. Video looks OK and resizing the guest window works so I'm not sure.

Maybe these ?
[https://www.virtualbox.org/ticket/13615](https://www.virtualbox.org/ticket/13615)
[https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1443853](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1443853)

Most probably, bapoumba. To be honest I won't be bored by it, as it's my testing box.

---

### Post by bapoumba on 2016-04-15
> **slickymaster said:**
> Most probably, bapoumba. To be honest I won't be bored by it, as it's my testing box.
Thanks slicky. It's been working since then so sorta solved :)

---

