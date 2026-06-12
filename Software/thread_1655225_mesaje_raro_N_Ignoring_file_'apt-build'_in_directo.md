---
title: "mesaje raro N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d"
date: 2010-12-29
forum: Software
---

### Post by 3nG3ndR0 on 2010-12-29
hola al hacer sudo apt-get update me da un mensaje raro al finalizar la actualización de repositorios:

```
Obj http://ppa.launchpad.net maverick/main i386 Packages                       
Obj http://ppa.launchpad.net maverick/main Sources                             
Obj http://ppa.launchpad.net maverick/main i386 Packages                       
Descargados 2279B en 6s (369B/s)                                               
Leyendo lista de paquetes... Hecho
N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension

```

---

### Post by asterix77 on 2010-12-30
Al parecer se trataría de un bug reportado en Maverick

[https://bugs.launchpad.net/ubuntu/+source/apt-build/+bug/693715](https://bugs.launchpad.net/ubuntu/+source/apt-build/+bug/693715)

Al parecer existe una forma de fijarlo en:

[http://www.webupd8.org/2010/08/fix-ignoring-file-save-in-directory.html](http://www.webupd8.org/2010/08/fix-ignoring-file-save-in-directory.html)


Espero que te pueda servir


Saludos

---

### Post by 3nG3ndR0 on 2010-12-30
gracias por responder, ya había probado eso y ni me funciona sigue igual.

---

### Post by moreback on 2010-12-30
En ese directorio se guardan los depósitos agregados con **Orígenes de software** (Sistema -> Administración) o vía apt-add-repository.

¿De seguro están bien creados estos archivos y que no tienes ninguno con mala sintaxis?

---

### Post by disparil on 2011-03-08
No le gusta el fichero sin extensión **apt-build**... o eso es lo que parece.

Yo he probado eliminándolo y ya no se me queja. :confused:

---

