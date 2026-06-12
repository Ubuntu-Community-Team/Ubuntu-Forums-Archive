---
title: "Problema con google earth"
date: 2009-10-04
forum: Software
---

### Post by MPx1 on 2009-10-04
Buenas, si, yo otra vez.. jeje.. bueno tengo un problema con Google Earth. me baje en bin [version 4.3], lo instalo y todo bien.. pero a la hora de ejecutarlo me salen estas ventanitas:

[IMG]http://img340.imageshack.us/img340/7210/googleearth.png[/IMG]

[IMG]http://img101.imageshack.us/img101/1017/cache.png[/IMG]

[IMG]http://img101.imageshack.us/img101/2121/avisogoogle.png[/IMG]

esto es lo que hice:

bajar el binaro 
 darle permisos chmod +x nombre_binario.bin
  ejecurtalo [./nombre_binario.bin]

pero aun asi.. me salen esas ventanas..

NOTA: no instale la ultima version porque no se ve bien la textura del mundo [para ser mas preciso, se ve la tierra toda amarilla]

disculpen por los screenshot gigantes.. :P

Gracias

---

### Post by SLA_leandrin on 2009-10-04
Está tratando de crearte un subdirectorio en el home del root... se me ocurre que tal vez cambiando el propietario del archivo funcione.

En el directorio dondé está el archivo cambiá el dueño con chown
```
sudo chown nombre_de_usuario\: nombre_de_archivo
```

Probá a ver que pasa...

---

### Post by MPx1 on 2009-10-04
te agradezco.. pero no pasó nada.. :( sigue igual

---

### Post by mama21mama on 2009-10-04
yo lo instalo [siempre de medibuntu]("http://mamalibre.eshost.com.ar/?q=node/199")

---

### Post by MPx1 on 2009-10-07
Disculpa mama, pero no me gusta agregar repositorios de terceros.. :P

---

### Post by guillermolisi on 2009-10-07
> **MPx1 said:**
> Disculpa mama, pero no me gusta agregar repositorios de terceros.. :P
Si te referis a los repositorios de Medibuntu, los vengo usando desde hace ya mucho tiempo y nunca tuve problemas, todo lo contrario me los han resuelto.

Medibuntu es de terceras partes pero no son repositorios de un individuo, es todo un proyecto grupal ([https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)**Medibuntu**)

---

### Post by MPx1 on 2009-10-07
pss.. probe, pero me salen las ventanas iguales.. arranca el programa pero en la pantalla en donde supuestamente aparece el mundo esta todo negro.. :(

---

### Post by mama21mama on 2009-10-07
te fíjaste si tenes 3d y aceleración?

---

### Post by MPx1 on 2009-10-08
[IMG]http://img230.imageshack.us/img230/5692/pantallazoenvyng.png[/IMG]

---

### Post by guillermolisi on 2009-10-08
Estas iniciando la aplicacion con Compiz activo ? que pasa si lo desactivas ?

---

### Post by MPx1 on 2009-10-08
no, está desactivado..

---

### Post by SLA_leandrin on 2009-10-08
El problema que te está tirando es porque no tenés permisos de escritura en un directorio del root.

QUe pasa si lo ejecutas con sudo? probaste? o no queres?

---

### Post by MPx1 on 2009-10-09
en un principio instale el binario con sudo y me tiró ese error, depues le di permisos al binario para mi usuario, lo instalo y me tira error, y finalmente, lo instalo desde los repositorios de Medibuntu y me tira error, solo que en este ultimo caso en donde, supuestamente aparece el mundo, se ve todo negro..

---

