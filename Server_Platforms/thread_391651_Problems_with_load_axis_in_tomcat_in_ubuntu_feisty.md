---
title: "Problems with load axis in tomcat in ubuntu feisty"
date: 2007-03-23
forum: Server Platforms
---

### Post by romaluca on 2007-03-23
I upgrade my ubuntu and ubuntu have move axis folder from /usr/tomcat 5.5/webbapps to /var/lib/tomcat5.5/webapps

But now axis not is loaded if i click on start in tomcat manager i receive this message:
FAIL - Application at context path /axis could not be started

Why??
What cai i do?
Thanks

---

### Post by vguhesan on 2007-04-22
I upgraded to Fiesty and my Tomcat does not come up at all. I even tried to uninstall and re-install but same issue. The script under /etc/init.d/tomcat5.5 seems to come up but no logs files are created and java-catalina is not one of the processes running in the memory...

Port is also not bound...

Does anyone having similar issues?

Venkatt

---

### Post by Jof84 on 2007-04-22
Have a look at this. It helped for me:

[https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/97096](https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/97096)

---

