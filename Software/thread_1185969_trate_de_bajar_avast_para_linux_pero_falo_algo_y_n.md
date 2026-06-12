---
title: "trate de bajar avast para linux pero falo algo y no lo puedo borrar"
date: 2009-06-12
forum: Software
---

### Post by zhelo on 2009-06-12
baje desde la pagina de avast la version .deb y no se intslao, luego me paso too esto

Imagen1: [http://i42.tinypic.com/1417a77.jpg](http://i42.tinypic.com/1417a77.jpg)



Imagen2: [http://i41.tinypic.com/21aljsm.png](http://i41.tinypic.com/21aljsm.png)


Imagen3: [http://i40.tinypic.com/2a7u5hd.jpg](http://i40.tinypic.com/2a7u5hd.jpg)

no puedo borrarlo :(

---

### Post by CdK1 on 2009-06-12
sudo dpkg -l  nombredelpakete

para saber tus packages instalados dpkg -l

por favor envia tu sources.list y versión de Ubuntu

---

### Post by pagondel on 2009-06-12
> **CdK1 said:**
> sudo dpkg -l  nombredelpakete

para saber tus packages instalados dpkg -l

por favor envia tu sources.list y versión de Ubuntu

Para desinstalar un Paquete:
```
sudo dpkg -r nombredelpakete
```

La verdad no se para que necesitarias de Avast en Ubuntu... Siempre que sepas lo q estas haciendo tu sistema estara en perfectas condiciones ;)

---

### Post by Carlos C on 2009-06-12
Me sumo a los consejos y también recomiendo:
```
sudo dpkg -C
```
o
```
sudo dpkg --audit
```
Ambas opciones buscan paquetes que han sido instalados parcialmente y te sugieren que hacer con ellos para hacerlos funcionar.

---

### Post by moreback on 2009-06-12
NO entiendo por qué está haciendo una actualización de la distribución siendo que ya lo tiene instalado

????

---

### Post by zhelo on 2009-06-14
> **CdK1 said:**
> sudo dpkg -l  nombredelpakete

para saber tus packages instalados dpkg -l

por favor envia tu sources.list y versión de Ubuntu

me salio esto:

```
zhelo@querencia:~$ sudo dpkg -1 avast4workstation
[sudo] password for zhelo: 
dpkg: opción -1 desconocida

Escriba dpkg --help para ayuda sobre instalar y desinstalar paquetes 
[*];
Use `dselect' o `aptitude' para una gestión más amigable de los paquetes;
Escriba dpkg -Dhelp para una lista de los valores de depuración de dpkg;
Escriba dpkg --force-help para una lista de opciones para forzar cosas;
Escriba dpkg-deb --help para obtener ayuda sobre manipulación de archivos .deb;
Escriba dpkg --license para ver la licencia (GPL de GNU), el copyright y la
ausencia de garantía 
[*].

Las opciones marcadas con 
[*] producen una salida extensa,
¡fíltrela con `less' o con `more'!

```

---

### Post by zhelo on 2009-06-14
que puedo hacer?

---

### Post by zhelo on 2009-06-14
de este tema 
[http://ubuntuforums.org/showthread.php?t=1185969](http://ubuntuforums.org/showthread.php?t=1185969)

estuve viendo y creo que podria borrar el paquete o la instalacion mala como super usuario, el problema es que no se en que lugar se alla
como puedo saber la ruta del error?

---

### Post by pagondel on 2009-06-14
Cambiar es uno (1) por una l (L, ele) como deberia ser ;)
Saludos!

---

### Post by zhelo on 2009-06-14
> **pagondel said:**
> Cambiar es uno (1) por una l (L, ele) como deberia ser ;)
Saludos!

me salio esto compañero

```
zhelo@querencia:~$ sudo dpkg -l avast4workstation
Desired=Unknown/Install/Remove/Purge/Hold
| Estado=No/Instalado/Config-files/Desempaquetado/Fallo-config/Medio-inst/espera-disparo/pendiente-disparo
|/ Err?=(ninguno)/Retenido/Requiere-reinst/X=ambos problemas (Estado,Err: mayúsc.=malo)
||/ Nombre         Versión       Descripción
+++-==============-==============-============================================
rFR avast4workstat 1.3.0          avast! antivirus for Linux
zhelo@querencia:~$ 

```

que hago??

---

### Post by pagondel on 2009-06-14
yo haria un:
```
 sudo dpkg -r avasr4workstation
```

Saludos! 8)
PD:eso elimina el paquete :P

---

### Post by Carlos C on 2009-06-14
> **zhelo said:**
> de este tema 
[http://ubuntuforums.org/showthread.php?t=1185969](http://ubuntuforums.org/showthread.php?t=1185969)

estuve viendo y creo que podria borrar el paquete o la instalacion mala como super usuario, el problema es que no se en que lugar se alla
como puedo saber la ruta del error?

zhelo, quiero que pongas atención a dos cosas que me parecen importantes:

1. Uní este thread con el anterior. Si vas a seguir tratando el mismo problema por favor no abras un hilo nuevo sino que continua con el que ya abriste.

2. Pon más atención con la manera en que escribes, así como con el lenguaje que usas, si cometes errores al tipear debes corregirlos. La idea es que la información sea fácilmente encontrada mediante un buscador y comprensible incluso para personas cuyo idioma nativo no es el español.

Te pido que mires acá antes de volver a publicar un post:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

---

### Post by zhelo on 2009-06-14
> **pagondel said:**
> yo haria un:
```
 sudo dpkg -r avasr4workstation
```Saludos! 8)
PD:eso elimina el paquete :P
[COLOR=Red]no hay ningun pauqte instalado

[/COLOR]> zhelo, quiero que pongas atención a dos cosas que me parecen importantes:

1. Uní este thread con el anterior. Si vas a seguir tratando el mismo problema por favor no abras un hilo nuevo sino que continua con el que ya abriste.

2. Pon más atención con la manera en que escribes, así como con el lenguaje que usas, si cometes errores al tipear debes corregirlos. La idea es que la información sea fácilmente encontrada mediante un buscador y comprensible incluso para personas cuyo idioma nativo no es el español.

Te pido que mires acá antes de volver a publicar un post:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

[COLOR=Red]disculpa compañero[/COLOR]

---

