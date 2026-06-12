---
title: "postgresql install problems"
date: 2009-11-12
forum: Server Platforms
---

### Post by Bladergroen on 2009-11-12
In our lab we use a xubuntu system (9.04) for analysis purposes. Therefore we need to install a program which uses postgreSQL.
So I installed postgresql 8.3.8 from source according to the documentation by postgreSQL.
Before that I used the command "adduser" to activate a linux postgres user account. 
So now I have two linux accounts: one with sudo rights and the postgres with basic rights.
With everything set (all config files, databases, database accounts etc.) the server is automatically started at login with the sudo account. That works.
But from this account I cannot use any commands like pg_start etc. I have to su - postgres to do this. When I restart the server from there, I get error messages that IPv4, 6 and ip address sockets can't be opened. (while the server was just running before stopping it...)
I did set "-A INPUT -i lo -j ACCEPT"  in the iptables file, (which is confirmed when I use "sudo iptables -L", (only when logged in in the sudo account, I can't check this when logged in in the postgres account!).
So when I finally want to install the end-client software, that fails, because it can't somehow connect to the database.
please help, I'm already working on this for 2 weeks!

Thanx in advance,

reno

---

