---
title: "Server processes?"
date: 2012-07-05
forum: Server Platforms
---

### Post by d4m1r on 2012-07-05
Hey guys, so I did a basic install of vanilla 11.10 Server (32 bit) and I am trying to clean up the processes....With apache2, ufw, mysql, and DNS services stopped, the server is *still* using 130MB/512MB. Basically, would someone be able to tell me what the process names below are and what they do/if they are needed? Thanks in advance! :P

dovecot?

winbindd?

nmbd?

qmgr?

pickup?

udevd?

getty?

upstart?

atd?

---

### Post by cariboo on 2012-07-06
> **d4m1r said:**
> Hey guys, so I did a basic install of vanilla 11.10 Server (32 bit) and I am trying to clean up the processes....With apache2, ufw, mysql, and DNS services stopped, the server is *still* using 130MB/512MB. Basically, would someone be able to tell me what the process names below are and what they do/if they are needed? Thanks in advance! :P


> dovecot?

An email transport agent

> winbindd?

Used by Samba

> nmbd?

Used by Samba

> qmgr

> pickup?

> udevd

The device manager used by the Linux kernel

> getty

A Linux program to control virtual or real terminals

> upstart 

Used by Ubuntu to start services

> atd?

Used by Linux to run a job at a later date

---

### Post by d4m1r on 2012-07-06
Thank you! Simple and to the point. Seems like most of those are required services (based on my needs) so I'll let them run.

Marking thread as solved :p

---

