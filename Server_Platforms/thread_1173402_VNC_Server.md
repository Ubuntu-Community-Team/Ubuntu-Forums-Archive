---
title: "VNC Server"
date: 2009-05-29
forum: Server Platforms
---

### Post by zemon_ on 2009-05-29
I have six users on one server each running there own vnc sessions.

I want to set these VNC sessions to start automatically at boot.

Could someone explain how to do this?

---

### Post by LepeKaname on 2009-05-29
I suppose you know how to start them manually...

Then, use:

# update-rc.d start_vnc defaults

in which start_vnc will contain the manual startup commands.

---

### Post by zemon_ on 2009-09-07
I start them manually by logging in as the user and then starting the vncserver.

Login as userone

```
$ vncserver :1 
```

How would I put the manual commands in the start_vnc?

---

### Post by zemon_ on 2009-09-09
I tried this but still does not work.

[HTML]su - userone -c "vncserver :1"[/HTML]

Inside the start_vnc file.

[HTML]update-rc.d start_vnc defaults[/HTML]

Can anyone help??

---

