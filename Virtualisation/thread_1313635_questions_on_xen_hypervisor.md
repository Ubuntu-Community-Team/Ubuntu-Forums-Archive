---
title: "questions on xen hypervisor"
date: 2009-11-03
forum: Virtualisation
---

### Post by sdowney717 on 2009-11-03
[http://www.xen.org/products/xenhyp.html](http://www.xen.org/products/xenhyp.html)

it is a type 1 hypervisor so it boots itself and then you run multiple guests?

what would be the effect of running xen and having a windows xp guest and a ubuntu guest running concurrently, could you share files, run the os's at near native speeds etc...?
how good is it for usb 2.0 support?
how about 3d video?
[http://en.wikipedia.org/wiki/Xen](http://en.wikipedia.org/wiki/Xen)

[http://www.youtube.com/watch?v=m7XO3Gf9yGE&feature=related](http://www.youtube.com/watch?v=m7XO3Gf9yGE&feature=related)

[http://www.youtube.com/user/CitrixDemo#p/a](http://www.youtube.com/user/CitrixDemo#p/a)
[http://www.youtube.com/user/CitrixDemo#p/a](http://www.youtube.com/user/CitrixDemo#p/a)
[http://www.youtube.com/watch?v=msyvpFqFl0I&feature=related](http://www.youtube.com/watch?v=msyvpFqFl0I&feature=related)

---

### Post by kameleon25 on 2009-11-04
I am currently running Ubuntu server 8.04.3LTS with xen installed on a dualcore AMD machine. I have 8 DOMU's installed. Of which there is:

1x Windows 7
1x Windows server 2003
3x Ubuntu 8.04 PV 32-bit
1x Centos 5.3 PV
2x Ubuntu 8.04 PV 64-bit

All of them are able to communicate to one another just as if they were seperate machines. If you have a seperate video card you could pass that through to one of the VM's, though I have no experience with that. Same with USB. 

As for speed, the full virt machines (windows based) seem to run about par with a full hardware installed machine in my experience. The para-virt linux machines are claimed at 90-95% native speed but I cannot tell a difference from one of the PV to a full machine. 

Hope that helps some.

---

### Post by sdowney717 on 2009-11-04
what is the way to do this.
I currently have 2 partitions, one ix vista, one is ubuntu.

must you start with a zen boot and have a singular separate file for each os? like vmware,
OR can you somehow use your current installed os's each in their separate partitions?

---

### Post by kameleon25 on 2009-11-04
The way I do it is with LVM. All my vm's use LVM as the image files cause more overhead and thus affect performance a bit. Plus with the LVM snapshot feature it is a "snap" to do a backup. There is a way to access a physical disk for a DOMU. While I have never accessed a full disk, I would asume it would be similar to the LVM way of a phy: disk command in your cfg file.

To install xen depends on your version of ubuntu. I use only the server version (and 8.04LTS) so it is as simple as: sudo aptitude install ubuntu-xen-server. Also, to do a windows guest you will need a CPU that supports full virtualization. It must be an Intel chip with Intel-VT or an AMD with AMD-v (or similar). Most all your dual core AMD chips have them, while Insmell jips alot of users with this feature.

---

### Post by sdowney717 on 2009-11-04
ok, i installed those packages. I then rebooted
I dont think it is working, the screen flashes like crazy with a lot of text about sr1 media.
then it finallly stops flashing and drops me at a login prompt asking for user name and password. I log in but what next?
I am sitting at a console prompt
 Is there a guide?

---

### Post by sdowney717 on 2009-11-04
disaster now cant log into vmware server

[http://www.linuxquestions.org/questions/linux-software-2/cannot-open-vmware2.0-on-ubuntu-8.04-677090/](http://www.linuxquestions.org/questions/linux-software-2/cannot-open-vmware2.0-on-ubuntu-8.04-677090/)

i had to remove 3 modules and i had to rebuild the server

---

### Post by kameleon25 on 2009-11-04
Correct, Xen and VMware do not play well together. If you are using the desktop version of ubuntu you will need to install the "ubuntu-xen-desktop" package rather than the "ubuntu-xen-server" package. What version are you running? like 8.04, 8.10, 9.04, 9.10 and desktop or server? Also it would be helpful to know what processor you have to see if it has virtualization support.

---

### Post by sdowney717 on 2009-11-04
running karmic desktop
i have an e6550 core 2 duo

---

