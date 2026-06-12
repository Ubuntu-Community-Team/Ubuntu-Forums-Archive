---
title: "How to permanently disable apache on boot?"
date: 2011-11-12
forum: Server Platforms
---

### Post by kaurman on 2011-11-12
Hi!

In case of a development environment one has no need to have neither mysql nor apache constantly running. Disabling the startup of mysqld on boot was rather easy but apache is more stubborn.... There is the 'update-rc.d -f apache2 remove' methd which works but only as long as apache does not get updated... If the package is upgraded the whole thing starts all over again.

Is there any more permanent solution to disable the startup of apache?

I could add 'service apache2 stop' to rc.local but it seems a bit silly.... and I am not even 100% sure it works.

---

### Post by AlexDudko on 2011-11-12
> chkconfig apache2 off
If there isn't this command
> apt-get install chkconfig
But it won't give you permanent solution either. Still you can run
> chkconfig --list after  update to see which services are started at boot time and then turn off those you don't need.

---

### Post by Lars Noodén on 2011-11-12
> **kaurman said:**
> Is there any more permanent solution to disable the startup of apache?



Yes.

```

sudo update-rc.d -f apache2 remove

```

---

### Post by kaurman on 2011-11-12
> **Lars Noodén said:**
> Yes.

```

sudo update-rc.d -f apache2 remove

```

If this is irony then I am not getting it cos that's exactly what I have done so far. True, in my post i omitted the sudo part which is self-evident.

But if I am really missing something, I'd be grateful for your further explanation.

---

### Post by Lars Noodén on 2011-11-12
You could manually remove the Apache2 script from the following directories, but that is the same thing that the above update-rc.d perl script does.

/etc/rc0.d
/etc/rc1.d
/etc/rc2.d
/etc/rc3.d
/etc/rc4.d
/etc/rc5.d
/etc/rc6.d
/etc/rcS.d

Note that either way the changes take effect the next time you change run levels (usually reboot).

---

### Post by kaurman on 2011-11-12
> **Lars Noodén said:**
> You could manually remove the Apache2 script from the following directories, but that is the same thing that the above update-rc.d perl script does.

/etc/rc0.d
/etc/rc1.d
/etc/rc2.d
/etc/rc3.d
/etc/rc4.d
/etc/rc5.d
/etc/rc6.d
/etc/rcS.d

Note that either way the changes take effect the next time you change run levels (usually reboot).

Ok but my point is that the changes only last till the apache package is upgraded (a security update etc..). I would like to find a way that would permanently disable the on boot startup (so that upgrading the apache package wouldn't cause automatic startup again).

---

### Post by Lars Noodén on 2011-11-13
> **kaurman said:**
> Ok but my point is that the changes only last till the apache package is upgraded (a security update etc..). I would like to find a way that would permanently disable the on boot startup (so that upgrading the apache package wouldn't cause automatic startup again).

Ah.  That's either a bug or a misfeature in the update.  Either way the chance to get it changed would be by filing a bug report in Launchpad.

---

### Post by AlexDudko on 2011-11-13
It's not a bug, it's a usual behavior for Debian based distro's (Debian including).
It's a good practice for servers: there's no need to restart it and to restart a service after it was updated. It restarts automatically.

---

### Post by Lars Noodén on 2011-11-13
Ok. So it does a restart even if the service is not running.  I can't think of a convenient way to change restart's behavior.

---

### Post by kaurman on 2011-11-13
ok...

While we're at it, maybe someone could shed some light on that ([apache security tips]("http://httpd.apache.org/docs/2.0/misc/security_tips.html")):
> 
One aspect of Apache which is occasionally misunderstood is the feature of default access. That is, unless you take steps to change it, if the server can find its way to a file through normal URL mapping rules, it can serve it to clients.

For instance, consider the following example:

 # cd /; ln -s / public_html 
 Accessing [http://localhost/~root/](http://localhost/~root/) 

This would allow clients to walk through the entire filesystem. To work around this, add the following block to your server's configuration:

 <Directory /> 
 Order Deny,Allow 
 Deny from all 
 </Directory> 

This will forbid default access to filesystem locations. 

Apache doesn't share one's whole filesystem by default, does it? To me it seems too insane. So, what is really meant here?

So far i have believed that webroot determines the folder(s) shared but the thing quoted above confused me... My server is set to only listen locally anyway but I'd still like to understand the thing I quoted so any help is much appreciated

---

### Post by AlexDudko on 2011-11-13
It may work if...
If you don't think about security and deliberately give access to your whole file system. If you don't use any other security tools, for instance, SELinux or AppArmor.

---

### Post by kaurman on 2011-11-13
In a typical home network with a router, closed ports and no port forwarding, one should be rather safe anyway as for outside access but the paragraph I quoted is so confusing I just had to ask:D Anyone?

---

### Post by AlexDudko on 2011-11-14
So, what's so confusing about that paragraph? There are  only tips for securing your server.

---

### Post by satanselbow on 2011-11-14
> For instance, consider the following example:

 
It is quoted as an "extreme" example of what not to do - apache is not set to share your / by default and never has been.

---

