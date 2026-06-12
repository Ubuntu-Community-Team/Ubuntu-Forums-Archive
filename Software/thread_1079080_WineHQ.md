---
title: "WineHQ"
date: 2009-02-24
forum: Software
---

### Post by sirkurt on 2009-02-24
Bueno esto es mas que nada para tener algo de informacion.
Viendo la pagina de [WineHQ]("www.winehq.org") entre en la data base de aplicaciones soportadas y vi muchos juegos soportados a la perfeccion, y juegos que no son precisamente el buscaminas de windows, sino juegos como el world of warcraft y otros bastante nuevos.

Alguien tiene algo de informacion sobre ese programa? 
Que es especificamente, es una version de wine para juegos o es una actualizacion para wine?

como instalarlo en ubuntu?
yo segui los pasos indicados [ACA]("http://www.winehq.org/download/deb") pero no encontre nada nuevo entre los programas.

Bueno si alguien tiene algo de info sobre esto me vendria bien leerla en español porque enteindo ingles pero no al 100% y entre las cosas que quiero ejecutar ubuntu, aunque no como algo primordial, tambien se encuentran los juegos de windows asi que les agradeceria la info.

Saludos y gracias

---

### Post by Air23 on 2009-02-24
Hola, te cuento que la pagina winehq.com es la pagina oficial de Wine. No se trata de ninguna version especial ni nada diferente. Mas informacion [_aca_](http://es.wikipedia.org/wiki/Wine) y  [_aca_](http://www.guia-ubuntu.org/index.php?title=Wine).

En cuanto a la instalacion, ¿no te aparecio una entrada de nombre "wine" en el menu aplicaciones?

Si no aparecio, lo podes instalar de 2 maneras:

1 - Abrir una terminal y escribir
```
sudo apt-get install wine
```
2 - Instalarlo mediante synaptic (Sistema > Administracion > Gestor de paquetes Synaptic)

---

### Post by sirkurt on 2009-02-24
acabas de resolver mis dudas, yo pense que wine hq era una utilidad para correr aplicaciones que necesiten aceleracion grafica.
Si lo tengo instalado y me aparece en el menu de aplicaciones.
El unico problema es que no pude usar un reproductor de video que me gusta bastante y que por ahora solamente esta disponible para windows,el Gom Player.
Pero bueno eso vere como lo resuelvo mas tarde.
Gracias

---

### Post by sajnox on 2009-02-24
Repdroductor de video ??

```
sudo apt-get install vlc
```

---

### Post by sebasthian777 on 2009-02-24
1) vlc... una grosura... mismo en windows lo uso...

2) wine? otra grosura... no solo por los juegos... en si es algo muy util y a lo cual se nota que le estan invirtiendo unas cuantas horas. es increible ver que tan compatible se volvie en los ultimos tiempos.

---

### Post by sirkurt on 2009-02-24
si al vlc ya lo tengo pero no lo uso Xd uso el MPlayer porque ahi me funcan bien todos los tipos de videos.

---

### Post by luks911 on 2009-02-24
> **sirkurt said:**
> si al vlc ya lo tengo pero no lo uso Xd uso el MPlayer porque ahi me funcan bien todos los tipos de videos.

Si usás MPlayer, entonces me permito recomendarte SMPlayer. Está en los repositorios y es una interfaz para el MPlayer que incluye gran cantidad de opciones y mejoras. Y a mí me gusta mucho, qué joder.

Saludos

---

### Post by sebasthian777 on 2009-02-25
mmm yo me prendo tmb y lo voy a testear hoy cuando vuelvo a casa a ver que tan bueno esta...

off topic: Lo primero que me enamoro del pingüinito este fueron los repositorios ^^ :P

---

### Post by GGsalas on 2009-02-27
> **Air23 said:**
> 

En cuanto a la instalacion, ¿no te aparecio una entrada de nombre "wine" en el menu aplicaciones?

Si no aparecio, lo podes instalar de 2 maneras:

1 - Abrir una terminal y escribir
```
sudo apt-get install wine
```
2 - Instalarlo mediante synaptic (Sistema > Administracion > Gestor de paquetes Synaptic)

En la [web de wine]("http://www.winehq.org/download/deb") dice que hay que instalar una clave al sistema APT
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
y luego añadir un repositorio:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

¿Que diferencia hay con la instalación que propones vos, además que tu modo de instalar es más simple

Saludos.

---

### Post by Air23 on 2009-02-27
> **GGsalas said:**
> En la [web de wine]("http://www.winehq.org/download/deb") dice que hay que instalar una clave al sistema APT
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
y luego añadir un repositorio:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

¿Que diferencia hay con la instalación que propones vos, además que tu modo de instalar es más simple

Saludos.
La diferencia esta en la version de wine que instalas. En los repositorios de intrepid esta la version 1.0.1 de wine, mientras que en los repos de wine van por la 1.1.15.
Mas alla de eso la instalación es igual independientemente del repositorio usado (ya sea via synaptic o sudo apt-get install)

---

### Post by GGsalas on 2009-03-02
> **Air23 said:**
> La diferencia esta en la version de wine que instalas. En los repositorios de intrepid esta la version 1.0.1 de wine, mientras que en los repos de wine van por la 1.1.15.
Mas alla de eso la instalación es igual independientemente del repositorio usado (ya sea via synaptic o sudo apt-get install)

¿Se supone que la versión de los repositorios de intrepid es más estable o nada que ver?

---

### Post by Air23 on 2009-03-02
> **GGsalas said:**
> ¿Se supone que la versión de los repositorios de intrepid es más estable o nada que ver?

Segun [http://www.winehq.org/](http://www.winehq.org/) (arriba a la derecha) la version que viene en intrepid (1.0.1) es la estable.

---

