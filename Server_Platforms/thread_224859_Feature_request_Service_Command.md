---
title: "Feature request: Service Command"
date: 2006-07-28
forum: Server Platforms
---

### Post by llbbl on 2006-07-28
I really miss the service command in Fedora. Is there anyway that this can be ported to Ubuntu?  

#service httpd restart (easy)
#/etc/init.d/ httpd restart (not as easy)

Here are two basic possible solutions. I was thinking of adding /etc/init.d/ to my PATH variable. I was also thinking that it might be possible to do something with the alias command. 

Service command does more than that thou, status-all is useful. 

```
[llbbl@localhost ~]$ service
Usage: service < option > | --status-all | [ service_name [ command | --full-restart ] ]

```

---

### Post by jordilin on 2006-07-28
I would take a look at what the command service does. I mean, perhaps is a link to /etc/init.d, so it does the same as just writing /etc/init.d and then you can implement it in Ubuntu.

---

### Post by LordHunter317 on 2006-07-28
There's invoke-rc.d for starters.  

But I don't know why you think /etc/init.d/httpd start is any less easy.  It's equally easy.

---

### Post by llbbl on 2006-07-28
It is more to type. Just the one word serivce you can type very fast. Which is a great help when running a server and you need to quickly restart something like the server or networking or mysql or whatever. It is a great time saver!

---

### Post by LordHunter317 on 2006-07-28
Seeing as you have tab complete, it's not anymore to type.

It's actually *less* to type, unless you have a special bash completion (or zsh or whatever you use) setup for the service command.  RH doesn't provide one by default, so you don't.

If you really want it that bad, add this to your ~/.bashrc:```
function service {
  /etc/init.d/$0 $1
}
```

---

### Post by fdoving on 2006-07-29
You can install the 'debian-helper-scripts' package. It includes a simple 'service' script.

Basically an alias: /etc/init.d/$1 $2 $3
The package however includes some other nice tools.
I use 'psp' alot.


- Frode

---

### Post by llbbl on 2006-07-31
Thanks everyone for the contributions!

---

