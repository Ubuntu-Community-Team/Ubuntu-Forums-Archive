---
title: "Can't start Tomcat 6"
date: 2010-05-11
forum: Server Platforms
---

### Post by mosquetero on 2010-05-11
Hi!

I am trying to start the Tomcat Server 6 to deploy a .war file in the webapps folder. If I try to do it by typing:

```
sudo ./ /usr/share/tomcat6/bin/startup.sh
```

I get the next log:

```
Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:       /usr
touch: cannot touch `/usr/share/tomcat6/logs/catalina.out': No such file or directory
./catalina.sh: 357: cannot create /usr/share/tomcat6/logs/catalina.out: Directory nonexistent

```

If I do it by typing sudo /etc/init.d/tomcat6 start, I get no problems and looks like it is working since I get a IT WORKS! when writing localhost:8080/ as the URL in my browser. However, it does not uncompress the .war and even if I uncompress it by hand and place the folder in the webapss, it does not shows the webapplication :(.

Anyone can help me please??

Thanks

---

