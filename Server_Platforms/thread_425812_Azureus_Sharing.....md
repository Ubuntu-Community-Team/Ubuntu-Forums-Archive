---
title: "Azureus Sharing....?"
date: 2007-04-27
forum: Server Platforms
---

### Post by Reever-6 on 2007-04-27
I am fairly new to the ubuntu society, I would like to soon be able to replace my windows desktop aside from gaming. Basically, what I am trying to do is download .torrent files to my Linux box with my XP machine. I am able to access the drive I am saving them to (250GB Seagate), but I cannot save them directly to the share from Firefox. I would really like to alleviate this problem. Azureus will be autoloading any new torrents in said foler. I have set the folder to have no password and that does not appear to work, I am just really not sure where to go from here.


Thanks in advance for any support.

---

### Post by jiminycricket on 2007-04-28
Can you access anytthing on the Ubuntu network shares?  Have you enabled an account using smbpasswd?  [https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88](https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88)

Also, if you want something lighter than Azureus, rTorrent is a command-line bittorrent client that will auto-monitor a folder for .torrents like you want.  Then you use ssh to monitor it.

---

### Post by Reever-6 on 2007-04-28
i am fully able to access my shares, and I can save to them as well, I am just unable to save a .torrent file directly from my XP machine with firefox. I am not even 100% it is possible, just hoping so. Thanks for the advice on rTorrent, I am checking it out now.

---

