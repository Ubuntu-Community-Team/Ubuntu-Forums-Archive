---
title: "instalar ESP-R en Ubuntu"
date: 2009-06-18
forum: Software
---

### Post by pat0v3n on 2009-06-18
holas instale muy hace muy poco el Ubuntu para probar un prograa en el que trabajo y necesito ayuda sobre "La instalacion del ESP-R en el ubuntu", desde ya gracias.-

ubuntu v9.04

---

### Post by Patriciologico on 2009-06-18
Hola pat0v3n y bienvenido,
  
 No me queda claro que es el ESP-R, me podrías dar mas datos?

Saludos!


PD: Escribir en mayúsculas, es sinónimo de dar gritos en la web, nadie quiere que le pidan ayuda gritando, por favor edita tu pregunta.

---

### Post by gmunioz on 2009-06-18
Hola:

ESP-r es un instrumento de modelización para la simulación de la térmica,

visual y acústica de los edificios y la evaluación del uso de la energía

y las emisiones de gases relacionados con el medio ambiente y sistemas de

control de materiales de construcción. 

En la realización de sus evaluaciones, el sistema está equipado con el

modelo de calor, el aire, la humedad y las corrientes de energía 

eléctrica en el usuario determina la resolución. 

El sistema está diseñado para el sistema operativo Unix, con el apoyo de 

las implementaciones para Solaris y Linux, y está disponible sin costo 

alguno en virtud de su licencia Open Source. 

La versión específica para Ubuntu se descarga desde:

```
http://www.esru.strath.ac.uk/Downloads/ESP-r_linux_binaries/esp-r_v11.7_linux_precomp.run  
```

Y las instrucciones para su configuración se descargan desde:

```
http://www.esru.strath.ac.uk/Downloads/Linux/Ubuntu_8.4_for_esp-r.pdf
```

---

### Post by CdK1 on 2009-06-18
Aplica:

wget 
[http://www.esru.strath.ac.uk/Downloads/ESP-r_linux_binaries/esp-r_v11.7_linux_precomp.run](http://www.esru.strath.ac.uk/Downloads/ESP-r_linux_binaries/esp-r_v11.7_linux_precomp.run)

Luego: sh archivo.run

---

### Post by pat0v3n on 2009-06-19
soy extremadamente nuevo en el manejo de ubuntu y las instrucciones que salen en la pagina de esp-r son instrucciones mas para suicidarce que para entenderlas, la verdad una  amiga me a estado ayudando a instalarlo y hasta el momento y despues de mucho leer lo instalo, actualizo el PATH e instalo muchas de las bibliotecas que pide, excepto por una -libgfortran.so.1- la que encontre eventualmente y bajo, pero al momento de instalarlo con GDebi me aparece lo siguiente:

Error: La dependencia no se puede satisfacer: gcc-4.1-base (= 4.1.2-21ubuntu1)

Runtime library for GNU Fortran applications
Library needed for GNU Fortran applications linked against the shared library. 

reitero denuevo el interes por ayudar gracias.-

---

### Post by gmunioz on 2009-06-19
Hola pat.....:

Baja los archivos desde estos sitios:

```
https://launchpad.net/ubuntu/hardy/i386/gcc-4.1-base/4.1.2-21ubuntu1

https://launchpad.net/ubuntu/intrepid/i386/libgfortran1/4.1.2-21ubuntu1
```

Y los instalas  en ese orden, mediante gdebi.

Luego cargas synaptic (sistema - administración - gestor de paquetes 

synaptic)

Buscas el archivo gcc-4.1-base en la pantalla de la derecha.

Lo iluminas

Pulsas paquete (tercer opción de su menu)

En el menu desplegable marcas bloquear versión.

Con esto evitas que se actualice desde synaptic y te dañe libgfortran1

al actualizarlo.

Luego en una consola (aplicaciones - accesorios - terminal) ejecutas:

```
echo gcc-4.1-base hold | sudo dpkg --set-selections
```

Con esta orden evitas que se actualice el paquete desde apt-get y

aptitude.

---

