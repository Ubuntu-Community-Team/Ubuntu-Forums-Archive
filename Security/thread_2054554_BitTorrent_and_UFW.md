---
title: "BitTorrent and UFW"
date: 2012-09-07
forum: Security
---

### Post by Kopkins on 2012-09-07
Hello,

I'm using GUFW to configure the settings. 

I can't seem to be able to get torrents to work. Both Deluge and Transmission can't get through the firewall.

For deluge, I have ports 6881:6891 for incoming connections. I have outgoing set to use random ports. 

In GUFW I used the preconfigured settings to try to allow torrents. I did allow, out, application, deluge. 

However, I still can't make connections while the firewall is up. 

Temporarily I set allow, in, application, deluge. But it didn't change the application's behavior. Still can't get through.

With transmission, incoming connection port is 6881. Same deal, no connections are being made. 

What am I doing wrong?

Thanks,
Kopkins

---

### Post by cariboo on 2012-09-07
Are you behind a router? If so you have to set up port forwarding for the ports you've opened in your firewall.

---

