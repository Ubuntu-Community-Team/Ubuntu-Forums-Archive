---
title: "Nas?"
date: 2017-11-18
forum: Server Platforms
---

### Post by gb6903 on 2017-11-18
Forgive me if this isn't in the correct section.

I have multiple external USB drives that I would like to be available over my LAN, Is the item I'm looking for some kind of NAS? Please advise.

---

### Post by darkod on 2017-11-18
Yes, you will have to install a server that will have all those disks attached and can share them to other devices on the network. But usb hdd will not have very good speed shared like that, usb is in general very slow for regular data transfers.

---

### Post by gb6903 on 2017-11-18
> **darkod said:**
> Yes, you will have to install a server that will have all those disks attached and can share them to other devices on the network. But usb hdd will not have very good speed shared like that, usb is in general very slow for regular data transfers.

Well, at least they're all either 3.0 or SSD. So I would need something like this: [https://www.amazon.com/gp/product/B075N1BYWX/ref=s9_acsd_newrz_hd_bw_buNOX_c_x_w?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=merchandised-search-3&pf_rd_r=JNG7PPSMAJEVDW39XRM8&pf_rd_t=101&pf_rd_p=05da1ecf-d1bf-536d-a13e-0943e329ff4d&pf_rd_i=13436301](https://www.amazon.com/gp/product/B075N1BYWX/ref=s9_acsd_newrz_hd_bw_buNOX_c_x_w?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=merchandised-search-3&pf_rd_r=JNG7PPSMAJEVDW39XRM8&pf_rd_t=101&pf_rd_p=05da1ecf-d1bf-536d-a13e-0943e329ff4d&pf_rd_i=13436301)  ?

Maybe it would be easier just to make a server on my PC to stream the music,

---

### Post by gb6903 on 2017-11-18
But now with something like [this]("https://www.amazon.com/Cloud-Personal-Network-Attached-Storage/dp/B00EVVGAD0/ref=lp_13436301_1_4?s=pc&ie=UTF8&qid=1510993824&sr=1-4&th=1"), would I still be able to plug my external drives into it?

---

### Post by LHammonds on 2017-11-18
Why complicate it?  Why not just connect all the USB drives to a single machine (Raspberry Pi?), mount all of them to /mnt/usb/1, /mnt/usb/2, etc. and then setup a samba share to /mnt/usb

LHammonds

---

