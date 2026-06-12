---
title: "Actualicé VLC 2.0, problema con mencoder"
date: 2012-02-25
forum: Software
---

### Post by nestord61 on 2012-02-25
Hola, soy usuario de Ubuntu 11.10 y  actualicé VLC a la versión 2.0 , a partir de ese momento no puedo subtitular archivos avi.
En una terminal pongo lo siguiente
"mencoder pelicula.avi -sub subtitulo.srt -oac copy -ovc lavc -o peliculasubtitulada.avi -subcp latin1 -subfont-text-scale 2.8"
y me responde esto
"mencoder: relocation error: mencoder: symbol ff_codec_bmp_tags, version LIBAVFORMAT_53 not defined in file libavformat.so.53 with link time reference"
Digo que es despues de actualizar porque antes lo hacia sin ningun problema.
Busque en google pero esta todo en ingles
Gracias
Nestor

img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by guillermolisi on 2012-02-27
Tal vez utilizando la ultima version de VLC, la 2.0.0-8, el tema este solucionado. Digo tal vez porque no probe si tu inconveneinte efectivamente se resuelve con esa version.

Me llamo la atencion que durante la ultima semana hubo varias actualizaciones de VLC, asi que estuvieron trabajando duro para solucionar algunos problemitas que, seguramente, estan documentados en el changelog del paquete.

---

### Post by nestord61 on 2012-02-27
Hola Guillermo, sigo participando, todo igual
Nestor
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by sebastianabate on 2012-03-04
Nestor, me parece que el problema que tenés es con la versión de libavcodec53 que está en el PPA del VLC 2; aparentemente tiene una incompatibilidad con la versión de mencoder que tenés instalada (fijate este bug en Debian [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=653887](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=653887), que es sobre mplayer, pero los dos están basados en el mismo código)

Las opciones que tenés a mi entender son tres:

1- Hacer downgrade del VLC para poder instalar una versión anterior de libavcodec53
2- Buscar algún ppa con una versión svn de mplayer que no tenga este problema (en el bug de Debian aclaran que en las últimas versiones svn el tema está solucionado, pero aparentemente es medio problemático hacer un backport)
3- Usar ffmpeg para agregarle los subs al avi, porque en el ppa del VLC2 está el paquete de ffmpeg que corresponde con el de libavcodec53

Espero que te haya servido esta data.

---

### Post by nestord61 on 2012-03-04
Gracias Sebastian, en la semana con un poco de tiempo me fijo, gracias nuevamente
Nestor

---

### Post by nestord61 on 2012-03-12
Sigo igual

img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

