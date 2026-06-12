---
title: "Ayuda Cedega"
date: 2009-02-16
forum: Software
---

### Post by sirkurt on 2009-02-16
bueno la cuestion es la siguiente

quiero emular juegos de windows dentro de ubuntu 8.04 entonces averiguando vi que la mejor convinacion era cedega y wine logre instalar todo instale un juego llamado timeshift solo para provar y a la primera se ponia la pantalla negra como para entrar, se escuchaban los sonidos de las presentaciones de los fabricantes pero no se veia nada cuando pasaban esas presentaciones tiraba un error que no llegue a capturar.

Bueno pense y me parecio obvio que tenia que instalar directx 9.0c en wine y lo ise tal cual esta en [este manual]("http://tecnologiaslibres.net/2008/11/14/tutorial-instala-direct-x-90c-usando-wine/").

bueno una vez hecho eso trato de abrir el juego y me aparece la apicacion minimizada de iniciando timeshift, pasa un tiempo corto y desaparece sin que pase nada.

ese es el problema en si nose si sera el juego o la forma en la que trato de ejecutarlo.

otra cuestion es esta :

quiero instalar un juego que tengo dividido en 2dvds el Lost Planet: Extreme Condition para probar como es el rendimiento bajo ubuntu el problema es que en la instalacion cuando me pide el 2do dvd no me deja sacarlo ya que cedega dice que no se puede parar la emulacion.

se me ocurrio que podia ser util copiar la iso del segundo dvd a la pc y montarla directamente desde ahi pero nose que programas usar.

bueno les dejo este par de consulatas haber que pasa

---

### Post by Hei Ku on 2009-02-16
Podes montar una iso con el comando:

sudo mount -t iso9660 -noloop <archivo.iso> /media/cdrom

La carpeta cdrom tiene que existir

---

### Post by sirkurt on 2009-02-16
si mas bien lo que busco es un programa, ademas la idea es copiar la iso del dvd a la maquina para luego montarla con cedega.

---

### Post by sajnox on 2009-02-17
> **sirkurt said:**
> se me ocurrio que podia ser util copiar la iso del segundo dvd a la pc y montarla directamente desde ahi pero nose que programas usar.

bueno les dejo este par de consulatas haber que pasa

Para copiar la iso podes usar el k3b, es un programa muy completo. Para instalarlo tenes que ejecutar

```
sudo apt-get install k3b
```

Una vez que tenes la iso podes hacer como te dice Hei Ku, o podes agregar algun programa para montar iso, furiou iso (algo asi se llama, buscalo con synaptic)

Pregunta: El juego que queres instalar esta en la base de datos de Cedega? Buscaste la instalacion de ese juego en ubuntu en google?

Consejo: El correcto ortografico no muerde

---

### Post by sirkurt on 2009-02-17
solamente los juegos contenidos en la base de datos cedega funcionan?

lo mas seguro es que si es asi ese sea el problema por el cual no pude correr el juego

---

### Post by sajnox on 2009-02-17
> **sirkurt said:**
> solamente los juegos contenidos en la base de datos cedega funcionan?

No necesariamente, hay juegos que pueden correr usando cedega sin que esten en la base de datos. Si estan es por que es lo mas seguro que anden.

Saludos

---

### Post by matias_tati on 2009-07-19
Yo no pude instalar ningun juego cedega por que sera?

---

