---
title: "Guardar paquetes descargados durante la instalación"
date: 2010-10-27
forum: Software
---

### Post by Spity on 2010-10-27
Hola! 

Al instalar Ubuntu, durante la instalacion, se descargan algunos paquetes, imagino que de idioma y algunos mas.
Mi pregunta es si puedo guardar dichos paquetes (los he buscado por el sistema pero no los encuentro) porque me imagino que mientras se instalan quedaran en algun directorio temporal del sistema (livecd). 
Tengo la idea de hacer una instalación y que no descargue los paquetes sino que los lea desde los que he guardado. Se entiende?

---

### Post by EnriqueK on 2010-10-28
**/var/cache/apt/archives**

---

### Post by Spity on 2010-11-11
Hola!

Ya lo he solucionado y te corrijo, durante la instalación están ubicados en:
/target/var/cache/apt/archives

---

### Post by guillermolisi on 2010-11-11
No se que version de Ubuntu estas utilizando pero en la 10.04.01 el directorio /target no existe, a menos que se borre luego de terminada la instalacion. El resto de la estructura si.

---

### Post by alfplayer on 2010-11-11
Probablemente, /target es el mount point durante la instalación del root del sistema instalado.

---

