---
title: "Partial Directory Listings VSFTPD or Index File?"
date: 2008-09-18
forum: Server Platforms
---

### Post by metalcoat on 2008-09-18
I get only a partial directory listing from any FTP client for directories that range to over 1000.  It won't even complete locally. Is there a way where I can index the folders so that all you would have to download is at max 1 files with all directories in it.  I tried google but I'm not sure what I am looking for.

Any solutions are welcomed.

---

### Post by Vishal Agarwal on 2008-09-18
You can see only the files, as per there permission. if depends on that, with what login you are logging in. Only those files you can see with FTP client.

---

### Post by metalcoat on 2008-09-18
Yes but the permissions are all set, I can access them through ftp it just won't list all of them (Type name in). It seems that the listing hangs around the same time for every client, except firefox.  Firefox will actually load an additional round of directory names then hang as if the server stop sending them.

---

### Post by metalcoat on 2008-09-19
Well I'm not quite sure what the problem is but after uninstalling and reinstalling pure-ftpd instead, load times are instantaneous.  Not sure if it was due to my configuration files or what but this worked right off hand.

---

