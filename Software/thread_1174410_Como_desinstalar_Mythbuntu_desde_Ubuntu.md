---
title: "Como desinstalar Mythbuntu desde Ubuntu?"
date: 2009-05-30
forum: Software
---

### Post by flakojaime on 2009-05-30
HOla.

Tuve la brillante idea de instalar Mythbuntu y no me inicia, se queda con la pantalla negra.

Como no inicia, no se como lo puedo desinstalar.

Como se puede hacer desde ubuntu? algun comando desde la consola?

Gracias

---

### Post by Carlos C on 2009-05-30
Mythbuntu es una distribución linux, no es un programa. Si lo que deseas es cambiar de distribución, es decir instalar ubuntu, puedes usar el LiveCD de Ubuntu y volverlo a instalar. Si tienes un sistema de particionado manual puedes no formatear tu home para no perder los datos, sino, es probable que tengas que formatear todo. Al menos es lo que se me ocurre en este minuto.

Saludos.

---

### Post by abn91c on 2009-05-30
trata du usar ```
sudo apt-get remove mythbuntu-desktop
```

---

### Post by flakojaime on 2009-05-30
Hola.

Tengo instalado Ubuntu (fue lo primero que instalé) y despues instalé mythbuntu.

El problema es que nunca me funcionó el mythbuntu, se queda la pantalla negra y no funciona.

Intente con el 

sudo apt-get remove mythbuntu-desktop

pero no funciona. (esta instalado con un particionado a parte).

saludos...

---

### Post by radixs on 2009-05-31
> **flakojaime said:**
> Hola.

Tengo instalado Ubuntu (fue lo primero que instalé) y despues instalé mythbuntu.

El problema es que nunca me funcionó el mythbuntu, se queda la pantalla negra y no funciona.

Intente con el 

sudo apt-get remove mythbuntu-desktop

pero no funciona. (esta instalado con un particionado a parte).

saludos...

Como dijo Carlos C. Mythbuntu es una distribución GNU/Linux no es un programa ni tampoco un entorno de escritorio por lo tanto no creo que funcione tipeando

sudo apt-get remove mythbuntu-desktop

la solución ya esta dada por Carlos C. si quieres quitarlo debes instalar otra distro.

---

### Post by Carlos C on 2009-05-31
> **flakojaime said:**
> (esta instalado con un particionado a parte).
¿Lo que está en una partición aparte es tu "/home"? Explica bien por favor cuál es la situación de tu disco. Sería bueno que nos dijeras qué resultado te da el siguiente comando:
```
sudo fdisk -l
```

---

### Post by flakojaime on 2009-05-31
HOla.

Esto me sale en fdisk -l

[B]Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0003128b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1945    15623181   83  Linux
/dev/sda2            1946       30401   228572820    5  Extendida
/dev/sda5            1946        2194     2000061   82  Linux swap / Solaris
/dev/sda6            2195       30075   223954101   83  Linux
/dev/sda7           30076       30379     2441848+  83  Linux
/dev/sda8           30380       30401      176683+  82  Linux swap / Solaris

Disco /dev/sdb: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000af2bf

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       30097   241754121    5  Extendida
/dev/sdb2           30098       30401     2441880   83  Linux
/dev/sdb5               1       30075   241577374+  83  Linux
/dev/sdb6           30076       30097      176683+  82  Linux swap / Solaris[/B]


Tengo 2 instalaciones de mythbuntu (una que comparte el primer disco con ubuntu y otra montada en el segundo disco).

Si debo hacer una nueva instalacion:

perderé los datos personales?
se borraran las configuraciones de las tarjetas de video  y del escritorio? Me costo un poko configurar el compiz fusion.:D

Gracias por la ayuda.

Jaime

---

### Post by Carlos C on 2009-06-02
Hola. Creo que tienes un poco de desorden en tu disco jeje. Te sugiero que te ordenes. 
Algunos datos que debes tener en cuenta:

[LIST]
[*]No es necesario que cada versión de linux que tengas instalada posea su propia partición "swap". Puedes hacer que todas las que compartan el disco usen la misma partición. Es una partición que se usa como area de intercambio, es decir, es allí donde se almacena información para no saturar la memoria ram.
[*]Puedes tener hasta 4 particiones primarias, se crea una partición extendida sólo cuando el numero de particiones debe ser mayor a 4.
[*]Si vas a reinstalar ubuntu y no quieres perder tus datos debes, durante la instalación, escoger un particionado manual. Luego escoges los puntos de montaje de cada partición. Este paso permite que más de una distro comparta el mismo swap, ya que aquí dices dónde montaras cada partición. La primera partición la montas en "/". La partición que antes solía tener tu home la montas en "/home", pero no seleccionas la casilla para que sea formateada. De esa manera conservarás tus datos.
[*]Respecto al resto de las particiones, yo que tú las borraría e instalaría la otra distro de nuevo o, mejor aún, ampliaría mi home para tener más espacio.
[/LIST]
    
Saludos.

---

