---
title: "teamspeak server"
date: 2009-09-12
forum: Server Platforms
---

### Post by I WILL DO IT on 2009-09-12
so i got my team speak server running ect ect, can some one tell me how to configure ect ect. plz and thank you

---

### Post by cariboo on 2009-09-12
Link please.

---

### Post by slakkie on 2009-09-12
> **I WILL DO IT said:**
> so i got my team speak server running ect ect, can some one tell me how to configure ect ect. plz and thank you

Connect to your ts server on the correct port, which you can find in:

/etc/teamspeak-server/server.ini

You will see somehthing like:

```

HTTPServer Port=14534

```

Now connect to that port via http

[http://youserver:14534](http://youserver:14534)

Then login with your admin password, and fiddle with the settings, although you can set most of the things directly in the server.ini file I just mentioned.

Good luck and read the docs provided by the package and/or teamspeak server website.

---

### Post by abaden on 2009-09-12
Did you check out the [documentation]("http://www.teamspeak.com/?page=tutorial_b") on the Teamspeak site?

To configure a Teamspeak server you need to access the web interface. This can be found at yourip:14534. For example, 
```

http://10.0.0.1:14534

```

There is an INSTALL readme file in the tss2_rc dir too that should help you.


Alex

---

