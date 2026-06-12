---
title: "july 2013 lat update broke apache+php+mysql"
date: 2013-07-31
forum: Server Platforms
---

### Post by cxescalona on 2013-07-31
Hi, I upgrade my ubuntu this morning and the update broke the apache server.

I first time, the apache2 server was upgraded, but it removes "libapache2-mod-php5".

Then I use aptitude to reinstall "libapache2-mod-php5" and the unique solution to aptitude is:



  >    Eliminar los paquetes siguientes:                                                                             
1)     php5-json                                                                                                   


     Instalar los paquetes siguientes:                                                                             
2)     apache2-mpm-prefork [2.2.22-1ubuntu1.4 (precise-security, precise-updates)]                                 
3)     apache2-utils [2.2.22-1ubuntu1.4 (precise-security, precise-updates)]                                       
4)     apache2.2-common [2.2.22-1ubuntu1.4 (now, precise-security, precise-updates)]                               
5)     libapache2-mod-php5 [5.3.10-1ubuntu3.7 (now, precise-security, precise-updates)]                            
6)     php5-cli [5.3.10-1ubuntu3.7 (now, precise-security, precise-updates)]                                       


     Desactualizar los paquetes siguientes:                                                                        
7)     php5-common [5.5.1+dfsg-1~precise+1 (now, precise) -> 5.3.10-1ubuntu3.7 (precise-security, precise-updates)]
8)     php5-mysql [5.5.1+dfsg-1~precise+1 (now, precise) -> 5.3.10-1ubuntu3.7 (precise-security, precise-updates)] 




and this remove php5-mysql

if I try to reinstall php5-mysql, it remove "libapache2-mod-php5" again....

---

