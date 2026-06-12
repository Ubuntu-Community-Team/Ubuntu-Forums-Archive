---
title: "phpbb3/unbuntu question"
date: 2010-09-09
forum: Server Platforms
---

### Post by rollnhvy on 2010-09-09
I am in the middle of installing phpbb3. The install wont continue becuase i cant write to the file config.php. It see's the file but doesnt have permission to write to it. I logged in as ROOT and changed the permissions but it didnt help. I am a total new with the unix/linux operating enviroment so please go easy on me. Currently i am set up as localhost(server is in living room).

---

### Post by rollnhvy on 2010-09-10
bump for some help

---

### Post by lisati on 2010-09-10
When I installed phpBB3 on my [server]("http://lisati.homelinux.com/forum"), I followed the guide [here]("https://help.ubuntu.com/community/PhpBB3"). The only thing I recall doing differently to what the guide says is using "forum" instead of "phpBB3" in the step for setting up the symbolic link.

Edit: Just a thought: Part of the problem might be an "ownership" issue. On my server, the phpBB files are all owned by "root". 
Another place to look might be the [phpBB forums]("http://www.phpbb.com/community/viewforum.php?from=submenu&f=46")

---

### Post by Nythain on 2010-09-10
oi, ya screwed up changing the persmissions somehow... a simple
```

sudo chmod a+rw /path/to/config.php

```
should really be all you need, and only during the installation, im sure afterwards it should warn to change it back to
```

sudo chmod o-w /path/to/config.php

```
for security reasons, but thats a different story... really though, it shouldnt matter who owns the file (in fact, root:root is probably a good idea), but the file needs to be writeable by the webserver, wich is usually run as www-data or just www user, so that the install script can make the necessary config changes at install time.

---

