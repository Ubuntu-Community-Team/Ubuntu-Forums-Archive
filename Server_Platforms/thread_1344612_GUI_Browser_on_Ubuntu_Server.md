---
title: "GUI Browser on Ubuntu Server?"
date: 2009-12-03
forum: Server Platforms
---

### Post by Stan* on 2009-12-03
I need to forward a port in the router while I'm not at the server. I have access to the server via SSH, and I installed lynx to go to the page of the router to edit the config.
Howerver, I can't get logged in because the login-button is not a button, but some kind of image I think. Anyway, I can't submit the form.

Is there a way to browse with a GUI in Ubuntu Server? Because the router is only accessible inside the network, and I'm now at a different location.

Thanks in advance.

Stan

---

### Post by Bachstelze on 2009-12-03
Since you have SSH access to the server, you can create a SSH tunnel that will allow you to connect to your router from wherever you are. Do something like

```
ssh -L 8080:192.168.1.1:80 user@server
```

Of course replace 192.168.1.1 with the IP of your router. Now you can access it at [http://127.0.0.1:8080](http://127.0.0.1:8080)

---

### Post by Stan* on 2009-12-03
But now I still have the problem that I can't change anything. With elinks I can submit the login-form, with lynx I can't. But with both browsers I can't change anything in the router, because I can't see a proper interface. It seems the browser doesn't execute the JavaScript-code. I just see this when I logged in:

[img]http://img511.imageshack.us/img511/7272/schermafbeelding2009120.png[/img]

When I press 'OK' I'm redirected to the login-page.

---

### Post by Bachstelze on 2009-12-03
> **Bachstelze said:**
> Now you can access it at [http://127.0.0.1:8080](http://127.0.0.1:8080)

... On your Mac, of course, not from inside the SSH session.

---

### Post by Stan* on 2009-12-03
Aaah I get it. Nice, this works. But the form action in the router login-page is 192.168.2.1, so every time I try to login I'm redirected from localhost:8080 to 192.168.2.1, so the page is not loaded. Is there a solution for it?
Thank you for your help so far.

---

### Post by Bachstelze on 2009-12-03
> **Stan* said:**
> Aaah I get it. Nice, this works. But the form action in the router login-page is 192.168.2.1, so every time I try to login I'm redirected from localhost:8080 to 192.168.2.1, so the page is not loaded. Is there a solution for it?

I'm afraid there isn't, that's very poor design... If you have a desktop machine on the network, you can maybe install VNC on it to have a GUI browser to connect to the router. Or try to find a CLI one that will work, maybe w2m or lynx, if links doesn't.

---

### Post by Stan* on 2009-12-03
Hmm, too bad. Maybe I can edit the OS of the router. Anyway, many thanks for you help.

---

