---
title: "I can't connect to my localhost using Nessus. Why?"
date: 2007-05-18
forum: Server Platforms
---

### Post by RonB123123 on 2007-05-18
I can't connect to my localhost using Nessus. Why?

I can go to websites and my internet is working fine. I tried turning off Firestarter and trying to connect again with Nessus, but I keep getting the same error.

[quote=Error]
Could not open a connection to localhost
[/quote]

Can anyone help?

---

### Post by ricrac on 2007-05-18
Are you running nessusd?

---

### Post by RonB123123 on 2007-05-19
I installed Nessus, and then just went to Applications > Internet > Nessus and then ran the program. I don't think I got Nessusd, but I could be wrong. I downloaded another Nessus related application in order to create a username, which worked perfectly. 

But when I run Nessus, it opens up a Window, and the first thing I need to do is connect to my localhost, which gives me an error when I click on Connect.

---

### Post by ricrac on 2007-05-19
It's a client server app, localhost is the default because many people use both on the same machine.  The server nessusd can be on any machine, the client is the source of testing.

Check synaptic, you need nessus, nessusd and nessus-plugins installed.

---

### Post by Seti on 2007-07-05
Nope, still can't connect.
even after making a user...

```

nessus-adduser

```
and following the steps.

???

---

### Post by ohioboy757 on 2007-07-05
Is nessusd running?

Try this in a terminal window:

```
ps aux | grep nessusd
```

This will let us know if the daemon is running.

---

### Post by mirceade on 2007-08-30
For Christ sake. Just start the daemon: sudo /etc/init.d/nessusd start

---

