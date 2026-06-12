---
title: "403 Forbidden Error when trying to connect to server"
date: 2009-04-09
forum: Server Platforms
---

### Post by redonwhite on 2009-04-09
Hello,  Im following directions from the following link to set up Jinzora on my Ubuntu 8.10 server edition server with LAMP and SSH installed.

 [http://en.jinzorahelp.com/wiki/Linux_Installation_with_shell_access](http://en.jinzorahelp.com/wiki/Linux_Installation_with_shell_access) 

Im on the last step.  Im doing this through SSH to my server.  I type

```
$ chmod 744 configure.sh
```

then

```
$ sh ./configure.sh

You are now in setup mode.
Please direct your web browser to the directory where you installed Jinzora
and load index.php - you will then be taken through the complete setup
```


Then i direct my browser from my main PC to [http://serveripaddress/jinzora2](http://serveripaddress/jinzora2)

i get 403 Forbidden Error. You don't have permission to access /jinzora2/ on this server.

Any ideas what I'm doing wrong or how i get permission?  The jinzora File is sitting in /var/www/.

---

### Post by windependence on 2009-04-10
This is probably because /var/www is owned by the www-data user. You can change it to your user by doing:

```
sudo chown -R *yourusername* /var/www
```You will probably not want to keep it that way unless you will be the only user accessing the files. I don't know squat about Jinzora so my advice would be to find a good tutorial and read it carefully to find out who should own the directory after the install.

-Tim

---

