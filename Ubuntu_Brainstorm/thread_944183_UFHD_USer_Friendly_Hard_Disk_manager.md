---
title: "UFHD: USer Friendly Hard Disk manager"
date: 2008-10-11
forum: Ubuntu Brainstorm
---

### Post by YigalB on 2008-10-11
Adding another hard disk today is not user friendly.
It requires several steps, even with Gparted. For example: mount is an OS command, not user. I need a disk to use, I don't care the stages it has to go through.

I suggest the UFHD will analyse the starting point )how many disks, what their status) and give options for the final stage (what will they be called, to format or not etc), and with the most common defaults - press OK and the utility will do all.

Since all hardware is supported anyway, this is only a simple GUI thing, but this will help a lot to bring Ubuntu one step forward to be an OS for the people, not for the experts.

---

### Post by gnomeuser on 2008-10-11
We already have this, David Zeuthern the HAL maintainer (and Red Hat employeee) is working on the HAL replacement DeviceKit. The first bit of that to drop is DeviceKit-disks which has enabled him to write gnome-disk-utility as well as some libraries to attach such functionality in relevant places on your desktop. This would mean you would get nice little pop ups for SMART warnings, nice formatting capabilities for your media as well as other handy disk interaction. His palimpsest application will then tie all this together so you have a disk manager application in addition to all this nice integration.

Once Ubuntu adopts this work (likely for Jaunty) you will get this and much much more.

DeviceKit/DeviceKit-disks presentation:
[http://people.freedesktop.org/~david/devkit-presentation-davidz-aug2008.pdf](http://people.freedesktop.org/~david/devkit-presentation-davidz-aug2008.pdf)

DeviceKit-power presentation:
[http://lists.freedesktop.org/archives/devkit-devel/attachments/20080819/2a77ebbc/attachment-0001.pdf](http://lists.freedesktop.org/archives/devkit-devel/attachments/20080819/2a77ebbc/attachment-0001.pdf)

---

### Post by YigalB on 2008-10-11
THanks.
I read the ppts and loved the approach.
I will be happy to help if needed with testing - I install computers often, mostly 3-5 years old.

---

### Post by gnomeuser on 2008-10-11
> **YigalB said:**
> THanks.
I read the ppts and loved the approach.
I will be happy to help if needed with testing - I install computers often, mostly 3-5 years old.

The code is not available in Ubuntu currently (probably will be imported some time after Jaunty opens). If you want to try it now, Fedora 10 has it and the beta for that was recently released. Otherwise I suspect you will have to wait.

The code is still rather young and the integration you look for is a bit in the future but this is the right approach.

You could also compile it yourself, it's parallel installable with HAL so it would be non destructive. For that I would definitely recommend following the mailing list:

[http://lists.freedesktop.org/archives/devkit-devel/](http://lists.freedesktop.org/archives/devkit-devel/)

It's not as active as one might like but I suspect that will get better as distributions pick up the code, currently it's only in Fedora and in the hands of a few select developers so they tend to work things out in private instead of on the list.

---

