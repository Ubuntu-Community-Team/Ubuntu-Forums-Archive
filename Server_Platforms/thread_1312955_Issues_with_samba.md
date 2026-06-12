---
title: "Issues with samba"
date: 2009-11-03
forum: Server Platforms
---

### Post by mjfroggy on 2009-11-03
Hello,

I have setup a new home server (trying to get better at setting ubuntu lamp boxes). I was able to setup samba once before but this time for what ever reason I cant get it working. I sudp apt-get install samba and then config the smb.conf file I edited 

My issue is I still can not map to the server from my windows desktop. I am able to ssh in and of course get to the box in a browser via http

So I am thinking my config file is not correct. I also made sure I setup a user in the smbusers file 

in my smb.conf file I have made sure the following is uncommented
security = user
username map = /etc/samba/smbusers

comment = Home Directories
browseable = yes
writable = yes
valid users = %S

any suggestions would be appriciated. 
Thanks

---

### Post by Iowan on 2009-11-03
I presume that's just a sampling from smb.conf (you have [global] and [homes])? You created a user via **smbpasswd**?

---

### Post by mjfroggy on 2009-11-05
Hello

yes thats just a small bit of the conf file I have also setup the smbpassword and made sure I restarted samba yet still can get in t the samba share ??

---

