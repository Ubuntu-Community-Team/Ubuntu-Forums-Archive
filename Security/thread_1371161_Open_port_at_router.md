---
title: "Open port at router"
date: 2010-01-03
forum: Security
---

### Post by ozzyprv on 2010-01-03
I recently installed rTorrent.
I realized today that I never forwarded any port on my router (a WRT54G running DD-WRT build v24-sp2 mega.

How is this possible? 

I thought that ALL the ports were closed by default by my router.

---

### Post by HermanAB on 2010-01-03
The initial connection is made from the inside out.  You may get better bandwidth if you forward some ports, but modern bittorrent clients are quite good at getting going regardless of your configuration.

---

### Post by lovinglinux on 2010-01-03
As already explained in the previous post, if you do not open a port you are still able to download because your client will still request connections to other users. On big swarms, the download speed is not affected that much.

Additionally, most BitTorrent clients offer UPnP feature, which automatically opens the necessary ports in the router (if enabled on both).

For additional explanations on how BitTorrent works and how to configure it, see [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by ozzyprv on 2010-01-03
Thank you folks.

---

