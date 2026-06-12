---
title: "add new user to phpmyadmin"
date: 2013-07-03
forum: Server Platforms
---

### Post by giobaxx on 2013-07-03
Hi,....firs sorry for my english..

I'm tryng to install and configure LAMP solution on my UBUNTU. i have installed all the software, and i want to create some user in phpmyadmin to admnistrate his own database.

i insert a username( for example alex) a passoword(es: 12345) and at the voice "host" i select from the combobox "ANY HOST". I though that the user alex can log-in on phpmyadmin from every host.

But when i tried to login with username alex  i receive the error "#1045 Cannot log in to the MySQL server"...that error from any host i try to connect(local or not). 

If I choose "local" instead of any host i can login.....from any host(local or remote).....that make me a bit confused...:(

someome...can help me to undestand how it works?......what it means to select "any host" instead local?

in a professional enviroment what a have to choose? local....any host or other?

tanks Giovanni

---

### Post by DJ_Max on 2013-07-03
What do you mean "login from any host"? Through the webinterface or from a script?

---

### Post by cariboo on 2013-07-04
Can you actually access mysql from any other host aside from localhost. By default mysql is only accessible from the system it is installed on. To allow access from other systems on your network, you need to modify /etc/mysql/my.cnf. Change the line:

```
bind-address		= 127.0.0.1
```

to

```
bind-address            = <server-ip-address>
```

where server-ip-address = the ip address of your server.

**Note:** it is not advisable to  leave mysql open to the internet, as unless you are using a strong password, the admin user is already know in a default Ubuntu install, and it is just a matter of brute forcing the mysql password.

---

### Post by giobaxx on 2013-07-04
i have create this user on phpmyadmin

username:alex
host:any
password:12345

if i try to login from the webinterface of **localhost/phpmyadmin** i receive error 1045

i made the same configuration on a remote computer on internet(virtual server on linode) i connect for example to **75.21.84.85/phpmyadmin** i received the same error ----> no access in local or remote

i have tried with other user

username:joe
host:local
password:12345

with that user i can have access locally with **localhost/phpmyadmin** and remotely **75.21.84.85/phpmyadmin** --->so with local i have access locally and all over

so with local i tell you to phpmyadmin that mysql is on the same computer of phpmyadmin?..or what?

---

