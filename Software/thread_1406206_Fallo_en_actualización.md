---
title: "Fallo en actualización"
date: 2010-02-13
forum: Software
---

### Post by guidito73 on 2010-02-13
Bueno, puse a actualizar por Synaptic y tras la descarga de los paquetes me sale el siguiente error: (Vale aclarar que estoy usando Lucid Lynx)

>  E: No se pueden corregir los paquetes que faltan

W: Falló al obtener [http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/indicator-application_0.0.13-0ubuntu1_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/indicator-application_0.0.13-0ubuntu1_i386.deb)
  404  Not Found


W: Falló al obtener [http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/libappindicator0-cil_0.0.13-0ubuntu1_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/libappindicator0-cil_0.0.13-0ubuntu1_i386.deb)
  404  Not Found


W: Falló al obtener [http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/libappindicator0_0.0.13-0ubuntu1_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/libappindicator0_0.0.13-0ubuntu1_i386.deb)
  404  Not Found


W: Falló al obtener [http://ar.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.29.90-0ubuntu1_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.29.90-0ubuntu1_i386.deb)
  404  Not Found


W: Falló al obtener [http://ar.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.29.90-0ubuntu1_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.29.90-0ubuntu1_i386.deb)
  404  Not Found


W: Falló al obtener [http://ar.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.29.90-0ubuntu1_all.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.29.90-0ubuntu1_all.deb)
  404  Not Found



---

### Post by josecuervo86 on 2010-02-13
Fijate que los enlaces aparecen rotos

Podes mostrar lo que tenes en /etc/apt/sources.list y en etc/apt/sources.list.d?

---

### Post by guidito73 on 2010-02-13
> **josecuervo86 said:**
> Fijate que los enlaces aparecen rotos

Podes mostrar lo que tenes en /etc/apt/sources.list y en etc/apt/sources.list.d?

sources.list:

> # deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Alpha i386 (20100113)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main

sources.list.d:(en tres archivos distintos)

> deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/docky-core/ppa/ubuntu](http://ppa.launchpad.net/docky-core/ppa/ubuntu) lucid main

---

### Post by josecuervo86 on 2010-02-13
Parecen estar bien, pero siguiendo la ruta de los enlaces [0] donde salta el error me encontré que esta buscando paquetes pero con otro nombre. Ejemplo:

Busca esto: indicator-application_0.0.13-0ubuntu**[COLOR="Red"]1[/COLOR]**_i386.deb
Pero en cambio esta este: indicator-application_0.0.13-0ubuntu**[COLOR="red"]2[/COLOR]**_i386.deb

[0] [http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/](http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/)

---

### Post by guidito73 on 2010-02-13
> **josecuervo86 said:**
> Parecen estar bien, pero siguiendo la ruta de los enlaces [0] donde salta el error me encontré que esta buscando paquetes pero con otro nombre. Ejemplo:

Busca esto: indicator-application_0.0.13-0ubuntu**[COLOR="Red"]1[/COLOR]**_i386.deb
Pero en cambio esta este: indicator-application_0.0.13-0ubuntu**[COLOR="red"]2[/COLOR]**_i386.deb

[0] [http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/](http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/)

Qué raro. Qué recomendas que haga?

---

### Post by josecuervo86 on 2010-02-13
Probaste con sudo apt-get update? Es lo que yo haria, porque me parece que han actualizado los paquetes pero vos tenes los viejos

---

### Post by guidito73 on 2010-02-13
> Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Translation-es              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-es                         
Des:1 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid Release.gpg [189B]                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/main Translation-es                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Translation-es        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Translation-es          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Translation-es        
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-es 
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-es                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/restricted Translation-es               
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/universe Translation-es                 
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/multiverse Translation-es               
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/main Translation-es             
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/restricted Translation-es       
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/universe Translation-es         
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/multiverse Translation-es       
Des:2 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid Release [57,2kB]                      
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages          
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates Release    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                             
Des:3 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/main Packages [1.401kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources          
  404  Not Found
85% [3 Packages 1186264/1.401kB 84%]                                30,9kB/s 6s^C
guido@guido-desktop:~$ ^C
guido@guido-desktop:~$ sudo apt-get update
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Translation-es              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Translation-es        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-es                         
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid Release.gpg                             
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/main Translation-es                     
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/restricted Translation-es               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Translation-es          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Translation-es        
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-es                         
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-es 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release             
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/universe Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/multiverse Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/main Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/restricted Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/universe Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/multiverse Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid Release
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Des:1 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/main Packages [1.401kB]               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources
  404  Not Found
Des:2 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/restricted Packages [6.208B]          
Des:3 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/main Sources [655kB]                  
Des:4 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/restricted Sources [3.681B]           
Des:5 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/universe Packages [5.475kB]           
Des:6 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/universe Sources [3.156kB]            
Des:7 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/multiverse Packages [186kB]           
Des:8 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/multiverse Sources [119kB]            
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/main Packages                   
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/restricted Packages             
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/main Sources                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/restricted Sources              
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/universe Packages               
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/universe Sources                
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/multiverse Packages             
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates/multiverse Sources              
Descargados 9.813kB en 6min 13s (26,3kB/s)                                     
W: Imposible obtener [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/main/source/Sources.gz](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.


Eso sale haciendo un sudo apt-get update. Aparentemente, se rompieron los repositorios :S

---

### Post by josecuervo86 on 2010-02-13
Eso parece por que fijate que aca [0] no aparece lucid

[0] [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/)

---

### Post by guidito73 on 2010-02-14
> **josecuervo86 said:**
> Eso parece por que fijate que aca [0] no aparece lucid

[0] [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/)

Es raro porque no encuentro nada por la red tampoco. No estará reportado?

---

### Post by josecuervo86 on 2010-02-14
Yo creo que todavía no han hecho la actualización de los paquetes que han subido. La verdad que no entiendo muy bien como es el tema, pero calculo que el sistema hace una verificación de los paquetes en la red en base a una "lista" que le debe llegar y que le dice cual es el paquete que esta disponible. Al no saber que ese paquete esta disponible, entonces no lo descarga y sigue buscando el viejo, que como no lo encuentra te tira error. Igual estas son todas suposiciones mias y estaría bueno que alguien que sepa aclare el asunto! :)

---

### Post by juancarlospaco on 2010-02-15
Lucid va a fallar y es normal, hasta que sea final.

No uses los mirrors de Argentina para Lucid, usa el principal.

---

