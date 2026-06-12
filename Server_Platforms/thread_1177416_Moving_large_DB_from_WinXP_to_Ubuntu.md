---
title: "Moving large DB from WinXP to Ubuntu"
date: 2009-06-03
forum: Server Platforms
---

### Post by bryder on 2009-06-03
Hello,
I am somewhat new to Ubuntu server administration and have a question about a problem I've been having. I've been trying to move a large MySQL database (12GB) from a Windows server to my new Ubuntu server running on VMware. 

First, I tried just copying it over by setting up a SAMBA share and doing the copy from the Windows side but I keep getting the error "Cannot copy database.sql: The path is too deep."

I then mounted a windows network drive from the Ubuntu server and tried to do the copy that way. This seemed like it would have worked but was going very slow (30kb/sec) and so I stopped it. I may still come back to this. Lastlly, I tried setting up an FTP server (vsftpd) on the Ubuntu server and doing the copy from a FTP client on the Windows server, but I keep getting some sort of timeout and the copy re-starts.

What is the best way to move an 12GB database dump file file from Windows to Ubuntu? Can I transfer the data directly from server to server or should I just copy the file? Thanks for any direction you can point me in.

Thanks.
- Dave

---

### Post by Zeosa on 2009-06-03
It sounds oddly like a hardware problem to me. Try changing out the network cables first as it's the simplest thing. It could also be a faulty NIC in one or both of the machines as well.

---

### Post by bryder on 2009-06-03
Hmmm, that could be. 

Like I said, it's running on a VMware server. This server has two other virtual servers running, but without much traffic at all. The hardware has two NIC's as well. Are there software tools to analyze this sort of thing?

Thanks.

---

