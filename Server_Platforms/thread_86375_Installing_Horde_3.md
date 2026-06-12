---
title: "Installing Horde 3"
date: 2005-11-05
forum: Server Platforms
---

### Post by igb on 2005-11-05
I have been using Horde2 on my Hoary server for ages. When I set up a new server with Breezy I installed Horde3. In apache I have:

 ```
       Alias /mail/ "/usr/share/horde3/"
        <Directory "/usr/share/horde3/">
            Options Indexes MultiViews
            AllowOverride All
            Order allow,deny
            Allow from all

        </Directory>
```

When I access [http://myhost/mail/](http://myhost/mail/) I should get directed to a page that lets me do the inital configuration of Horde. However, I get the following error:

The requested URL /horde3/login.php was not found on this server.

Running [http://mydomain/mail/test.php](http://mydomain/mail/test.php) shows the test page correctly and this doesn't report any errors. Has anyone managed to configure horde3 on Breezy?

Ian.

---

### Post by jameso on 2005-11-16
I had the same problem.

I edited the config/registry.php file, and I got a bit further (the page loads etc).

However, things still seem to be quite broken.

I think I'll try and install Horde from scratch.

---

### Post by genii on 2006-01-11
I'm having similar problems, seems to be related to the default options that PHP and PEAR get installed with. "test.php" has a *LOT* of red entries. Gonna try some stuff and report back.

---

### Post by alklein on 2006-01-12
I just installed Horde3 last night using synaptic.  I noticed some of the packages were version 3 and others seemed to still be on version 2.  I can't list which are which because I'm at work and access is restricted.  

After quite a bit of hunting around, I discovered the MySQL setup scripts for the apps.  I can authenticate as Administrator and a newly created user.  I am seeing a recurring error on every screen, no matter who I log in as - the top left frame shows:

Notice: Only variable references should be returned by reference in /usr/share/horde3/lib/Horde/Notification.php on line 98

This message appears consistently, no matter what screen in Horde I'm in.  It also seems the permissions for the default installs are wrong - I've had to manually update all the config files and get an error on saving them from the web interface under "setup".

If anyone has successfully installed Horde 3 and related packages on 5.10, I'd appreciate any insight or advice.

Adam Klein

---

