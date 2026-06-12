---
title: "BIND9 not showing in &quot;Services Setup&quot;"
date: 2005-10-31
forum: Server Platforms
---

### Post by hostile on 2005-10-31
Hello everyone,

How do I get system services to show up in the GUI?:

System -> Services

BIND is not showing up there for me, and I would like to know how to correct this should I install any other services and they do not appear.

TIA.

---

### Post by dbee on 2005-10-31
If you've just installed bind, you'll have to kill the GUI and start it up again for new programs to show ...

---

### Post by hostile on 2005-11-01
> If you've just installed bind, you'll have to kill the GUI and start it up again for new programs to show ...

Nope... it's not there...

:confused:

If I do a ps aux, I can see that named is running, and I don't have a problem controlling it from init.d, it's just I'd like it to be listed under the GUI services applet... call me anal...

---

### Post by dbee on 2005-11-01
try 
```

killall gnome-panel

```
... not too sure what the gui services applet is, cause I have no system -> services on my ubuntu (hoary).

... can you add panel by right-clicking on the bottom right-hand side of the screen ? 
Even though that's probably not what you're looking for.

---

### Post by hostile on 2005-11-01
[QUOTE=dbee]try 
```

killall gnome-panel

```
... not too sure what the gui services applet is, cause I have no system -> services on my ubuntu (hoary).

... can you add panel by right-clicking on the bottom right-hand side of the screen ? 
Even though that's probably not what you're looking for.[/QUOTE]



Under the Breezy GUI, its under System -> Administration -> Services.

Once that is open, it's a list of all the daemons your system is running. You can then put a check beside them to either start at boot or not. named is not there at all for me...

---

