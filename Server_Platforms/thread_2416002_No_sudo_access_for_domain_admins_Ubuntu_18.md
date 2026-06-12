---
title: "No sudo access for domain admins Ubuntu 18"
date: 2019-04-03
forum: Server Platforms
---

### Post by savagetwinky on 2019-04-03
So, the reason why I'm posting this and not googling is because I did google and I'm super confused and frustrated. Mostly there is just too much information and I've fought through adding a build machine to a domain with varying degrees of success. I am *NOT* an it person. I have very very limited knowledge about netwowrking, I understand LAN, DNS and local IPs.. 

So I used this guide to connect my machine to a domain after installation
[https://www.server-world.info/en/note?os=Ubuntu_18.04&p=realmd](https://www.server-world.info/en/note?os=Ubuntu_18.04&p=realmd)

Other guides didn't work with logging domain users in. After I could log in, I used pam-auth-update to allow creating folders.

 Then I added %domain^admins ALL=(ALL) ALL to sudoers using visudo. This is based on our ubuntu 14 server.

And it didn't work. At least with my account. I tried a few things in [https://askubuntu.com/questions/455211/how-to-add-domain-admins-to-sudoers/756625](https://askubuntu.com/questions/455211/how-to-add-domain-admins-to-sudoers/756625) and not much help. To me this looks like they are throwing random stuff against the wall.

---

