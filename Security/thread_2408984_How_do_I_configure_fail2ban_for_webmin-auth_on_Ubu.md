---
title: "How do I configure fail2ban for webmin-auth? on Ubuntu Server 18.04"
date: 2018-12-26
forum: Security
---

### Post by techcomputerworld on 2018-12-26
Hello, I have configured fail2ban in Ubuntu Server 18.04 in the jail.local file, I have copied it to jail.local as I said in a tutorial and you configure everything about that file.
I put these lines in this configuration and it still does not work after logically restarting



[webmin-auth]
enable = true # Indicamos que el jail está habilitado 
port = 10000 # Puerto que vamos a bloquear
filter = webmin:auth # Nombre del filtro que vamos a aplicar
logpath = /var/log/auth.log # Log donde se registran los intentos de acceso en webmin, podría variar según la distribución de linux
maxretry = 2 # Número de intentos para banear IP

this configuration is to protect the webmin I want to install it in a VPS

---

### Post by TheFu on 2018-12-29
If you want to protect webmin, don't allow any remote access at all.  Force it only to be available to 127.0.0.1 users, then only allow ssh remote access using key-based authentication, never passwords.  Then you would use ssh as a SOCKS proxy from your browser to tunnel into the server, effectively accessing the system from localhost.

But really, if you care about security, don't use webmin at all.

---

