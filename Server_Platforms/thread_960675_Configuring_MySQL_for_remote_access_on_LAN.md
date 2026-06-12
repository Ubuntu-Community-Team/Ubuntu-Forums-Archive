---
title: "Configuring MySQL for remote access on LAN"
date: 2008-10-27
forum: Server Platforms
---

### Post by dhmicro on 2008-10-27
Hello,

I have installed MySQL on 8.04 Server Edition and can connect at the console without any problems.  When I try to connect from another workstation on the LAN, I get "Host xxxx is not allowed to connect to this MySQL server".

Can anyone help me configure my.cnf to allow me to connect to the MySQL server from another workstation?

Thank you for any help.

---

### Post by tlcoffee on 2008-10-27
Hello there,

Open your /etc/mysql/my.cnf file in your editor.

scroll down to the entry:

bind-address = 127.0.0.1

and you can either hash that so it binds to all ip addresses assigned

#bind-address = 127.0.0.1

or you can specify an ipaddress to bind to. If your server is using dhcp then just hash it out.

Then you'll need to create a user that is allowed to connect to your database of choice from the host/ip your connecting from.

Login to your mysql console:

**milkchunk@milkchunk-desktop:~$ mysql -uroot -p**
**GRANT ALL PRIVILEGES ON *.* TO 'user'@'%'** **IDENTIFIED BY 'some_pass' WITH GRANT OPTION;**
[FONT=Verdana]You change out the 'user' to whatever user your wanting to use and the '%' is a hostname wildcard. Meaning that you can connect from any hostname with it. You can change it to either specify a hostname or just use the wildcard.

Then issue the following:
[/FONT]**FLUSH PRIVILEGES;**

Be sure to restart your mysql (because of the config file editing):

**/etc/init.d/mysql restart**

---

### Post by koenn on 2008-10-27
you need to grant permissions to remote users, something like

GRANT [action, eg SELECT, CREATE, DROP] to user@workstation IDENTIFIED BY password

look in the mysql documentation for exact syntax.



edit: ah, better answer already given ....

---

### Post by dhmicro on 2008-10-27
I have set the bind-address to the static IP on the lan for this server and restarted the MySQL server.  So I can't login remotely as the 'root' user?

---

### Post by tlcoffee on 2008-10-27
> **dhmicro said:**
> I have set the bind-address to the static IP on the lan for this server and restarted the MySQL server.  So I can't login remotely as the 'root' user?

sure you can, but you'll need to set it to the hostname or ip address you want to use. However, I wouldn't advise opening the root user like that. You can simply use the command above on creating a user and it will have the permissions your going to require for any of the databases.

**GRANT ALL PRIVILEGES **<--- States the user will have all the privileges

**ON *.* **<--- all databases

**TO 'user'@'%'** <--- to user @ any connecting hostname or ipaddress

**IDENTIFIED BY 'some_pass' **<--- with the password you changed 'some_pass' to
[B]
WITH GRANT OPTION;[/B] <--- gives the user the option to grant more privileges (aka administrative permissions) and closes out the command with the ;

---

### Post by dhmicro on 2008-10-27
That did the trick, thank you very much.

---

### Post by tlcoffee on 2008-10-27
> **dhmicro said:**
> That did the trick, thank you very much.

Your welcome. Glad to help.

---

