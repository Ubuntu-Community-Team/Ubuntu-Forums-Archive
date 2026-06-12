---
title: "[SOLVED] Interfaces - HowTo config"
date: 2008-06-03
forum: Server Platforms
---

### Post by CyberDean on 2008-06-03
In the Interfaces config file it references seeing Interfaces(5) for more information about Interfaces config file.  Where do I find this Interfaces manual?  I am assuming the (5) will be section or chapter five.  

I am setting up a server on Ubuntu 8.04 and I need to setup two (2) ethernet cards in Interfaces config file, but would like to understand all I can about the Interfaces config.

Thanks.

I would also like to setup Interfaces for "Dynamic" IP addressing if possible.  Any insight.

---

### Post by andol on 2008-06-03
```
man interfaces
```
or to be more explicit
```
man 5 interfaces
```

The 5 refers to in what section of the man(ual)-documentation you want to look for your page.

---

### Post by CyberDean on 2008-06-03
Thanks andol for the guick reply, hope this answers my questions.

---

