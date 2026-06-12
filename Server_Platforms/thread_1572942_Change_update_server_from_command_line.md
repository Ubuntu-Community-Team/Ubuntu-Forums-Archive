---
title: "Change update server from command line"
date: 2010-09-12
forum: Server Platforms
---

### Post by fei on 2010-09-12
On Ubuntu Desktop editions, there is a GUI application which allows easily changing to a different server. It can even find out how one is the fastest update server.

Is there a corresponding command line tool available to do this? Because I'm using the Server edition without GUI. I hate to manually edit /etc/apt/source.list.

:)

---

### Post by alan8 on 2010-09-12
Hi, there is a CLI packages manager. Run

```

aptitude

```command... however I am not sure if you can change repository location with it.

---

### Post by Nythain on 2010-09-12
edit --

lol, re-read that, was gonna tell ya to just edit sources.list by hand... which you're trying to avoid doing... thats about the only way i really do it, but the above mentioned
aptitude
should allow for it similarly to synaptic in one way or another

---

### Post by slakkie on 2010-09-12
```

sudo perl -p -i.orig -e 's/archive.ubuntu.com/nl.archive.ubuntu.com/' /etc/apt/sources.list 

```

Something like this?

---

### Post by lgvh on 2010-11-27
I think that this is the information that you are looking for:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

