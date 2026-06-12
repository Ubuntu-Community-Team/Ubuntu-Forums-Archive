---
title: "Help with vsftpd please"
date: 2014-02-21
forum: Server Platforms
---

### Post by Rufus100 on 2014-02-21
I'am new to Ubuntu. I search for internet how to install/run vsftpd.
I make change in vsftpd.conf:

[LIST]
[*]listen=YES
[*]anonymous_enable=NO
[*]local_enable=YES
[*]write_enable=YES
[*]local_umask=022
[/LIST]
Then i create a user
[LIST]
[*]sudo -- useradd admin1
[*]passwd admin1
[LIST]
[*]123321
[/LIST]

[*]sudo usermod --home /var/www/ admin1
[*]sudo chmod 755 /var/www
[*]
[/LIST]
I have used FileZilla, at host I enter my IP, at username admin1 and at password 123321.
It have connected but I could not write files.(error 550)
So I 
[LIST]
[*]sudo chmod 777 /var/www
[/LIST]
Then everything was perfect. But when I log out and enter again it gives me error 500.

At every step I 


[LIST]
[*]sudo service vsftpd restart
[/LIST]
I even restart PC., but I cant get rid of errors.

Thanks.

---

