---
title: "Ayuditas para un shell script"
date: 2009-12-17
forum: Software
---

### Post by cladelpino on 2009-12-17
Gente, como están ? Ando necesitando un poco de ayuda. El tema es que estoy escribiendo un shell script para disparar el paso de música desde la consola, por ejemplo, poner a reproducirse un cd entero usando el script. El tema es que no me manejo tanto como pienso se manejan uds con las expresiones como sed, grep, find, dir, etc.
El programa que utilizaría para reproducir sería el rhythmbox, porque me gusta y nunca me trajo problemas, además de proporcionar una interface amigable para la gente no acostumbrada al entorno ubuntu que pueda pasar por mi pc. 

Para pasarle los temas al rhythmbox (via rhythmbox-client --enqueue) necesito que esten separados los filenames solamente por espacios. 

Ej: rhythmbox-client --enqueue 01-blabla 02-blaba 03-blabal

Entonces lo que yo necesito y aún no pude lograr es que, estando ubicado dentro de un directorio, donde tengo los archivos de musica que componen el cd, se los pueda pasar al cliente de esa forma que los entienda. Que comandos o pedazos pequeños de código se les ocurren ? Estoy seguro que para aquellos más acostumbrados a trabajar en un entorno de consola es una terrible huevada lo que estoy preguntando, pero yo no pude encontrar todavía la solución. 

Les agradezco enormemente y luego les comentaré más de que se trata el script (si es que lo logro concretar jeje)

Saludos! 
claudio

---

### Post by euzkoarima on 2009-12-18
A ver, si quiero listar separados por un espacio todos los archivos (no directorios) dentro de un determinado directorio, puedo hacerlo así (suponiendo que estoy parado en el directorio que quiero)

```
find -P . -maxdepth 1 -type f -printf %f\ 
```

Explicación:

-P : para no seguir enlances
.  : directorio actual
-maxdepth 1 : que no siga buscando en directorios que estén adentro del directorio en el que busco
-type f : solo archivos
-printf %f\ : imprimir el nombre del archivo (%f) seguido de un espacio en blanco (\ )

Ojo, notar que luego de la barra invertida va un espacio en blanco.

Cambiando . por el directorio en cuestión y cargando una variable con el resultado de esto deberías poder armar tu comando.

Si tiene el problema de un útimo espacio en blanco, pero si es lo último del comando no va a traer problemas.

Saludos,
Eduardo

---

### Post by smo0th on 2009-12-18
Talvez algo asi ayude..


```

#!/bin/bash

IFS=""
LIST=`ls -m *.mp3 | sed 's/[ \t]\+/\n/g' | sed 's/[ \t]\+/\n/g'`
IFS=","
LIST=($LIST)
for (( i=0; i<${#LIST[@]}; i++)); do
	rhythmbox-client --enqueue ${LIST[$i]}
done
```

solo hay ke depurar un poco el output de ${#LIST[@]} pero se me acabo el tiempo y tengo ke irme... suerte!!

---

### Post by cladelpino on 2009-12-21
Como están ? Bueno al final me di cuenta de que dandole al comando todos los temas directamente no funcionaba, o algo estaba haciendo mal yo, así que opte por hacer un lazo y todo resultó mas simple. Gracias igual euzokarima y smo0th. Por ahora el script quedo así (supuestamente estando dentro del directorio de interés):

```
ARCHIVOS="*.mp3"
for a in $ARCHIVOS 
do
echo "$a"
rhythmbox-client --enqueue "$a"
done
```

Esto funciona. Ahora el tema es llegar al bendito directorio. Las dudas que tengo para esta cuestión son dos: 

1) puede estar un parámetro del script compuesto por más de una palabra ? por ejemplo se puede encerrar una frase o título entre comillas y que sea tomado como un solo valor ? 

de esta forma pensaba resolver el problema de llegar al directorio del CD en cuestión (Asumiendo que el script esta en el directorio Music y que la estructura es /Artista/CD)
con algo tipo: 

```
ls -R | grep -xi $1 | grep -viw .*:
```

(el ultimo grep esta para eliminar las entradas de ls -R que listan los contenidos de dicha carpeta).

Aquí viene mi segunda duda que es 
2) ¿Como catzo hago, para que pueda cambiar al directorio cuya ruta es la que obtuve con el comando ese? probe pipeandolo a un cd o definiendo una variable pero la verdad no puedo. 

Espero que alguno pueda ayudarme aunque sea un poquito. Muchas gracias y saludos.

Claudio

---

### Post by smo0th on 2009-12-21
Hola,

Para llegar al directorio haz simplemente un cd <path>

No entendi la segunda pregunta =/

---

### Post by cladelpino on 2009-12-21
esta bien, pero como cambio al directorio si ese nombre es una variable introducida por el usuario ? o si ese directorio, es un subdirectorio de uno de los que esta en el actual (y a priori no se sabe de cual) ? 
con:

ls -R | grep -xi $1 | grep -iw .*:
ese comando me devuelve la ruta del directorio al que quiero ir. La pregunta es, ¿Cómo hago para efectivamente ir a ese directorio? 

Saludos y espero haber sido claro
Claudio

---

### Post by smo0th on 2009-12-21
Ok, si ese comando te devuelve el directorio al que quieres llegar entonces usa

```
cd `ls -R | grep -xi $1 | grep -iw .*`
```

para ir a ese directorio.

salu2!

---

### Post by euzkoarima on 2009-12-21
> **cladelpino said:**
> 
1) puede estar un parámetro del script compuesto por más de una palabra ? por ejemplo se puede encerrar una frase o título entre comillas y que sea tomado como un solo valor ? 


En si ya te contestó smo0th, pero creo que esto quedó colgado, y si, lo que encerras entre comillas se toma como un único parámetro.

Saludos,
Eduardo

---

### Post by smo0th on 2009-12-22
pero ten cuidado y fijate ke son tildes inversas (`) y no comillas simples (')

salu2 

O:)

---

