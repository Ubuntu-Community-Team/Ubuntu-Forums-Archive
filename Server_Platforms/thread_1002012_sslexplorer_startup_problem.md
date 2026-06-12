---
title: "sslexplorer startup problem"
date: 2008-12-04
forum: Server Platforms
---

### Post by loonyjuice on 2008-12-04
Picture the scene: 

Sslexplorer is setup successfully and all is well. You can login, do what you like and logout as often as you like.

Then you reset your Ubuntu box.

You then try to connect to said box again, using sslexplorer, and it states invalid credentials! How can this be? I've already set the wrapper.conf file to add this line:

*wrapper.java.additional.1=-Dfile.encoding=UTF-8*

and in the system.properties file:

*file.encoding=UTF-8*

Can anyone explain why, once it's come back up again, the only way I can get sslexplorer to work is to do:

sudo /etc/init.d/sslexplorer restart

I'm using intrepid, if it matters?

Thanks in advance,

Martin

---

### Post by loonyjuice on 2008-12-09
Shameless bump. Anyone?

---

