---
title: "MiniDlna Folder Structure"
date: 2013-12-22
forum: Server Platforms
---

### Post by adam17 on 2013-12-22
Hi, 

I am using Ubuntu 12.04 LTS as a server and Minidlna as upnp software. I have different locations where I have video coming from. e.g HD Video, TV Shows, Regular Videos. When accessing the sever everything is shown together under the Video folder. Is there a way to separate this so when you browse the folders it shows HD Video, TV Shows & Video as a sub directory?

If not is there a different UPNP program that will do this?

Thanks 

Adam

---

### Post by adam17 on 2013-12-22
Hi All, 

I managed to find a solution to this problem and thought I would share.

First I created a folder named MyDlnaShares and inside created symbolic links to the locations of my media. 

Then using sudo nano minidlna.conf I added the MyDlnaShares folder to the scanned folders section (instead of each folder individually) 

This then shows the folder structure I was after.

---

### Post by kashifsmalik on 2014-02-27
Thanks for posting back the solution you came up with. I found it helpful.

> **adam17 said:**
> Hi All, 

I managed to find a solution to this problem and thought I would share.

First I created a folder named MyDlnaShares and inside created symbolic links to the locations of my media. 

Then using sudo nano minidlna.conf I added the MyDlnaShares folder to the scanned folders section (instead of each folder individually) 

This then shows the folder structure I was after.

---

