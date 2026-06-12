---
title: "Problem to access share by symbol link"
date: 2010-03-31
forum: Server Platforms
---

### Post by marslin on 2010-03-31
Ubuntu server 8.04
Samba version 3.0.28a

Config:
1) I created 2 shares in Samba, one is "/home/aaa" and the other is "/home/bbb". Both have the same owner, say "jack", with permission 775
2) I created one link named "pubshare" in "aaa" pointing to "bbb". "ln -s /home/bbb pubshare"
 
Problem:
I connected to aaa from a Winxp client with account "jack" and access pubshare, (say cd pubshare), it prompts "access denied"
 
Experiment I've done
1) login local machine with account jack, cd /home/aaa, then cd pubshare. It works fine. (So I believe link works fine and permission of bbb is correct)
2) connect directly to /home/bbb with account jack from the Winxp client. It works fine too. (So I believe the samba config is correct)
3) I did not face this problem until I used "apt-get ugrade" several days ago.
 
Any suggestion?
 
Thank you in advance.

---

### Post by capscrew on 2010-04-01
> **marslin said:**
> Ubuntu server 8.04
Samba version 3.0.28a

Config:
1) I created 2 shares in Samba, one is "/home/aaa" and the other is "/home/bbb". Both have the same owner, say "jack", with permission 775
2) I created one link named "pubshare" in "aaa" pointing to "bbb". "ln -s /home/bbb pubshare"
 
Problem:
I connected to aaa from a Winxp client with account "jack" and access pubshare, (say cd pubshare), it prompts "access denied"
 
Experiment I've done
1) login local machine with account jack, cd /home/aaa, then cd pubshare. It works fine. (So I believe link works fine and permission of bbb is correct)
2) connect directly to /home/bbb with account jack from the Winxp client. It works fine too. (So I believe the samba config is correct)
3) I did not face this problem until I used "apt-get ugrade" several days ago.
 
Any suggestion?
 
Thank you in advance.

I believe this is due to an update.  See [**_[COLOR="Blue"]here [/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1440993")for info on symlinks.

---

### Post by marslin on 2010-04-01
Cool. By adding following in smb.conf and restart samba and issue is gone.
 
Thanks a lot !!:popcorn:
 
[global]
wide links = yes
unix extensions = no

---

