---
title: "Upstart: &quot;on started mysql&quot; does not work"
date: 2008-05-15
forum: Server Platforms
---

### Post by timothyp on 2008-05-15
Hi,

I need to define an upstart job which is executed AFTER
mysql has been started.


```

start on started mysql
stop on stopped mysql

console output

script
 echo "Firewall configuration"
 sh /usr/bin/firewall-after-mysql.sh
end script

```


But it is never executed. Any ideas?

---

