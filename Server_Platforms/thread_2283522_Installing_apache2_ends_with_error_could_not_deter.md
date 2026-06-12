---
title: "Installing apache2 ends with error could not determine domain name, using 127.0.1.1"
date: 2015-06-22
forum: Server Platforms
---

### Post by richlion2 on 2015-06-22
Hello, 

I am trying to install the Apache2 server using the following link:
[https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

The command is:
> 
sudo apt-get install apache2


The error message is:
> 
Enabling site 000-default.
 * Starting web server apache2                                                                                                                        AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message




I found some hints, however they seem to relate to problems when people have the apache server already installed.

These are my PC details:
> 
rysiek@Richlion5:~$ uname -a                                                                                                                                                                                          
Linux Richlion5 3.13.0-55-generic #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux                                                                                                                 
rysiek@Richlion5:~$ hostname                                                                                                                                                               
Richlion5                                      


Is there anyone who can point me to how my PC has to be setup?

This is my /etc/hosts file:

```

rysiek@Richlion5:~$ cat /etc/hosts
127.0.0.1       localhost                                                                                                                                                                                
127.0.1.1       Richlion5                                                                                                                                                                                
                                                                                                                                                                                                                
# The following lines are desirable for IPv6 capable hosts                                                                                                                                                                 
::1     ip6-localhost ip6-loopback                                                                                                                                                                                         
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```

Regards, 
Richard

---

### Post by SeijiSensei on 2015-06-22
Is that the /etc/hosts file on the server or on the client?  If it's only on the client, try adding an equivalent entry in the server's /etc/hosts for 127.0.1.1 as you did on the client, then restart Apache.  if that doesn't fix the problem, then edit the file /etc/apache2/sites-available/000-default.conf and replace the line:
```
#ServerName www.example.com
```
with 
```
ServerName richlion5
```
Restart Apache.

---

### Post by richlion2 on 2015-06-22
Hi, 

I did not manage to install the apache server. That is why I don't have any apache config files to change. 

I just have a normal PC -client installation. Can this be used as a base for a web server, or do I need to install the Ubuntu server for a better result?

/etc/hosts is my client file. 

Thanks,
Richard

---

### Post by Habitual on 2015-06-22
```
sudo echo "ServerName localhost" >> /etc/apache2/apache2.conf ; apache2ctl reload 
```

---

### Post by pissedoffdude on 2015-06-23
Looks like it's trying to use the fully qualified domain name.  What's the result of ```
hostname -f
```.  You should be good to go by adding the fully qualified hostname to the hosts file.

EDIT: Or if it's anti-that, explicitly define your fully qualified hostname and add it to your hosts file

---

### Post by richlion2 on 2015-06-24
[Edited] ...

It seems there quite a few links, however I can't still see which version of Linux should I use, should I use the Server or Desktop.
This seems like a nice guide, but does not provide with that answer:
[http://www.penguintutor.com/linux/installing-lamp](http://www.penguintutor.com/linux/installing-lamp)

[http://www.makeuseof.com/tag/build-linux-web-server-computer-part-1/](http://www.makeuseof.com/tag/build-linux-web-server-computer-part-1/)

[http://www.boutell.com/newfaq/creating/domainathome.html](http://www.boutell.com/newfaq/creating/domainathome.html)
Does anyone use this type of domain for a web server:
[http://freedns.afraid.org/](http://freedns.afraid.org/)

I'll be back at home today and post my settings later.

Regards, 
Richard

---

