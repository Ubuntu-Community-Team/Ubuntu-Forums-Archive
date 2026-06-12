---
title: "Kernel panic"
date: 2013-02-14
forum: Software
---

### Post by Meliss on 2013-02-14
Hola hace un tiempo que estoy usando Ubuntu 10.04, la última actualización del Kernel fue a la 2.6.32-45-generic.

Hoy se me ocurrió instalar el kernel 3.4 y seguí las instrucciones de este tutorial: [http://www.k0braintheworld.com/2011/07/23/instalar-kernel-30-en-ubuntu/](http://www.k0braintheworld.com/2011/07/23/instalar-kernel-30-en-ubuntu/)

al reiniciar y entrar a la opción linux 3.4 me salió este mensaje y se quedó allí:
[http://imgur.com/eD7pu4d](http://imgur.com/eD7pu4d)
[http://imgur.com/X5TtyMu](http://imgur.com/X5TtyMu)

No podía reiniciar ni nada y tuve que desconectar el cable de energía y volver a encender la laptop; como aun tenía la opción de linux 2.6.32-45-generic inicié desde ahí sin problemas; no sé si hice algo mal porque no quiero tener que reinstalar otra vez desde cero y tampoco quiero que se borre la opción de linux 2.6.32-45-generic porque ya no podría entrar.

Buscando un poco me encontré con este post [http://ubuntuforums.org/archive/index.php/t-1769102.html](http://ubuntuforums.org/archive/index.php/t-1769102.html)
pero no comprendo bien si se pueda tratar de los mismo

Al ejecutar
sudo fdisk -l
me sale:

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x5f4fbff6

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2              13       19457   156181319+   7  HPFS/NTFS
/dev/sda3           19457       38914   156285953    5  Extendida
/dev/sda5           19457       38119   149900288   83  Linux
/dev/sda6           38119       38914     6384640   82  Linux swap / Solaris

hasta aqui llegué, ojala me puedan ayudar

---

### Post by guillermolisi on 2013-02-14
Aparentemente si, se trata de lo mismo pero, en tu lugar, si quisiera contar con las bondades de un kernel LTS como es la version 3, actualizaria a la 12.04.

Eso si, vas a tener que elegir que escritorio grafico usar ya que viene con Unity, Gnome2 con aceleracion grafica y Gnome 2 fallback (sin aceleracion ni efectos).

Actualizando todo el sistema mantenes la coherencia de versionado de los paquetes que forman parte de GNU/Linux y no solamente modificas el kernel.

---

### Post by biale on 2013-02-14
Cuando se instala un nucleo muy distinto (2.6.x vs 3.x) existe el riesgo de que el nuevo nucleo no funcione y también existe el riesgo (no muy obvio) de no poder arrancar ni siquiera con el nucleo anterior.

En mi caso, mande al diablo el area de pruebas que estaba usando e hice el reporte a Launchpad.

O sea que la recomendación de Guillermo es mucho mas sensata de lo que parece y debería ser tenida en cuenta.

---

### Post by Meliss on 2013-02-15
> **guillermolisi said:**
> Aparentemente si, se trata de lo mismo pero, en tu lugar, si quisiera contar con las bondades de un kernel LTS como es la version 3, actualizaria a la 12.04.

Eso si, vas a tener que elegir que escritorio grafico usar ya que viene con Unity, Gnome2 con aceleracion grafica y Gnome 2 fallback (sin aceleracion ni efectos).

Actualizando todo el sistema mantenes la coherencia de versionado de los paquetes que forman parte de GNU/Linux y no solamente modificas el kernel.

Gracias por la respuesta. No crees que pueda ocurrir algún error similar al actualizar a la versión 12.04, revisando encontré que a algunas laptop les sale el kernel panic al actualizar

---

### Post by biale on 2013-02-15
La palabra actualizar tiene dos significados.

Uno sería instalar desde cero la nueva versión pero sin formatear la partición home y con todos los backups del caso (Minimo la configuración y los datos).

El segundo sería correr una actualización desde la versión anterior. De nuevo, con todos los backups del caso.

Estadísticamente el segundo metodo tiene una tasa de fallos (aprox) del 30%. Yo me refería solo al primer método y siempre considerando pruebas y la posibilidad de una vuelta atras.

Cuando actualizas solo el nucleo y los desniveles son grandes hay otras piezas que van a quedar fuera de sincronismo. La probabilidad de tener problemas futuros (y para colmo sin previo aviso) aumenta mucho.

---

### Post by guillermolisi on 2013-02-15
> **Meliss said:**
> Gracias por la respuesta. No crees que pueda ocurrir algún error similar al actualizar a la versión 12.04, revisando encontré que a algunas laptop les sale el kernel panic al actualizar

Y dentro de esos casos de laptops con kernel panic, esta tu marca y modelo ?

De cuando son esos reportes de fallos por kernel panic ?
Una cosa es actualizar de 10.04 a 12.04 a la semana de haberse liberado la ultima y otra muy distinta es hacerlo ahora.

Generalmente soy de actualizar una version sobre otra y, hasta aqui, tuve inconvenientes pero referidos a cambios profundos en Apache, por ejemplo, y en maquinas que ofician de servidores.

Las pocas veces que realice una "actualizacion" fresca, preservando la particion Home, fue cuando use Arch y volvi a Ubuntu y cuando decidi cambiar la politica de particionado de los discos por otra mas adecuada al uso que les doy a mis maquinas.

---

### Post by Meliss on 2013-02-15
> **guillermolisi said:**
> Y dentro de esos casos de laptops con kernel panic, esta tu marca y modelo ?

De cuando son esos reportes de fallos por kernel panic ?
Una cosa es actualizar de 10.04 a 12.04 a la semana de haberse liberado la ultima y otra muy distinta es hacerlo ahora.

Generalmente soy de actualizar una version sobre otra y, hasta aqui, tuve inconvenientes pero referidos a cambios profundos en Apache, por ejemplo, y en maquinas que ofician de servidores.

Las pocas veces que realice una "actualizacion" fresca, preservando la particion Home, fue cuando use Arch y volvi a Ubuntu y cuando decidi cambiar la politica de particionado de los discos por otra mas adecuada al uso que les doy a mis maquinas.

Entonces me recomiendas que actualice con la opción del gestor de actulizaciones?

Tengo dudas para actualizar porque temo que se puedan borrar mis archivos y los programas que tengo instalado y las configuraciones, además de mis marcadores del navegador xD

---

### Post by guillermolisi on 2013-02-17
Antes de llevar a cabo cualquier modificacion de estas caracteristicas, backup, copia de resguardo de los contenidos alojados en /home/<tu_usuario>, de minima.

---

