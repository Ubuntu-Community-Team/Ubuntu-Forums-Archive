---
title: "Help with Samba, its slow but SFTP isn't. Why?"
date: 2016-03-13
forum: Server Platforms
---

### Post by JamesDonaldChilds on 2016-03-13
Hi, I have a server set up for media and I have Samba set up to easily move new files to the server. The problem I am having is Samba transfers never break 2MB/S where SFTP easily goes over 20MB/s. I've googled and found a couple of configurations I am supposed to add to smb.conf, which I have and did restart smbd and nmbd, but I still get terrible transfer speeds with Samba, any advice?

---

### Post by wellsilva-email on 2016-03-15
> **JamesDonaldChilds said:**
> Hi, I have a server set up for media and I have Samba set up to easily move new files to the server. The problem I am having is Samba transfers never break 2MB/S where SFTP easily goes over 20MB/s. I've googled and found a couple of configurations I am supposed to add to smb.conf, which I have and did restart smbd and nmbd, but I still get terrible transfer speeds with Samba, any advice?

Hi James, 

Try the configs  in this [link]("http://www.eggplant.pro/blog/faster-samba-smb-cifs-share-performance/") in your samba configuration file.

Hope to have helped, let us know how it worked out for you.

---

### Post by lukeiamyourfather on 2016-03-15
What is the underlying storage and what are the specs of the machine? It might be async versus sync writes.

---

