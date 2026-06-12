---
title: "Si alguien tuvo problemas con pulseaudio-equalized en Ubuntu 13.04"
date: 2013-05-19
forum: Software
---

### Post by Pablo Daniel on 2013-05-19
Hola a todos! que tal? 

Tuve la idea de instalar pulseaudio-equalizer en Ubuntu 13.04 pero no funcionaba de ninguna forma y se me ocurrio buscarle una solucion que me sirvio y espero que les sirva de mucho. El ecualizador esta funcionando y se nota la diferencia.

El ecualizador de pulseaudio no se instala bien en ubuntu 13.04 debido a que fue diseñado para funcionar hasta el momento en ubuntu 12.04. 

La solucion que encontre es:

ir a la terminal, en el dash, abrirla y pulsar enter: 

Con la terminal abierta escribir:

```
sudo add-apt-repository ppa:psyke83/ppa
```

(esta orden busca los repositorios, llamados PPA donde esta pulseaudio equalizer, pero no va a encontrar el archivo)

Escribir apt-get update y presionar enter para que actualice. Dara un mensaje avisando que el repositorio de pulseaudio-equalizer no esta todavia para Raring.

```
sudo apt-get update
```

Reinciar el sistema luego.

La solucion es buscar el sitio ppa:psyke83/ppa en google y bajar pulseaudio-equalizer primero:

[http://ppa.launchpad.net/psyke83/ppa/ubuntu/pool/main/p/pulseaudio-equalizer/pulseaudio-equalizer_2.7_all.deb](http://ppa.launchpad.net/psyke83/ppa/ubuntu/pool/main/p/pulseaudio-equalizer/pulseaudio-equalizer_2.7_all.deb)

Una vez bajado este archivo, para instalarlo necesitan dos dependencias:

ladspa-sdk
swh-plugins

De donde obtenerlas:

Ubuntu Packages buscando Raring:

[http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/l/ladspa-sdk/ladspa-sdk_1.13-1ubuntu1_i386.deb](http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/l/ladspa-sdk/ladspa-sdk_1.13-1ubuntu1_i386.deb)

[http://mirror.anl.gov/pub/ubuntu//pool/universe/s/swh-plugins/swh-plugins_0.4.15+1-7_i386.deb](http://mirror.anl.gov/pub/ubuntu//pool/universe/s/swh-plugins/swh-plugins_0.4.15+1-7_i386.deb)

Al intentar instalarlas con Gdebi, puede que pida los otros archivos y no deje instalarlos. En ese caso hay que abrir pulseaudio-equalizar y dejar que el sistema baje e instale los archivos pulsando instalar con la maquina conectada a la red. Al instalar el programa todo parece normal
pero al ejecutarlo no funciona. Estas son las causas y como las solucione:

El archivo pulseaudio-equalizer instala pulseaudio-equalizer y pulseaudio-equalizer-gtk en usr/bin, con los archivos presets en share/pulseaudio-equalizer, que contienen la configuracion del sistema de sonido. El sistema al intentar ejecutarse, mira en la cuenta de usuario para buscar la carpeta oculta ./pulse, para buscar la misma configuracion que no existe.
Para crearla hay que ir a Nautilus, preferencias, y elegir que muestre los archivos ocultos, cerrarlo y volverlo a abrir para ver los archivos ocultos. Luego se puede crear una carpeta nueva llamada ./pulse. y dejar abierto nautilus

El sistema ademas, busca los archivos ./ presets, que deberian estar en /home/cuenta de usuario/./pulse/presets, que estara vacia. Para copiar los archivos que pide, hay que abrir pulseaudio-equalizer_2.7_all.deb con el gestor de archivadores:

Luego ir abriendo cada carpeta hasta esta ubicacion /usr/share/pulseaudio-equalizer. Aqui se encontrara la carpeta presets, que es justamente la que el programa pide. Se la puede extraer a la carpeta /home/cuenta de usuario, y de alli copiarla a la carpeta ./pulse, y quedara asi:

/home/cuenta de usuario./pulse/presets

El sistema instala un archivo llamado pulseaudio-equalizer.py en la carpeta /usr/share/pulseaudio-equalizer, y este le dice como ejecutar el ecualizador. 
El script busca un archivo llamado gnome-volume-control.svg en esta carpeta, pero el archivo no se encuentra.
Dentro de la terminal, conviene ejecutar la orden: sudo nautilus, luego escribir la contraseña y buscar este archivo en la carpeta usr/share/pulseaudio-equalizer y abirlo con gedit para editarlo.
Una vez abierto el archivo con gedit con doble click, dentro del archivo pulseaudio-equalizer.py hay que buscar esta linea:

icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")

Cambiarla por esta ubicacion:

icon = self.window.set_icon_from_file("/usr/share/icons/Humanity/apps/16/gnome-volume-control.svg")

Cerrar al archivo y todas las ventanas abiertas, y abrir el progeama desde el dash de unity buscando pulseaudio-equalizer. Estos pasos solucionan el problema mientras el autor del programa diseña una version para Ubuntu 13.

---

### Post by VictorVE on 2013-06-14
Gracias Pablo Daniel, realmente funciona.

Este se siente mejor que el equalizador sugerido para 13.04 acá:

[http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)

Se valora y agradece.

---

