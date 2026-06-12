---
title: "Apache restart results with a fail! Help!"
date: 2005-12-20
forum: Server Platforms
---

### Post by Darkness3477 on 2005-12-20
Hello everyone, i was following the guide on apache servers found on [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP). I was doing everything it said, finally it told me to restart, that resulted in an error. 
I then decided to try and just start it, thinking that it couldn't restart because it was never on. When i did that i got an syntax error message. I fixed that, then upon restarting a new error came up saying : Syntax error on line 28 of /etc/apache2/apache2.conf:
PidFile not allowed here

Now, i really don't like any of this because i just want a place to write php and MySQL enabled pages freely, and then open up that file to the net to show people. After those people have finished looks, i can then turn it off so no one apart from the local host (My computer) has access to it.

So could someone help me out in fixing apache, maybe pointing me to a website that has the correct apache2.conf file so i can copy and paste it, and then tell me how i can make a http server thingy.

Thank you for your help.

---

### Post by Juippisi on 2005-12-21
Apache2 is, well, stupid, because it has separated the config files. But, this is how I have done the thing:

juippis@tykki ~ $ cat /etc/apache2/httpd.conf | grep -i pid
# PidFile: The file in which the server should record its process
PidFile "/var/run/apache2.pid"


Maybe your "PidFile" -line is on the wrong place or you don't have rights to the place where it saves.

juippis@tykki ~ $ ls -l /var/ | grep -i run
drwxr-xr-x   5 root root 4096 Nov 20 03:05 run


Or maybe...
[http://httpd.apache.org/docs/1.3/mod/core.html#pidfile](http://httpd.apache.org/docs/1.3/mod/core.html#pidfile)
"The PidFile directive sets the file to which the server records the process id of the daemon. If the filename does not begin with a slash (/) then it is assumed to be relative to the ServerRoot. The PidFile is only used in standalone mode."

---

### Post by Darkness3477 on 2005-12-21
Hey, thanks for that.

I fixed it, what had happened was i deleted <Directory> from it accidently, then when i put it back in I put it in the wrong spot. Anyway, fixed it now and Localhost is working. 

Now i'll go and search for ways to get the  /var/www/ file accisible to others through the internet.

---

