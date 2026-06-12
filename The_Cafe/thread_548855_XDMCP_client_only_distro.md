---
title: "XDMCP client only distro"
date: 2007-09-11
forum: The Cafe
---

### Post by Biochem on 2007-09-11
I'm looking for a distro that would only allow to connect to an XDMCP server. Nothing fancy just the terminal.

I google around but I only found how to's for using full linux install or setup server. 

Will I get what I want if I do a minimum server install with o nly X and GDM?

---

### Post by Dr Small on 2007-09-11
Possibly, I would imagine.

---

### Post by Rui Pais on 2007-09-12
> **Biochem said:**
> I'm looking for a distro that would only allow to connect to an XDMCP server. Nothing fancy just the terminal.

I google around but I only found how to's for using full linux install or setup server. 

Will I get what I want if I do a minimum server install with o nly X and GDM?

I don't think such a thing exist...

On my very old computer, that servers only as a XDMCP client, i use the [minimal Ubuntu CD]("https://help.ubuntu.com/community/Installation/MinimalCD") followed by an **apt-get install xorg gdm** and a configuration of gdm.conf. 

It's the closest of what you ask. Minimal CD has only a few 8M, it's much more strip it down then server version.

hth

---

