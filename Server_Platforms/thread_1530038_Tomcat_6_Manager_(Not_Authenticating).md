---
title: "Tomcat 6 Manager (Not Authenticating)"
date: 2010-07-13
forum: Server Platforms
---

### Post by px7659 on 2010-07-13
Hello,

I'm having an issue using tomcat6-admin. I installed Tomcat 6 using Ubuntu Software Center and also installed the tomcat6-admin package.

I got the server on [http://localhost:8080](http://localhost:8080) and it seems to be fine. But I can't seem to use the manager. 

So I edited **/var/lib/tomcat6/conf/tomcat-users.xml** and added:

```

<role rolename="manager"/>

<role username="manager" password="manager" roles="manager/>
```

However, if I try to then go to the manager again [http://localhost/manager/html](http://localhost/manager/html), a dialog box will appear prompting for my credentials, where I would enter **manager** as both the user name and password. However, the dialog box just continues to reappear, looping the authentication sequence.

By clicking on **cancel** an HTTP 401 error will appear.

Is there any workaround I can do, or am I doing anything wrong?

---

