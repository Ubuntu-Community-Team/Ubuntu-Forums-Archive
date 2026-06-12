---
title: "vsftpd external connection issue"
date: 2012-03-16
forum: Server Platforms
---

### Post by duceduc on 2012-03-16
I have been tackling this for days and I cannot get vsftpd to work for all users connected outside my network. Some users reported to connect fine, others cannot. They would be connected to my host but it times out after 15 seconds. This time out error suggest that my port ranges has not been set. It is, however. They have tried it on winscp and filezilla client.

What I have done thus far is opened port 21 both on server and my router. I also setup a port range as well on my router, server firewall and in the vsftpd config file. 

[screenshot1]
[IMG]http://img.photobucket.com/albums/v645/duceduc/ss/vsftp-connection-error-01.jpg[/IMG]
[screenshot2]
[IMG]http://img.photobucket.com/albums/v645/duceduc/ss/vsftp-connection-error-02.jpg[/IMG]

---

