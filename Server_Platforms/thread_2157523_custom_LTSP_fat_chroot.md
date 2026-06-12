---
title: "custom LTSP fat chroot"
date: 2013-06-25
forum: Server Platforms
---

### Post by xris_xcess on 2013-06-25
Hi:

I'm currently running a small computer lab in a school. I hava an ubuntu server set up running LTSP and the lab pc's start up as fat-clients running xubuntu-desktop. It runs very well and I has been much easier to maintain, and a lot faster, than the older shared-nfs-root we had before.

However, I would like to try and minimize the xfce4 install, instead of the whole xubuntu-desktop package. I already did a bare minimal xcfe4 install on a hdd and it's just what we need for the students.

I duplicated this install on the server with debootstrap/chroot, set up the ndb-server configs, modified pxelinux.cfg/default and tried it. The clients boot and things seem to get loading but... it all stalls when the ndb-image starts loading. I get a "... Negotiating..." message and then nothing.

Since I didn't use the ltsp-build-client script, I wonder if there are packages or  settings that I'm overlooking, I have tried to compare it with my current fat-chroot and have duplicated as much as I have found...

Anyone have experience building a custom image for ltsp?

Or should I do it backwards? Install xubuntu-destop and then try to slim it down? Or even specify my own custom-desktop package and parse that to the ltsp-build-image script?

---

### Post by xris_xcess on 2013-07-05
Well... I gave up in the end. I couldn't track down the changes that ltsp-build-image does when it creates the chroot. I'll have to head over to the ltsp project page for more details. However, I'm trying something very particular as well. Building a 13.04 chroot on a 12.04 server. I understand that the deboostrap package has some problems sometimes building "downstream".

Anyway, I got almost my cake by building a "thin" chroot first and then using ltsp-chroot to install xfce4 and related packages. The final image is about 40% smaller. Overall, I'm not sure if having the latest version of xubuntu would actually make much of a difference on my current setup.

What I AM trying to figure now is what I can leave out of the image with the ltsp-update-image -e flags. At the moment I have boot var/cache tmp. I have been looking into var/lib and the modules folders. Does anyone know what definitely is not going to be necessary on a fat-client? Most of my hardware is pretty standard and will not change much, ie. a controlled environment.

Any ideas? or any hints where I could ask for more detailed info?

---

