---
title: "Custom Backup Server - Issues with Mounting"
date: 2011-10-04
forum: Server Platforms
---

### Post by Orion2014 on 2011-10-04
So I have a box that is a custom backup server. It used to run Ubuntu 10 LTS but its now running 11. 

Basically Ubuntu sits on a 2TB HDD with a Gnome share setup where all my windows servers dump their backup files every night. 

All total, the backup usually comes out to about 100GB every night. My windows server 2008 machines are set up to erase the backup from the night before. I then have two scripts running through the day on the server. 

One copies last nights backup onto a 500GB USB external HDD to come home with me that night. I bring the HD in every morning and plug it back in, and the script is set to run at around 9:30 am. 

I also have a script that I call my "Mirror" script, which mirrors the files in my backup share onto a hot-swap 1TB SATA drive. This hard drive gets swapped out once a month, and I use this as my monthly drive. 

Before on Ubuntu 10, I never had any issues, but now for some reason when I plug in the USB drive, it does not mount it back to the same mount point as before, its supposed to mount to /media/river, but it mounts it to /media/river_

Any ideas, what can I do to make this thing mount correctly?

---

