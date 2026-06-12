---
title: "Ubuntu (or maybe Kubuntu) for home server"
date: 2011-03-04
forum: Server Platforms
---

### Post by PhilFr on 2011-03-04
Hi all,

At the moment I have FreeNAS as my home server and mainly use it for file sharing, backup of windows PCs and video/audio streaming.

Unfortunately I have some problems with it (mainly setting up the ftp server, bit torrent client and a few more). So I decided to change it and try something new. After some research I found out that Ubuntu server edition could be the next best thing (don't want to pay Microsoft for WHS).

So since I am a bit new to linux (just fooled around with Kubuntu sometimes) I have some questions that I hope you can solve:

1. I haven't used any form of command line since my ZX spectrum +2 :P, so would like to use a web interface when accessing the server

2. Keep the capabilities of the FreeNAS system (streaming to windows PC and PS3)

3. Some new features I would like are torrent downloading, remote access to my files, printer sharing, Itunes access.

4. At the moment FreeNAS uses UFS as the filesystem and I got about 2TB full of data. If I change to Ubuntu will I lose the data (due to formating for a new File system)?

5. Anything else that can be done would be welcome

Also, if you could also give me a hint as to how I can do all this I would appreciate it :D

---

### Post by headvampyre@hotmail.co.uk on 2011-03-04
Firstly - NO Kubuntu for a server, if your wishing for a GUI, use Xubuntu.

Streaming support can be added with PS3MediaServer :)

For remote access - You could use Samba, or install NFS and install NFS-Tools on windows.

You'll need to backup your data and transfer it back to the Linux EXT4 filesystem :)

As for web interfaces, you have EBox and Webmin :)

---

