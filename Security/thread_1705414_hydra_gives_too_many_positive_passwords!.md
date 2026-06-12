---
title: "hydra gives too many positive passwords!"
date: 2011-03-12
forum: Security
---

### Post by wanalex on 2011-03-12
Hi everybody, 

I've got some hotspot networks, with different kinds of APs. So I need to be sure that's nobody can get in my aps and routers!!!

I've installed Hydra quite successfully under ubuntu. I can run the command line only but not xhydra. 

Anyway, I can get the password of a wrt54gl with the following command:

hydra -l admin -P pass2.txt -e ns -vV 192.168.2.1 http-get / 

I got the usual [80][www] host: 192.168.2.1 login: admin   password: rex

It works the same with a smc router that pop up asking for a username and a password. Perfrect. 


When It comes to test a zyxel router, hydra becomes crazy and gives me a positive authentication for every password!!!.

[80][www] host: 192.168.2.1 login: admin   password: rex
[80][www] host: 192.168.2.1 login: admin   password: blue2
[80][www] host: 192.168.2.1 login: admin   password: red3
[80][www] host: 192.168.2.1 login: admin   password: Joe
[80][www] host: 192.168.2.1 login: admin   password: fox ...

The login page url looks like this [http://192.168.2.xxx/index.asp](http://192.168.2.xxx/index.asp)
and there is no where to input the login, only a field for the password.

Is my router protected from password attack or I've done a mistake in hydra?
Any idea how to solve this?

---

### Post by n~kf)}BW% on 2011-03-12
It's because you didn't set hydra to recognise the error page when you enter a wrong password, so hydra thinks you're logged in when the html page changes. Look it up in the options.

---

### Post by wanalex on 2011-03-12
Thanks for your clear answer :)

By any chance, could you post a sample for this option?

on the webpage, there is only one field! the Password one. How to deal whith that?

Thanks

Alex

---

