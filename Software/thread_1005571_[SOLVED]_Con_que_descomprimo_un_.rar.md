---
title: "[SOLVED] Con que descomprimo un .rar?"
date: 2008-12-08
forum: Software
---

### Post by DrKenobi on 2008-12-08
Hola: la cosa es simple, Tengo que descomprimir un archivo con extension ".rar" y hasta el momento no lo he logrado. Ya instale con el "Add/Remove..." dos programas que decian poder descomprimir estos archivos y naaada...

Alguno que ustedes usen que SI pueda manejar estos archivos?

Gracias

---

### Post by ABCC on 2008-12-08
Just type:
```
sudo aptitude install rar unrar
```

in a terminal or look them up with Synaptic.

ABCC

---

### Post by c4d0rn4 on 2008-12-08
yo uso el que trae por defecto ubuntu con nautilus. File-roller. Lo único que instalé para darle soporte a ese formato es rar. (si, se mataron en el nombre)

```
sudo apt-get install rar
```

Creo que hay una diferencia sutil en entre unrar y rar; parte de ella creo tiene que ver con licencias y el soporte para crear archivos.

---

### Post by santiagoward2000 on 2008-12-08
> **c4d0rn4 said:**
> Creo que hay una diferencia sutil en entre unrar y rar; parte de ella creo tiene que ver con licencias y el soporte para crear archivos.

En realidad, la diferencia es que **rar** comprime y **unrar** descomprime. Pero los 2 tienen licencias privativas. La alternativa libre para descomprimir es **unrar-free**.
Una vez instalado alguno de los 2 (**unrar** o **unrar-free**) podés descomprimirlo con file-roller como los otros formatos.
Saludos!

---

### Post by rodolfojavier1982 on 2008-12-08
Yo utilizo el winrar con wine (lo instale para poder usar el winrar), pero me parece que tiene un periodo de 40 dias de prueba o algo asi. Voy a ir buscando otras alternativas como las que listaron arriba... :mad:

---

### Post by sambita on 2008-12-08
> **ABCC said:**
> Just type:
```
sudo aptitude install rar unrar
```



Hace eso y vas a poder desomprimir, si te funciona por favor marca el thread como solved

---

### Post by DrKenobi on 2008-12-08
Primero probe con el "unrar-free" pero no anduvo (este tiene una limitacion)
Despues probe con el "unrar" y anduvo perfecto
El "rar" no lo instale porque dice que es shareware y dura 40 dias. Me coformo compimiendo en ".zip".

Gracias!!!

---

### Post by sambita on 2008-12-08
> **DrKenobi said:**
> El "rar" no lo instale porque dice que es shareware y dura 40 dias. Me coformo compimiendo en ".zip".


Me acabo de enterar, no lo tenía instalado, siempre uso zips o .7z, que tiene un buen nivel de compresión.

---

### Post by euzkoarima on 2008-12-09
+1 al 7z

---

### Post by pol666 on 2008-12-09
Yo estoy usando fileroller de gnome en kde por que el ark apesta.
Pero tampoco me gusta mucho, una pena.

---

### Post by faktorqm on 2008-12-10
> **euzkoarima said:**
> +1 al 7z

+1

---

### Post by jorgito on 2010-01-12
Hola a todos, 

También necesité desempaquetar archivos .rar, pero algo no va:


```
jorge@jorge-desktop:~$ sudo aptitude install rar unrar
[sudo] password for jorge: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
No se encontró ninguna versión candidata para rar
No se encontró ninguna versión candidata para unrar
No se encontró ninguna versión candidata para rar
No se encontró ninguna versión candidata para unrar
Se ELIMINARÁN los siguientes paquetes:
  arj{u} librpm0{u} librpmbuild0{u} librpmio0{u} linux-headers-2.6.31-14{u} 
  linux-headers-2.6.31-14-generic{u} rpm{u} 
0 paquetes actualizados, 0 nuevos instalados, 7 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 86,7MB.
¿Quiere continuar? [Y/n/?] n
Cancela.
jorge@jorge-desktop:~$ 

```

Estoy usando Karmic, y no se si la solución dada funciona para esta versión.

En todo caso... como es el tema de liberar 86 megas despues de no instalar nada?

Saludos

---

### Post by guillermolisi on 2010-01-12
> **jorgito said:**
> Hola a todos, 

También necesité desempaquetar archivos .rar, pero algo no va:


```
jorge@jorge-desktop:~$ sudo aptitude install rar unrar
[sudo] password for jorge: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
No se encontró ninguna versión candidata para rar
No se encontró ninguna versión candidata para unrar
No se encontró ninguna versión candidata para rar
No se encontró ninguna versión candidata para unrar
Se ELIMINARÁN los siguientes paquetes:
  arj{u} librpm0{u} librpmbuild0{u} librpmio0{u} linux-headers-2.6.31-14{u} 
  linux-headers-2.6.31-14-generic{u} rpm{u} 
0 paquetes actualizados, 0 nuevos instalados, 7 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 86,7MB.
¿Quiere continuar? [Y/n/?] n
Cancela.
jorge@jorge-desktop:~$ 

```Estoy usando Karmic, y no se si la solución dada funciona para esta versión.

En todo caso... como es el tema de liberar 86 megas despues de no instalar nada?

Saludos
Para que encuentre los paquetes que solicitas tenes que tener activo el repositorio Multiverse, cosa que pareceria no estar asi ya que busque con Synaptic y esos paquetes (y muchos otros mas) aparecieron enseguida.

---

