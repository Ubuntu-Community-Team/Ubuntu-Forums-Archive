---
title: "apache2-mpm-itk restart problem"
date: 2011-06-03
forum: Server Platforms
---

### Post by MisterM on 2011-06-03
Hi,

I'm trying to use apache2-mpm-itk on a new ispconfig 3 installation. I mostly followed the instructions in [The Perfect Server - Ubuntu 10.04 [ISPConfig 3]]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p4") article, with some changes: I didn't install apache2-mpm-prefork, apache2-suexec and libapache2-mod-suphp, and instead installed apache2-mpm-itk. I then changed SuexecUserGroup to AssignUserId in ispconfig.vhost and apps.vhost. Furthermore, I copied all the prefork settings in apache2.conf to <IfModule mpm_itk_module>[...]</IfModule>.

Now, the itk module seems to be working fine - i.e. the scripts run as the correct user. However, apache now produces an error when I try to restart it:
```
Address already in use: make_sock: could not bind to address 0.0.0.0:80
```

It seems that the init script is unable to terminate any of the apache processes running under the webX users. When I run 'service apache2 stop', all the root and www-data owned apache processes stop, but the webX owned ones remain. If I then kill them with 'killall -9 apache2', I can start apache again.

This happens every time I had previously opened any site on the server, even ispconfig. If I don't open any site after starting apache, it restarts fine, since there is no webX owned apache process running.

Did I mess something up in the configuration? What could be the cause of this problem?

---

