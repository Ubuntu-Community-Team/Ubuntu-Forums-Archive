---
title: "Has anyone installed Ubuntu Server 18.04.1 LTS on Ryzen 5 2400G?"
date: 2018-08-30
forum: Server Platforms
---

### Post by darkod on 2018-08-30
Hi all,

I was wondering if anyone did a clean install of 18.04 (18.04.1) server on Ryzen 5 2400G? I have seen some comment that as a "new" CPU on the market it has some issues with linux that might take time to resolve. However, most of the quick search results were returning discussions mainly about the GUI, video drivers, etc... I don't put any GUI on the server, in my case I don't care much about video as long as it has basic video for the installation process. Later it will be headless anyway.

And I will be using the good old -server- ISO, not the new -live-server- ISO.

My hope is also to make ECC working which might be a challenge not only because ubuntu, but also because it seems brands advertise boards as ECC but did not really go into details to really implement the design as it should be.

Since there is limited choice of AM4 ECC boards I went with Gigabyte AX370-Gaming 5, paired with the 2400G and Kingston Server Premier ECC ram (Micron die). I am perfectly aware this is not server grade HW and would never recommend it for a business, but with limited budget and for a home server I decided to give it a shot.

I should be able to try all of this soon...

---

### Post by oldfred on 2018-08-30
Hi, darkod,

I do not have a server, so do not know anything specific. But since many issues are common, I try to save some of those in my notes.

On Ryzen I have this, which is desktop, but it seems you would need a newer kernel like 4.17.
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1)

I recently rebooted into my 18.10 install and it updated to 4.17kernel. I do prefer LTS, but if you need newer kernel 18.10 may be a short term easier way to get it. Otherwise you add the ppa like phoronix does.

---

