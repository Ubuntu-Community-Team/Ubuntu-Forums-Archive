---
title: "Problemas con permisos de escritura"
date: 2008-06-28
forum: Software
---

### Post by javier-2714 on 2008-06-28
hola a todos tengo un celu con memoria micro sd la cual la conecto al lector de memorias para copiar y cargar musica,fotos,etc el tema es que de un día para el otro cuando quiero borrar algo me dice que no tengo permisos le quiero cambiar los permisos me dice cambiando permisos pero no pasa nada gogleando encontré este comando chmod u+rw /media/disk no se si es correcto 
como hago para volver a tener permisos de escritura nuevamente estoy utilizando ubuntu 7.04 espero alguna ayudita gracias.

---

### Post by Alvaro77 on 2008-06-28
> **javier-2714 said:**
> hola a todos tengo un celu con memoria micro sd la cual la conecto al lector de memorias para copiar y cargar musica,fotos,etc el tema es que de un día para el otro cuando quiero borrar algo me dice que no tengo permisos le quiero cambiar los permisos me dice cambiando permisos pero no pasa nada gogleando encontré este comando chmod u+rw /media/disk no se si es correcto 
como hago para volver a tener permisos de escritura nuevamente estoy utilizando ubuntu 7.04 espero alguna ayudita gracias.

Hola Javier, prueva con lso siguientes comandos: 

[COLOR="RoyalBlue"]#sudo chmod 777 ruta_de_tu_dispositivo_montado[/COLOR] (das todos los permisos al dir del dispositivo)
ó
[COLOR="RoyalBlue"]#sudo chmod 777 ruta_de_tu_dispositivo_montado/*[/COLOR] (das todos los permisos al contenido del dir del dispositvo -archivos de fotos, musica, lo q sea q tengas-).

si quieres solo escritura:

[COLOR="RoyalBlue"]#sudo chmod a+w ruta_de_tu_dispositivo_montado[/COLOR] (a todos les agrega escritura) 
[COLOR="RoyalBlue"]#sudo chmod a+w ruta_de_tu_dispositivo_montado/*[/COLOR]

si quieres que a solo al usuario propietario pon u+w en lugar de a+w

o prueva como root también :P.


saludos.-

---

### Post by javier-2714 on 2008-06-28
agradezco tu rápida respuesta pero no hay caso me dice  cambiando los permisos pero no hace nada alguna idea que pasa.

javier@javier-desktop:~$ sudo chmod 777 /media/disk
Password:
chmod: cambiando los permisos de `/media/disk': Sistema de solo lectura

javier@javier-desktop:~$ sudo chmod 777 /media/disk /*
chmod: cambiando los permisos de `/media/disk': Sistema de solo lectura

javier@javier-desktop:~$ sudo chmod a+w /media/disk
chmod: cambiando los permisos de `/media/disk': Sistema de solo lectura

javier@javier-desktop:~$ sudo chmod a+w /media/disk /*
chmod: cambiando los permisos de `/media/disk': Sistema de solo lectura
javier@javier-desktop:~$ 

hace como que cambia pero no puedo escribir en la memo solo veo lo que hay

---

### Post by Mauro22 on 2008-06-28
verificaste a que grupo pertenece la microSD. 

Una vez, ubuntu me la cambio al grupo root

Abri la consola y logeate como root

```
sudo su
```

y despues un 

```
ls -l
```

y fijate si el grupo es el tuyo y no root.

---

### Post by javier-2714 on 2008-06-28
hice sudo su   después ls -l y me tira todas las carpetas que tengo en mi carpeta home cundo la pongo se monta automáticamente en el escritorio hice click izquierdo propiedades permisos es soy propietario pero pertenese al grupo root les dejo un pantallazo  si pongo mi pendriver figura igual grupo root pero ahi si me permite escribir.

---

### Post by Mauro22 on 2008-06-28
Probaste haciendo un:

sudo chown -R usuario:grupo /media/disk


??

Fiajte que es el nombre de usuario, luego dos punto ( : ) y luego el grupo.

---

### Post by javier-2714 on 2008-06-28
Hice: 

 sudo chown -R javier:javier /media/disk 

dice cambiando pero

no pasa nada no lo cambia no entiendo que pasa??????

---

### Post by Mauro22 on 2008-06-28
Usas gnome no?


Probaste iniciando nautilus como root?? y ver si de ahi te deja copiar y eso...


Alt + F2 y pones gksudo nautilus


De ultima vas a tener q formatear la sd desde linux usando fat.

---

### Post by javier-2714 on 2008-06-28
si fue lo primero que probé me dice que no puede porque es de solo lectura 
también probé de formatearlo y me dice lo mismo ya no se que mas hacer!!!!

---

### Post by Mauro22 on 2008-06-28
Vamos a pensar mas lejos... Probaste otro sistema opertivo ademas de ubuntu? otro lector de tarjetas? otra tarjeta?

:confused:

---

### Post by javier-2714 on 2008-06-29
Si compre una targeta nueva y me hace lo mismo también desde winxp hace tiempo que me dice lo mismo que no tengo permiso de escritura pero desde ubuntu no tenia problema hasta ahora también estuve mirando en propiedades volumen opción de montaje empieza con "ro" a diferencia que si conecto mi pendrive comienza con "rw" es lo único que encuentro de diferente no se porque se cambio esta opción y si la cambio y pongo rw me tira error no puede montar el dispositivo.

---

### Post by fgl82 on 2008-06-29
Quiza sea una pregunta tonta, pero no tendrá la memoria en cuestión un switch de protección contra escritura que esté en "on", bloqueando justamente la posibilidad de escribir en la misma?

Es lo que se me ocurre dado que te lo hace en linux y en windows tb...

---

### Post by javier-2714 on 2008-06-29
ojala fuera eso tiene esa proteccion pero ya le di para los dos lados y aparte compre otra memoria nueva y tambien hace lo mismo tendra algun problema el lector de memorias.

---

### Post by fgl82 on 2008-06-30
Probaste cambiarlo de puerto usb? yo tengo un puerto usb en el cual el lector me lee las MMC pero no las SD. Cambié de puerto y anduvo la SD...

---

### Post by javier-2714 on 2008-06-30
Cambie de puerto pero tampoco me deja me prestaron una cámara digital con memoria sd si pongo la memoria de la cámara en el lector de memorias igual no permite escribir pero si conecto la cámara con la memo si me permite escribir ahora si pongo mis memos en la cámara y la conecto no me deja escribir tampoco la verdad que no entiendo que es lo que pasa.

---

### Post by fgl82 on 2008-06-30
jajajajaja!!! es mortal tu problema :P

A ver si entiendo:

1) TU lector NO TE DEJA ESCRIBIR en TUS MEMOS
2) TU lector NO TE DEJA ESCRIBIR en LA MEMO DE LA CAM
3) la cam NO TE DEJA ESCRIBIR en TUS MEMOS
4) la cam ESCRIBE lo mas bien en SU MEMO

Conclusiones aparentes: 

1) tu lector no anda, por lo menos la parte de SD, probá con otro, tanto tus memorias como las de la cam (no con una cam, otro LECTOR, quizá sea lo mismo pero mejor descartar posibles "diferencias de funcionamiento por diferente dispositivo")
2) quizá tus memorias TAMBIÉN esten jodidas, probá OTRO LECTOR con OTRAS MEMORIAS

después dejá dicho como fué todo, estoy re intrigado con tu problema!!!

---

### Post by javier-2714 on 2008-06-30
Interpretaste perfecto cuando sepa que es lo que pasa te comento pero lo que creo es que el lector de memorias funciona mal y la memo nueva que compre no funciona algo mas puede pasar después te comento bien cual era el temas gracias por sus consejos.

---

### Post by javier-2714 on 2008-07-02
Bueno ya esta el tema es asi el lector de memorias hera el que no me permitía escribir en las memos y la memo nueva que compre también tinia problemas por suerte entro todo en garantía y me lo cambiaron ahora puedo escribir en las memos con el lector gracias por su tiempo saludos.

---

