---
title: "sftp server &quot;connection reset by peer&quot;"
date: 2006-03-27
forum: Server Platforms
---

### Post by Biffy on 2006-03-27
Today i tried for the first time to set up my own sftp server. This is my problem:

I am using Ubuntu breezy. 

First, i installed ssh. Then i created a user.

I had a couple of friends that would aid me in testing my new sftp server. I told my first friend to download the WinSCP 3.8 beta and to install it.

Ok, so he can connect to my server, browse around and upload files. But, the problem is that after having uploaded for a while, it just stops uploading and his client kinda freezes. So, the upload just crashes. Not after a given amount of time tough, it can crash the first second and it can crash after having uploaded files for 10 mins. The error message he recieved was: "Connection reset by peer".

So i tought maybe there is something wrong with his connection, so i asked another friend. He downloaded WinSCP 3.7.6 

He could do the same thing. He connected without any problem but when uploading files, it crashed just like it did for my first friend. His error message was "software Caused connection abort"

I have a D-link 604 broadband router. I have port forwarded port 22 and also opened port 22 in the firewall. My friends told me their IP-adresses but they where not in the firewall log. I dont know where my ssh logfile is.

Can someone help me? Why are the file transfers crashing after a while?

---

### Post by Biffy on 2006-03-27
I've been testing some more with my friend. It seems this does not only happen on sftp, it also happens in ftp using vsftpd.

He connects and starts the upload. The speed is going very much up and down all the time. Like the transfer isnt stable at all. Sooner or later the transfer dies and my friend has to reconnect.

I've tried on my other computer as well, and the same thing happens there.

---

### Post by Biffy on 2006-03-28
On my vsftpd server, the speed is very stable when people are downloading from it. When uploading, the speed varies a lot and then it just stops.

---

### Post by Avicus on 2006-03-28
I too have this same problem. I've tried vsftpd and proftpd. Same problem. No idea why.

---

### Post by purefan on 2007-09-25
hasnt happened to me nor was I who found the fix but a friend was having this exact same problem with sftp connections, he used Filezilla to connect and when he used the IP it would work but if instead you entered the domain it would show the connection reset by peer error. May be worth giving it a shot

---

