---
title: "how to install UEC in one machine"
date: 2010-02-28
forum: Server Platforms
---

### Post by nicolasdiogo on 2010-02-28
hi folks,

does anyone know of an article that explains how to install all Ubuntu Elastic Cloud on one single machine?

i understand that it should be ideally used with at least two; but i am trying to test it and i do not have two machines to use.

thanks,

Nicolas

---

### Post by ICEB3AR on 2010-02-28
The following is only a guess:

Basically i would say you have to install a system and in this something like virtualbox or anything similar and then install the uec on this. Another way wouldn't even make sense or? To my mind a cloud should use the hardware of many computer (at least 2) to solve one problem.

---

### Post by nicolasdiogo on 2010-03-15
thanks,

i solved the problem by ditching ubuntu as a host and adopted PROXMOX to host all virtual machines.

it is a very interisting solution.

i am using it to host my ETL and database projects, and webservers and it is working fine so far and VERY fast with low resource usage.


i will keep you posted..

with regards,

---

### Post by vanvanvan on 2010-05-21
Hi nicolasdiogo
Could you tell me,what system hardware do you use to run PROXMOX .
I want to run PROXMOX for a test as you did,but i only have a 32-bit computer,i saw on the PROXMOX official website ([http://pve.proxmox.com/wiki/Installation](http://pve.proxmox.com/wiki/Installation)) they says the minimum requirement is a 64-bit CPU.
Can i use PROXMOX ?

---

### Post by nicolasdiogo on 2010-05-24
did you see this?

[http://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_Lenny_on_32-Bit_Processor](http://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_Lenny_on_32-Bit_Processor)

---

### Post by xlai on 2010-06-11
[http://kiranmurari.wordpress.com/2010/03/19/uec-cc-nc-single-machine/](http://kiranmurari.wordpress.com/2010/03/19/uec-cc-nc-single-machine/)
you can read this

---

