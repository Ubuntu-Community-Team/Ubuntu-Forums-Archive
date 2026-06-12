---
title: "Apache2 won't start in Dapper"
date: 2006-06-28
forum: Server Platforms
---

### Post by LeeM on 2006-06-28
I had been using apache2 successfully under Breezy Badger. After upgrading to Dapper, I can't start apache2. I tried uninstalling it, and re-installing, but it still doesn't start.

When I issue the command:
/usr/sbin/apache2ctl start
I get:
(13)Permission denied: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

Any clues what I am doing wrong?

Thanks!

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by falcon15500 on 2006-06-28
Are you running that command via sudo?  Or as root?
Enter this:
```
netstat -A inet -l --numeric-ports
```
And see if there is anything else listening on port 80.

falc

---

### Post by superpwnage on 2006-06-29
[QUOTE=LeeM]I had been using apache2 successfully under Breezy Badger. After upgrading to Dapper, I can't start apache2. I tried uninstalling it, and re-installing, but it still doesn't start.

When I issue the command:
/usr/sbin/apache2ctl start
I get:
(13)Permission denied: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

Any clues what I am doing wrong?

Thanks!

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)[/QUOTE]

You need to run it as the root user. Type-
```
sudo /usr/sbin/apache2ctl start
```

It will then ask you for your password. Type it in (you wont be able to see it) and it should start up just fine. Hope this helped,

-Ben

---

### Post by LeeM on 2006-06-29
[QUOTE=superpwnage]You need to run it as the root user. Type-
```
sudo /usr/sbin/apache2ctl start
```

It will then ask you for your password. Type it in (you wont be able to see it) and it should start up just fine. Hope this helped,

-Ben[/QUOTE]
Thanks to Ben and falc for the observation that I need to issue the command as root! I feel incredibly doofus! Somehow I forgot that minor detail. It works fine now.

Lee

---

### Post by dbarbour on 2006-07-17
I want to reopen discussion on this topic as I'm experiencing a similar issue.

I upgraded to Dapper from Breezy earlier today by changing alli nstances of "breezy" to "dapper" in apt's sources.list. Then issued **apt-get update**, **apt-get dist-upgrade**, and **apt-get upgrade**. Further, I disabled PHP4 and then upgraded to PHP5.

During the **dist-upgrade** I was asked about keeping my custom Apache configs in **/etc/apache2/sites-enabled** and I told my box to keep my configs.

After all is said and done, i can't connect to the box via HTTP. So I checked all running processes with **ps -A** only to find that Apache isn't running. :confused: 

So I tried starting the server manually with **/etc/init.d/apache2 start**.. no dice. Then tried **/usr/sbin/apachectl start**.. no dice. There are no error messages or anything. The box merely returns me to the command prompt. I *AM* logged in as root.

Further, I ran netstat to see if the box was listeing on port 80 and I got nothing. So I'm kinda lost. Currently resorted to running my site on a Windows box with IIS and desperately want to get my Ubuntu box back up and running.

Any help you can offer would be awesome.

---

