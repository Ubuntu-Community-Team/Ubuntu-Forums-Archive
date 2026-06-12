---
title: "Ubuntu Server 22.04"
date: 2023-03-07
forum: Server Platforms
---

### Post by charmand3r on 2023-03-07
Hi there everyone i recently installed ubuntu server on an older laptop for extra storage i have had no issues ssh into it or anything like that i was just wondering if it is at all possible to access media on the server and stream it on my xbox one instead of copying x movie or tv show to a usb and doing it that way 

Many thanks 
Charmand3r

---

### Post by MAFoElffen on 2023-03-08
I do Plex Server from my Ubuntu Server and stream it through a Plex App on my XBox.

---

### Post by ActionParsnip on 2023-03-08
If you can SSH to the server then you have an SFTP server by default. Secure and no additional config needed

---

### Post by SeijiSensei on 2023-03-08
I run the bog-simple minidlna server. All you need to do is edit the configuration file to point to your media directories, and off you go. All my devices see it including TVs, smartphones, and my PS4.

You just need to edit (as root with sudo) the file /etc/minidlna.conf. Find the lines that begin with "media_dir" and have them point to the various directories on the server where the files are stored. You can discriminate among video, audio, and pictures.

---

### Post by slickymaster on 2023-03-08
*Thread moved to **Server Platforms**.*

---

