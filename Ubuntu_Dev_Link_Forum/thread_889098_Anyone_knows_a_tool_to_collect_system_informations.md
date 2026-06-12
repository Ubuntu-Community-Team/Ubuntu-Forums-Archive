---
title: "Anyone knows a tool to collect system informations?"
date: 2008-08-13
forum: Ubuntu Dev Link Forum
---

### Post by roalme on 2008-08-13
Hi,
I've been looking for a tool to collect and show me a set of system informations. The informations that I want may be organized in three groups:

1. Software Information: Information like Operating System Version, Softwares that are initialized when the system initializes, User and Groups, etc...
2. Hardware Information: Information about the hardware, like total memory, Processor, and so on.
3. Network Information: Information like connection speed, type of connection, network configuration, ...

There are a software that runs at Windows (called SIW) that collects all that informations, and I'm looking for some tool that runs similarly (at Ubuntu).


Thanks in advance,
Rodrigo Almeida

---

### Post by falcon61102 on 2008-08-13
If you go to Add/Remove Programs and perfrom a search for System Information, they have a couple apps similar to what you are looking for.  One is actually called System Information.

---

### Post by PC_load_letter on 2008-09-05
Fo hardware info try 
```
sudo lshw
```in a terminal.
If you want the output in an html file, type:
```
sudo lshw -html >file.html
```

---

