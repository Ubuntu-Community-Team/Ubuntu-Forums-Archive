---
title: "HowTo levantar server Urban Terror"
date: 2009-07-24
forum: Software
---

### Post by vladzur on 2009-07-24
Aquí les dejo unas indicaciones de cómo levantar un server dedicado de Urban Terror

Primero deben descargar el UT

```
wget ftp://ftp.snt.utwente.nl/pub/games/urbanterror/UrbanTerror_41_FULL.zip
```

luego, hay que descomprimir


```
unzip UrbanTerror_41_FULL.zip
```

por defecto se descomprime en /UrbanTerror

deben darle permisos de ejecución a ioUrTded.i386

```
chmod +x ioUrTded.i386
```

para configurar el server, deben editar el archivo server.cfg, que esta en /q3ut4

```
gedit server.cfg
```

y pueden ejecutar el servidor desde el directorio de Urban Terror

```
ioUrTded.i386 +set fs_game q3ut4 +set dedicated 2 +set net_port 27960 +set com_hunkmegs 128 +exec server.cfg

```

Para que sea un poco más elegante, pueden crear un script como éste

```

#!/bin/bash

while true
do
/home/usuario/urbanterror/ioUrTded.i386 +set fs_game q3ut4 +set dedicated 2 +set net_port 27960 +set com_hunkmegs 128 +exec server.cfg
echo "server caido en `date`" > ultimo_crash.txt
done

```

para que lo puedan ver desde la Internet, deben abrir el puerto del router, en este caso el 27960 UDP y TCP

eso sería.

Ah, claro, como no soy tan genio, estas instrucciones y más detalles en [http://www.urbanterror.net/new_urt_manual/]("http://www.urbanterror.net/new_urt_manual/")

---

### Post by nopersona on 2009-07-24
Buena la explicación, clarita. Ahora, me asalta una duda, es posible cambiar la configuración a un CTF u otros? gusto de los consumidores.

---

### Post by moreback on 2009-07-25
Mmmhh... es un servidor con consola vía stdin/stdout... en una de esas revivo [mi antiguo proyecto]("http://sags.sourceforge.net").

---

### Post by vladzur on 2009-07-25
> **nopersona said:**
> Buena la explicación, clarita. Ahora, me asalta una duda, es posible cambiar la configuración a un CTF u otros? gusto de los consumidores.

Claro, en el server.cfg hay una opcion "set g_gametype"

```
set g_gametype "4" // 0=FreeForAll, 3=TeamDeathMatch, 4=Team Survivor, 5=Follow the Leader, 6=Capture and Hold, 7=Capture The Flag, 8=Bombmode
```

---

