---
title: "Mounting Problems"
date: 2009-11-06
forum: Server Platforms
---

### Post by Mudsk122er on 2009-11-06
Hay guys this is my first post on here and im abit of a newbie to Ubuntu! 
 
I have set up a "home server" using ubunutu 8.04LTS, i have in the most part had alot of success with this using guides and so on.
My goal for this server is to only have a power and network cable plugged in so all i need to do is press the on button to turn it on and press it once again to shut down safely.
 
Here is my problem, (if this has been covered before please accept my appologies)
When i turn it on and log in the hard 3 additional hard drives installed seem to mount ok and i can access them over the home network. however when i just turn the comp on and dont log in i can only see the folders that originate on the root hard drive.
It seems to me that there is a mounting problem of some sort, possibly somthing to do with a start up service that needs to be installed?
Ideally i would prefer to not have to log on to the server every time I turn it on.
 
Please let me know if there is anything critical i have missed that will help!
or if indeed i need to explain myself better
 
Thanks for your help
 
Mudsk122er

---

### Post by karlson on 2009-11-06
> **Mudsk122er said:**
> Hay guys this is my first post on here and im abit of a newbie to Ubuntu! 
 
I have set up a "home server" using ubunutu 8.04LTS, i have in the most part had alot of success with this using guides and so on.
My goal for this server is to only have a power and network cable plugged in so all i need to do is press the on button to turn it on and press it once again to shut down safely.
 
Here is my problem, (if this has been covered before please accept my appologies)
When i turn it on and log in the hard 3 additional hard drives installed seem to mount ok and i can access them over the home network. however when i just turn the comp on and dont log in i can only see the folders that originate on the root hard drive.
It seems to me that there is a mounting problem of some sort, possibly somthing to do with a start up service that needs to be installed?
Ideally i would prefer to not have to log on to the server every time I turn it on.
 
Please let me know if there is anything critical i have missed that will help!
or if indeed i need to explain myself better
 
Thanks for your help
 
Mudsk122er


Check if the drives you want to see are in /etc/fstab.  If not add them there.

---

### Post by Mudsk122er on 2009-11-06
Karlson thanks for the heads up, ill chk that as soon as i get back from work!

---

