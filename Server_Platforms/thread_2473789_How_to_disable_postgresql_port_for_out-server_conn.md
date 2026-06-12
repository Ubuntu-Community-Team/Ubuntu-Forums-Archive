---
title: "How to disable postgresql port for out-server connection?"
date: 2022-04-14
forum: Server Platforms
---

### Post by mxcdh on 2022-04-14
[COLOR=#000000][FONT=Verdana]I installed on my dedicated server ubuntu 20.04, docker, and container with postgressql. I have problem beacouse I want that ubuntu blocked all connection with postgressql, out-server from domain, ip server etc, which added to server.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]At the moment I can connect with PostgreSQL:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]via ssh[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]via server ip. ip.ip.ip:5432/...[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]via all domain which added to nginx like domain1.com:5432 etc.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I want disabled connection via server ip and all domain which added to nginx[/FONT][/COLOR]

---

### Post by The Cog on 2022-04-14
Welcome to the forum.

For preventing direct connection to postgresql, the easiest thing to do is to configure it to only listen on 127.0.0.1 address. This is a configuration option for the database. The same goes for nginx. That said, configuring a firewall that only allows incoming connections to services you want to be accessible (ssh on tcp:22 perhaps). gufw (or the text mode ufw if your server has no graphics) is the standard firewall to use.

For preventing access to users who are already logged into the server (e.g. with an ssh login), that's very difficult, may not even be possible without configuring AppArmour.

---

### Post by SeijiSensei on 2022-04-14
By default, postgresql on Ubuntu only allows connections via a local socket or via localhost.

All the access is controlled by rules in /etc/postgresql/[version]/main/pg_hba.conf. The current version is 12, so you need to examine  /etc/postgresql/12/main/pg_hba.conf.

```

# "local" is for Unix domain socket connections only
local   all             all                                     peer
# IPv4 local connections:
host    all             all             127.0.0.1/32            md5
# IPv6 local connections:
host    all             all             ::1/128                 md5

```

I'll warn you that this is a pretty complex file if you need to make changes. However, out-of-the-box only connections to 127.0.0.1 and its equivalent IPv6 address are permitted.

---

