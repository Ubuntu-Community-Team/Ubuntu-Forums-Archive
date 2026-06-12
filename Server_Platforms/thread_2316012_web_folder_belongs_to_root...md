---
title: "web folder belongs to root.."
date: 2016-03-04
forum: Server Platforms
---

### Post by jonathan_3 on 2016-03-04
Hey, I am quite new to ubuntu servers and linux in general (even though I have tried it out several times over some years now). And I just installed Ubuntu server 14.04 with LAMP. 
My question is why my web folder belongs to root? Isnt root kind of sacred and should not be used as webfolder? Earlier I have been using an other user and wonder if this is something that has changed resonantly or not? 

I tried to search this question up at the web, trying to find a kind of "how to" set up the webfolder and user access. 
I would be very happy for all help I can get!

Preferably a link to how to make it work as it should, if anyone know about an easy explanation / walk-through that I could use.  

Thanks!

---

### Post by houstonbofh on 2016-03-04
root is the user with all permissions.  But a file owned by root means you need all permissions to edit it.  Note that Ubuntu uses sudo which gives you root like permissions on a per command basis...

That all said, I se up my web servers a little less securely. The web directory on down is root:www-data with 644/755 and I put myself in the www-data group.  That way I can edit them without needing root.  Handy when you have mounted the drive remotely with ssh.

---

### Post by jonathan_3 on 2016-03-04
So you change the permissions of the default webfolder then? From root:root to root:www-data ?

---

### Post by darkod on 2016-03-05
If by default webfolder you mean /var/www/html, I just checked on a friends webserver and it is owned by root. So I would say that is normal. Why do you want to change it?

Also note that if the permissions are rwxr-xr-x and you only change the group to www-data, that still does not allow W for that group/users. And for only R, you already have that for all the world.

---

