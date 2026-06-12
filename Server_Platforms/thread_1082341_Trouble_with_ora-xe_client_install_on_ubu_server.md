---
title: "Trouble with ora-xe client install on ubu server"
date: 2009-02-27
forum: Server Platforms
---

### Post by paddydd on 2009-02-27
Hi,
  I really do appreciate this forum and have not posted that much since there is so much information that already resides within it.
  I did a search on this topic and I did not see any info so I am posting this question.

  Since I was so successful with the oracle install on 8.10 Desktop, I decided to try to install oracle XE client with UBUNTU 8.10 Server. I ran through the normal OS install steps --meaning i took all of the defaults except that I set it up with a static IP address --. Once the OS install was complete I ran the dpkg command to install the oracle package. Upon doing this I discovered that I needed an oracle user, group and the libaio1 package. So I created an oracle group and oracle user and I pulled down the libaio1 pkg.
  However, unlike the desktop install, this Oracle package install did not complete correctly. I am receiving an error that the chmod command cannot find the sqlplus directory. This directory was created via the GUI install using the Desktop. The full path name to the directory is:

/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/sqlplus

The script finishes with a message about Processing Triggers.

There is no message that states the install was successful or not but I am guessing the missing client directories will be an issue.

Has anyone seen this or have any ideas how I can proceed.

I can revert back to using 8.10 Desktop but since these are smaller computers I would like to slim down the memory usage.

Any help, comments and responses are appreciated.

Thanks
Paddy

---

