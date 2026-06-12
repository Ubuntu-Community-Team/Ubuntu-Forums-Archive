---
title: "New to ubuntu, unknown issues."
date: 2015-10-29
forum: Server Platforms
---

### Post by joe_johnson on 2015-10-29
Hello, I am trying to get this program working on my ubuntu called "eBot", it's a program for counter strike and helps with servers. However, I have run into just issue after issue and have no idea what im doing.

[https://github.com/deStrO/eBot-CSGO/wiki/Install](https://github.com/deStrO/eBot-CSGO/wiki/Install)

This is what is coming up, I don't know how to reset my ubuntu, I don't know what I should do and how to do it. Any ideas? Thanks!

[IMG]https://i.gyazo.com/9969c4a775c6ec41820ad5ab9afb1c2b.png[/IMG]

---

### Post by darkod on 2015-10-29
Is this the server version? You are installing ubuntu-desktop on it?

Anyway, it looks like broken dependencies... Try something like:
```
sudo apt-get install -f
sudo dpkg-reconfigure -a
```

See if that leads you anywhere...

---

### Post by joe_johnson on 2015-10-29
Thanks for the reply, when I do it I get this after a little bit, but I can't click ok. Also, I don't have to type sudo but I am using the VPS's server console, so I'm guessing that's why?

[IMG]https://i.gyazo.com/d063f1aaf60e9b62fbbf58f6581c602f.png[/IMG]

Also, like I said I don't know much about this stuff :D I know it runs ubuntu v14. And idk if I need ubuntu desktop or what, I just wanna get ebot running on it :D

---

### Post by darkod on 2015-10-29
In similar text menus you usually use Tab to move to the Ok option. Then with Enter to use it. You see the cursor is on the last line, with Tab it should move to Ok.

---

### Post by joe_johnson on 2015-10-29
Thanks a lot, but now it shows this.

[IMG]https://i.gyazo.com/7359a0f529b33d77d4b938e8edbb1ecf.png[/IMG]

---

### Post by darkod on 2015-10-29
This is related to the GUI we discussed. You might have followed some tutorial that also installs a GUI on the server. Usually there is no need servers to run GUI interface, and in most cases it's not even recommended to.

Try to redo the procedure but look real carefully at it first, and avoid installing a GUI if it's not needed.

---

### Post by joe_johnson on 2015-10-29
I didn't see anything regarding GUI/Ubuntu desktop when I went through the list of certificates.

---

### Post by TheFu on 2015-10-29
Looks like something tried to install ubuntu-desktop package. Not good on a remote server. compiz requires 3d-accelerated GPU which no VPS will support. I think compiz is part of the ubuntu-desktop dependencies.

I ran a CS server about 10yrs ago on a headless Linux server. 
At this point, I would flush this VPS, get a new one with a fresh install and avoid installing **any** desktop applications. Not worth screwing around trying to fix it. One of the good things about a VPS is dumping it when things break like this.
Whenever installing any other packages, look for "unity*" or "desktop" anything in the dependency list - don't install those. Sometimes dependencies from a development system will be accidentally included to prevent pure-servers from working. Be diligent.

---

### Post by joe_johnson on 2015-10-30
I got hold of a new dedi, and I ran the install succesfully. However now the issue I'm getting is "websocket server crashed" I believe it had something to do with when installing mysql it asked if I wanted to put on a database like a database-common or something, I think I should of pressed no. Any ideas? Is this a simple fix?

[IMG]https://i.gyazo.com/75c241edcc11529a474c81341ab8aa91.png[/IMG]

---

