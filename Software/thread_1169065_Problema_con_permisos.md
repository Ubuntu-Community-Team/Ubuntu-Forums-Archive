---
title: "Problema con permisos"
date: 2009-05-24
forum: Software
---

### Post by leosr on 2009-05-24
Hola.
Instalé Jaunty, todo salió bien. Pero ahora tengo problema con los archivos y carpetas de mi /home, me aparece como propietario a root. Hay forma de cambiar el propietario de carpetas, sub-carpetas y archivos, todo de una vez?
Aclaración: tengo el /home en otra partición.
Gracias!

---

### Post by Hei Ku on 2009-05-24
dentro de /home/<usuario>, pones: 

```

sudo chown -R <usuario>:<usuario> * 

```

---

### Post by emiliano_raso on 2009-05-24
> **Hei Ku said:**
> dentro de /home/<usuario>, pones: 

```

sudo chown -R <usuario>:<usuario> * 

```

Pregunta, mi usuario es emiliano, entonces como me quedaria?

1) sudo chown -R emiliano:emiliano * 
2) sudo chown -R <emiliano>:<emiliano> *

---

### Post by Hei Ku on 2009-05-25
La opcion 1.

---

### Post by emiliano_raso on 2009-05-25
> **Hei Ku said:**
> La opcion 1.

Ok. Gracias. Y agrego una pregunta. Porque pasa lo que le pasó al OP? Porque me pasó dos veces de 200 veces qeu instalé Ubuntu siempre de la misma forma.

---

### Post by Hei Ku on 2009-05-25
A mi me paso al principio, hace mucho, por jugar con el sudo como no debía. No sé cuál puede ser tu caso particular, pero muchas veces eso tiene que ver.

---

### Post by emiliano_raso on 2009-05-25
> **Hei Ku said:**
> A mi me paso al principio, hace mucho, por jugar con el sudo como no debía. No sé cuál puede ser tu caso particular, pero muchas veces eso tiene que ver.

A mi me paso 2 o 3 veces apenas terminé de instalar ubuntu
En la 7.04, en la 8.04 y en la 8.10

---

### Post by leosr on 2009-05-25
> **Hei Ku said:**
> dentro de /home/<usuario>, pones: 

```

sudo chown -R <usuario>:<usuario> * 

```

Gracias por tu respuesta!
No se arregló con lo que sugerís, las sub-carpetas siguen perteneciendo a root.
Despues de instalar Jaunty, luego de que se hace el login, apareció el siguiente mensaje: "Se está ignorando el archivo $HOME/.dmrc del usuario. Esto impide que se guarden la sesión predeterminada y el idioma. El archivo debería pertenecer al usuario y tener los permisos 644. El directorio personal del usuario debe pertenecer al usuario y no ser escribible para otros usuarios."
Fuera de ese mensaje funcionaba todo bien, estaba todo como lo tenía en Intrepid. Entonces quiese "arreglar" ese problema ejecutando Nautilus como root y cambié las propiedades de /home a mi usuario. Después de eso no me volvió a reconocer mi configuración y las carpetas de mi /home pertenecen a root. Como ves no acostumbro a usar la consola.
Alguna idea?

---

### Post by Hei Ku on 2009-05-25
sudo chown -R <usuario>:<usuario> .*

El * no toma a veces los archivos ocultos, pero con eso debería andar.

---

### Post by leosr on 2009-05-25
> **Hei Ku said:**
> sudo chown -R <usuario>:<usuario> .*

El * no toma a veces los archivos ocultos, pero con eso debería andar.
Gracias!
Solucioné lo de las carpetas y archivos de mi /home (no estoy seguro como) pero sigo con el problema con el archivo .dmrc, 644 según vi en otro post quiere decir:
propietario: lectura y ecritura
grupo; lectura
otros: lectura
Así están los permisos del archivo pero sigue apareciendo ese mensaje al iniciar.

Saludos.

---

### Post by Hei Ku on 2009-05-25
quien es el owner del archivo? Porque si el propietario es root, estas en la misma.

---

