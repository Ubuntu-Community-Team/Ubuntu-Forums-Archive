---
title: "How do I make a script that automaticlly restarts samba on boot?"
date: 2009-12-30
forum: Server Platforms
---

### Post by blubaustin on 2009-12-30
I was wondering how do I make a bash script that automatically restarts samba after all the services are running? The reason I ask is because ubuntu 9.10 has a bug where smb is conflicting with nmbd and if I restart smb at boot it fixes the problem. So I just need it where the system automatically restarts smb. Thank you.

---

### Post by BkkBonanza on 2009-12-30
You can add a line to /etc/rc.local - it is run after all other init scripts.
eg. add,
/etc/init.d/samba restart

---

### Post by blubaustin on 2009-12-31
Thank you, but why does it say that this script does nothing by default? And do I need to keep the exit 0 also?

---

### Post by BkkBonanza on 2009-12-31
It says that because by default there are no commands added to the script.
Make sure you add any line you wish to run before the exit line, otherwise it will exit before it runs your command.

---

### Post by blubaustin on 2010-01-07
Thank you very much, that solved my problem. ^_^

---

### Post by dandirk on 2010-01-10
hmmm question of curiosity...

Why isn't a sudo command/sudoers edit needed in this script?

---

### Post by BkkBonanza on 2010-01-10
rc.local runs as root during the init sequence.

---

