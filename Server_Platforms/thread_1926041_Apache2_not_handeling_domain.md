---
title: "Apache2 not handeling domain"
date: 2012-02-15
forum: Server Platforms
---

### Post by brent1975 on 2012-02-15
Hello, This morning I noticed that apache is not working properly. I am running ubuntu server 10.04 with apache2. I have a small forums on my server for reference for screw ups.. lol  Anyways I am able to get to the site via the static IP of the server and it works fine. But when I go to the domain forums.iso-world.com it does not pull this up. I have checked to make sure that the IP has not changed for TWC which it hadn't. I have made sure that port forwarding was still good and it was. I also verified that UFW was still allowing port 80 requests and all seems good. I even disabled UFW just for trouble shooting. I'm really not sure what log I need to be looking at to see what the issue is here. Any help would be greatly appreciated.

Thanks,

---

### Post by brent1975 on 2012-02-16
I am not sure if there is a bug in apache2 or not but here is what I did to fix my problem.

I went into /etc/apache2/sites-enabled and removed the 2 files I had in  there domain.com and sub.domain.com. Then went into  /etc/apache2/sites-available and ran 

sudo a2ensite sub.domain.com
&
sudo a2ensite domain.com

followed by

sudo /etc/init.d/apache2 reload

This worked for me...

---

