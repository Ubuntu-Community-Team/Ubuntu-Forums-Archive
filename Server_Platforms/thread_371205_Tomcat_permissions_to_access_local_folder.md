---
title: "Tomcat permissions to access local folder"
date: 2007-02-26
forum: Server Platforms
---

### Post by lamadredelsapo on 2007-02-26
I'm trying to grant read permissions to a local folder from a web service, but even though I've added the following 
```
grant codeBase "file:/home/fernando/movies" {
  permission java.io.FilePermission "<<ALL FILES>>", "read";
};

grant codeBase "file:/home/fernando/movies/*" {
  permission java.io.FilePermission "<<ALL FILES>>", "read";
};
```

into the catalina.policy file I'm not able to put it to work. Any ideas?

---

### Post by lamadredelsapo on 2007-03-01
No one has done this ever?

---

### Post by lamadredelsapo on 2007-03-01
Just fixed it, it is as easy as creating a file like AXIS.policy under /etc/tomcat5/policy.d, and adding to it something like:
```
grant{
  permission java.io.FilePermission "yourLocalFolder", "read";
};
```

This would be automatically added to catalina.policy when tomcat is restarted.

With the above code what you grant is reading permissions to any class loaded by tomcat.

Hope this helps anyone with little knowledge about AXIS (my case).

---

### Post by sandeep_khurana on 2008-04-17
Did you make entries for AXIS?

Actually i am also making web services using Axis2, but not getting why axis needs permission in policy file. i made a simple web service.....

Can you help explain me the scenario....

Thanks..

---

