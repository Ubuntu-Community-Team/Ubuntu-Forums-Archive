---
title: "access MySQL from another box or client"
date: 2008-05-13
forum: Server Platforms
---

### Post by Data-Base on 2008-05-13
Hello,

we have 2 Ubuntu Servers and both are LAMB,

now we need to have one of them have a full access to the other database to make a backup (using phpMyAdmin or any other tool)

I know there is a network limitation problem

how should I configure the setting in /etc/mysql/my.cnf so I'll let other tools and programs access the database from another box


Thank you

---

### Post by cdtech on 2008-05-13
You just want to use one of the servers for backup? Is that what you want?

---

### Post by Data-Base on 2008-05-13
> **cdtech said:**
> You just want to use one of the servers for backup? Is that what you want?

simply yes

---

### Post by koenn on 2008-05-13
> **Data-Base said:**
> 
how should I configure the setting in /etc/mysql/my.cnf so I'll let other tools and programs access the database from another box

you have to make mysql listen on the ip address of the server's NIC :

```
	## my.cnf
	# listen port : bind to real address i.s.o. local loopback
	bind-address            = 192.168.10.12
```

---

### Post by hyper_ch on 2008-05-13
I wouldn't config my.cnf like that... I'd rather create a mysql user with according rights and that might access from a remote location.

---

### Post by koenn on 2008-05-13
> **hyper_ch said:**
> I wouldn't config my.cnf like that... I'd rather create a mysql user with according rights and that might access from a remote location.
that remote user still needs to talk to the database from a remote location. So how are you going to accomplish that _without_ that database daemon listening on a network interface ?

The only other ways I can think of is
A/ through a ssh tunnel - but your post doesn't even hint at that, let alone explain how to configure it.

B/ telekinetics, telecybernetics, or an application of quantum field theory. None of these is currently supported in Ubuntu.

---

### Post by Data-Base on 2008-05-13
> **koenn said:**
> you have to make mysql listen on the ip address of the server's NIC :

```
	## my.cnf
	# listen port : bind to real address i.s.o. local loopback
	bind-address            = 192.168.10.12
```

I will try that tomorrow

but I need to restart MySQL if I change the configuration file for sure, right?

---

### Post by koenn on 2008-05-13
> **Data-Base said:**
> I will try that tomorrow

but I need to restart MySQL if I change the configuration file for sure, right?
right

---

