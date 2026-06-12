---
title: "How to use usb-device on ubuntu server?"
date: 2011-08-18
forum: Server Platforms
---

### Post by Tombellens on 2011-08-18
Hello , 
i would like to get data from an usb-device and display this data on a webservice with ubuntu server.
How can  I do this ?
Greets ,

---

### Post by dave01945 on 2011-08-18
i know how you can view the files on the usb not sure about the web service though can you be more specific

to use the usb it needs to be mounted

```
blkid    ##this will list all the storage devices connected
mkdir /mnt/usb    ## this is were it will be mounted
mount /dev/xxx /mnt/usb   ## this will mount it replace xxx with your device name that you found with blkid
```


hope this helps

---

### Post by PierreRobiquet on 2011-08-18
If it's going to be permanently attached to the system you might want to add an entry to /etc/fstab to ensure it is mounted on every boot.

---

### Post by SeijiSensei on 2011-08-18
You should also use the UUID method of identifying USB devices since they may not have a fixed device identifier.

You'll see that /etc/fstab uses UUID identifiers by default.  Just run "sudo blkid" as mentioned above to see the UUID associated with your USB filesystem.

As for displaying the files with a webserver, you should start with this guide: [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

---

### Post by Tombellens on 2011-08-18
[LEFT]Hello , 
thanks all for your fast answers :)
I think this will be usefull and I will let you know if it works . 
Thanks!

[/LEFT]

---

