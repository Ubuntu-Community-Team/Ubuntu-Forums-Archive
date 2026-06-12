---
title: "Remote Desktop encryption"
date: 2005-05-11
forum: Server Platforms
---

### Post by lewiz on 2005-05-11
Hi,

After digging around I found out the Remote Desktop (server) functionality is provided by vino-server.  This is compiled with gnutls for encryption support.

However, I can't seem to find a vncviewer capable of using the crypto.  This does seem a little odd to me and I have to wonder why Hoary doesn't use vino-server's encryption by default (that is the default, although the Ubuntu guys seem to have changed it).

Anybody know why it is like this, if I'm doing something wrong, or where I can find a suitable vncviewer?

Thanks,

---

### Post by JonahRowley on 2005-05-11
Use an SSH tunnel.  Not only will this provide encryption, but you won't have to expose the port to the world without authenticating first.  Look at the -L switch in **man ssh**.

---

### Post by lewiz on 2005-05-11
[QUOTE=JonahRowley]Use an SSH tunnel.  Not only will this provide encryption, but you won't have to expose the port to the world without authenticating first.  Look at the -L switch in **man ssh**.[/QUOTE]

Well, that's one way to do it, I suppose.  It's not quite what I had in mind but it will certainly do for now ;)

Maybe vncviewer will be built with the appropriate libraries in Breezy!

---

