---
title: "Help With Truecrypt Script"
date: 2009-11-30
forum: Security
---

### Post by HalfEmptyHero on 2009-11-30
I'm trying to write a bash script to run at startup that will automatically mount a truecrypt volume I have using a keyfile. The plan is to use an SD card to keep a keyfile that I only keep in the computer when I am using it. I am using the following command, which does work how I want it.

```
truecrypt -t /dev/sda2 /mnt/Private --password=""  -k "/media/PORTABLE/.prkyrc" --protect-hidden=no
```


I don't know much bash, and what I want to do is to have the script check first if /media/PORTABLE is mounted, and if not check if the SD card is present (should be at /dev/mmcblk0) and mount it if it is. Then, check if the truecrypt volume is mounted, and if it isn't then mount it. Obviously if it is already mounted it will do nothing, and if the SD card is not present, do nothing as well.

Anyone want to help me out?

---

### Post by sobol_rz on 2009-11-30
touch file_name
mcedit file_name
#!/bin/bash
mkdir /media/PORTABLE
mount /dev/mmcblk0 /media/PORTABLE
truecrypt -t /dev/sda2 /mnt/Private --password=""  -k "/media/PORTABLE/.prkyrc" --protect-hidden=no

f10

update-rc.d file_name defaults 99 - read some about adding scriptsin ubuntu/debian ;]
MAYBE... never do this on my machine xD sorry :)

regards ;]

---

