---
title: "vsftpd, large files, and write errors"
date: 2007-09-04
forum: Server Platforms
---

### Post by drewtown on 2007-09-04
I am running a person vsftpd server with only sftp access that I have set up at home.  My brother in a different state is trying to upload large files to me but only has 40KB/s upload and whenever he tries to upload these large files, it says "File name write error" on his client.

There is still free space on the disk.

On a LAN there doesn't seem to be this problem.

Is there a way to correct this so we can do this or do you have recommendations for a more reliable form of file transfer that would involve just us (not p2p).

---

### Post by HermanAB on 2007-09-04
It sounds like your brother has a high error rate on his connection, with the result that when a file is 'large enough', it always fails.  The simple solution is to split the files into smaller pieces using 'split' and 'merge'.  You can get those for Windoze too.

A better solution is to use rsync instead of FTP.

Cheers,

H.

---

