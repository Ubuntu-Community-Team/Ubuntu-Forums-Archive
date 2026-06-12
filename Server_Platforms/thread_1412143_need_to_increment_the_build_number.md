---
title: "need to increment the build number"
date: 2010-02-20
forum: Server Platforms
---

### Post by husskii on 2010-02-20
Hi Im trying to get vrtualmin to work on my ubuntu 8.04 server and after Checking Configuration, I get the follow message, that
 
     >  BIND DNS server is installed, and the system is configured to use it.

      Mail server Postfix is installed and configured.

BUT I also get this error......
      The Suexec command on your system is configured to only run scripts under /var/www, but the Virtualmin base directory is /home. CGI and PHP scripts run as domain owners will not be executed.

.. your system is not ready for use by Virtualmin.
-----------------------------------------------------------

Then I found a post that was supposedly the fix to this problem, its called ""Rebuilding Suexec with Different defaults""
and after following a few simple steps like 
```
cd /usr/src
apt-get build-dep apache2.2-common
apt-get source apache2.2-common
cd apache2-2.2.3/
```
then editing debian/rules to change the docroot from /var/www to /home/hosting 
And now Im at a step I know nothing about and was hoping someone could shed some light on it for me...

I need to stop apache getting overwritten with the same version next time you update, and to do that I need to, increment the build number. by running ```
dch -i 
```and edit the build notes at the top to what Ive changed.
that's were I get stuck I know nothing about how to increment the build or at least what to change...

Help on this step would be greatly appreciated

Thanks in advance
Husskii

---

### Post by FuturePilot on 2010-02-20
Hopefully this will help you out [https://wiki.ubuntu.com/PackagingGuide/Complete#changelog]("https://wiki.ubuntu.com/PackagingGuide/Complete#changelog")
There's also some versioning info here [https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage#Versioning]("https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage#Versioning")

Basically if it says something like -1ubuntu2 you want to change it to -1ubuntu3~custom. Note that because of the ~custom (or whatever you choose to call it) if there is a new version pushed out by Ubuntu it will supersede your custom build version.

---

