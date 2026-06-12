---
title: "nagios question"
date: 2010-10-24
forum: Server Platforms
---

### Post by newbie_css on 2010-10-24
hey everyone

im new here. thx for ur guys' helps in advance


if i wanna monitor a ip address like 198.168.71.23 

should i edit switch.cfg or localhost.cfg? or other configure file?

thx so much for your help, and sry about my short knowledge. 

-----------------------------------------------------------------------------------------------------

2nd question is about samba

i did install every samba packages for folder sharing

but i still got error msg 'no such file/folder' when i start samba in terminal 

i tried to restart nmbd and smbd; they r not working to fix this problem

if anyone know how to fix it, i will be so appreciated

thx again

---

### Post by newbie_css on 2010-10-24
sry, i think i posted my thread at wrong place. anyone can move to server platforms?

or can i open a new thread over there?:confused:

thx

---

### Post by newbie_css on 2010-10-24
hey everyone

im new here. thx for ur guys' helps in advance


if i wanna monitor a ip address like 198.168.71.23 

should i edit switch.cfg or localhost.cfg? or other configure file?

thx so much for your help, and sry about my short knowledge. 

-----------------------------------------------------------------------------------------------------

2nd question is about samba

i did install every samba packages for folder sharing

but i still got error msg 'no such file/folder' when i start samba in terminal 

i tried to restart nmbd and smbd; they r not working to fix this problem

if anyone know how to fix it, i will be so appreciated

thx again

---

### Post by cariboo on 2010-10-24
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by koenn on 2010-10-25
2 completely unrelated issues in the same thread is also not a good idea

---

### Post by koenn on 2010-10-25
> **newbie_css said:**
> 
if i wanna monitor a ip address like 198.168.71.23 

should i edit switch.cfg or localhost.cfg? or other configure file?


nagios will read pretty much any file that has a .cfg extension an is in /etc/nagios

so you could make a specific file per host, or per group of hosts, or just throw it anywhere. 

```

define host{
        use                     generic-host  ; Name of template
        host_name               name_goes_here
        alias                   Novell Server #1
        address                 192.168.1.2
        }

```

this will work because other settings will be inherited from the config file that contains  a definition for 'generic-host' 


You probably neet to read a bit on nagios config.
This guy has the right idea :
[http://www.standalone-sysadmin.com/blog/2009/07/nagios-config/](http://www.standalone-sysadmin.com/blog/2009/07/nagios-config/)

---

### Post by newbie_css on 2010-10-25
> **koenn said:**
> nagios will read pretty much any file that has a .cfg extension an is in /etc/nagios

so you could make a specific file per host, or per group of hosts, or just throw it anywhere. 

```

define host{
        use                     generic-host  ; Name of template
        host_name               name_goes_here
        alias                   Novell Server #1
        address                 192.168.1.2
        }

```this will work because other settings will be inherited from the config file that contains  a definition for 'generic-host' 


You probably neet to read a bit on nagios config.
This guy has the right idea :
[http://www.standalone-sysadmin.com/blog/2009/07/nagios-config/](http://www.standalone-sysadmin.com/blog/2009/07/nagios-config/)


thx so much koenn, i will try it 
:D

---

