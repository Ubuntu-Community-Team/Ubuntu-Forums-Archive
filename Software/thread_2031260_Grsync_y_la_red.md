---
title: "Grsync y la red"
date: 2012-07-21
forum: Software
---

### Post by Apipote on 2012-07-21
Hola a todos.

No puedo "ver" mi red con grsync o freefilesync en 12.04.1 con samba instalado y funcionando (en 12.04, no se que pasaba pero no funcionaba). A tal punto que pude setear mi impresora usb en el router e3000 con el firmware TomatoUsb instalado.

Es frustrante ver que si veo la red en windows 7 al querer sincronizar carpetyas con freefilesync y mi NAS. Anda bien y rápido.

Leí que necesito algo de ssh en algún tutorial de sincronización, pero no puedo ver la red y por lo tanto acceder a las carpetas de mi NAS.

Ayuda por favor, y gracias por adelantado.

---

### Post by papibe on 2012-07-22
Hola Apipote.

Para que Grsync/rsync sincronize a un sistema remoto tiene que ser a través de ssh o, conectándose a un servicio (daemon).

Si tu NAS no es un sistema Linux, FreeBSD o similar , esto no se puede hacer.

Sin embargo, puedes montar el directorio temporalmente en tu sistema de archivos. De esta manera el directorio remoto se ve igual que un directorio local. Grsync no tendría problemas para sincronizar de esta manera.

Espero que estas ideas te ayuden.
Avísanos cualquier cosa.
Saludos.

---

### Post by Apipote on 2012-07-22
Si es un sistema linux (debian). Es un western digital mybooklive de 2tb. Lo loco es que en la red, lo veo y accedo a sus archivos con Nautilus.
Pero no se como hacer para que grsync (unison o el que sea) lo vea y por lo tanto sincronice carpetas como SI hace windows 7.
Sabes como hacer eso?
Gracias.

---

### Post by papibe on 2012-07-22
Alternativas:
[LIST=1]
[*]La más fácil, pero tienes que tener mucho cuidado con la recursion (excluir este directorio o usar la opción -x): El directorio remote que puedes ver on Nautilus está montado discretamente en el directorio ~/.gvfs
[*]Montar el share. Necesitas instalar el paquete cifs-utils, crear un directorio y montar el share para que aparezca local para Grsync.
[*]Installar ssh on el sistema Debian. Installar el paquete openssh-server. Después de eso puedes usar el destino como:
```
rsync -av /path/al/fuente_local  usuario@server_debian:/path/al/dir_remoto
```
[/LIST]
Avísanos que decides y como te va.
Saludos.

---

### Post by Apipote on 2012-07-22
Uy, me supera.
No hay nada mas fácil?
Me parece que mi error es el no saber escribir los parámetros en grsync.
Si mi usuario es "javier" y mi pc es "decima" y el nas es "mybooklive" y el entorno de red es "workgroup".
Ahh e instalé el ssh server.
?

---

### Post by papibe on 2012-07-22
Una vez que ssh server está instalado en el sistema Debian, lo primero es probar la conexión remota (si la conexión remote funciona, Grsync también).

Desde tu computadora conectate remotamente al server de la siguiente manera:
```
ssh mybooklive
```
o 
```
ssh userio_de_Debian@mybooklive
```
Avísanos como te va.

---

### Post by hictio on 2012-07-23
Estás seguro que el servidor remoto, al que te querés conectar para hacer los backups, tiene SSH habilitado y el servicio está escuchando en el puerto?
Desde tu máquina, podés testear rápidamente la conexión básica TCP. Abrí un Terminal, y tipeá:

```

telnet direccion.ip.remota 22 ENTER

```

Si el SSH está corriendo y escuchando en el servidor remoto, tendrías que ver similar a esto:

```

Trying direccion.ip.remota...
Connected to direccion.ip.remota.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.3

```

Para salir, tipeá ENTER un par de veces.

---

### Post by Apipote on 2012-07-23
Ah ah, por la pagina web del NAS se puede activar el ssh. Luego cuando llegue a casa pruebo y les cuento.
Gracias !!

---

### Post by Apipote on 2012-08-04
Funciona, pero me pide una clave. Cuando la pongo me la rebota, es la que uso para entrar por la página web del Nas.
Que hago?
Gracias

---

### Post by hictio on 2012-08-04
Mmmmhhh... Pareciera que via SSH es otro usuario, o bien, otra contraseña diferente que la que se usa via webfront...
Con qué usuario te conectás al webfront, y con que usuario estás haciendo los tests de conexión via SSH?

---

### Post by Apipote on 2012-08-04
Ahora entro perfectamente por la consola si uso: sudo ssh mybooklive Me pide una clave que me fijé es welc0me por default en el NAS, y ya estoy adentro. Evidentemente el ssh anda perfecto.
Pero con el grsync nada. Sigo pensando que no pongo bien los parámetros en carpeta origen y destino.

Alguna sugerencia?

Ahh me olvidaba, con DejaDup puedo hacer un backup perfectamente por ssh.

Gracias !!

---

### Post by hictio on 2012-08-05
El grsync con qué usuario lo estás ejecutando?

---

### Post by Apipote on 2012-08-07
javier...es el usuario de mi pc. 
Algo pasa con grsync porque pongo como origen el NAS: 

root@192.168.1.110:/Public/Shared Pictures

Y como destino el portatil usb: /local/Samsung/Public/Shared Pictures

Y me da error como que no encuentra el directorio del NAS.

Estoy seguro que es una pelotudez...

---

### Post by marohds on 2012-08-08
Creo que el problema lo tenés en la ruta a la carpeta.
 
Tenés que anteponer el caracter "\" a los espacios en blanco de archivos y carpetas.
 
Probá con la siguiente manera:
 
root@192.168.1.110:/Public/Shared\ Pictures
 
Suerte!

---

### Post by Apipote on 2012-09-09
Nada che. Un embole.
Todo parece estar bien, pero no entiendo porque me da error.
Origen: root@192.168.1.110/Public/ (el NAS)

Destino:/media/SAMSUNG/Public (el disco USB conectado a mi pc).

Alguna sugerencia?

Gracias !!

---

### Post by Apipote on 2012-09-11
Upsss...
Nadie por acá ?

---

### Post by Apipote on 2012-09-29
Ahh bueno, gracias !!
Vaya foro !!
:D :D

---

### Post by papibe on 2012-09-30
Por default la cuenta root no está habilitada, y por lo tanto no va a aceptar connections a través de ssh, y menos con rsync.

Mi primera sugerencia sería cambiar el diseño de lo que estás haciendo para que uses cuentas de usuarios normales.

En caso de que no tengas otra alternativa que usar root, tienes que habilitar la cuenta primero. Si te puedes conectar con ssh, significa que puedes hacer rsync.

Cuéntanos como te va.
Saludos.

---

### Post by Apipote on 2012-10-01
Gracias por darme bola !!
Si, siempre lo hice con el ssh habilitado del NAS. Y nada.
Es increíble con no pueda ver la red ni en grsync ni en freefilesync (y en win 7 puedo... sin hacer nada raro).
Que dificil se hace a veces !!
Ya corté por lo sano, me harté y lo hago en mi otra pc con win 7.
Gracias igualmente !!!

---

