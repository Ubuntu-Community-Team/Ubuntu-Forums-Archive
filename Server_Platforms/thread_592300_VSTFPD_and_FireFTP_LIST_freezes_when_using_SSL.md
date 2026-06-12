---
title: "VSTFPD and FireFTP: LIST freezes when using SSL"
date: 2007-10-26
forum: Server Platforms
---

### Post by Badbunny on 2007-10-26
I have tried to get my ftp server running so I can access my files anywhere. I've had some problems with it and it seems that I have narrowed the list of suspects down to SSL encryption. I can access my files just fine if I don't use encryption, but if I enable it from the client software, the connection freezes after LIST command. And yes, I have enabled SSL from vsftpd.conf :)

From what I've read, it seems that FireFTP isn't the greatest client out there, so maybe that is causing my problems? It seems to me that I have vsftpd.conf just as it should be. As I can access the computer without encryption, this can't be a firewall issue. 

Can someone tell me how to test this? What client should I be using? Optimally, it would be a portable client. I tried iFTP, but that got me nowhere.

---

### Post by whit on 2007-10-26
Freezing after a LIST sometimes has to do with whether you're making an "active" or "passive" connection. If your server's allowing both, you might toggle that on the client and see if it makes a difference.

---

### Post by Badbunny on 2007-10-26
I believe I found the solution [here.]("http://www.linuxquestions.org/questions/linux-software-2/vsftpd-ssl-passive-listing-problem-262063/") At least it seems to work for now.

---

