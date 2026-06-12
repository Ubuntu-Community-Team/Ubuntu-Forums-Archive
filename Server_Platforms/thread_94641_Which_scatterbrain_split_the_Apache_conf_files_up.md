---
title: "Which scatterbrain split the Apache conf files up?"
date: 2005-11-24
forum: Server Platforms
---

### Post by ChristAlmighty on 2005-11-24
Thanks that's a whole lot better! :rolleyes:

---

### Post by LordHunter317 on 2005-11-24
It's a good thing, and frankly, if you can't immediately understand why, I'm not sure it's even worth my breath to explain it to you.

Modular configurations are a good thing for everyone, really.

---

### Post by ChristAlmighty on 2005-11-24
Everybody? Maybe multitasking schizophrenics yes. I'll tell you what has happened right now. Someone let a C++ programmer loose on the user interaction end of Apache2 hence the conf files everywhere. Apache is a web server used by laymen not a C++ compiler that loads a hundred header files from everywhere. Programmers who needs em, talk to the computer cos the end user ain't listening.

---

### Post by LordHunter317 on 2005-11-24
[QUOTE=ChristAlmighty]Everybody?[/quote]Yes, nearly everyone, and I'll explain how:[list][*]It's better for packages because they don't have to write code to edit a file when you install a 3rd party Apache module.  They simply have to add/remove files.  This is orders of magnitude easier.  It also benefits the system administrator because installing the module package is all they need to do.[*]It's better for system administrators who have many virtual sites because the sites are now split up in to logical chunks.[*]The a2* commands mean I don't have to fire up a text editor to just enable/disable a site or  module.  This is a big advantage doing administration over slow remote links.[/list]

> Someone let a C++ programmer loose on the user interaction end of Apache2 hence the conf files everywhere.No, Apache2's source ships with a single monolithic configuration file.  This is a Debian/Ubuntu specific customization, and the package documentation is explained by many.

> Apache is a web server used by laymenNo, it's used by professional system and network administrators primarily.  Then software developers, like myself.  Finally, laymen.  

> Programmers who needs em?You do.  If you absorbed all this energy trolling into critical analysis, you might actually see the benefit.

---

### Post by ChristAlmighty on 2005-11-24
Trolling!? I'll use 1.3 until I find a less cryptic web server.

---

### Post by LordHunter317 on 2005-11-24
You are.  You've yet to give a valid reason as to why the configuration layout Ubuntu provides is a bad thing, and I've provided several valid reasons as to why it's a good thing.

Debian's Apache 1.3 isn't monolothic either.

---

