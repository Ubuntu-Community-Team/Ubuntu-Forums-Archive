---
title: "Auto mounting shared folders with open-vm-tools"
date: 2010-10-14
forum: Virtualisation
---

### Post by SRamsesIV on 2010-10-14
I was having trouble trying to sort out the auto mounting of my VMWare shared folders using open-vm-tools and I couldn't easily find this information so I thought I might share my results. Perhaps if someone has a better solution, I would love to here it.

The problem as I see it is that the standard configuration for the open-vm-tools package modprobe's the vmhgfs module too late in the init process (it is in the open-vm-tools init script). So if I add a mount to /etc/fstab for the shared folder, then the system complains at boot time that it can't perform the mount.

My solution was to add the following line to /etc/fstab (with the noauto so that it is ignored at boot)
```
.host:/  /mnt/hgfs  vmhgfs  defaults,noauto,uid=1000,gid=1000   0   0
```

and then also added this udev rule
```
ACTION=="add", KERNEL=="vmhgfs", RUN+="/bin/mount /mnt/hgfs"
```

Then when the module is inserted the system mounts the shared folders and everyone seems happy.

I would have preferred to have the gnome desktop auto-mount the shared folders (as if they were a CD, or USB flash drive) but I haven't yet figured out how to configure that. If anyone can point me in the right direction, please do so.

Perhaps I missed some configuration or setup instructions for how to install open-vm-tools, though.  Is there a "proper" way to configure open-vm-tools? I'd also like to have it remember the size of the desktop - anyone have pointers on doing that?

In case it matters: I am using open-vm-tools 2010.06.16-268169-3ubuntu1 (maverick)

---

### Post by SRamsesIV on 2010-10-25
So I found a solution to my not being able to configure a default custom resolution. Again, it would be great if anyone had any better information than this. Please respond with your best ideas for how I could do anything better.

In order to solve the default custom resolution problem I first created a xorg.conf file (using 'Xorg -configure' in a console login). Within that file I merged the following:

```

Section "Screen"
   # ...
   SubSection "Display"
      # ...
      Depth 24
      Virtual 1808 1130
      Modes "1808x1130@60"
   EndSubSection
EndSection

```

Now with those two new lines added ('Virtual' and 'Modes') my display comes up with 1808x1130 listed as one of the standard resolutions and I can set it as the default resolution using the 'Make Default' button. Then whenever I login I get my custom resolution back without any complaints from the system or having to tweak it again using the mouse.

---

### Post by ersk99 on 2011-01-06
In answer to your first post, what I did was add the mount and umount to /etc/init.d/open-vm-tools script. For example the start and stop cases looks like the following:
 
```
 
case "${1}" in
   start)
      # Check if we're running inside VMWare
      exit_if_not_in_vm
      log_daemon_msg "Loading open-vm-tools modules"
      log_progress_msg "vmhgfs"; modprobe vmhgfs
      log_progress_msg "vmsync"; modprobe vmsync
      log_end_msg 0
      log_daemon_msg "Mounting hgfs"
      mount -t vmhgfs .host:/ /mnt/hgfs
      log_end_msg 0
      log_daemon_msg "Starting open-vm daemon" "vmtoolsd"
      /usr/bin/vmtoolsd --background /var/run/vmtoolsd.pid
      log_end_msg 0
      ;;
   stop)
      # Check if we're running inside VMWare
      exit_if_not_in_vm
      log_daemon_msg "Stopping open-vm guest daemon" "vmtoolsd"
      if [ -f /var/run/vmtoolsd.pid ]
      then
         kill $(cat /var/run/vmtoolsd.pid)
      fi
      log_end_msg 0
      log_daemon_msg "Unmounting hgfs"
      umount /mnt/hgfs
      log_end_msg 0
 
      log_daemon_msg "Removing open-vm-tools modules"
      log_progress_msg "vmhgfs"; modprobe -r vmhgfs
      log_progress_msg "vmsync"; modprobe -r vmsync
      log_end_msg 0
      ;;

```
 
This works for me.

---

### Post by pilgrim333 on 2012-01-06
Hi Ersk99,

   I copied your file and put it in /etc/init.d/open-vm-tools but when I restart ubuntu, /mnt/hgfs didn't get mounted.  Is there something else I need to do to get your open-vm-tools to run on boot up?

Thanks alot!

> **ersk99 said:**
> In answer to your first post, what I did was add the mount and umount to /etc/init.d/open-vm-tools script. For example the start and stop cases looks like the following:
 
```
 
case "${1}" in
   start)
      # Check if we're running inside VMWare
      exit_if_not_in_vm
      log_daemon_msg "Loading open-vm-tools modules"
      log_progress_msg "vmhgfs"; modprobe vmhgfs
      log_progress_msg "vmsync"; modprobe vmsync
      log_end_msg 0
      log_daemon_msg "Mounting hgfs"
      mount -t vmhgfs .host:/ /mnt/hgfs
      log_end_msg 0
      log_daemon_msg "Starting open-vm daemon" "vmtoolsd"
      /usr/bin/vmtoolsd --background /var/run/vmtoolsd.pid
      log_end_msg 0
      ;;
   stop)
      # Check if we're running inside VMWare
      exit_if_not_in_vm
      log_daemon_msg "Stopping open-vm guest daemon" "vmtoolsd"
      if [ -f /var/run/vmtoolsd.pid ]
      then
         kill $(cat /var/run/vmtoolsd.pid)
      fi
      log_end_msg 0
      log_daemon_msg "Unmounting hgfs"
      umount /mnt/hgfs
      log_end_msg 0
 
      log_daemon_msg "Removing open-vm-tools modules"
      log_progress_msg "vmhgfs"; modprobe -r vmhgfs
      log_progress_msg "vmsync"; modprobe -r vmsync
      log_end_msg 0
      ;;

```This works for me.

---

### Post by John Peterson on 2012-02-07
Thanks!

Why isn't this added automatically in Ubuntu 11.10?

---

### Post by mlevin2 on 2012-03-22
> **pilgrim333 said:**
> Hi Ersk99,

   I copied your file and put it in /etc/init.d/open-vm-tools but when I restart ubuntu, /mnt/hgfs didn't get mounted.  Is there something else I need to do to get your open-vm-tools to run on boot up?

Thanks alot!

You need to create the directory first. Otherwise the mount will fail.

```
sudo mkdir /mnt/hgfs
```

---

