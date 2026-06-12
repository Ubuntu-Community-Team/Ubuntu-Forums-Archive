---
title: "Pregunta repositorio, Clave publica"
date: 2008-10-30
forum: Software
---

### Post by victor_nesta on 2008-10-30
Desde ayer que no puedo actualizar la lista de repositorios.  Por culpa de Medibuntu
Me sale el siguiente error

W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783

Desactivo el repo y sale lo mismo. 

hasta ayer funcionaba joya, ni idea que paso.

¿Tengo que colgar mi clave publica en algun lado? ¿Como? por que no pude

---

### Post by chakersito on 2008-10-30
Victor, proba con esto:
```
$ sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
Creo que con eso deberia funcionar.

Saludos.

Hugo

---

### Post by victor_nesta on 2008-10-30
> **chakersito said:**
> Victor, proba con esto```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
Creo que con eso deberia funcionar.

Saludos.

Hugo

Si, es justamente ahí donde esta el problema.

mira después del kering, empieza el update y aparece

Leyendo lista de paquetes... Hecho
W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
medibuntu-keyring ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

Sige con el resto y cierra con 
Descargados 205B en 44s (5B/s)
Leyendo lista de paquetes... Hecho
W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problema

Sera que hoy es el dia de lanzamiento y tienen despelote con los repo?

---

### Post by chakersito on 2008-10-30
Entonces es probable que se haya caido algo en el medio, pero dudo que el problema sea tuyo.
Debe estar todo hasta las p****** por el tema de la release.

---

### Post by victor_nesta on 2008-10-30
Si, la verdad nose, ya veremos.
Igualmente 1000 Gracias

Aca dejo una captura, no agrega la key
[http://img84.imageshack.us/my.php?image=14633225am0.jpg](http://img84.imageshack.us/my.php?image=14633225am0.jpg)

---

### Post by santiagoward2000 on 2008-10-30
Hola!
Es un problema temporal de los repositorios de Medibuntu. A mí me pasa todo el tiempo. Seguro que para mañana se va a arreglar. No te preocupes, seguro que no es nada en tu máquina.
Saludos!

---

