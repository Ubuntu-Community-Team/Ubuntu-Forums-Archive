---
title: "Copiar Archivos Listados en un Texto"
date: 2011-12-04
forum: Software
---

### Post by GGV on 2011-12-04
Buenas tardes!!, Soy bastante nuevo en esto, asi que espero me tengan paciencia!.
El asunto que me trae hasta aca, es que estoy tratando de hacer un script para transferencia automatizada de archivos via FTP.
Aunque parezca mentira, se me complica a la hora de "seleccionar" los archivos que quiero transferir.
Intente con ls > lista.txt, y consigo una lista de los archivos a mover, pero no he podido hacer que el comando cp me levante la lista. Hay alguna manera?
Me imaginaba que quizas con  cp < lista.txt /dir origen  /dir destino  iba a funcionar, pero no hay caso. Solo recibo el mensaje cp: se omite el directorio «/dir origen/».
Intente de todo, y no hay caso.
Cualquier ayuda/consejo/sugerencia sera bienvenida!
Muchas gracias!!

PD:Estoy trabajando con Ubuntu Server 11.04

---

### Post by euzkoarima on 2011-12-04
No estoy seguro de como querés armalo, pero te fijate esto a ver si te ayuda
Armé dos directorios A y B puse varios archivos en A y bajé sus nombres a otro archivo con el siguiente comando (desde la terminal, parado en el directorio A)

```
ls -1 > archivos.lst
```

De ahí borre algunos y ahora quiero copiar solo los que están en ese listado desde A hasta B
Para eso armo un script (y lo llamo copia.sh)

```
#!/bin/bash
cat $1 |
while read file
do
	echo "copiando "$file
	cp "$file" ../B/
done
```

Le agrego permiso de ejecución al script y finalmente (parado en A) ejecuto

```
./copia.sh archivos.lst
```

Con eso logro copiar los archivos como CREO que tratás de hacer.

Ahora bien, podemos hacer que sea un poquito más general podemos cambiar el "../B/" por un segúndo parámetro, y el script quedaría

```
#!/bin/bash
cat $1 |
while read file
do
	echo "copiando "$file
	cp "$file" $2
done

```

Tiene la ventaja que puedo estar parado en cualquier lado, y si las lista de archivos contiene el pahtname completo al archivo que querés copiar, podés copiar archivos de cualquier lado (en distintos directorios).

Te doy ejemplo de corrida capturado de mi terminal

```
euzkoarima@voyager:~/Escritorio$ '/home/euzkoarima/Escritorio/A/copia.sh' '/home/euzkoarima/Escritorio/archivos2.lst' '/home/euzkoarima/Escritorio/B' 
copiando /home/euzkoarima/Escritorio/A/a Capacitar-Mejorar.odt
copiando /home/euzkoarima/Escritorio/A/TODO.txt
copiando /home/euzkoarima/Escritorio/A/twitter.txt

```

Comentario final, en lugar de tipear todo un pathname, por ejemplo el del segundo parámetro con el directorio B, simplemente arrastro la carpeta B sobre la terminal y me copia el path completo.

Saludos,
Eduardo

---

### Post by GGV on 2011-12-04
Eduardo, un millon de gracias !!!!. Funciono perfecto... No lo implemente tal-cual, pero lo adapte a lo que necesito, y funcione de mil maravillas.
Basicamente, lo que hago es copiar los archivos listados del FTP, moverlos a un directorio de trabajo, y luego borrarlos del FTP (Solo los archivos que ya copie).
Asi que con el script que me pasaste, mas algunas modificaciones, quedo de 10!.
Ahora, sin embargo, tengo otro problema con el que llevo ya un par de horas y me esta comiendo la cabeza...
Alguno archivos del FTP tiene un ;1 luego de la extension de archivo. Tipo, imagen1.jpg;1 o conf.ini;1 o incluso imagenx.jpg;3.
Estoy tratando de renombrar los archivos, quitando SOLO el ;X de la extension, y no doy en el clavo.
Trate con 'rename -v 's/\.*;#/\.*/' *.*' y sin cardinal, con ?, etc, etc... creo que el problema arranca con el ; propiemente dicho. Me toma los ; como referencias a subdirectorios (que no hay) y asi estoy.
Alguna idea? Conoces algun otro comando? Con la instruccion mv me fue peor.
De nuevo, un millon de gracias!!

---

### Post by euzkoarima on 2011-12-04
Que bueno que te haya servido !!

Con respecto al rename proba

```
rename -v 's/;\d$//' *
```

Esto funcionaría si lo que tenés al final del nombre es ; y 1 solo dígito
Si son 1 o más dígitos (p. ej. algo;23) usa

```
rename -v 's/;\d+$//' *
```

Ojo, que si tenés p. ej. archivo;1 y archivo;2 el primero te lo cambia a archivo y el segundo te da error y lo deja igual

Saludos,
Eduardo

---

