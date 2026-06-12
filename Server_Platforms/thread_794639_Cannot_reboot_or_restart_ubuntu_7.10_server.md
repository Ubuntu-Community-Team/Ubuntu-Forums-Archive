---
title: "Cannot reboot or restart ubuntu 7.10 server"
date: 2008-05-14
forum: Server Platforms
---

### Post by Collino on 2008-05-14
Hello all......

Bear with me as this is quite a long story

Basically I cannot perform a reboot on my server - to which I only have ssh access as its a dedicated server rented from 123-serv.

More info on it can be found here: [http://ubuntuforums.org/showthread.php?t=708617](http://ubuntuforums.org/showthread.php?t=708617)

It came supplied as 6.06 LTS but after having various issues, I thought an upgrade to 7.10 would fix some problems. It did, but some others still remained. I'm still under the impression that I am in a jailed environment, despite asking for "root" access from the support team. Problems experienced included ftp issues, denyhosts blocking me as it wasn't set up properly. However I have seemingly overcome these issues - its not perfect but its fine - running a standard LAMP with vhosts on apache. Everything was going well, until now

After having done some development work on my local machine, I went to upload everything to the server which all went swimmingly and everything seemed to work.

As a bit of general housekeeping I decided to do a reboot of the machine, however on trying to run: "shutdown -r now" i get the following:

```
root@ds3478:/# shutdown -r now

Broadcast message from root@ds3478
        (/dev/pts/1) at 1:47 ...

The system is going down for reboot NOW!
shutdown: Unable to send message: Connection refused
```

Similar result with reboot and init 6. 

What is likely to be stopping the reboot? - anything I can check

Thanks

---

### Post by cdtech on 2008-05-15
update-initramfs -u -k `uname -r`

After having installed a new kernel (or an update version of it) or also other boot related stuff it might be necessary to rebuild the initial ramdisk using the following command in order to get the changes to take effect.

Maybe this might help, won't hurt.

---

### Post by Collino on 2008-05-15
Thanks for your reply, I tried "update-initramfs -u -k `uname -r`"

and it came back with:

```
update-initramfs: Generating /boot/initrd.img-2.6.22-8-server
Cannot find /lib/modules/2.6.22-8-server
update-initramfs: failed for /boot/initrd.img-2.6.22-8-server
```

On looking it seems there is nothing at all in /lib/modules/

What next?

---

