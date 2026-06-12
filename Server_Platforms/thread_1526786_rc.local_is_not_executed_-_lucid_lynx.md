---
title: "rc.local is not executed - lucid lynx"
date: 2010-07-08
forum: Server Platforms
---

### Post by aba3k on 2010-07-08
My commands are not executed in rc.local, i can execute them fine typing them.  Don`t matter the command, they`re not executed.
As a example the command:
echo "81920" > /proc/sys/net/netfilter/nf_conntrack_max
is not executed.
rc.local don't appear to be executed during bootime, i can execute they latter typing:
invoke-rc.d rc.local start

tips?

---

### Post by cdenley on 2010-07-08
Seems to work fine for me.
```

ls -l /etc/rc.local
cat /etc/init/rc-sysinit.conf
cat /etc/init.d/rc.local
cat /etc/rc.local

```

---

### Post by sisco311 on 2010-07-08
Upstart operates asynchronously. rc.local often runs too soon. Try adding a sleep command at the top of the script:
```
sleep 10
echo "81920" > /proc/sys/net/netfilter/nf_conntrack_max

```
Or write an Upstart job,
/etc/init/my-job.conf:
```

#
#/etc/init/my-job.conf
#

description     "whatever"

start on virtual-filesystems

script
echo "81920" > /proc/sys/net/netfilter/nf_conntrack_max
end script

```

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by MidSpeck on 2010-07-08
sisco311's answer is probably what you need.  However, make sure that /etc/rc.local has the execute bit set or it won't run.
```
chmod +x /etc/rc.local
```

---

### Post by leif_anderson on 2010-07-25
I had the same problem. The sleep command sisco311 suggested worked fine for me. Thank you. Now my trackpoint works fine again. The old settings nearly broke my finger in a half

---

