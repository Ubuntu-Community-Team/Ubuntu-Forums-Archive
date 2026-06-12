---
title: "FTP or Samba?"
date: 2006-06-16
forum: Server Platforms
---

### Post by Enigmatic on 2006-06-16
I want to have some files on a few machines shared, and I'm wondering what would be easiest and more efficient to setup - either Samba or FTP.

I would need to have easy synchronization capability, and different user permissions and respective shares. 

I assume that both can do this, but I'd like some feedback on which would be a better choice. I'm considering FTP slightly more at this point.

---

### Post by rbalfour on 2006-06-16
I am guessing, the "other" pcs, some will be Windows...
Go with Samba..if not and the other PCs are Linux, go with sshfs...

---

### Post by blkish on 2006-06-17
it largely depends on what you're trying to achieve. 

if they are windows pcs, samba is a sound choice (not sure of the level of 'synchronisation' available - do you mean enabling 'offline access' as available on win2k server?)

ftp is a very reliable way of moving data around (SFTP or FTP over SSH if your network isn't private)

have a good day :)

blkish

---

### Post by Enigmatic on 2006-06-17
There are two Windows PCs and another Linux PC. FTP works nicely, but I want to sync my Evolution mailboxes between the laptop and desktop as well. Would I need to have SAMBA for that? 

SAMBA would be much more straightforward for a simple network share, wouldn't it? It's just more annoying to setup I'm finding, since I can't get SWAT running.

---

### Post by blkish on 2006-06-18
it sounds like samba would be your preffered option here.

i would recommend you look into webmin - a system administration interface - which will make the setup and maintenance of your samba sharees/server easier.

it's (sadly) no longer available as a debian/ubuntu package, but the downloadable version from [www.webmin.com](www.webmin.com) installs easily and works fine on dapper.

you might also like to try out the 'Stress Free Tiger' theme for webmin from [http://www.stress-free.co.nz/content/view/141/2/](http://www.stress-free.co.nz/content/view/141/2/)  -  much nicer than the default

blkish

---

