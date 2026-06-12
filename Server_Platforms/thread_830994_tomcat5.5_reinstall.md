---
title: "tomcat5.5 reinstall"
date: 2008-06-16
forum: Server Platforms
---

### Post by dexter.deepak on 2008-06-16
i tried a complete removal of tc5.5 from my ubuntu (gutsy) system which was successful.. now i am trying the reinstall of tc5.5 from synaptic manager, but it is giving some errors like this :
 E: tomcat5.5: subprocess post-installation script returned error exit status 1 
E: jspwiki: dependency problems - leaving unconfigured 
E: tomcat5.5-admin: dependency problems - leaving unconfigured 
E: tomcat5.5-webapps: dependency problems - leaving unconfigured 

now i wonder which dependencies i have left... i am marking all the dependencies pointed by synaptic

this message is persisting through all my post installations.

now i just cant figure out what to do in order to have a "FRESH" tomcat :confused:

---

### Post by dexter.deepak on 2008-06-16
please reply...i cant either repair nor remove and reinstall tc...
i am stuck:mad:

---

### Post by dexter.deepak on 2008-06-16
..and whatever i am installing through synaptic..it gives the same error message after each install :

E: tomcat5.5: subprocess post-installation script returned error exit status 1
E: jspwiki: dependency problems - leaving unconfigured
E: tomcat5.5-admin: dependency problems - leaving unconfigured
E: tomcat5.5-webapps: dependency problems - leaving unconfigured

---

### Post by norbini on 2008-10-13
I realise this might be a bit late for you dexter.deepak, but I had a similar problem and wanted to post the fix that got it working for me.

I roughly followed the advice in the following post:
[https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/229404](https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/229404)

Basically:
$ sudo gedit /etc/default/tomcat5.5

Uncommented the JAVA_HOME line and resaved.
The line now looks like:

JAVA_HOME=/usr/lib/jvm/java-6-sun

on my system, but your path may differ I suppose.

Then:
$ sudo apt-get -f install

Hope this helps.

---

### Post by juliangamble on 2008-11-05
Can I just say - fixing jspwiki after the ibex upgrade was a royal pain! 

Package maintainers - please fix this! 

Here is what I did:

1. Upgraded to ibex from hedgehog using aptitude

2. Follow the instructions here:
[http://roshan18.wordpress.com/2007/11/18/using-servlets-in-ubuntu-gutsy-gibbon/](http://roshan18.wordpress.com/2007/11/18/using-servlets-in-ubuntu-gutsy-gibbon/)

3. Change the mods to jk.load to this:
---apend
JkWorkersFile /etc/libapache2-mod-jk/workers.properties
JkLogFile /var/log/apache2/mod_jk.log
JkLogLevel debug
#JkLogStampFormat .[%a %b %d %H:%M:%S %Y] .
JkMount /jsp-examples ajp13_worker
JkMount /jsp-examples/* ajp13_worker
JkMount /servlets-examples ajp13_worker
JkMount /servlets-examples/* ajp13_worker
JkMount /jspwiki ajp13_worker
JkMount /jspwiki/* ajp13_worker

4. Add the following to the second line of
/etc/apache2/sites-enabled/000-default

JkMountCopy On

5. Change the following:
/etc/jspwiki/jspwiki.properties

#     java.security.policy=/path-to/jspwiki.policy
java.security.policy=/usr/share/jspwiki/WEB-INF/jspwiki.policy

#jspwiki.aclManager          = com.ecyrd.jspwiki.auth.acl.DefaultAclManager



Could we NOT repeat this for 9.04 please?

(Or at least have some public documentation on how this is done)

JG

---

