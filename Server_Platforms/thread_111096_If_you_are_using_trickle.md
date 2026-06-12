---
title: "If you are using trickle"
date: 2006-01-01
forum: Server Platforms
---

### Post by jimbodot on 2006-01-01
How does trickle work?

Does it need to restart a connection, or does it adjust the speed of an existing connection on demand.

---

### Post by ScatterBrain on 2006-01-01
It's my understanding that you use trickle to control the bandwidth of the program that is lauched by trickle.

```
trickle -u <upload speed> -d <download speed> <app name here>
```

Once the command is complete, the effects of trickle stop as well.

---

### Post by 23meg on 2006-01-01
It only limits the connection speed of the individual program you point it to and you don't need to restart the connection. For a global userspace bandwidth regulator, look into wondershaper.

---

