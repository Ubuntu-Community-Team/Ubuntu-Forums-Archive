---
title: "howto make uec-component-listener startup when system boot up?"
date: 2011-07-16
forum: Ubuntu Cloud and Juju
---

### Post by zhangr on 2011-07-16
As the title,

I've install Cloud controller and node controller on the same box for test.

And I found although /etc/init/uec-component-listener.conf exists, but it won't start up automatically when system boot up. That means I have to login and bring it up every time when I restart the cc.

I've investigated the upstart configuration file, it have following entries to control when to bring it up:
```

start on (started eucalyptus-cloud and started eucalyptus-cc)
stop on (stopping  eucalyptus-cloud or stopping eucalyptus-cc)

```
But I suspect it doesn't work at all.

Do you have any ideas?
1) Do not suggest me use update-rc.d to add sysv style startup script, I've tried, it won't work, because in the beginning of start script it have following specify the script name:
```

INITSCRIPT="$(basename "$0")"

```
So after you add it into rc2.d, its name will be something like S95uec-component-listener, and system can't find it in init.d

2) Do not suggest me to add the command "start uec-component-listener" into rc.local. Since I want to stop it when turn off the box.

Thanks in advance.

---

### Post by Buslawekee on 2011-07-29
> **zhangr said:**
> As the title,

I've install Cloud controller and node controller on the same box for test.

And I found although /etc/init/uec-component-listener.conf exists, but it won't start up automatically when system boot up. That means I have to login and bring it up every time when I restart the cc.

I've investigated the upstart configuration file, it have following entries to control when to bring it up:
```

start on (started eucalyptus-cloud and started eucalyptus-cc)
stop on (stopping  eucalyptus-cloud or stopping eucalyptus-cc)

```But I suspect it doesn't work at all.
   [bladeless   fan](http://www.bladelessfanstore.com/) [x360key](http://www.x360keymall.com/)   [buy fan](http://www.bladelessfanstore.com/oscillating-fans.html) 
Do you have any ideas?
1) Do not suggest me use update-rc.d to add sysv style startup script, I've tried, it won't work, because in the beginning of start script it have following specify the script name:
```

INITSCRIPT="$(basename "$0")"

```So after you add it into rc2.d, its name will be something like S95uec-component-listener, and system can't find it in init.d

2) Do not suggest me to add the command "start uec-component-listener" into rc.local. Since I want to stop it when turn off the box.

Thanks in advance.
I can't find that

---

