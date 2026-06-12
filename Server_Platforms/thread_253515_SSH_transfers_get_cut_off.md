---
title: "SSH transfers get cut off"
date: 2006-09-08
forum: Server Platforms
---

### Post by linuxpenguin on 2006-09-08
I use OpenSSH for BitTorrent.  Sometimes when I'm transferring my downloads the files are too big and the connection gets dropped right in the middle of transferring the file.
Is there somewhere I can set the max connection time or something?

---

### Post by JLTB on 2006-09-08
Hmm,

Could be the provider your server is with is limiting your connection (not much you can do about that), could be your internet connection is unstable (from client end), also could be your ssh client is using unsupported or strange ssh options.

I once had an experience where the OS X application Cyberduck refused to transfer more than 1 MB across an SFTP connection.  I ended up having to tweak some Max packet settings on the client.

Last but not least, try RSYNC.  This tool is too reliable for words.  My life would be hell without it.

James.

---

### Post by linuxpenguin on 2006-09-08
No, this is my server.  It's using Ubuntu 6.06 Server with OpenSSH.  I'm running it out of my house (my school is blocking the BitTorrent port so I need to do this to download torrents).

Problem is that some of these files are like a couple gigabytes and take a really really long time to transfer, and sometimes I come back to my computer to see that it says "stalled".  I can still control the command line through SSH, though - I can ctrl-c out of the program and run another command.

I'm thinking that OpenSSH may be trying to disconnect after a few hours of me not typing commands or something, could be wrong though.

---

