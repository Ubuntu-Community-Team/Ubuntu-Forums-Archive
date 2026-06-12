---
title: "php won't run outside a certain directory"
date: 2008-06-19
forum: Server Platforms
---

### Post by majikins on 2008-06-19
Hello

For some reason any php file that is located outside a certain directory won't run.  Instead the browser says it wants to download the file.  

The correct php modules are loaded.

I've looked at config files to see if there is a reference to only run php from a certain directory and can't find any.

Can someone help please?

---

### Post by Titan8990 on 2008-06-19
Is this issue only with the machine that is hosting the pages?

---

### Post by majikins on 2008-06-22
No - even when I connect from another pc.

I've fiddled around and managed to 'fix' problem.  Machine was set up with the virtual hosts option for apache.  I created another virtual host file pointing to the right directory.  now all php files get executed along that path.  Anything outside that path gets asked to be downloaded by browser.

Can someone explain this please?

---

### Post by mbeach on 2008-06-22
Where were the php files located?  Were they outside where the default configuation file (/etc/apache2/sites-available/default) had listed?

---

