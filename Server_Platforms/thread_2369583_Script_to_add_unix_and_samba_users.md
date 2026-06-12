---
title: "Script to add unix and samba users"
date: 2017-08-24
forum: Server Platforms
---

### Post by marta2 on 2017-08-24
Hi,
I'd like to know if it's possible to write an script asking for a user and a password, and with these add a Unix and Samba user.
For this, I've written this script and when I execute it, it asks for the password, because I don't know how to assign it.
```
[COLOR=#000000][FONT=Arial]#!/bin/bash[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]echo -n “Usuario: “[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]read usuario[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]echo -n “Contraseña: “[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]read contrasena[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo adduser --force-badname $usuario[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo adduser $usuario clientes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo smbpasswd -a $usuario[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo service smbd restart[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]exit[/FONT][/COLOR]

```
Can anybody tell me how to do it

Thanks

---

