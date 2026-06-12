---
title: "vsftpd not reachable via web"
date: 2007-05-26
forum: Server Platforms
---

### Post by steve909 on 2007-05-26
Hello all, first post!
I was using SuSE but have come over to ubuntu recently. I had a vsftp server running on SuSE no problems, with anonymous users able to upload remotely.
I have installed vsftpd on ubuntu and can access it locally via fire ftp in firefox. It's running, and acting as it should i.e. changes directory, local downloads ok. No error messages.
I've opened ports on my router, as before (20,21) but when I try and connect from my mobile phone web access (my way of testing!) I see the web access light on the router flash for a second or two and then get a 'the page you are looking for is unavailable' message. If it was permissions or file location problems I would still expect to see the ftp root banner with an empty file tree.
I can access via the LAN from a windows XP machine.

Can anyone please suggest why I can't access remotely like before?

Thanks
Steve

---

### Post by Mr. C. on 2007-05-28
Some tips:

Check your vsftpd logs.  What do they indicate for the failed FTP login attempts?  No log entires in this case will indicate your firewall is blocking the remote connection.

From a remote network, use an FTP client you can control (eg. not your cell phone; try telnet or ftp command line).   (ask a friend to connect to your server, or PM me with the IP address and I'll check).

MrC

---

