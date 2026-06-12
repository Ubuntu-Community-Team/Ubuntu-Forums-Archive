---
title: "Screen and init.d scripts"
date: 2013-08-04
forum: Server Platforms
---

### Post by Jeremy Reid on 2013-08-04
Dear Ubuntu Forum Users,

I am currently running a Ubuntu 12.04 LTS server, which employs a number of customized .sh scripts in /etc/init.d/ to facilitate the launch of numerous services on system startup. A few of these scripts include the use of 'screen'.

However, when I login to the server - after startup - and type 'screen -r' to connect to a screen, there are no screens listed. When I enter htop, the services are launched.

Why is it not possible for me to attach myself to a screen session launched via init.d?

Jeremy Reid

---

### Post by GwL3eNC on 2013-08-04
Hi,

I dont used screen in scripts. I think the problem is CTRL+A and CTRL+D.
As i used screen i type

screen

and then return.
After that i start my process. Then i have to do CTRL+A and CTRL+D before i exit
my session. When i come back screen -r ever worked for me. I would realy like to now if a script can do the
CTRL+A and CTRL+D for you.

---

### Post by Jeremy Reid on 2013-08-04
> **GwL3eNC said:**
> 
I think the problem is CTRL+A and CTRL+D... I would realy like to now if a script can do the CTRL+A and CTRL+D for you.

I completely agree and, like you, wonder if a .sh script can trigger CTRL+A+D (screen detatch) for me.

Does anyone know?

---

### Post by CharlesA on 2013-08-04
I used to use this to launch a backup script via cron.

The same options should apply.

```
/usr/bin/screen -d -m -S DailyBK /scripts/daily.sh

```

---

### Post by Jeremy Reid on 2013-08-04
This is the .sh script I have placed in /etc/init.d/:

```

#!/bin/bash
/usr/bin/screen -d -m -S CSS /home/arthur/css/srcds_run

```

The script executes correctly on server launch, but when I try to access the screen I am told "There is no screen to be resumed.".

Have I done something wrong?

---

### Post by Jeremy Reid on 2013-08-04
AH! I think I have found my solution:

When using the command 'sudo screen -r', I am able to access the screen!

How foolish I have been - init.d runs all commands as root. Is there a way of running a command as a user other than root?

UPDATE:

Found my answer, use 'su [username] -c "commandgoeshere" '

Thank you all!

---

