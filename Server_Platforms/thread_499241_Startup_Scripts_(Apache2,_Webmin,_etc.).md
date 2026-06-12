---
title: "Startup Scripts (Apache2, Webmin, etc.)"
date: 2007-07-12
forum: Server Platforms
---

### Post by Footballkid4 on 2007-07-12
With all my servers configured, I'm down to making the last minute tiny configuration changes.  What I want now is for webmin to auto-start, but I believe it needs root for that, and init scripts aren't run as root.  Additionally, Apache2 needs to start but it requires a PEM passphrase for my SSL.  Normally, I wouldn't really care about manually starting this, but it becomes a pain when Apache tries to autostart, doesn't get a password, and then just sits there in the process list.  I have to run a ps aux | grep apache, find it, kill the process, and then I can start a new one.  I read about the following directive:

SSLPassPhraseDialog

But I'm not familiar enough with C to make a program, and I definitely don't want my plain text password kept in my apache conf file.

Additionally, in order to keep my wireless connection working, I'm using ndiswrapper.  I had a few questions about that.  Does ndiswrapper startup after login or before login?  If it starts up before login, is there any way I could make a script that will start up after ndiswrapper but before login, so that I can run:

```
iwconfig wlan0 essid x mode managed
```

Because that is the only way my card will reconnect to the router after a restart.

---

### Post by jtc on 2007-07-12
Init-scripts are run as the root user.

Curious, why do you use a passphrase on your apache certificates?

---

### Post by Footballkid4 on 2007-07-12
Not on the certificates, that was incorrect...it needs a passphrase for the key file, and I'm not going to follow the countless tutorials that say to unencrypt the key file, because that defeats the purpose of having SSL security in the first place.

Additionally, I don't think the init scripts are run as root, because webmin doesn't start up unless I specifically tell it to, and it's located in my init.d directory.  I don't think much of anything is run as root unless specifically told to.

---

### Post by jtc on 2007-07-12
> **Footballkid4 said:**
> Not on the certificates, that was incorrect...it needs a passphrase for the key file, and I'm not going to follow the countless tutorials that say to unencrypt the key file, because that defeats the purpose of having SSL security in the first place.
I was referring to the key file. Please explain to me how having the private key unencrypted (without password) defeats the purpose of SSL security? 

> **Footballkid4 said:**
> Additionally, I don't think the init scripts are run as root, because webmin doesn't start up unless I specifically tell it to, and it's located in my init.d directory.  I don't think much of anything is run as root unless specifically told to.
Actually it is the other way around. Init-scripts are always run as root. Once run as root many daemons then drop privileges to a non-root user.

---

### Post by Footballkid4 on 2007-07-12
> Now server.key contains an unencrypted copy of the key. If you point your server at this file, it will not prompt you for a pass-phrase. HOWEVER, if anyone gets this key they will be able to impersonate you on the net. PLEASE make sure that the permissions on this file are such that only root or the web server user can read it (preferably get your web server to start as root but run as another user, and have the key readable only by root).
Though that does imply that someone would have to have access to my server, it's still an unnecessary risk I'd rather not take unless absolutely needed.  If I could create a compiled C program that has the password stored but not readable...that would be perfect.

---

