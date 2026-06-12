---
title: "Totally hosed apache2 after dist-upgrade"
date: 2008-06-20
forum: Server Platforms
---

### Post by TANGUN on 2008-06-20
Ok. The working server was running Server 6.10

I thought it would be a good idea to upgrade to a newer version.

BAD IDEA.

Now, apache2 will not start at all. It will not accept the /etc/apache2/apache2.conf file(Syntax error on ln 116). It's telling me that /etc/apache2/mods-enabled/mod-security.load has a syntax error on ln 1 and that /usr/lib/apache2/modules/mod-security.so doesn't exist.

This really bites. After the upgrade everything worked just fine for the rest of the evening. I shut it down for the evening and brought it up in the morning only to be greeted by the ability to type only in all caps (?), the server giving me a login but then still loading some modules and then appearing to hang on the last one...but if you hit enter it drops you to the login. What the hell. I've been searching for answers on this and it's driving me insane.  I'll post the file lines that are supposedly wrong.

apache2.conf line 116:
Include /etc/apache2/mods-enabled/*.load

mod-security-load line 1
LoadModule security_module /usr/lib/apache2/modules/mod_security.so

Update:
I tried to reinstall apache2...yet another bad idea. Now trying to restart apache gives me a: No apache MPM package installed.

I'm already guessing I have to reinstall everything...but I'm hoping there's a slightly less painful way to fix this.

Help?

---

### Post by TANGUN on 2008-06-20
Well. After doing some digging I think I found out what the whole problem is. Somewhere along the line mod_security was removed from the package lists. Somehow, the reference to it is still in some apache2 update file. So, somehow I managed to find a way to upgrade Ubuntu, completely screw up every single setting and hose several months of work. Great. I have to reinstall everything I had to see if it will ever work again. This is as bad as a Windows update.

---

### Post by lodp on 2008-06-20
You shouldn't have to do a complete re-install if it's only apache2 that isn't working properly.

I'm not an expert, but what I would try is something like

> 
sudo a2dismod mod_security

or if that doesn't work, remove /etc/apache2/mods-enabled/mod_security.load manually.

That should keep it from trying to load that module that isn't there..

---

