---
title: "how to install call of duty united offensive server as a daemon in ubuntu server?"
date: 2009-12-05
forum: Server Platforms
---

### Post by markspoiss on 2009-12-05
hi! i need help littlebit. i installed Cod UO server on my ubuntu server.. now i want taht... i want that server starts automatically when i start my computer and with configuration files. how i can do that?

right now i start like this manaually:

./coduo_lnxded +set fs_game panzer +set dedicated 2 +exec dedicated.cfg +map_rotate

fileas are in /etc/coduo

sry about my inglish:)

Thnx!

---

### Post by Jekshadow on 2009-12-13
```
echo "./coduo_lnxded +set fs_game panzer +set dedicated 2 +exec dedicated.cfg +map_rotate" > start_cod.sh

chmod +x start_cod.sh
```

Then you just have to go into the directory and type "./start_cod.sh"

---

