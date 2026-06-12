---
title: "vbox ubuntu desktop + server using samba"
date: 2017-11-24
forum: Virtualisation
---

### Post by takun2 on 2017-11-24
Okay, let me give you my setup first:

I have one computer running Ubuntu Server 16.04.3 LTS. This server has 4 drive partitions setup through samba.

I also have a Win10 computer running vbox Ubuntu Desktop 16.04 LTS. Both host/guest can access the 4 drives by IP/network.

On to the problem:

I have the aforementioned drives mapped on Windows, and have tried to set vbox to automount those folders. They do not appear to actually be mounting anywhere. For example one of them is called vdrive in vbox and I am unable to mount it or browse to it (using sudo mount -t vboxsf vdrive ~/vdrive). It doesn't give an error, it just hangs like it is trying to but never goes anywhere, 20 minutes later I end up giving up and just stopping it.

I can mount the samba drives directly from the network screen, however they have a smb://server/drive1 location instead of a normal /media or /mnt location. How do I get these drives to have a local directory so that I can save files directly to them without having to save them first in the ~/downloads?

For example, I have a file I want to add to the server. When I download it through Firefox, I don't have the option to select the smb://* locations, even if I click + Other Location, the only option there is the / directory. I know in the past I have been able to have Ubuntu automount a sharedrive and it puts a folder on the desktop to access it, but this doesn't seem to work.

The usernames are different for the desktop and server, and when I access it through network, I do have to type in the server username, workgroup, and password, which lets me have access to those files through the file browser, so I know the vbox can access the fold, just not how to let firefox or any other app save to them directly.

---

### Post by ODTech on 2017-11-24
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Your googlefu is lacking :)

---

### Post by takun2 on 2017-11-24
It has been a long time for me sensei, thank you for teaching. (And yeah, I clearly wasn't searching for the right thing, I kept looking for samba instructions). I actually just cut the middle man out and directly connected to the server using that article instead of the mirrored windows. I appreciate you linking that to me.

---

