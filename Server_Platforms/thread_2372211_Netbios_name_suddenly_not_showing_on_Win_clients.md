---
title: "Netbios name suddenly not showing on Win clients"
date: 2017-09-22
forum: Server Platforms
---

### Post by keith30 on 2017-09-22
We have Ubuntu 16.04 acting as a server in our small office. It is basically just a file server to the client PC's and is set up with WINS. It has been behaving fine until earlier this week when it no longer seems to be broadcasting its name to the client PC's. We can still reach our files by entering \\server or the IP into the address bar of Windows Explorer but it doesn't show up in Network Neighbourhood. Net view command comes back with a Windows system error 6118 and when I run nbtstat -a server it lists the server but doesn't have a MBrowse entry. Some help would be great thanks.

---

### Post by SeijiSensei on 2017-09-22
Is nmbd running as well as smbd?

Do you have a "netbios name" parameter set in smb.conf?

Is the server configured to be a local master?  If not, give that a try.

---

### Post by keith30 on 2017-09-25
Thanks for your comments. Both nmbd and smbd are running and the netbios name is in the .conf.  Other settings such as local master are also there. It was working fine a week ago and nothing has changed in any conf files so I'm a bit perplexed.

---

### Post by SeijiSensei on 2017-09-25
Do you see anything unusual in log.nmbd?

---

### Post by keith30 on 2017-09-26
Small update. I temporarily managed to get it showing again in Windows Network Neighbourhood by restarting nmbd. However, overnight it dropped again. I will investigate log.nmbd.

---

### Post by keith30 on 2017-09-28
Delving a bit deeper slowly I tried sudo smbstatus. This gives a few lines response but does refer to ignoring unknown parameter "cups option". Might this be of any relevence? lib/param/loadparm.c:1617 (lpcfg_do_global_parameter)

I also ran systemctl status nmbd which reports the Samba name server SERVER has stopped being a local master browser source3/nmbd/nmbd_become_lmb.c:418 failed to register name WORKGROUP<1d> on subnet 192.168.1.114 and also failed to register/refresh name WORKGROUP<1d> on subnet 192.168.1.114

Any thought or advice appreciated thanks

---

### Post by keith30 on 2017-09-29
Resolved! After finding and reading the log.nmbd file I found that an old XP pc in the office which is only used for short periods of time was electing itself as master browser. I have no idea why it suddenly decided to do this, but I have now put it in its place.

---

### Post by SeijiSensei on 2017-09-29
Glad to see you figured it out!  I was running out of ideas.

You might want to mark the thread [SOLVED].  You can do this from the Thread Tools drop-down at the top of this page.

---

