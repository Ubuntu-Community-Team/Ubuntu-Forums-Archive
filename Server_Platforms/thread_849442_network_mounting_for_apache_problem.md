---
title: "network mounting for apache problem"
date: 2008-07-04
forum: Server Platforms
---

### Post by michael1991j on 2008-07-04
i have two servers running Ubuntu  hardy  32bit   and i am trying to mount the 500g drive  over the network. the reason why i am want to network mount is because all my web data is on the 500g and comp2 is running all the apache mysql and php. what i am using is sshfs.  

> sshfs 192.168.1.5:/server/var/www/html/  /var/www/html
i can mount the drive perfectly but the problem is permission everything i have to do on this drive requires the root user name and when i am trying to use apache it gives me a forbiddin error when i access the file i tried to change the use name for apache from www-data to root but when i start apache it says i cant use root does anybody know how i can change the permissions on sshfs so i can use it for apache on my other server
    _network___
   |          |
192.168.1.5   192.168.1.6    
  |                 |
comp1            comp2
|   |               |
80g 500g           160g

 another thing is that on computer one it is mounted as  a vol and not as a basic ext3 i was wondering if that could be the issues and finally both file directory have chmod 777 permissions


thank you in advance 
Michael

---

