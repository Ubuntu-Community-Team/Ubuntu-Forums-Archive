---
title: "¿Cómo vaciar de la papelera archivos que no se dejan eliminar?"
date: 2009-07-03
forum: Software
---

### Post by jorval on 2009-07-03
Hola amigos. No podía eliminar de mi papelera un archivo. Tengo Ubuntu 8.04 

Sencillamente puse en terminal el siguiente comando: > sudo rm -rf ~/.local/share/Trash/files/*

En esta dirección encontrarán más antecedentes, espero les sirva.


[http://comohagoenlinux.blogspot.com/2007/11/cmo-vaciar-la-papelera-en-ubuntu-cuando.html]("http://comohagoenlinux.blogspot.com/2007/11/cmo-vaciar-la-papelera-en-ubuntu-cuando.html")

---

### Post by aledruetta on 2009-07-03
Alguna vez, lo que hice fue: 

```
sudo nautilus
```

y ahí borré el contenido de esa carpeta. Por ahí, cuando uno no tiene buena memoria para recordar comandos, es una alternativa.

Saludos,
Alejandro.

---

### Post by Patriciologico on 2009-07-06
Cuando uno elimina archivos de un usuario cualquiera como root (ej. sudo nautilus) los archivos borrados se van a la papelera root y siguen quedando en el sistema. Cuando se utilice esta opcion, asegurense de borrar con shift+Supr (eliminacion permanente) o luego de haber enviado a papelera vaciar la papelera root.

Saludos!

---

### Post by dnovai on 2009-07-06
Cuál es la papelera *root*?
Está oculta o algo así? Cómo puedo tener acceso a ella?
Perdón, pero soy ***newbie*** en esto.


Saludos!

---

### Post by Patriciologico on 2009-07-06
/root/.local/share/Trash

Saludos!

---

