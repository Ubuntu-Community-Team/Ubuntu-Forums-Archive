---
title: "I can't get rid of Firestarter!"
date: 2010-12-03
forum: Security
---

### Post by Enigma* on 2010-12-03
I uninstalled Firestarter and installed the Gufw interface.  I configured Gufw and it seems to work fine.  However, at startup, a prompt comes up asking, "usr/sbin/firestarter needs administrative privileges.  Please enter your password."  

I tried purging Firestarter and reinstalling the Gufw interface - it still comes up.  How do I get rid of it?

I would appreciate any help.

---

### Post by rburkartjo on 2010-12-04
eni the just is you cant.  i have it set to autoload at startup and still have to put in my password. 
here is a link you might want to read

[http://ubuntuforums.org/archive/index.php/t-960846.html](http://ubuntuforums.org/archive/index.php/t-960846.html)

---

### Post by uRock on 2010-12-04
Moved thread to Security Discussions sub-forum.

> **rburkartjo said:**
> eni the just is you cant.  i have it set to autoload at startup and still have to put in my password. 
here is a link you might want to read

[http://ubuntuforums.org/archive/index.php/t-960846.html](http://ubuntuforums.org/archive/index.php/t-960846.html)
You do not need to set GUFW to autostart. Its rules will automatically be loaded at boot without having the GUFW front end open. To verify this you can run **sudo ufw status** to see that it has the rules you previously created with GUFW. Example:```

rabbit@rabbit-desktop:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
631/tcp                    ALLOW       Anywhere
135,139,445/tcp            ALLOW       Anywhere
137,138/udp                ALLOW       Anywhere
22                         ALLOW       Anywhere

5353                       DENY OUT    Anywhere

```

---

### Post by CharlesA on 2010-12-04
What did it say when you purged firestarter?

```
sudo apt-get purge firestarter
```

---

### Post by cariboo on 2010-12-04
Just to add to what the other guys have said, make sure firestarter isn't running when you purge it, as it will leave bits of itself  on the system.

---

### Post by uRock on 2010-12-04
> **cariboo907 said:**
> Just to add to what the other guys have said, make sure firestarter isn't running when you purge it, as it will leave bits of itself  on the system.
To do this, open a terminal and run [B]sudo killall firestarter :D
[/B]

---

### Post by FuturePilot on 2010-12-04
You probably have some script running when you login to start Firestarter. Check what things you have autostarting. In KDE there's a tool in System Settings for scripts and programs to run at login.

---

### Post by bodhi.zazen on 2010-12-05
> **CharlesA said:**
> What did it say when you purged firestarter?

```
sudo apt-get purge firestarter
```

This ^^

simply removing firstarter does not remove the configuration files.
```
sudo apt-get install firestarter 
sudo apt-get purge firestarter
```

This is a long standing "bug" in firestarter (conflicts with UFW, leaves config files when removed). As firestarter is no longer maintained (it just keeps getting re-packaged), I doubt this will ever be "fixed".

---

