---
title: "problema .dmrc"
date: 2008-10-23
forum: Software
---

### Post by tsueseres on 2008-10-23
me sale esto al inicio no se que es y ni como arreglarlo

se esta ignorando el archivo $HOME/.dmrc del usuario. 
el archivo debe pertenecer al usuario y tener los permisos 644
el directorio personal del ususario debe pertenecer al usuario y no ser escribible para otros usuarios

---

### Post by guisheca on 2008-10-23
Poné eso mismo en un buscador y te salen mil resultados. Es un problema bastante típico.
Saludos.

---

### Post by faktorqm on 2008-10-24
```
sudo chgrp usuario /home/usuario 
sudo chown usuario /home/usuario 
sudo chmod 700 home/usuario 
sudo chmod 644 /home/usuario/.dmrc
```

Donde dice "usuario" va el tuyo, obviamente....

guisheca: lee [http://ubuntuforums.org/showthread.php?t=361022](http://ubuntuforums.org/showthread.php?t=361022), seccion II punto 7 ;)

Salu2!

---

### Post by LW7ELK on 2009-06-05
Tuve este mismo problema hoy con Ubuntu 9.04, y la solución de **faktorqm** me funcionó perfecto, Muchas Gracias!!

Pero lo hice con una diferencia. Por error agregé una "/" entre "700" y "home/usuario" en la tercera línea.
Me quedé con la duda porque funcionó, ahora mi duda es: ¿**faktorqm**, te faltó escribir la "/" o ese comando va así?
Pregunto porque la consola todavía no es lo mío, sólo aprendí a usar unos poquitos comandos, generalmente copio y pego :(

Code:

sudo chgrp usuario /home/usuario 
sudo chown usuario /home/usuario 
sudo chmod 700 home/usuario 
sudo chmod 644 /home/usuario/.dmrc

---

### Post by staar on 2009-06-05
está bien como lo hiciste, faktorqm se equivocó...

saludos

---

