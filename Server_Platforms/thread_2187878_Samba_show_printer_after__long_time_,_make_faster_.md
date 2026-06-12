---
title: "Samba show printer after  long time , make faster discovery from windows"
date: 2013-11-14
forum: Server Platforms
---

### Post by enjoy10 on 2013-11-14
Hi there,
I have set-up cups with samba integrate everything working fine , all the printers are sharing  in the network , 
mac clients works fine, *Bonjour* protocol is very fast :P

im using ubuntu 12.04 64bit with samba  3.6.3-2ubuntu2.8  and cups 1.5.3-0ubuntu8 

the only issue is for the any windows(xp/vista/7) clients, when I tried to search the printer from "panel control">"add a device" it will take 20-40 sec , :(

Is there config to make more fast the print sharing ? Faster I mean when I search on windows machine it will come out in 1-5 sec .

I don't care about sharing file  and the printer are just sharing in local in different vlans.

I have tried some optimization the  config without any relevant result. 

From the default config  smb.conf :
I have change few things :   
 socket options = IPTOS_LOWDELAY TCP_NODELAY
 name resolve order = bcast host

 :confused: that I'm not sure if this setting have need to be change :
disable netbios = No

and also I'm not running a wins server ,
do you think is better to run ? it will make faster the discovery device ?


update: yes if I install on windows, "bonjour print services for windows " ,
 it's working like on mac the printer come out immediately, but I want zero config from the windows client . 

thanks a lot

---

