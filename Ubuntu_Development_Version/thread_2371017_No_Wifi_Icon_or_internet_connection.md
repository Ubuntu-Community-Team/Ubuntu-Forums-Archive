---
title: "No Wifi Icon or internet connection"
date: 2017-09-09
forum: Ubuntu Development Version
---

### Post by joseph123321123 on 2017-09-09
Hi, 

So I just upgraded my distro and am now unable to connect to the internet. There is no wifi icon in the menu and nothing in network manager.

I tried 'sudo service network-manager restart', that didn't do anything though.

I also looked at software and updates - additional drivers, wasn't anything there though.

Any ideas?

Thanks.

---

### Post by wildmanne39 on 2017-09-09
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by jeremy31 on 2017-09-09
*Thread moved to **Networking & Wireless**.*

---

### Post by joseph123321123 on 2017-09-09
Hi,

Here is the link to the output:

[https://pastebin.com/DrX3jWuu](https://pastebin.com/DrX3jWuu)

Thanks.

---

### Post by wildmanne39 on 2017-09-09
Do you know that you are using the developmental version of Ubuntu, it should only be used by people reporting bugs, let me know if you want to keep using it before we continue if so I will move it to the developmental forum.

---

### Post by joseph123321123 on 2017-09-09
Oh yeah, I'm happy with the dev version. I've been using it for a few months now without any problems.

Basically what happened was my laptop froze whilst installing updates. I then restarted it, however it didn't boot properly so i was going to do a clean install, however I saw an option to upgrade when I booted from the live usb. Most of the settings etc are as before, however the wifi icon isn't there and I cant connect to the internet without an ethernet cable. I think there may also be something wrong with the bluetooth though I haven't looked it at yet.

---

### Post by wildmanne39 on 2017-09-09
*Thread moved to **Ubuntu Development Version**.*

---

### Post by wildmanne39 on 2017-09-09
Try:
```
sudo apt install --reinstall linux-headers-$(uname sudo-r) build-essential
```
Reboot

---

### Post by joseph123321123 on 2017-09-09
Thank you so much!

That's sorted it

---

### Post by wildmanne39 on 2017-09-09
Your welcome glad it is working.:)

---

### Post by cariboo on 2018-07-28
Thread closed.

---

