---
title: "service [re]start problem...have screenshot"
date: 2011-01-18
forum: Server Platforms
---

### Post by alfamuzjak on 2011-01-18
Tell me why i can't stop or restart service with:
```
sudo /etc/init.d/vsftpd restart
```

or:
```
sudo service vsftpd restart
```

I attach my screenshot

---

### Post by RobbanC on 2011-01-18
Not sure. Tried to google and see what could be found. Looks like a bug somewere around the service-command. Again, I'm really not sure and can not find anything useful when searching.

Does it work anyway if you ignore the warning and use:
```

sudo /etc/init.d/vsftpd restart

```

Maybe someone else knows a better solution, to be able to use command 'service' ???

---

### Post by alfamuzjak on 2011-01-18
> **RobbanC said:**
> Not sure. Tried to google and see what could be found. Looks like a bug somewere around the service-command. Again, I'm really not sure and can not find anything useful when searching.

Does it work anyway if you ignore the warning and use:
```

sudo /etc/init.d/vsftpd restart

```

Maybe someone else knows a better solution, to be able to use command 'service' ???

.../etc/init.d/vsf... never worked for me.
I dont know why

---

### Post by koenn on 2011-01-18
according to the warning, ```
sudo restart vsftpd
``` might work.

to see why "sudo /etc/init.d/vsftpd restart" doesn't work, you might just read the file /etc/init.d/vsftpd and figure out why it would complain about such things.

---

### Post by GDR! on 2011-01-18
> **koenn said:**
> according to the warning, ```
sudo restart vsftpd
``` might work.

It will restart the computer, actually.

My suggestion is to look at ftpd error log in /var/log and see if the error is there. Something may also be in /var/log/messages. Otherwise I usually kill the service (killall -9 vsftpd) and start it from command line (vsftpd). This way 
you can see all the warnings vsftpd prints.

---

### Post by koenn on 2011-01-18
> **GDR! said:**
> It will restart the computer, actually.
doesn't look like it
```

@knoerft:~$ restart

restart: missing job name
Try `restart --help' for more information.

```

---

### Post by GDR! on 2011-01-18
Whoops. Sorry.

---

