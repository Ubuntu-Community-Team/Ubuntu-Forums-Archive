---
title: "apache - starting problem"
date: 2010-03-13
forum: Server Platforms
---

### Post by luftadler on 2010-03-13
Hi all

I have this problem with apache... 

Is not starting when i start the system and when i try to start it manually it give me this error

```

apache2: Could not reliably determine the server's fully qualified domain name, 
using 127.0.1.1 for ServerName
 
```
Thanks,
Cristian

---

### Post by helgman on 2010-03-13
Hello,

Try [this](http://wiki.apache.org/httpd/CouldNotDetermineServerName) out, might help. Just be carefull about what file you should use, I'm not sure if it's httpd.conf or apache2.conf.

Does it help?

Regards,
Helgman

---

### Post by luftadler on 2010-03-13
problem solved 
I remembered about this good material
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


```

$ echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
$ sudo /etc/init.d/apache2 restart
* Restarting web server apache2                           [ OK ]

```:D

Thanks again for helping,
Cristian

---

### Post by luftadler on 2010-03-13
so, after restart i see that the problem is not solved anymore :(
i have no error message but the apache is not starting automatically wen i start the system


any ideas?

---

### Post by helgman on 2010-03-13
Hrm ...

I'd try ```
update-rc.d <name_of_the_serivce> defaults
``` or something like that. If I'm not mistaken the name of the service is apache2 ...

Regards,
Helgman

---

### Post by luftadler on 2010-03-13
:D

ya... I've tried this:

```
sudo update-rc.d apache2 defaults
```

and now is starting perfect

Thanks Helgman, you saved my day.

---

### Post by luftadler on 2010-03-15
I don't now what is happening but after second reboot apache will not start anymore...
so, I've reinstall apache 2 and all dependencies and... I have the same problem
apache will not start after the second restart of the system and I have to start it manually

:-#

I don't now what to say more

---

### Post by luftadler on 2010-03-15
after siting disappointed in my chair ... I've had new idea 
how about to force setting* **symlinks*** to default
so:```

**sudo update-rc.d ****-f apache2 ****defaults**

```

And now seems to work, how it should be working.

---

### Post by helgman on 2010-03-15
Ah,

When you mention the -f I do remember it. Sorry for the (hopefully) temporary memory laps. Glad you figured it out!

Regards,
Helgman

---

