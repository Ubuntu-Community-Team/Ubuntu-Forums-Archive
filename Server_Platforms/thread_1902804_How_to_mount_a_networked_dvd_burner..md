---
title: "How to mount a networked dvd burner."
date: 2011-12-31
forum: Server Platforms
---

### Post by b2customrods on 2011-12-31
Im wanting to burn a dvd movie that I have on my Ubuntu server. The problem is that I dont have a burner on it. I do have a burner on a win 7 machine that I have shared over the network as drive "j" so the share on the network looks like //amd_x6/j

I mounted the dvd to /mnt/cdrom using 

sudo mount -t cifs //192.168.x.x/j /mnt/cdrom -o user=*username*

If I put a cd in the drive I can read it using ls to list the files. 

I tried using this command to burn a dvd movie.

sudo growisofs -spedd=2 -dvd-compat -Z /mnt/cdrom/ -dvd-video -V "The Thing" /home/beau/media/video/the_thing_2011/VIDEO_TS/ 

I get this

:-( unable to open64("/mnt/cdrom/",O_RDWR): Is a directory

any ideas as to how to remedy this?

Thanks

---

### Post by mapreri on 2012-01-01
the easiest way is copy the file on the win/ machine and there burn the cd.. 

> unable to open64("/mnt/cdrom/",O_RDWR): Is a directory sure :) you have to specify a device, not a mount point...

---

### Post by rsvancara on 2012-01-01
Can you make an iso out of the movie on windows and then copy it to Linux and mount it as a loop back file system?

---

### Post by Jive Turkey on 2012-01-02
Are you trying to use the burning device on the windows computer from the ubuntu server?  That sounds a little backwards, reading might work but burning will likely fail.  It would make more sense to access the source file/disk on the server with a burning application on the windows computer with the dvd burning device.

---

