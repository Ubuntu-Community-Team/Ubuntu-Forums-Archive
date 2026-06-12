---
title: "como ejecutar sript para poder para configurar hwawei810 y conectarse"
date: 2008-08-22
forum: Software
---

### Post by felagund72 on 2008-08-22
Holaa todos:
 gracias a faktorqm consegui este script de configuracion de modem 810 en este post
 [http://ubuntuforums.org/showthread.php?t=846069](http://ubuntuforums.org/showthread.php?t=846069)
Lo descargue al script y lo descomprimi en el escritorio de mi ubuntu 04.8 . 
El problema es que ahi termina mi sabiduria novatesca. 
¿Como sigo?
Alguno con paciencia me podria ayudar

 gracias

---

### Post by kornykyano on 2008-08-22
tenes que ir al archivo "black_script_eagle_v0.4.sh" y en propiedades > Permiso. Ahí mismo le das permiso para ejecutar el archivo como programa. Luego doble Click ,te aparecera una ventana en el que deberas ejecutar en Terminal y bueno este te ira preguntando...
Suerte.

---

### Post by felagund72 on 2008-08-24
Hice eso. Me pregunta de que empresa soy y puse 2 que corresponde a arnet luego me sale esto
mkdir: no se puede crear el directorio /lib/firmware permiso denegado
cp: no se puede crear el fichero regular/lib/firmware/ueagle es un directorio
dpkg la operacion solicitada precisa  privilegio de superusuario

Aqui me pide clave contraseña  ingreso los dos y empieza a ejecutarse, creo (se llena de lineas) y se cierra solo la terminal y ahi queda.
Seguramente hice algo mal  SOS SOS. Que hago?

---

### Post by kornykyano on 2008-08-24
Perdoname, porque yo me olvide de explicarte:
Hace lo siguiente:
1-Abris terminal y con el comando "cd" te dirigis a la carpeta donde tenes "black_script_eagle_v0.4.sh" Por ejemplo si descomprimiste en /home solo escribis ```
cd huawei810i
```
Proba con "ls" para mostrar el contenido de la carpeta. Deberia dar lo siguiente.
```

[COLOR="Red"]black_script_eagle_v0.4.sh [/COLOR]     [COLOR="Blue"]br2684ctl_20040226-1_i386.deb[/COLOR]
[COLOR="Blue"]br2684ctl_20040226-1_amd64.deb[/COLOR]  firmware
```
2-Pones para ejucutar el script ```
sudo ./black_script_eagle_v0.4.sh
```
Teclea tu contraseña y listo. Creo que no me olvido de nada.

Suerte!
PD:cuando decia "permiso denegado" era por que no eras administrador. Trata de jugar un poco con "cd" y "ls"

---

### Post by faktorqm on 2008-08-25
Hola me fui afuera el finde x eso no t conteste. 
la version 0.4 ya esta actualizada por la 0.6 si mal no recuerdo (corregi muchos errores) y lo tenes que ejecutar con:

```
sudo sh black_script_eagle_v0.6.sh
```

aca te dejo el link [http://ubuntuforums.org/attachment.php?attachmentid=78766&d=1216898225](http://ubuntuforums.org/attachment.php?attachmentid=78766&d=1216898225) Salu2!!

---

