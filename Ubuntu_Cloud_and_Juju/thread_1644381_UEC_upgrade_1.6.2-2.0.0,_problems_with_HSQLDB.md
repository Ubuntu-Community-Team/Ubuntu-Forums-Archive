---
title: "UEC upgrade 1.6.2-2.0.0, problems with HSQLDB"
date: 2010-12-13
forum: Ubuntu Cloud and Juju
---

### Post by amnovikov on 2010-12-13
Hello everyone!  

I`ve got problem during automated upgrade process from Eucalyptus 1.6.2 to 2.0.0 on UEC x64 10.0.4LTS to Ubuntu 10.10 server.  
In two words - apt-get and other tools(update-manager) find&amp;download and replace existing packages with new ones. With some packages there are configuration changes - so process ask user what config will be - old or new. 
So, the problem. 
I`ve replace /etc/eucaliptus/eucalyptus.conf ,cause some new values added, and remove JVM_MEM option &amp;quot;512m&amp;quot;. But when started some process that reconfig HSQLDB eucaliptus tables, it faced with java heap error, try to reconnect &amp;reconfig, but finally stuck. In some time, after manually running &amp;quot;dpkg --configure eucalyptus-java-common&amp;quot; and removing and then installing it again, DB reconfig process was also not successed, but it ends his work (not with Ctrl+C key) and update somehow finished. 
As it obvious in such condition there is now working cloud HSQLDB, but I also has some previous backups.  

My question is - can I somehow use these backups to restore previous 1.6 Cloud configuration (Users,Images, etc) and will I have to reconfig it again? If so - what commands can you give in advice?  

Further ---------   
Has anyone some ideas where I`m mistaken?  
On Ubuntu 10.10 server I temporary change apt repos to LTS and install eucalyptus v.1.6.2. Than recreate or check /var/lib/eucalyptus (especially ./keys ./.ssh and ./db directories ), than change back repos and do upgrade - only eucalyptus packages upgraded. Again error with java heap space - possible walrus db is too large:  

```
root@cloud:~# ls -la /var/lib/eucalyptus/db/ total 40344 -rw-r--r-- 1 eucalyptus eucalyptus 41093528 2010-12-10 21:00 eucalyptus_walrus.script  
```Now, there are such errors as - downgraded eucalyptus 1.6.2 doesnt work correctly and even allow to configure itself (web interface doesnt work, euca_conf --register-cluster .. also). Upgraded finally lost all db values and go with a new one made by own.  

What should I do to use data from old HSLDB? 
Where should I put options for JVM to not overheaped? (in eucalyptus.conf looks like it doesnt matter) 
or another comments, please

---

### Post by kim0 on 2010-12-13
Hi Amnovikov,
I would suggest posting your question on the mailing list as well, since it's too technical
Good luck

---

### Post by raymdt on 2010-12-15
Hi amnovikov,
this might help you

 [http://open.eucalyptus.com/wiki/backup-eucalyptus-16](http://open.eucalyptus.com/wiki/backup-eucalyptus-16)

[http://open.eucalyptus.com/wiki/EucalyptusUpgrade_v2.0](http://open.eucalyptus.com/wiki/EucalyptusUpgrade_v2.0)

regards

---

