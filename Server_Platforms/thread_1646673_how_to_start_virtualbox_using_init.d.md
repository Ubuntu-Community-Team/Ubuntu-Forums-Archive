---
title: "how to start virtualbox using init.d"
date: 2010-12-16
forum: Server Platforms
---

### Post by ryannathans on 2010-12-16
hey guys :) 

recently installed phpVirtualBox and VirtualBox on my 10.04 LTS ubuntu server

it's getting annoying having to type

```
/usr/bin/vboxwebsrv -b --logfile /dev/null >/dev/null  
```every time i reboot the server

tried for hours to make an init.d script that will run it but failed... haha

basically I just want it to automatically run the above command on every boot.

hoping you guys can help me out, please? 


-Much Appreciated
Ryan

---

### Post by rubylaser on 2010-12-16
Well here's a few easy commands to get it going...

```
sudo -i
```

```
nano /etc/init.d/vboxserver
```
and paste your line in...
```
#! /bin/bash
/usr/bin/vboxwebsrv -b --logfile /dev/null >/dev/null
```

```
chmod +x /etc/init.d/vboxserver
```

And add it to various runlevels
```
update-rc.d vboxserver defaults
```

Hope that helps.

---

### Post by ryannathans on 2010-12-16
thanks man, I will see if that works now, I did everything except the last command before :)

---

### Post by CharlesA on 2010-12-16
I just threw it in a crontab with the @reboot flag.

Found that easier then trying to make/create an init script.

---

### Post by rubylaser on 2010-12-16
That's a great solution as well.  I don't ever think to use crontab for services, but that's a quick way to do it.

---

### Post by ryannathans on 2010-12-16
YES! You are my hero xD hahaha 

thanks man!

---

### Post by rubylaser on 2010-12-16
Great, glad to hear it. Make sure to mark the thread as [COLOR="Red"][SOLVED][/COLOR] so that others can benefit when using the search function

---

### Post by ryannathans on 2010-12-16
done :D

---

