---
title: "Como instalo covergloobus en Jaunty? AYUDA!"
date: 2010-03-27
forum: Software
---

### Post by leonardo83 on 2010-03-27
buenas, tengo la version Jaunty de Ubuntu y recientemente vi que algunos usaban Covergloobus para mostrar la tapa de los artistas que escuchan, yo usaba Desktop art con el rhythmbox pero quiero probar el otro.
Entre a la pagina del programa, pero me da para agregar los archivos en repositorios para Karmic, y si me bajo los archivos fuente para compilar me da un error y no sucede nada, quisiera saber si alguno tiene jaunty y le funciona el programa como lo instalo, o si se puede bajar un .deb de alguna pagina, o si me pueden dar una mano.

Gracias espero respuesta :D

---

### Post by leonardomdq on 2010-03-28
Abri una consola y pone lo siguiente:

[FONT=Courier New]```
sudo  add-apt-repository ppa:gloobus-dev/covergloobus
``` 

```
sudo apt-get update
``` 

```
sudo apt-get install covergloobus
```[/FONT]

Una ves instalado te vas a Aplicaciones -> Accesorios > Covergloobus.


Saludos ;)

---

### Post by leonardo83 on 2010-03-28
> **leonardomdq said:**
> Abri una consola y pone lo siguiente:

[FONT=Courier New]```
sudo  add-apt-repository ppa:gloobus-dev/covergloobus
``` 

```
sudo apt-get update
``` 

```
sudo apt-get install covergloobus
```[/FONT]

Una ves instalado te vas a Aplicaciones -> Accesorios > Covergloobus.


Saludos ;)

gracias man!
vi ese paso y lo intente realizar antes pero me da este error:
```
sudo: add-apt-repository: command not found

```

Alguna idea? :confused:

---

### Post by guillermolisi on 2010-03-28
Sera por que estas usando JJ en lugar de KK ? Hay metodos de agregado de repositorios en KK que en JJ no existen.

---

### Post by leonardo83 on 2010-03-28
> **guillermolisi said:**
> Sera por que estas usando JJ en lugar de KK ? Hay metodos de agregado de repositorios en KK que en JJ no existen.

Debe ser, por eso mi pregunta inicial era si alguno lo tenia andando en Jaunty para ver como se instalaba, porque bajandoe l codigo fuente me daba error tambien u.u

O sea que no se puede instalar ???

---

### Post by guillermolisi on 2010-03-28
> **leonardo83 said:**
> Debe ser, por eso mi pregunta inicial era si alguno lo tenia andando en Jaunty para ver como se instalaba, porque bajandoe l codigo fuente me daba error tambien u.u

O sea que no se puede instalar ???
Solo me referia al metodo de agregado de repositorios, no al software en particular.

Y ahora que lo mencionas, Covergloobus tendra paquetes para JJ o solo para KK ?
Si solo tiene para KK sera un intenso trabajo encontrar la forma, si la hay, de que funcione en JJ.

---

### Post by leonardomdq on 2010-03-29
En el metodo de agregar repositorios patine yo, acostumbrado a KK.

Dejame que esta tarde me pongo en contacto con el desarrollador de Covergloobus y le pregunto en JJ que onda, creo que compilando no tendria que haber mayores problemas. Te digo porque para LL tampoco estan los repos y sin embargo compile con el bzr branch lp:covergloobus y salio andando.
Fijate de tener todas las librerias para compilar antes que nada.

Mas tarde te aviso.

Saludos


EDIT:
Ya me puse en contacto con el desarrollador [_JordiHP_ ]("http://gloobus.wordpress.com/"), me dijo que no tiene que haber ningun problema compilando.

Para compilar la ultima version bajate el [B]bzr branch lp:covergloobus
[/B]
_Antes que nada asegurate de tener todas las herramientas necesarias para compilar el programa._

```
build-essential , pkg-config , autoconf , automake, bzr y libtool
```Abris una consola y pones lo siguiente:

```
bzr branch lp:covergloobus
cd covergloobus
./autogen.sh --prefix=/usr/
make && sudo make install

```Si falla la salida avisa que lo vemos.

Saludo ;)

---

### Post by leonardomdq on 2010-04-01
Solucionaste? pudiste compilar Covergloobus?

---

