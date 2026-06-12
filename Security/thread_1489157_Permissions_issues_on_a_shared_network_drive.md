---
title: "Permissions issues on a shared network drive"
date: 2010-05-20
forum: Security
---

### Post by thumbmaster021 on 2010-05-20
Hello Ubuntu forums!

I have recently set up a home server using Ubuntu Server with TONS of cheap hard drive space thanks to LVM! Awesome! :)

I have also set up a bittorrent service using the Deluge bittorent(just the daemon) and used various online articles in order to set up an appropriate startup script.

I am accessing the fileshare directory(which I have put in /home/Shares) from different services, such as nfs and samba, depending on the client OS.

Now, the problem is, with all of these different ways of accessing, manipulating, and adding all these files from my local network, the files and folders permissions CONSTANTLY get to an incompatible state, in which one method can't access the files created using a different method, or even the files created with the bittorent client(which downloads its stuff into a folder in /home/Shares). I have to resort to constantly running the "sudo chmod -R a+rw /home/Shares"(which I am perfectly fine having all the files with that permission) in order to get everything working as it should again.

I'm wondering, is there any way to set up my Shares folder so that everything created inside it(no matter where it originated) will be accessible to everything else?

And just to note, everything is only accessible through LAN, and everyone on my home LAN network is trusted.

Thanks for any help in advanced!

---

