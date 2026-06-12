---
title: "Ubuntu - Containers"
date: 2016-03-07
forum: Ubuntu Cloud and Juju
---

### Post by iPrimo on 2016-03-07
Hi Team,
I am new to ubuntu and container visualization World.
I would like to ask does ubuntu (Specially Desktop and Mobile versions) support container visualization technologies?
For example if I install a Word processing application, can I trigger Suspend, Snapshot and... to the application ? (Like in VM world)
My understanding is, the existing container technologies (Docker and LXC) are only for applications with command line interfaces, and not developed for apps with GUI interfaces. is that a correct assumption ?
Thanks

---

### Post by slickymaster on 2016-03-07
Hi iPrimo, welcome to the forums.

See if any of these can help you: [http://www.ubuntu.com/cloud/lxd](http://www.ubuntu.com/cloud/lxd) and [https://insights.ubuntu.com/2016/02/16/zfs-is-the-fs-for-containers-in-ubuntu-16-04/](https://insights.ubuntu.com/2016/02/16/zfs-is-the-fs-for-containers-in-ubuntu-16-04/)

---

### Post by grahammechanical on 2016-03-07
On Ubuntu containers are Linux containers and LXC is what is used with LXD as a kind of container manager. Here is the publicity

[http://www.ubuntu.com/cloud/lxd](http://www.ubuntu.com/cloud/lxd)

From the point of view of the Ubuntu desktop user (and I speak from experience) LXC & LXD seem to be command line tools. And the focus of development is toward business use and not desktop use. This is my opinion from doing a little bit of experimentation with LXC. 

We can install different operating systems inside a Linux container (LXC) but the supplied images on the server seem to be server type images without a desktop. All the same I do not think it correct to see LXC as not being developed for GUI interfaces.

I have read that it is possible to run applications like Libreoffice in a Linux container. This would be done as a form of security. And I know that the soon to be released Ubuntu tablet running Unity 8 on Mir will be able to run Debian packaged applications like Firefox and Libreoffice in LXC containers.

Here is a video running Libreoffice on a Ubuntu phone. This is a demonstration of Ubuntu convergence. Plug in a keyboard and the Ubuntu tablet switches to desktop mode and stuff like Libreoffice can be run and they are runing in a Linux container (LXC) in order not to break the security model of Ubuntu for devices. 

[http://www.omgubuntu.co.uk/2016/02/ubuntu-convergence-x11-apps-video-demo](http://www.omgubuntu.co.uk/2016/02/ubuntu-convergence-x11-apps-video-demo)

I have used LXC on Ubuntu desktop and I have been able to set up Ubuntu desktop and the other Ubuntu desktop flavours in LXC containers and switch between them. So, it is possible.

I do not think that LXC does snapshots. On the desktop we switch between the host and the container by pressing Ctrl+Alt+F8 to get into the first container. Ctrl+Alt+F9 would take us to the second container. And so on. Depending on the number of containers we have created.  And Ctrl+Alt+F7 will take us back to the host (Ubuntu). We use a command to start & stop containers. I do not think that Linux containers do suspend. I do not think that they need to.

Virtual Machines & Linux containers are different technology. They do some of the same stuff but also different stuff. I can tell you this. A Linux container will take up next to no system resources. Unlike a VM. I do not have the RAM to run one VM but I was able to create several Linux containers with next to no adverse effect on system resources for the host system.

Regards.

---

