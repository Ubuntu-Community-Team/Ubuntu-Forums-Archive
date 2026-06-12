---
title: "Desktop Sharing Encrpytion"
date: 2017-02-17
forum: Server Platforms
---

### Post by jaytt on 2017-02-17
Hi

Running 16.10, and enabled Desktop Sharing options, port forwarding in router etc.
Installed RealVNC on  phone and it will not connect "unsupported mechanism" or the likes.

Ran DCONF-EDITOR and changed my /org/gnome/dekstop/remote access/require encrpytion to be off
and then
gsettings set org.gnome.Vino require-encryption false

It now works perfectly but I get a warning about unsecure connection (pretty sure this is not ideal though)

If I reenable encrpytion and look at logs on android it looks like the server is using Anon Diffie Hellman ciphers which Android no longer supports.

Is there a way to enable or change this to get it working with Android or do I leave unencrypted?
Otherwise, anyone know the steps to get it working with Encryption please?

---

### Post by wildmanne39 on 2017-02-17
*Thread moved to **Server Platforms**.*

---

