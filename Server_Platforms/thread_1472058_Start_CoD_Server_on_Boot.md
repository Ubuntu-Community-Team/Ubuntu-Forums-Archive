---
title: "Start CoD Server on Boot"
date: 2010-05-04
forum: Server Platforms
---

### Post by Frizianz on 2010-05-04
Hey Guys,

Whats a way to start the cod server as a specified user on system boot. Whats the best way for me to do this?
The cod server is located in the users home directory

Frizianz

---

### Post by Frizianz on 2010-05-04
Bump...

---

### Post by TheFuturian on 2010-05-06
This makes little sense. Do you mean a "Call of Duty" server? Is there a startup/shutdown script available for the service within /etc/init.d? If so I believe that the "update-rc.d" command can be used to set the service to run when the Server is booted.

```
man update-rc.d
```

---

### Post by windependence on 2010-05-06
Start up scripts can be placed in /etc/rc.local file 
so that they are executed at boot.

-Tim

---

### Post by Frizianz on 2010-05-07
Sorry For The Rushed Post. Im Looking For Something that will run on startup, and also be able to restart the server manually whilst not having to keep that ssh window open.

This Command needs to also be executed as a certain user. As its a security risk to run the server as root :)

---

### Post by windependence on 2010-05-07
To start a process non-interactively, follow it with an ampersand like this:

```
./cod2_lnxded  &
```

Then, you should be able to close the remote console and it will stay running. That is if it works like any other Linux command.

-Tim

---

### Post by Frizianz on 2010-05-07
Thanks. What Can I Add to the Script to make it run as the user cod4_1?

---

### Post by mrjerryk on 2010-05-27
I would like to know how to do this as well.  I am using screen right now and it's working fine.  But I would like it so I can just have it start at boot and restart if the server goes down so I can give other admins access to restart the server using rcon commands in the game without giving them ssh access to my linux box.  

I know it's possible with init.d and or cron but I have no idea how to set something like that up.  

The command to start my server is 
```
screen ./codwaw_lnxded +exec server.cfg +map_rotate
```

Thanks in advance for any help!

---

### Post by paddy.melon on 2010-05-27
> **Frizianz said:**
> Thanks. What Can I Add to the Script to make it run as the user cod4_1?

simply run it from that user, so ssh:

login
user: cod4_1
password: <ur passwd>

then execute the above command!

---

