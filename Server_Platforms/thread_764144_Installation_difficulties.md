---
title: "Installation difficulties"
date: 2008-04-23
forum: Server Platforms
---

### Post by jonathanlukens on 2008-04-23
I just got a new server, a Dell PowerEdge T105 (AMD Opteron).  I have server install CDs for Dapper and Gutsy.  

Neither of them installs like a snap -- Dapper doesn't recognize my Ethernet card and Gutsy won't mount the CD-ROM after installation is running.

Which of these problems is going to be easier to fix?

---

### Post by nanog on 2008-05-01
I have 2 T105s.

A known kernel bug prevents recent 64 bit distros from installing. 32 bit gutsy installs fine and its trivial to convert this to a server by uninstalling unbuntu-desktop and installing the server kernel. 


64 bit dapper installs fine but does not recognize the broadcom nic.
I installed the nic by manually compiling the broadcom driver module (bnx2). Another approach is to alien the rpm driver available from dell. 

For my second box I installed 64 bit hardy server on a 750 gb drive in another box. I swapped it into the t105, modprobed bnx2, restarted and have been enjoying cheap server goodness. 

Both machines have the 2.8 GHz Opteron 1220,  8 Gb RAM ($220), and 3 TB of storage (4 750 gb drives at $130 a pop) for less than a $1000 USA.

---

