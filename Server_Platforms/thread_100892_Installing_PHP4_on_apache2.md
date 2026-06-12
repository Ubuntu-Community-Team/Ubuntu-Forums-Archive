---
title: "Installing PHP4 on apache2?"
date: 2005-12-08
forum: Server Platforms
---

### Post by zhorty on 2005-12-08
Hi.
I'm trying to install the "libapache2-mod-php4" in Synaptic, but I get the error:
```
invoke-rc.d: unknown initscript, /etc/init.d/apache2 not found
```
I guess this is because I one day tryed to remove apache2 manually, and all things just fucked up. And sudo apt-get php4 don't work (Can't find the package).

And I can't even stop or restart the apache2 server (sudo /usr/sbin/apache2ctl stop), because I fucked that installation up as said :p

So, how can I delete the whole installation? I tryed apt-get remove apache2 and, apt-get clean apache2, but don't work.

So, any suggestions on anything here?

---

### Post by gruepig on 2005-12-08
Not sure if this will help, but try 'apt-get update' followed by 'apt-get install apache2' or 'apt-get -f install apache2' (-f is --fix-missing).

If you are getting specific errors, post them.  Also post the output of 'dpkg -l | grep apache' (which is one way to get a listing of installed or semi-installed apache packages and their current state).

---

### Post by arphe_el on 2005-12-14
i already installed my php4 and after that i type this command
 
sudo /etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)...
(98 ) Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
 *able to open logs    

what should i do to resolve this?

thanks GODspeed!:)

---

### Post by arphe_el on 2006-02-27
I already install apache triad (apachev2, phpv5, and mysqlv5) into my breezy debian package and it works for me.

please visit this site and download the package:

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

you can also e-mail the author of that software for any problem that you encounter and they are responding. Hope this helps you. GODspeed!

---

### Post by playboy601 on 2006-03-02
you may have regular apache running.. and its binding to port 80, not allowing apache2 to bind to it..

try this..
```
sudo /etc/init.d/apache stop
```

and then do..
```
sudo /etc/init.d/apache2 start
```

---

### Post by gruepig on 2006-03-02
To see what is using port 80, run 'sudo lsof -i | grep www'.

---

