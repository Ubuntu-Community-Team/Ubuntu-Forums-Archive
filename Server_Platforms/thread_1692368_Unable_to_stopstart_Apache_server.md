---
title: "Unable to stop/start Apache server"
date: 2011-02-21
forum: Server Platforms
---

### Post by hangle on 2011-02-21
I attempted to stop my apache server with the following command:
 :sudo /etc/init.d/apache2 stop

The script ran and it printed:
 * Stopping web server apache2   

However, I received the following message:
                                              
 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

I also got this message when i ran:

service apache2 stop

My question is what is this message telling me or is not telling me.

thank

---

### Post by volkswagner on 2011-02-21
run the following commands.

```
hostname
```

```
hostname -f
```

You can add the results from above in your /etc/hosts file, then restart apache2.

Do you have any virtual host files with a servername listed?

---

### Post by cariboo on 2011-02-21
You need a host name for 127.0.1.1 in order not to see the message. That should cause any problems stopping or starting apache

You set the hostname in /etc/hosts

---

