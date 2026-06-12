---
title: "Ayuda principiante"
date: 2009-08-05
forum: Software
---

### Post by camirie on 2009-08-05
Hola, me llamo Camilo. Soy de Moreno Pci de Bs As.
Instalé Ubunto 9.04 pero no me monta los discos. No sé que pasó, formatíe parte del disco en Ext3. Y el resto lo tengo con XP sp2, en ntfs. 
No me deja arrastrar los discos ni los íconos al escritorio. Puede ser un error de instalación? la verdad no tengo la más mínima idea.
lo que son aplicaciones arrancan y puedo browsear las carpetas desde el reproductor de música, obviamente no puedo escuchar por que no tengo los driver de mp3.

para complicar más las cosas, no tengo acceso a internet. Por que dónde vivo no llega la Banda Ancha, y para poner dial up me vuelvo mono. 
Necesitaria que me tiren un centro de como empezar, si me bajo algunos paquetes en el laburo y los llevo en un pendrive y los instalo, pero no me deja montar las unidades.

gracias.

---

### Post by gmunioz on 2009-08-05
Hola cam...:

Tu post esta bastante confuso, quizás es

reflejo de tu estado anímico respecto 

de Ubuntu.

En principio te sugiero recorras el foro

y la documentación.

Para montar particiones ntfs, te hacen falta

ntfs-3g, fuse-utils, y ntfs-config, tambien

son de utilidad las ntfsprogs y disk-manager

si esta disponible.

Te sugiero visites este sitio:

[http://novatocba.netii.net/](http://novatocba.netii.net/)

El el encontrarás como utilizar ubuntu sin 

internet, como actualizarlo y como habilitar

tu modem para conectarte por dial-up

---

### Post by camirie on 2009-08-06
Gracias. 
Voy a visitar la página y recorrer el foro. para ver si encuentro solución.

---

### Post by EnriqueK on 2009-08-06
Si podés correr el Live Cd de instalación en otra PC que tenga internet, o que tengas algún conocido con la misma versión de Unbuntu , te puedo dar detalles de como copiar los índices de repositorios para que mediante Synaptic podás instalar todo lo que quieras.
Si tenés un denominado winmódem. lo mas probable es que logres una conexión de apenas 14.4 kbps que es insuficiente para bajar cualquier paquete pero podés usarlo para instalar y mantener actualizados los índices de repositorios  .
Si tenés instalado la 9.04 64 bits, te puedo subir los índices a Rapidshare para que los copies en un proceso muy simple .

---

### Post by camirie on 2009-08-06
Tengo la de 32 bits.
En cuanto a lo del live cd, es buena idea tendría que venir un día al laburo y correrlo acá.
Estuve viendo algunas páginas y recorriendo el foro, creo que sé como pilotearlo.
gracias.

igual cualquier sugerencia es bienvenida. mi meta a corto plazo, es conseguir internet.

---

### Post by EnriqueK on 2009-08-06
Para que vayás madurando la idea de usar el Live Cd para generar y luego copiar los índices de repositorios-
1.- Corré el Live CD en un equipo con conexión , habilitá los reñpositorios u además los repositorios de Medibuntu , siguiendo las instruciones de syu sitio oficial [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
2,. Siempre en el Ubuntu Live CD ejecutá el siguiente Script o si no savés como ejecutar un Script , podés ejecutar cada sentencia en el orden indicado
```
#!/bin/sh
sudo apt-get update
cd /tmp
sudo tar -zcvf lists.tar.gz /var/lib/apt/lists
sudo tar -zcvf aptcopia.tar.gz /etc/apt
```
3.- Seguidamente abrí terminal y ponés  **nautilus /tmp ** se te va a abor la carpeta temporal **/tmp** y copias a un medio removible (pendrive) los archivos **aptcopia.tar.gz** y **lists.tar.gz** 
3.- Ahora vas a tu instalación de Ubuntu que no tiene Internet , ejecutá **nautilus /tmp** y copiás allí los archivos que tençes en el pendrive 
4.- Luego de estar totalmente seguro de haver copiado los archivos en /tmp, ejecutá este otro Script 
```
#!/bin/sh
sudo rm -Rf '/var/lib/apt/lists'
sudo rm -Rf '/etc/apt'
cd /tmp
sudo tar -zxvf lists.tar.gz --directory /
sudo tar -zxvf aptcopia.tar.gz --directory /
sudo apt-get update
```

Con todo esto ya tendrás copiado los índices de repositorios y lo que queda es usar Synaptic para instalar todo lo que quieras , tanto paquetes de programas como de actualizaciones, hay bastante loteratura al respecto, es muy simple el proceso, pero se hace un poco largo de explicar en palabras.
Por otra parte, igual vas a tener que usar Synapyic para poder descargar con otro equipo por que lo mas probable ws que con la conexión DialUp solo te va a servir para los índices de repositorios, olvidate de descargat paquetes a 14.4 kbps.

---

### Post by camirie on 2009-08-07
Muchachos, les cuento:
Lei lo de esta página, mis discos están montados.
Siempre lo estuvieron haciendo click sobre el Icono de la solapa Lugares>>etc. en la pantalla principal.
Logré instalar los restricted extras, con bastante sudor de bocha pero ya puedo reproducir video y escuchar música, leer archivos .doc con Open Office y no sé que más.
Ahora, más alla de que no pueda usar Synaptic para instalar paquetes desde la internet, existe otro método que no sea el del Live CD? 
otra consulta, Lo que no me deja es poner accesos directos en mi escritorio, tengo que colgarlos todos de la barra de tareas que esta arriba... me podrían dar una mano. Tal vez es problema de alguna autenticación que le estoy errando.
Igual estoy re chocho de haber podido instalar los restricted extras y haber podido explorar mís discos NTFS. siempre a travez de la terminal. ese es el único problema.

Saludos.

---

### Post by sitodonosti on 2009-08-07
para el acceso directo en el escritorio lo que puedes hacer es clickar con el boton derecho y darle a propiedades, despues en el escritorio le das a crear lanzador y copias lo que este en el lanzador del panel de gnome al que has creado en el escritorio y yasta!! 

un saludo desde donosti

---

