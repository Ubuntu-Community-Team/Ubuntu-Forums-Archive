---
title: "redirect output boot script"
date: 2012-09-12
forum: Ubuntu Application Development
---

### Post by cris_1986 on 2012-09-12
hy,
i have a python script. It works. 
example:
```

#!/usr/bin/env python
print "hello world"

```

i have put this script in the startup applications (system -> preference -> startup application)

i don't know if this script work at the boot. there is a way to redirect the output in a file?

This is my /home/user/.config/autostart/script.desktop file:

```

[Desktop Entry]
Type=Application
Exec=python /home/user/.scrscript/.script.py &> /home/user/log.txt
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[it_IT]=example
Name=example
Comment[it_IT]=python 
Comment=python 

```

---

### Post by iponeverything on 2012-09-12
```
Exec=python /home/user/.scrscript/.script.py > /home/user/log.txt 2>&1 &
```

---

### Post by brad103 on 2013-04-20
This doesn't work for me (12.04)


```
[Desktop Entry]
Type=Application
Exec=firefox file:///opt/peace/index.html?datamode=7 > /var/log/peace/firefox.log 2>&1 &
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_NZ]=firefox
Name=firefox
Comment[en_NZ]=
Comment=
```

```
ls -l /var/log

...
drwxrwxrwx 2 usr1              usr1    4096 Apr 20 20:27 peace
...
```

I tried with and without trailing ampersand (which is assumed anyway as it's startup apps are backgrounded tasks)

Any thoughts?

Thanks

---

### Post by brad103 on 2013-04-29
Anybody got any thoughts?

---

### Post by schragge on 2013-04-29
Well, firefox writing nothing on standard output when starting up is normal. What are you trying to log?

---

### Post by brad103 on 2013-04-30
I use window.dump from firefox and it outputs fine when run directly from a shell. Fair point, but I do expect valid output from firefox in this instance. Thanks

---

### Post by brad103 on 2013-05-06
Still unresolved. Any further advice?

---

