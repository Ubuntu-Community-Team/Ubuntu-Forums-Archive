---
title: "Best practice Ubuntu LAMP server setup"
date: 2010-03-09
forum: Server Platforms
---

### Post by caseyfw on 2010-03-09
Hi,

Didn't know where to go to ask this question, but figured I might get the best answer here.

I'd like to setup an Ubuntu LAMP server, and provide limited access to it for our in-house web developers/designers. I'm not quite sure how to go about the permissions side of things.

Which user/group should "own" the /var/www directory? Is it www-data?

How do I create user accounts (for our developers) that have access to the /var/www directory - do I create accounts then add them to the www-data group? Or should I make a special 'webdev' group and give it access somehow?

There must be hundreds of people who have created this sort of setup before - can someone fill me in on how it's done?

PS: I noted [this post]("http://ubuntuforums.org/archive/index.php/t-1052392.html"), but the guy comes across as a bit of a douche.

---

### Post by caseyfw on 2010-03-09
More questions:

What should the default permissions be of a file in the www directory, say a web page, like index.html, etc. Should it be owned by www-data and have only write and read by the owner and group?

Can you change the default permissions a file receives when it is created? For example, if a developer copies a whole tree of files into an SSH client, can you mandate what permissions those files will have, or is it determined via some process I'm not aware of?

Thanks,
Casey.

---

### Post by caseyfw on 2010-03-09
I'm beginning to think I've got this all wrong, because the www-data group isn't supposed to possess write permissions for most of the files on a webserver.

Am I supposed to make a user, say 'webdev' the owner of the /etc/www directory? Make this user a member of www-data, then restrict the permissions to be read only for the group? This would mean www-data could read, but not write files on the host. (most files, anyway - obviously some directories you would want to allow write access to).

Can someone tell me if I'm barking up the wrong tree?

---

### Post by zander1013 on 2010-03-10
hi casey,

you would be surprised how few are doing these things. ;)

i have been learning as i go and mostly having to figure stuff out myself.

i have a 9.10 ubuntu lamp set up here. i call it oznola. i set up oznola with all default install settings.

i can access the web root with [http://oznola.localdomain](http://oznola.localdomain) from other machines using a browser on my wlan behind my firewall.

try portscan to see what ports on it are open the only two open on mine by default are www and smtp. you will have to open new ports for ssh and ftp and just about any other way you want to access the server other than the default www or smtp.

after you setup ssh and ftp ports then you will have to add the users to the server as usual if you want them to access the web root using those methods you mentioned (ssh, ftp, https, .....,,,).

can you access the web root with http://<hostname>.localdomain on other computers on your (w)lan?

what are you using for your web development?

i use wordpress. so if i wanted developers to use wordpress after i had installed it on the server as usual i would just have them go to http://<hostname>.localdomain/wordpress/wp-admin which would give them the wordpress admin login page where you could handle the access and permissions through wordpress access acounts there and you won't have to deal with setting up anymore ports or adding users to the server.

i hope this brings some clarity to your situation. its the culmination of the last few weeks of my lone personal struggle.:lolflag:

if you have any more questions i will be around:)

---

### Post by Iowan on 2010-03-10
Though it's apparently undergoing a rewrite, [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") help page has info on virtual servers - and moving the DocumentRoot. The recommended guide is located [here]("https://help.ubuntu.com/9.10/serverguide/C/httpd.html") for 9.10.

---

### Post by NullHead on 2010-03-11
Honestly, I would just add each user to the group www-data that needs access. ```
sudo adduser <username> www-data
```

---

