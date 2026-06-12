---
title: "Server totally borked? grub_puts, lvm not available, etc"
date: 2010-05-06
forum: Server Platforms
---

### Post by JohnSka7 on 2010-05-06
Hello everyone,

Here's my problem: upgrade my server to 10.4 and now, when I restart, I get the "grub_puts" error.

Here's my setup: Virtualbox virtual machine with sda, sdb and sdc. 

I've followed a bunch of guides on how to reinstall grub/rescue grub, etc, but the most telling so far was in booting into Ubu Desktop LiveCD and then installing lvdisplay. When I run it, I see that my main boot has status: NOT available.

Any ideas how I can go about rescuing my system? I'd rather not do a fresh install, but if that's the only way...

---

### Post by JohnSka7 on 2010-05-07
ok, so I made some progress.

I booted into the ubuntu 10.4 LiveCD, then started terminal and did the following:

sudo apt-get install lvm2
sudo lvdisplay (to get the name of my device)
sudo vgchange -ay <device> (in my case, stout)
sudo mkdir /mnt/root
sudo mount /dev/stout/root /mnt/root

I was then able to do

sudo grub-install --root-directory=/mnt/root/ /dev/sda1

So it says it installed without a problem, but when I restart I just get a grub prompt. Any ideas where to go next?

---

### Post by rvause on 2010-07-06
Did you manage to find a way round this? I am in exactly the same situation.

---

### Post by JohnSka7 on 2010-07-08
Unfortunately, I found no answers for it so I just gave up and redid my machine. I made a new VHD and installed ubuntu, took the old VHD and loaded it off of the VHD, copied what I needed to copy and moved on with my life.

I love Ubuntu, but these things happen all too often to me and I hate not being able to easily fix, so I've gotten very used to reinstalling :(

---

