---
title: "Some zombies"
date: 2009-08-07
forum: Server Platforms
---

### Post by dragos2 on 2009-08-07
I have gnome-core applied there and I /etc/init.d/gdm restart. 
I think that is the cause.

Any ideas of how to get rid of them without a restart ?

```

dragos@ubu:~$ ps aux | grep Z
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
1007      3720  0.0  0.0      0     0 ?        Z    09:33   0:00 [xrdb] <defunct>
1007      5244  0.0  0.0      0     0 ?        Z    09:05   0:00 [xrdb] <defunct>
1007      8462  0.0  0.0      0     0 ?        Z    09:12   0:00 [xrdb] <defunct>
1007      9810  0.0  0.0      0     0 ?        Z    Aug06   0:00 [gnome-settings-] <defunct>
1007     10098  0.0  0.0      0     0 ?        Z    Aug06   0:00 [xrdb] <defunct>
1007     10220  0.0  0.0      0     0 ?        Z    Aug06   0:00 [xrdb] <defunct>
1007     10429  0.0  0.0      0     0 ?        Z    Aug06   0:00 [xrdb] <defunct>
1007     10600  0.0  0.0      0     0 ?        Z    Aug06   0:00 [xrdb] <defunct>
1007     10784  0.0  0.0      0     0 ?        Z    Aug06   0:00 [xrdb] <defunct>
1007     18100  0.0  0.0      0     0 ?        Z    07:07   0:00 [xrdb] <defunct>
1007     18421  0.0  0.0      0     0 ?        Z    07:21   0:00 [xrdb] <defunct>
1007     18627  0.0  0.0      0     0 ?        Z    07:33   0:00 [xrdb] <defunct>
1007     21967  0.0  0.0      0     0 ?        Z    08:51   0:00 [xrdb] <defunct>
1007     22324  0.0  0.0      0     0 ?        Z    08:53   0:00 [xrdb] <defunct>
1007     22440  0.0  0.0      0     0 ?        Z    08:56   0:00 [xrdb] <defunct>
1007     22519  0.0  0.0      0     0 ?        Z    08:57   0:00 [xrdb] <defunct>

```

---

### Post by Serangan on 2009-08-07
I use pkill -u <username>

Maybe this might work for you?

---

### Post by dragos2 on 2009-08-07
> **Serangan said:**
> I use pkill -u <username>

Maybe this might work for you?

Zombies can't be killed. Only if I kill the master process - the one I don't know.

---

### Post by wojox on 2009-08-07
> **dragos2 said:**
> Zombies can't be killed. Only if I kill the master process - the one I don't know.

Right you cannot kill what's already dead. You would have to kill the parent or live with it. Their dead so it's only taking up space in a file. I would try 
```
/etc/init.d/gdm stop
```
```
/etc/init.d/gdm start
```

---

### Post by dragos2 on 2009-08-07
> **wojox said:**
> Right you cannot kill what's already dead. You would have to kill the parent or live with it. Their dead so it's only taking up space in a file. I would try 
```
/etc/init.d/gdm stop
``````
/etc/init.d/gdm start
```

Before doing that comand I did not have any zombies. But I did a /etc/init.d/gdm restart
in order to kill a gnome session that hanged but it had some adverse effects.

You think that full stop and start will kill the zombies ?

---

### Post by scorp123 on 2009-08-08
> **dragos2 said:**
> Zombies can't be killed. Only if I kill the master process - the one I don't know. And if you use **ps -efH ** to see which process spawned which other process?

---

