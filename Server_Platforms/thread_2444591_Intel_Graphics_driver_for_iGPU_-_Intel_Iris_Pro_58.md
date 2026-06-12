---
title: "Intel Graphics driver for iGPU - Intel Iris Pro 580"
date: 2020-06-01
forum: Server Platforms
---

### Post by exsor65 on 2020-06-01
Hello everyone, 

Linux noobie trying to find out how to install Intel Graphics driver or to find out if there installed. 

Ubuntu Server 20.04 LTS - VM running on xcp-ng with GPU pass though  
Intel Iris Pro 580 iGPU

Many thanks in advance. :-)

---

### Post by deadflowr on 2020-06-01
intel drivers come ready made and installed.
But useless on a server unless you have X or wayland programs or display servers to utilize the drivers.
Ubuntu servers are typically command line systems without any display servers running.

---

### Post by exsor65 on 2020-06-02
Thank you Deadflowr, that make sense. I'm going to try installing a  desktop environment. in my case I'm trying to get plex to do video  transcoding.

---

### Post by exsor65 on 2020-06-03
Reporting back, installing a desktop environment did the trick. :-)

---

### Post by slickymaster on 2020-06-03
*Thread moved to **Server Platforms**.*

---

