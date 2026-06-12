---
title: "Installed postgresql10 snap, now how do I start it?"
date: 2018-10-24
forum: Server Platforms
---

### Post by Kimm on 2018-10-24
Hey!

I just installed ubuntu server on a virtual machine, and selected postgresql10 snap during install since I want to use postgres for my databases. Now, I have no idea how to actually start the postgres service, and I cant find anything on how to do so after installing it as a snap. I have tried different variants of:

*sudo systemctl start postgres/postgres10/postgresql/postgresql10/pgsql/pgsql10*

But I always get "Unit xx.service could not be found."

I also verified that the snap is actually installed by running:

*sudo snap install postgresql10*

From which I get: "snap 'postgresql10' is already installed', so I assume it was properly installed.

Sorry for the silly question, but I've been away from the Ubuntu world for a while and snaps are still fairly new to me.

---

### Post by slickymaster on 2018-10-24
*Thread moved to **Server Platforms**.*

---

### Post by seffyroff on 2018-11-13
Here's how I did it:

```
snap install postgresql10
adduser postgres
#(set a password, and accept all other defaults)
```
```
sudo su postgres
#(I had to add /snap/bin to the user's $PATH, like this:)
echo 'export PATH=$PATH:/snap/bin | tee --append ~/.bashrc
source .bashrc
```
Then the actual pg init stuff:
```
postgresql10.initialize newlocale en_US UTF-8
postgresql10.initialize initdb en_US UTF-8
postgresql10.pgctl -D /home/postgres/snap/postgresql10/common/data start
```

---

### Post by SeijiSensei on 2018-11-14
Why not just use the standard method via apt?

 PG installs flawleslly using this method and configures the system to start Postgres automatically at boot.

 I don't yet understand the fascination with snap packages.

---

### Post by Tadaen_Sylvermane on 2018-11-19
They are more windows like imo. Hence people love them. Apt is foreign to most.

---

### Post by jpnorair on 2019-06-13
Why use snaps?  Well, it's not really a choice with Ubuntu-Core.

I found this topic while trying to install postgresql10 on ubuntu-core18.  Here's the amended setup you need to do with Ubuntu-Core. (Thanks seffyroff for 90% of the work)

[COLOR=#000000]$ sudo snap install postgresql10
$ sudo adduser --extrausers postgres
#(set a password, and accept all other defaults)

$ sudo su postgres
[/COLOR]
[COLOR=#000000]Then the actual pg init stuff:[/COLOR][COLOR=#000000]
$ postgresql10.initialize newlocale en_US UTF-8
$ postgresql10.initialize initdb en_US UTF-8
$ postgresql10.pgctl -D /home/postgres/snap/postgresql10/common/data start

[/COLOR]

---

