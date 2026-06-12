---
title: "Problemas con el centro de software y gestor de paquetes"
date: 2011-04-09
forum: Software
---

### Post by enzo_86 on 2011-04-09
Que tal...bueno la verdad que soy bastante nuevo en ubuntu y por curioso empeze a bajar paqutes y programas que no sabia muy bien que era....la cosa que ahora cadqa vez que descargo algo o quiero un paquete de synaptic me tira este erro...bueno...espero que me puedan ayudar... UN ABRAZUNTU....CUAC!

Configurando adzapper (20090301-1) ... 
invoke-rc.d: unknown initscript, /etc/init.d/squid not found. 
dpkg: error al procesar adzapper (--configure): 
 el subproceso instalado el script post-installation devolvió el código de salida de error 100 
Se encontraron errores al procesar: 
 adzapper 
Configurando adzapper (20090301-1) ... 
invoke-rc.d: unknown initscript, /etc/init.d/squid not found. 
dpkg: error al procesar adzapper (--configure): 
 el subproceso instalado el script post-installation devolvió el código de salida de error 100 
Se encontraron errores al procesar: 
 adzapper 

:confused:

---

### Post by juancarlospaco on 2011-04-10
Proba en una Terminal ejecutando, de a uno a la vez:

sudo dpkg --configure -a

sudo dpkg --purge --force adzapper

sudo apt-get install -f

sudo apt-get clean ; sudo apt-get -qq update && sudo apt-get check && sudo apt-get autoremove

---

