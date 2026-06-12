---
title: "Depurar contenido de /home en forma segura"
date: 2009-10-09
forum: Software
---

### Post by leosr on 2009-10-09
Hola.

A mi /home lo tengo desde Hardy, puede que haya cosas que ya no sirven y estén ocupando lugar. Hay alguna forma segura de "limpiarlo" sin borrar nada vital? El "Encargado de limpieza" no me parece para nada seguro, por ejemplo.

Bueno... es todo por ahora :P
Salu2

---

### Post by luks911 on 2009-10-09
Como decís, el Encargado de Limpieza por ahora lo único que hace es borrar paquetes instalados que no están en los repositorios, o sea que instalaste desde algún .deb.
Lo que podés buscar en /home son directorios ocultos (los que empiezan con un punto "." y que desde nautlus los hacés visible con Ctrl+H) que hagan referencia a programas que instalaste, después los desinstalaste y ya no están.
También podés probar Bleachbit (está en repositorios), que borra cookies, enlaces rotos, miniaturas de imágenes y un par de etcéteras más.
De todos modos, no esperes ganar mucho espacio. Y no olvides que si no está roto quizá lo mejor es no arreglarlo :D

---

