---
title: "Server Configuration Command"
date: 2008-11-11
forum: Server Platforms
---

### Post by kambizkamrani on 2008-11-11
What is the command to return back to this configuration 'window' after completing installation?

[IMG]http://www.ubuntugeek.com/images/hardyl/30.png[/IMG]

I can't for the life of me figure it out, so any help would be really appreciated!

Thanks,

Kambiz

---

### Post by Iowan on 2008-11-11
I've never seen that page after initial visit...
 choose wisely the first time ;)

---

### Post by cariboo on 2008-11-11
I think you are looking for:

```
sudo tasksel
```

This will bring up the menu. See screenshot.

Jim

---

### Post by Vegan on 2008-11-11
I ended up setting up everything manually from the terminal window as that component did not install the LAMP etc as desired. No problem, I speak bash.

sudo apt-get install apache2
sudo apt-get install mysql
sudo apt-get install php5

etc etc etc

:guitar:

---

### Post by kambizkamrani on 2008-11-11
> **cariboo907 said:**
> I think you are looking for:

```
sudo tasksel
```

This will bring up the menu. See screenshot.

Jim

Many thanks Jim. I really appreciate it!

---

