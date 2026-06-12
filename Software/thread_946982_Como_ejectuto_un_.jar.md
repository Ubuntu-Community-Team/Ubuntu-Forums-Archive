---
title: "Como ejectuto un .jar"
date: 2008-10-13
forum: Software
---

### Post by victor_nesta on 2008-10-13
Es para el Jdownloader, que ya lo he usado en ubuntu. 
La cuestión es que reistale y no encuentro la aplicación para ejecutarlos.
Baje jre-6u7-linux-i586.bin, la ejecute en consola. e instale un par desde synaptic y nada.
No me acuerdo y ya me marie. y tengo ganas de llamar a SUN a putear.

---

### Post by kbzon_v8 on 2008-10-13
Proba con: -jar nombredelarchivo.jar desde la consola.

---

### Post by pol666 on 2008-10-13
es un archivo java, si no pasa nada haciendo doble click

abri una terminal, movete con cd /ruta de la carpeta donde este el jar

y hace un



 java -jar JDownloader.jar

---

### Post by victor_nesta on 2008-10-13
victor@equipodenesta:~/Escritorio/Backup ubu/Programas/Jdownloader/bin$ java -jar JDownloader.jar
El programa «java» puede encontrarse en los siguientes paquetes:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Pruebe: sudo apt-get install <paquete seleccionado>
bash: java: orden no encontrada



Bueh igual ya esta, sin ningún criterio en synaptic marque para instalar 
Sun-java-bin y aparte me marco dependencias Sun-java-jre y sun-java-plugin
y se resolvió.
Cuestión de suerte

Edito: Soy un maleducado. No dije Gracias.
GRACIAS!!!

---

### Post by kbzon_v8 on 2008-10-13
la suerte siempre juega en estos temas... lo bueno es cuando juega a favor y las cosas misteriosamente suceden... jejeje

---

### Post by faktorqm on 2008-10-14
A mi con el java de Sun directamente no me abre, uso openjdk o iced tea creo que se llama... a vos te anda bien con el de sun? salu2!

---

### Post by guisheca on 2008-10-14
Me parece a mi o se están complicando la vida muchachos. Lo unico que hay que hacer es tener instalado el runtime java. Basta con hacer esto que muestro en la imágen.
Despues hay que elegir dicho programa para ejecutar el archivo .jar y listo, nada del otro mundo. Yo uso el jdownloader de esa forma y jamás tengo drama.
Saludos.

---

### Post by victor_nesta on 2008-10-14
> **guisheca said:**
> Me parece a mi o se están complicando la vida muchachos. Lo unico que hay que hacer es tener instalado el runtime java. Basta con hacer esto que muestro en la imágen.
Despues hay que elegir dicho programa para ejecutar el archivo .jar y listo, nada del otro mundo. Yo uso el jdownloader de esa forma y jamás tengo drama.
Saludos.

Te juro que fue lo primero que hice, pero no se que tendré o que me faltara que no me cargaba.
La lógica indica que ESE es el adecuado para abrir los .jar, but...

---

### Post by guisheca on 2008-10-14
> **victor_nesta said:**
> Te juro que fue lo primero que hice, pero no se que tendré o que me faltara que no me cargaba.
La lógica indica que ESE es el adecuado para abrir los .jar, but...

Apa mirá vos, esas cosa a veces como que me desilusionan un poco, o mejor dicho, me quedan dando vueltas por la cabeza y me frustran :-k, porque no le encuentro explicación. Por que será que de forma inexplicable algunas cosas en algunos casos no funcionan y en otros no. 
Y eso mas allá del hardware, una ves en una misma máquina dos instalaciones de la misma versión de ubuntu dieron problemas distintos. En ese entonces la única diferencia fué que una instalación fué hecha mediante un cd "original" (enviado por canonical) y la otra mediante un cd descargado desde la net, por lo cual flashe que los cds originales de canonical en realidad son alguna release anterior al lanzamiento oficial de la versión final, esto debido a la intensa demanda desde todo el mundo y el apuro por satisfacerlas.
Que se yo, me agarran unos ataques de paranoia a veces :D
Saludos.

---

### Post by victor_nesta on 2008-10-14
Si, aparte te podes imaginar que yo con mis amplísimos conocimientos de Linux, menos que menos.

---

### Post by vgvvictor on 2009-03-03
Prueba con lo siguiente. Estoy casi convencido de que te funcionará:

```
cd /etc
sudo gedit profile
```

el este archivo de texto añade al final lo siguiente:

```
PATH="${PATH}:[ruta/donde/has/instalado/java*]/bin"
export PATH 
```

guardalo reinicia la sesion y listo

*en mi caso: /opt/jdk1.6.0_07

---

