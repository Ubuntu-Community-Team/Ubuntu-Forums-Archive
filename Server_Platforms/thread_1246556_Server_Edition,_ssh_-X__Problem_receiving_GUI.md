---
title: "Server Edition, ssh -X  Problem receiving GUI"
date: 2009-08-21
forum: Server Platforms
---

### Post by VipX1 on 2009-08-21
Host Ubuntu 9.04 Server Editiion, Client Ubuntu 9.04 Jaunty 

```
:~/Documents$ gedit 000-default~ 
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory

```

As a test I just opened the backup of the 000-default file and then posted the pre-error I get before the gedit opens on the ssh client, it works! I have xauth installed on the server.
I know to get Flash working on a 64bit version I had to put a .so file into a Firefox directory but that's where my knowledge of .so files ends unfortuately. There's no libatk entry in synaptic. There are a good few pages when I google libatk-bridge but maybe someone could point me in the right direction. Even just outline the problem would be great.

I should add I did have Gnome on the server at one stage but I took it off again.

---

### Post by SoftwareExplorer on 2009-08-22
sounds like the packages ia32-libs, at-spi, & libatspi-dbg have a file named that. If the server is 64 bit I'm betting that the ia32-libs is the one you need.

---

### Post by VipX1 on 2009-08-22
It was actually the other way round. My server is 32bit and my Client machine is 64bit. The Client had the files you mentioned installed but the Server did not. I installed them and the error is gone. The gedit page doesn't close straight away now and the Client asks if I want to force the close but before I can respond the page closes. I guess this is normal because of the communication between Server and Client before the page closes, now that it's working correctly.
Thanks.

---

### Post by SoftwareExplorer on 2009-08-22
Do you mind looking at [this thread]("http://ubuntuforums.org/showthread.php?t=1236138") of mine? It sounds like you might know how to do what I'm trying to do.

---

