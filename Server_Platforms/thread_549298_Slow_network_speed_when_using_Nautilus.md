---
title: "Slow network speed when using Nautilus"
date: 2007-09-12
forum: Server Platforms
---

### Post by fradav4 on 2007-09-12
When I access a samba share from Ubuntu to Ubuntu my transfer speed over my gigabit network is only about 6Mb/s.  Accessing the samba share from Windows (client) to Ubuntu (server) my transfer speed was about 40Mb/s.  So then I tried Ubuntu (client) to Windows (server) and my speed was back down to about 6Mb/s.  At this point I figured it was something wrong with Nautilus.  I used the command smbget from Ubuntu to Ubuntu and my speed was back up to about 40Mb/s.  For the sake of trying it I put a large file on my web server (Ubuntu) and was able to grab the file from both Ubuntu and Windows at around 40Mb/s.  

So it seems that when I try to drag and drop from Nautilus my transfer speed becomes almost 7 times slower!  

After searching this forum and doing a few google searches, it seems like I am not the only one with this issue.  Is there a known fix?  I love Ubuntu but this could be a deal breaker if I can't find a workaround.  We do massive amounts of media sharing between computers so I have to find a solution.  Thanks for any input.

---

### Post by cdenley on 2007-09-12
Try installing smbfs, then mount it as cifs using /sbin/mount.cifs or by adding an line for it in /etc/fstab. I think cifs is faster, so maybe smbget uses cifs but nautilus uses smb. I'm not really sure.

I just tested this, and mounting a share as cifs seems to work twice as fast, which is about the same as smbget for me.

```

sudo apt-get install smbfs
sudo mkdir /media/myshare
sudo mount.cifs //myserver/myshare /media/myshare -o uid=1000,user=username,pass=password
```

---

### Post by reckless2k2 on 2007-09-12
yeah i learned this in class that drag and drop gui stuff is much slower. i'm sorry i don't remember why. it is not just restricted to linux either. windows has the same issues.

---

