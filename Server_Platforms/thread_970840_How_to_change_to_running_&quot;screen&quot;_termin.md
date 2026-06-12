---
title: "How to change to running &quot;screen&quot; terminal?"
date: 2008-11-04
forum: Server Platforms
---

### Post by GodsDead on 2008-11-04
Hey all, my problem is that I don't know how to switch back to a started "screen" terminal once its been initialized.

I have a counter strike server that runs when i run a script i created with these settings for "screen":

```

#! /bin/bash
echo "Starting Counter-Strike:Source Server"
sleep 1
cd /mnt/sdb1/srcds/
screen -A -m -d -S css-server ./srcds_run -console -game cstrike +map breakfloor +maxplayers 16 -autoupdate
echo "The server will live soon.."

```

Because, i would like to be able to change maps, and use the CS:S Terminal when i want to, but also have it running in anther "screen" so i can still terminal into the server.

Cheers.

---

### Post by TwoWordz on 2008-11-04
Are you looking for "screen -r" ?

TW

---

### Post by hrod beraht on 2008-11-04
Yep, to reattach, use **screen -r**.
If there is more than one screen session running, **screen -Dr** will show a list of them along with their numbers. In that case, find the one you want and reattach using it's number, e.g. **screen -r 3852**

screen -DR -> list of detached screen
screen -r PID -> attach detached screen session
screen -dmS MySession -> start a detached screen session
screen -r MySession -> attach screen session with name MySession

Note, if you've got more than one screen session running, **screen -Dr** will show all *attached* and *detached* screens.

Bob

---

### Post by GodsDead on 2008-11-05
Oh ausom, cheers you two!
At first it wasnt working, then i added sudo and it worked, so how do i get out of this screen once im in it, back to the terminal/ssh?

Thanks =]

---

### Post by hyper_ch on 2008-11-05
> **GodsDead said:**
> Oh ausom, cheers you two!
At first it wasnt working, then i added sudo and it worked, so how do i get out of this screen once im in it, back to the terminal/ssh?

Thanks =]



```

ctrl-a + ctrl-d

```

---

### Post by GodsDead on 2008-11-05
Cheers!

---

