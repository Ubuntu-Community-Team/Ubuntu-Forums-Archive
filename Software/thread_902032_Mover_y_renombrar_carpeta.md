---
title: "Mover y renombrar carpeta"
date: 2008-08-26
forum: Software
---

### Post by niko_3100 on 2008-08-26
Muchachos a ver si estoy mal, para mover una carpeta con su contenido adentro no es mv -f origen destino ?? o mv -r ?? y ahora si la quiero renombrar no es mv nombreOrigen nombreDestino ?? estoy equivocado? porque quise hacer eso y para renombrar me copiaba el contenido original de la carpeta y creaba una carpeta con el nombreDestino dentro de la carpeta nombreOrigen, no puede ser que no pueda mover o renombrar carpetas... como odio trabajar con xp, me re olvido de los comandos... Fuc..king xp!!!

---

### Post by pablo atheist on 2008-08-27
que raro! yo hice mv nombreOrigen nombreDestino y me movió la carpeta con todo su contenido y renombrándola o sea por ejemplo
```
$ mv /home/pablo/hola1 /home/pablo/Escritorio/hola2
```

otra cosa creo que no existe la opción -r para el mv por lo menos en el man no esta

saludo

---

### Post by niko_3100 on 2008-08-27
si, en el man no esta, pero si quiero mover la carpeta con todo su contenido no me deja, me tira: no se puede mover, la carpeta no esta vacia o algo asi.... no entiendo..

---

### Post by faktorqm on 2008-08-27
La opción -r o -R no existen para el comando mv. No sé que estas intentando hacer, pero te propongo casos para ver si te ayudo.
Para cambiar el nombre de una carpeta, el comando es

```
mv nombre_actual nombre_que_queres
```

ahora, para mover la carpeta a otro directorio, lo haces igual que antes **(VERIFICAR QUE TENES PERMISOS DE LECTURA / ESCRITURA)**

```
mv nombre_actual /home/faktorqm/nombre_que_queres
```

Lo de los permisos es importante, si no tenes permisos suficientes, cuando intenta borrar la carpeta no puede por que tiene archivos adentro, y (creo) que no hace rm -R, sino rm por que se supone que pudo mover todos los archivos correctamente, cuando por algun motivo no puede, o no tiene permisos de lectura en el origen, o no tiene permisos de escritura en el destino, o el disco esta lleno (o mil errores mas pueden pasar) devuelve estado de error.
Si no sabes que permisos poner, siempre podes hacer sudo mv blabla...
Salu2!!

---

### Post by niko_3100 on 2008-08-27
con el tema de permisos estoy bien porque es una carpeta creada por mi usuario que la quiero mover del escritorio a mi /home, y lo otro lo que queria hacer es renombrar la Carpeta Escritorio por Desktop como era antes, para acceder al escritorio hacias cd Desktop y no cd Escritorio, por comodidad mas que nada.

---

### Post by niko_3100 on 2008-08-28
Cual seria el comando para mover una carpeta con todo lo que tiene adentro? Me podrian decir? muchas gracias.

---

### Post by faktorqm on 2008-08-28
es el comando que te puse arriba men! cual es tu problema?!? de ultima abri una consola, escribi sudo nautilus y te abre el explorador como root y hace todo lo que quieras con eso con todos los permisos y listo.

---

