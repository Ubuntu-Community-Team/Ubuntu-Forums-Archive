---
title: "No hay video con webcam bluetooth y skype"
date: 2011-12-08
forum: Software
---

### Post by asterix77 on 2011-12-08
Buenas a todos:

Tengo ubuntu lucid 32 bit y he instalado tanto por repositorio como de su web oficial skype. El problema es que al hacer la prueba de video en skype, no logro ver nada.

Uso mi nokia 5230 como webcam vía bluetooth, y programas como amsn o ekiga no tienen problema para usarla, solo en skype.

He seguido algunos consejos agregando lineas tales como al acceso directo

bash -c "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" 

bash -c LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so ./skype

etc, pero sin resultados

Este es el link donde obtuve la forma de hacerlo [http://yusuva.wordpress.com/2009/12/04/how-to-turn-your-camera-phone-into-a-bluetooth-webcam-in-linux-ubuntu/](http://yusuva.wordpress.com/2009/12/04/how-to-turn-your-camera-phone-into-a-bluetooth-webcam-in-linux-ubuntu/)

La verdad, me agrada usar mas esta forma de webcam ya que la imagen es muy nítida.

Desde ya agradezco su ayuda

Saludos

---

### Post by guillermolisi on 2011-12-09
Tengo dos maquinas en las que tenia el mismo problema y lo solucione con este script que ubique en /usr/local/bin
```
#!/bin/bash
export LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
exec skype

```
La webcam es una Genius USB con microfono incorporado de algo mas de cinco años de antigüedad (lamentablemente no encuentro ni recuerdo precisamente el modelo) y Skype no la reconocia ni cuadrada (a pesar de que fisicamente es un globito).

Corre tanto en 32 como en 64 bits con la ultima version de Skype para Linux.

Una de las maquinas corre Kubuntu 11.10, la otra Arch con KDE.

---

### Post by asterix77 on 2011-12-09
Hola Guillermo:

Realicé el script con una pequeña modificación en la ruta, ya que el archivo v4l1compat.so está en: /usr/lib/libv4l/v4l1compat.so, pero tampoco me ha funcionado.


Luego le di permisos de ejecución, lo moví a la carpeta /usr/local/bin/

Acto seguido lo invoqué desde la terminal, pero sigo igual.

Saludos

---

