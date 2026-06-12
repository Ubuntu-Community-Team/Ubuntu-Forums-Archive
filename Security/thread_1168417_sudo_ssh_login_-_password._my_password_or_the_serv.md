---
title: "sudo ssh login - password. my password or the server?"
date: 2009-05-24
forum: Security
---

### Post by shiningkenmonster on 2009-05-24
just got into the whole ssh thing.

when i open the terminal and type in:

```
sudo ssh website login
```
it ask for my password. Is it asking for the server password or my computer password?

I think it read somewhere states its suppose to be the server's login password.

I want to make sure. I don't want my admin host to have my computer root's password.

---

### Post by LinuxRules1 on 2009-05-24
Usually when you login to a system through ssh you have to specify a username. So it's asking for the password of the user your logging in as.

---

### Post by roman_platonov on 2009-05-24
to login you need use following command (without sudo)
ssh username@host

in you case first password request maked by sudo (you local admin password)

---

### Post by terrrorr on 2009-05-25
Hi,

Here is more info about sudo command. I hope you will understand what sudo eventually do. Normally users do not have to use sudo command if they are trying to create connection through ssh tunnel.

[http://en.wikipedia.org/wiki/Sudo]("http://en.wikipedia.org/wiki/Sudo")

Here is couple examples.

1. Server: 192.168.1.100, currently logged user and server side account is similar (server account: diipadaapa, currently logged user: diipadaapa)

ssh 192.168.1.100

2. server: 172.172.172, currently logged user and server side account is different (server account: diipadaapa, curently logged user: zigzag)

ssh 172.172.172.172 -l diipadaapa

In both cases, use server side account information to login

- Terrrorr

---

### Post by shiningkenmonster on 2009-05-26
i am still confuse here. is it asking for my super user password? or the ssh server's password? - it is a new ubuntu server by the way.

if it is server's password. I just want to know if my administrator has my password or not.

---

### Post by Boondoklife on 2009-05-26
> **shiningkenmonster said:**
> i am still confuse here. is it asking for my super user password? or the ssh server's password? - it is a new ubuntu server by the way.

if it is server's password. I just want to know if my administrator has my password or not.


When you connect to the server just use
```
ssh serverusername@serveraddress
```this will then prompt you for the password of the user specified.

if you are trying to login as root to a server named someserve.net then it would be
```
ssh root@someserve.net
```this will then prompt your for the root users password of the server you are connecting to

the sudo part is not needed as all that is doing is running the command with elevated privilages.

---

