---
title: "Problema al iniciar Ubuntu 10.04"
date: 2010-06-23
forum: Software
---

### Post by julicabrini on 2010-06-23
Lamentablemente tengo un problemita al iniciar la ultima version de ubuntu.

La cosa es asi, no arranca el modo grafico y me pide el usuario y contraseña por modo de texto. Los pongo y entra perfecto. Ahora pongo el comando startx para iniciar las graficas y me tira un error que mucho no entiendo pero creo que es algún conflicto con Nvidia.. A continuación pongo imágenes del error...

[IMG]http://s3.subirimagenes.com:81/fotos/previo/thump_4708314imagen0007.jpg[/IMG]

[IMG]http://s3.subirimagenes.com:81/fotos/previo/thump_4708330imagen0008.jpg[/IMG]

[IMG]http://s3.subirimagenes.com:81/fotos/previo/thump_4708334imagen0009.jpg[/IMG]

[IMG]http://s3.subirimagenes.com:81/fotos/previo/thump_4708338imagen0010.jpg[/IMG]

pone algo de revisar el archivo "xorg" pero no tengo ni idea..

Ubuntu estaba funcionando muy bien hasta que los drivers privativos de Nvidia me hicieron reiniciar la máquina... 

Agradecería mucho sus respuestas!!

Saludos!

---

### Post by alfplayer on 2010-06-24
La instalación del controlador de Nvidia fue exitosa? No surgieron errores?

---

### Post by SLA_leandrin on 2010-06-24
Fijate en tu archivo /etc/X/xorg.conf de hacer lo siguiente;

```
sudo cp /etc/X/xorg.conf /etc/X/xorg.conf.backup
sudo nano /etc/X/xorg.conf
```

Buscá en el archivo donde diga

```
driver="nvidia"
```

y cambialo por

```
driver="nv"
```

Y fijate si te arranca la interfaz gráfica.

---

### Post by julicabrini on 2010-06-24
Gente gracias por responder... Solucioné el problema desde el primer kernel de la version.. Actualizé todo y despues pude arrancar sin problemas... Perdon por responder tarde! 

Saludos y gracias nuevamente!

---

