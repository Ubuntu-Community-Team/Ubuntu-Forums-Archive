---
title: "problemas con Ubuntu 13.04"
date: 2013-05-20
forum: Software
---

### Post by Geero on 2013-05-20
.muy buenas, el asunto es que soy nuevo en todo lo que es linux, y leyendo me motive a empezar a ocupar ubuntu, la cosa esque he tenido unos problemas, como:
1°.- hice todas las actualizaciones pertinentes del sistema, pero en la consola(terminal) me aparece lo siguiente.

yo@esta_es_mi_Notebook:~$ sudoapt-get upgrade 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias        
Leyendo la información de estado...Hecho 
0 actualizados, 0 se instalarán, 0para eliminar y 0 no actualizados. 
2 no instalados del todo o eliminados. 
Se necesita descargar 0 B/27,5 kB dearchivos. 
Se utilizarán 0 B de espacio de discoadicional después de esta operación. 
¿Desea continuar [S/n]? s 
dpkg: error al procesarlibmjpegutils-2.0-0 (--configure): 
 el paquete libmjpegutils-2.0-0 no estálisto para configurarse 
 no se puede configurar (estado actual`half-installed') 
dpkg: problemas de dependencias impidenla configuración de gstreamer0.10-plugins-bad-multiverse: 
 gstreamer0.10-plugins-bad-multiversedepende de libmjpegutils-2.0-0; sin embargo: 
  El paquete `libmjpegutils-2.0-0' noestá instalado. 


dpkg: error al procesargstreamer0.10-plugins-bad-multiverse (--configure): 
 problemas de dependencias - se dejasin configurar 
No se escribió un informe «apport»porque el mensaje de error indica que es un mensaje de error asociadoa un fallo previo. 
                                          Se encontraron errores al procesar: 
 libmjpegutils-2.0-0 
 gstreamer0.10-plugins-bad-multiverse 
E: Sub-process /usr/bin/dpkg returnedan error code (1)

po lo visto no puede instalar algunas actualizaciones y queria ver que ocurre, para poder instalar estas actualizaciones


y lo 2°.- siento que ubuntu es mas lento el tiempo de respuesta del sistema (no en internet), y no se si realmente sea asi o sera la incompativilidad de mi laptop, y tambien en ocaciones al minimizar o cerrar las ventanas estas se frizean(no puedo hacer nada, aunque el puntero no se frezea) y para sacarlo devo apretar alt+tabular para desfrezearlo, y queria ver si podrian ayudarme que me gusta linux y no me gustaria volver al win7.

[B]mi laptop:

mi laptos es una HP Pavilion G4
6GB de memoria ram
targeta de video ATI Radeon HD 6320 (driver de ubuntu)
disco duro de 500GB

El sistema lo he instalado como amd64
le cree la particion (/) con 50gb
particion (swap)con 2gb
particion (/home) con el resto

Espero una respuesta, para poder ocupar linux correctamente, ya que como dije me ha gustado este SO.


[/B]

---

