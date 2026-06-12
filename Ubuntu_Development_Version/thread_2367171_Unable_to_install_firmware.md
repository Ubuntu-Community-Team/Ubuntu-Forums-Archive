---
title: "Unable to install firmware"
date: 2017-07-26
forum: Ubuntu Development Version
---

### Post by terry_gardener on 2017-07-26
I think i have figured out why i am having so much problems loading the desktop in X11 or wayland, prev posts saying the it is working for them, got me thinking. 

the thing is that nvidia gtx 900 series and above need digitally signed firmware which makes it non free software. i tested this by installing the nvidia-375 drivers not the nvidia-current drivers as these are too old (304 drivers) and i only had one option at logon screen i logged in and it worked as expected. i have downloaded the firmware files from git for my card but don't know how to install then when. 

it is a tar.gz file, i have extracted it. 
cd into the folder and the typed ./configure and got message permission required,
so tried sudo ./configure and got error command not found. 
tryed sudo /bin/bash ./configure and nothing happened 

please can you tell me how to install this firmware so i can test it. 

link to the tar.gz is 
[http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git]("http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git")

phoronix page 
[https://www.phoronix.com/scan.php?page=news_item&px=GTX900-Easy-Nouveau-Setup]("https://www.phoronix.com/scan.php?page=news_item&px=GTX900-Easy-Nouveau-Setup")

---

### Post by terry_gardener on 2017-07-26
when i use sudo make get message there is nothing to do. 
when i use sudo make install get find $(DESTDIR)$(FIRMWAREDIR) \( -name 'WHENCE' -or -name 'LICENSE.*' -or \
		-name 'LICENCE.*' \) -exec rm -- {} \;
then nothing happens.

---

### Post by cariboo on 2017-07-26
This had nothing to do with the thread it was in, moved to a thread of it's own.

---

