---
title: "Problema con el directorio /etc/"
date: 2009-11-07
forum: Software
---

### Post by fezh on 2009-11-07
Como me sugirió guillermolisi [acá]("http://ubuntuforums.org/showpost.php?p=8267892&postcount=19"), estoy haciendo un nuevo thread para evitar desvirtuar mi thread anterior.
Bueno, volviendo a mi (nuevo) problema, no puedo visualizar gran parte de los archivos/carpetas dentro del directorio /etc/, mucho menos modificarlos y abrirlos. ¿Alguna idea?

---

### Post by Mauro22 on 2009-11-07
/etc pertenece a root, para modificar archivos ahi tenes que ser root o tener privilegios (sudo)


Si estas en ubuntu, podes hacer un 'sudo nautilus' para recorrer /etc en forma grafica y con privilegios...

---

### Post by z37a on 2009-11-08
> **Mauro22 said:**
> /etc pertenece a root, para modificar archivos ahi tenes que ser root o tener privilegios (sudo)


Si estas en ubuntu, podes hacer un 'sudo nautilus' para recorrer /etc en forma gráfica y con privilegios...

También desde la consola podes hacer un "sudo -s" y ejecutas una instancia de BASH como root, podrías entrar ver y modificar a cualquier carpeta, además del /etc.

Lo único TENE MUCHO CUIDADO, lo resalto con mayúsculas por que en el /etc están todas las configuraciones que utiliza el sistema, en lo posible intenta antes de modificar algo hacer una copia de seguridad del archivo en cuestión, para que si algo no funciona lo volves a atrás fácilmente.

---

