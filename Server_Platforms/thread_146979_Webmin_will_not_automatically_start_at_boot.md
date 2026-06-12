---
title: "Webmin will not automatically start at boot"
date: 2006-03-19
forum: Server Platforms
---

### Post by wgregori on 2006-03-19
I installed Webmin the other night and the install completed successfully... webmin started and could access it via web.  However, upon restarting the server it did not startup.  I was forced to go in and stat it manually.  

Anyone had this problem?  Can anyone tell me what I need to change to get it to start automatically?

Thanks,
Wayne

---

### Post by phpcitizen on 2008-06-11
Yes, I have the same problem just started today.

Any heads up!? Please.

---

### Post by durkio on 2008-06-21
I had the same problem (Ubuntu 8.04 server);
In the webmin interface you also have the option to make webmin start when the system boots. It gave me a more detailled message:

Failed to open /etc/rc.d/init.d/webmin for writing : No such file or directory

So I googled how I could create a startupscript by myself, when I checked the setup.sh file, I noticed that executing 
/etc/webmin/start was enough.

Thanks to [http://remind-nix.blogspot.com/2008/06/how-to-start-script-at-boot-time.html](http://remind-nix.blogspot.com/2008/06/how-to-start-script-at-boot-time.html)
I solved the problem:

If you installed webmin in the default folder
(/etc/webmin/) you follow these steps:

1) cd /etc/init.d

2) create a new file with the name webmin
and fill it with this content:
#! /bin/sh

DEAMON=/etc/webmin/start

test -x $DEAMON || exit 0

. /etc/webmin/start


3) Save the file. 
4) Make it executable:
chmod 755 /etc/init.d/webmin

5) It must be started on boot,
we want to start it as root:
sudo update-rc.d webmin defaults

6) now reboot the system. When it
starts you will notice a message 
which says that webmin server is started.

P.S.
If something goes wrong and you want to
remove this addition in starting up, you
execute:

update-rc.d -f webmin remove

---

