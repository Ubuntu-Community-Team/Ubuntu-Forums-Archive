---
title: "LTSP won't log in."
date: 2008-09-28
forum: Server Platforms
---

### Post by kino6113 on 2008-09-28
i have just setup a ubuntu 8.04 server and installed ltsp on it. 

the thin clients boot fine over the network. it comes up this the ubuntu login screen. i tryed the root account, my user account, and the account i just made named test. the root and my account look like there loging in but i just get bounced back to the login. the test one says that the password is incorrect.

if i go to tty1 it says that all the users logins are incorrect. so right now im stuck. i have done the ltsp ssh command thing and that still didn't work.

---

### Post by lykwydchykyn on 2008-09-28
What desktop environment is set up for the thin clients to log in to?

---

### Post by kino6113 on 2008-09-28
i belive the ubuntu default one. im not quite sure. its running off the 8.04 server edition. then i installed ltsp-server. im going to try to to ltsp-update-image again and see what happens.

---

### Post by lykwydchykyn on 2008-09-28
By default, what LTSP does is create just enough of a client install to connect back to the server to log in.  So you need to install xorg and some kind of desktop environment on the server (which is not default on server edition-- it installs CLI only).  LTSP can also be configured to log in to a different machine, hence a GUI isn't a package dependency.

Try this on the server:
```

aptitude install xorg gdm xfce4

```
You can install gnome or kde instead of xfce4 if you like.  But after installing those, run:
```

invoke-rc.d gdm start

```

Then boot your client and see if you can log in.

---

### Post by kino6113 on 2008-09-28
is this going to install a gmd on the server. i want that to stay cli only.


im going to install this and see what happens anyhow.

---

### Post by lykwydchykyn on 2008-09-28
I suggest you take a look at this page and read about how ltsp works:  
[http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server.html)

The LTSP client does the X11 equivalent of "remote desktop" to the server when it boots.  So if the server is not running a GUI, it has nothing to connect to.  This is why you cannot log in to your clients.

You have to do one of the following:
 - install a GUI on the server
 - Configure the clients to connect to a different machine, which has a GUI
 - Configure the clients to have their own environment to log in to.  

All of this information should be in the edubuntu handbook.

---

### Post by kino6113 on 2008-09-28
thank you that did infact work.. if i wanted to install fluxbox and the gnome desktop what would the apt-get commands for that be?

---

### Post by lykwydchykyn on 2008-09-28
That would be:
```

aptitude install gnome

```
and 
```

aptitude install fluxbox

```

---

