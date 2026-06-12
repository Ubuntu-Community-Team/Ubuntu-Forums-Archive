---
title: "Re: TENGO INSTALADO UBUNTO 7.04 , se gana si de pasa al 9.04 , como se hace?"
date: 2009-09-04
forum: Software
---

### Post by EDGAR MORENO on 2009-09-04
Señores quisiera saber si alguno ha tenido ya esta experiencia de tener Ubunto 7.04 y querer  pasar a instalar Ubunto 9.04 , en ese caso como se hace? (soy un completo aficionado a esto , por lo tanto no se mucho de instalación de programas y o borrarlos en caso de que no sirvan , etc etc)  de antemano muchas gracias por sus aportes a mi inquietud , el caso es que quisiera ir actualizando mi ubuntu para tener posibilidad de tener algún programa que me sirva para hacer dibujos tridimensionales en arquitectura , para ello entonces surge la segunda pregunta que tengo para los grupos de maravillosos amigos y familia Ubunto que se que nos apoyan a todos los que elegimos esta plataforma  
SÍNTESIS DE MIS INQUIETUDES 

Tengo instalado Ubunto 7.07 hay conflictos si se instala Ubunto 9.04  ¿cual seria la mejor manera de hacerlo? 

qué programas se pueden instalar para dibujos arquitectónicos en ubunto  parecidos a Sketchup
¿los hay para Ubunto 7.04? o tengo que instalar el ubunto 9.04 para poder disfrutar de un buen programa de dibujo tridimensional?

de nuevo muchísimas gracias por estos favores y no se olviden a los amigos que me respondan como hago caricaturas , sera un placer dibujarlos sin costo alguno  este es mi sitio para que vean mis dibujos [http://caricaturascr.blogspot.com/](http://caricaturascr.blogspot.com/)

---

### Post by EDGAR MORENO on 2009-09-04
Señores quisiera saber si alguno ha tenido ya esta experiencia de tener Ubunto 7.04 y querer pasar a instalar Ubunto 9.04 , en ese caso como se hace? (soy un completo aficionado a esto , por lo tanto no se mucho de instalación de programas y o borrarlos en caso de que no sirvan , etc etc) de antemano muchas gracias por sus aportes a mi inquietud , el caso es que quisiera ir actualizando mi ubuntu para tener posibilidad de tener algún programa que me sirva para hacer dibujos tridimensionales en arquitectura , para ello entonces surge la segunda pregunta que tengo para los grupos de maravillosos amigos y familia Ubunto que se que nos apoyan a todos los que elegimos esta plataforma
SÍNTESIS DE MIS INQUIETUDES

Tengo instalado Ubunto 7.07 hay conflictos si se instala Ubunto 9.04 ¿cual seria la mejor manera de hacerlo?

qué programas se pueden instalar para dibujos arquitectónicos en ubunto parecidos a Sketchup
¿los hay para Ubunto 7.04? o tengo que instalar el ubunto 9.04 para poder disfrutar de un buen programa de dibujo tridimensional?

de nuevo muchísimas gracias por estos favores y no se olviden a los amigos que me respondan como hago caricaturas , sera un placer dibujarlos sin costo alguno este es mi sitio para que vean mis dibujos [http://caricaturascr.blogspot.com/](http://caricaturascr.blogspot.com/)

---

### Post by hockeytux on 2009-09-04
Tienes que actualizar version por version - no puedes 'saltar' desde 7.04 a 9.04. Primero actualizas a 7.10, despues 8.04 y 8.10 y solo de 8.10 puedes actualizar a 9.04. Es mas seguro.

---

### Post by joseluis on 2009-09-05
A mi, en general, no me sirve (ni me convence) actualizar de una versión a otro. Prefiero instalar desde cero. Y mucho más desde una versión dos años más vieja, que tendrías que hacer cuatro pasos previos. Instalá la 9.04 o mejor aún, esperá un mes más y metele la 9.10.

Para dibujos tridimensionales, probá con Blender, que también tiene versión Windows.

Saludos

---

### Post by juancarlospaco on 2009-09-05
Espera 1 mes y instala, formateando en EXT4.
*Se ven Koalas en el horizonte...*

---

### Post by Mister X on 2009-09-05
yo soy partidario de ir actualizando las versiones y no instalar de cero cada vez que sale una nueva version, si mantenes una instalacion "prolija" (con pocos programas por fuera de la distribucion), las actualizaciones se realizan sin problemas.

pero en este caso como te dijeron vas a tener que pasar por cada una de las versiones intermedias, yo si estuviera en tu caso haría un backup e instalaría la 9.04 de cero

saludos!!

---

### Post by EnriqueK on 2009-09-05
Aunque quieras no vas a poder hacer actualizaxiones escalonadas por que tanto los repositorios de la 7.04 como la de la 7.10 dejaron de estar activos.
Si lo que querés es hacerlo de una forma desatendida, recomiendo en una **migración** y esta se basa en crear la lista de paquetes instalados en la 7.04 y usarla en una instalación de cero de cualquier otra versión, y cuando digo cualquiera , es cualquiera y no necesariamente otro Ubuntu, por ejemplo acabo de hacer una migración de Ubuntu 9.04 64 bits a Debian Lenny 32 bits y antes había hecho otra de Ubuntu a PCLinuxOS . distro esta que usa paquetes RPM de Red Hat, pero emplea el gestor de paquetes APT  Debian .
La Lista de paquetes la creas usando Synaptic --> Archivo-->Guardar selecciones como--> marcas el casillero "guardar el estado completo no solo los cambios" , le das un nombre--> Guardar . esto va a generar un archivo de textos plano en la que figuran solo los nombres de los paquetes y no la versión de los mismoas , esto es lo que va a permitr que la otra instalacióm use esta info para descargar/instalar esos mismos paquetes pero para la versión que corrsponda- En la nueva instalación abre Synaptic --> Archivo--> Leer selecciobes--> doble click sobre el archivo creado en la instalación anterior . pulsar el botón Aplicar de Synaptic , acepta todo lo que te pida y a esperar, esta espera puede ser muuuy larda ya que va a r  depender de tu conexión-
El éxito de la migración va a depender de elegir los repositorios lo mas equivalenmtes posibles de la instalación origen.

---

### Post by juancarlospaco on 2009-09-05
Pero la serie 9.x trae la ventaja del filesystem EXT4, 
un upgrade no te va a upgradear el filesystem.

---

### Post by gmunioz on 2009-09-05
Hola edg....:

1- "..... Tengo instalado Ubunto 7.07 hay conflictos si se instala Ubunto 9.04 ¿cual seria la mejor manera de hacerlo? ....?

En mi opinión, basada en mi experiencia, que naturalmente tiene disímiles
y opuestas, te sugiero:

Pongas a resguardo tus archivos (pendrive - cd- dvd) e instales en:
Una partición primaria, activa, sistemas de archivos ext4, de unos 14 
gigas, punto de montaje /
Una partición lógica, sistema de archivos intercambio, de unos 2 gigas
montaje por defecto (swap)
Una partición lógica, sistema de archivos ext4, de unos 5 gigas, punto
de montaje /home
Una partición lógica, sistema de archivos ext4, del resto de los gigas,
punto de montaje /home/usuario/datos
Esto lo haces cuando al comenzar el particionamiento durante la 
instalación eliges manual, borras las particiones existentes y creas
las nuevas, aplicando luego los cambios.
Con el procedimiento descripto por enriquek, se reinstalaran 
automaticamente tus aplicaciones actuales, si estan disponibles.
A partir de esta instalación, tendrás tus archivos alojados en
/home/usuario/datos a salvo para futuras instalaciones, igual que
las configuraciones de tus aplicaciones en /home. para poder copiar
y borrar en /home7usuario/datos debes ejecutar una vez instalado e
iniciado el sistema la orden en consola:
sudo chmod -Rf 777 /home/usuario/datos

2 - "...qué programas se pueden instalar para dibujos arquitectónicos en ubunto parecidos a Sketchup ..."

[http://www.blender.org/](http://www.blender.org/)

[http://www.artofillusion.org/](http://www.artofillusion.org/)

[http://www.crystalspace3d.org/main/Main_Page](http://www.crystalspace3d.org/main/Main_Page)

[http://freewrl.sourceforge.net/](http://freewrl.sourceforge.net/)

[http://k3dsurf.sourceforge.net/](http://k3dsurf.sourceforge.net/)

[http://www.kpovmodeler.org/](http://www.kpovmodeler.org/)

[http://www.povray.org/](http://www.povray.org/)

---

### Post by EDGAR MORENO on 2010-02-18
Gracias por las respuestas , sigo estudiando el caso , un poco lento, ya que no se nada de programacion y temo dañar lo que tengo , en fin les agradezco mucho lo que me han dado y ahora que tengo un tiempo vere como puedo seguir aprendiendo en el mundo de UBUNTU 
una pregunta amigos , ¿con lo que tengo ( ubunto 7-04) se puede instalar algun programa como alguno de los que menciona el amigo Gmunioz?

---

