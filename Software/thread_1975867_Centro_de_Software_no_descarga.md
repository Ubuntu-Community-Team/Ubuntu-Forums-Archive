---
title: "Centro de Software no descarga"
date: 2012-05-07
forum: Software
---

### Post by Byzance on 2012-05-07
Hola gente! Como andan? Espero que bien.
 Les comento que hace dos o tres días empecé a leer mucho sobre Ubuntu y bueno, ayer me lance a instalarlo. Sabia que no iba a ser facil para alguien como yo que nunca use otro SO que no sea Windows pero decidí darme maña. Hasta hace unas horas no hice nada del otro mundo, fue algo engorroso hacer las particiones y instalar algunos programas con el Terminal, pero nada del otro mundo, peeeero, el problema llego cuando quise instalar un Emulador de PS2 (la consola de videojuegos). El Emulador se llama PCSX2 y requiere de una Bios de PS2 para funcionar, no encontré ninguna para Linux por lo que se me ocurrió instalar Wine e iniciar el emulador en su versión para Windows que tengo en el back-up, ya con dicha Bios. Bueno, ahí el problema, no puedo bajar el Wine desde el Centro de Software, nada mas llega a reconocer el tamaño de la aplicación y no lo descarga, luego como a los 15 min sale el cartel que dice "Falló al descargar los archivos de paquetes. Compruebe su conexión a internet" Y en la pestaña detalles dice esto:
> Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/pool/main/f/fonts-unfonts-core/fonts-unfonts-core_1.0.3.is.1.0.2-080608-5ubuntu1_all.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/f/fonts-unfonts-core/fonts-unfonts-core_1.0.3.is.1.0.2-080608-5ubuntu1_all.deb) Connection failed 

Probé con 2 versiones distintas de Wine que aparecían en el buscador de aplicaciones y con todas paso lo mismo, también probé reiniciar la conexión y la PC, sin embargo no soluciono nada. Alguna idea de que ocurre? 

Disculpen si entre mucho en detalles pero fue para que entiendan mejor y ver si cometí algún error de mi parte. Espero que puedan ayudarme.

Saludos!

---

### Post by euzkoarima on 2012-05-08
Por lo que dice el error es un problema de conexión, que puede ser de tu lado, o del lado del repositorio.
Proba de cambiar el repositorio, por ejemplo al servidor principal.

Saludos
Eduardo

---

### Post by El Potro on 2012-05-24
> requiere de una Bios de PS2 para funcionar, no encontré ninguna para Linux por lo que se me ocurrió instalar Wine e iniciar el emulador en su versión para Windows que tengo en el back-up, ya con dicha Bios.

La bios es un archivo que termina en .bin. Es tan fácil como fijarse en la carpeta de este emulador de windows, buscar ese archivo .bin, y listo, usalo en el pcsx2 en Ubuntu.

Lo del problema para bajar paquetes de los repositorios: suele pasar. Probá como te dijeron con otra fuente o esperá un poco, suele solucionarse con el tiempo.

---

