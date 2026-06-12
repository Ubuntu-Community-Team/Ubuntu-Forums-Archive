---
title: "Udisks automounting USB"
date: 2012-08-31
forum: Server Platforms
---

### Post by Thierry51 on 2012-08-31
Hi everyone, 

I'm running on my PandaBoard an ubuntu-server and just noticed that usb keys are not mounted automatically, i installed then packages udisks and udisks-glue, but the problem persists.

i've to launch manually the udisks --mount /device command or udisks-glue after plugging the device to get in mounted! i must also be on root otherwise mounting fails ...

Have you an idea please?

Thanks!

---

### Post by TREESofRIGHTEOUSNESS on 2013-01-01
Hi I am looking around trying to figure out udisks-glue myself, and came across your post.  I am sorry you haven't gotten a reply yet... I found this page and it might help
[http://www.raspberrypi.org/phpBB3/viewtopic.php?f=26&t=24637](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=26&t=24637)
it is for the raspberry pi, but the info is suitable for any arch.
I'll post the relevant post here
```


So i finally got this to work.. And heres how for others to see:

I know, theres probably another way, but at least this works pretty well for me 

From the beginning:
sudo apt-get update
sudo apt-get install udisks-glue
sudo nano /etc/rc.local
And then add the following two lines between the description and "exit 0"
sudo udisks --unmount /dev/sda1
sudo udisks --mount /dev/sda1 --mount-options umask=0000

The above works perfectly.. Everyone has read/write permissions for the drive automaticly. I can even attach different harddrives and just reboot the Pi and they will have read/write permissions too. And it works over network from a windows PC too.

I know this might not be the best way to do it, but it works just as i want it too, and i thought that maybe others would want it too.

```

I don't think the sudo command is needed in the rc.local file, though...

---

