---
title: "Reinstalar OpenOffice 3.1.0"
date: 2009-05-13
forum: Software
---

### Post by kornykyano on 2009-05-13
Bonyour!! amigotes :D

Estoy por reintalar Openoffice para tener la ultima versión (3.1.0) y tengo una duda respecto al mensaje que da el desintalador:

**sudo apt-get remove openoffice*.***

[B]Desinstalando openoffice.org3 ...
dpkg - atención: al desinstalar openoffice.org3, el directorio /opt/openoffice.org3/share/uno_packages/cache'
no está vacío, no se borra.
dpkg - atención: al desinstalar openoffice.org3, el directorio /opt/openoffice.org3/share/uno_packages'
no está vacío, no se borra.
dpkg - atención: al desinstalar openoffice.org3, el directorio /opt/openoffice.org3/share'
no está vacío, no se borra.
dpkg - atención: al desinstalar openoffice.org3, el directorio /opt/openoffice.org3'
no está vacío, no se borra.[/B]

Lo debería borrar manualmente o lo dejo?? no habría problemas cuando lo instale el nuevo openoffice?

Au revoir!

---

### Post by pablo.s on 2009-05-13
> **kornykyano said:**
> Estoy por reintalar Openoffice para tener la ultima versión (3.1.0) y tengo una duda respecto al mensaje que da el desintalador:

**sudo apt-get remove openoffice*.*** 

Si desinstalás un paquete te 
desinstala las dependencias.
Si no las desinstala, con un
-purge lo hace. Pero no veo la
necesidad de usar *.* para
desinstalar. Te has confundido
de sistema operativo?

---

