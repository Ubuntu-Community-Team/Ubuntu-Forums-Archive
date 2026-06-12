---
title: "[SOLVED] Use mozilla to download to SFTP server- NO GO"
date: 2008-10-10
forum: Server Platforms
---

### Post by bcn17 on 2008-10-10
I am using rtorrent combined with screen on a 8.04 server. I have a watch folder set so that as soon as a torrent is placed in the folder the torrent starts. I either have to download the torrent from the cli ```
wget torrentlocation.torrent
``` or I have download the torrent to my desktop and via the "Connect to Server" option under places drag the torrent into my watch folder using the graphical sftp. It is very easy however, assuming the server is mounted, why can't I just tell mozilla to save the file into the watch folder. As of right now if I say "save to disk" and then click the sftp server and navigate to the folder and hit save it downloads and everything appears fine except the torrent is nowhere to be found!

By the way I am using keys, no passwords and the server file system is mounted.

---

### Post by jpkotta on 2008-10-11
I don't understand.  The server's fs is mounted on the client but you can't save anything to it?

---

### Post by bcn17 on 2008-10-18
Well, that's why it's weird. The I can save things too the server, just not directly with Firefox's "save". If I save the file to my desktop then drag it over it's just fine. hmmmm- I'll have to see if it works in 12 days... 8.10!

---

### Post by jpkotta on 2008-10-18
So you're using the built-in sftp of Nautilus?  There are better, more transparent ways.  
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)


Samba is also a good solution.  It gives you more options and control, but is harder to set up.

---

### Post by bcn17 on 2008-10-20
I'm gonna have to check this out- but I'm to busy right now!! Thanks a bunch :)

---

### Post by bcn17 on 2008-11-01
Well, sshfs was VERY easy to set up- Works very nicely- still want to look into samba though to see what it has to offer. THANKS!

---

