---
title: "bugs kde"
date: 2009-02-04
forum: Software
---

### Post by tsueseres on 2009-02-04
he encontrado varios bugs en el escritorio de kde, de los cuales creo que muchos ya se han dado cuenta pero quiero postearlos para que me ayuden a resolver los que no he resuelto


1.cuando se abre en una terminal
sudo dolphin y luego se cierra, despues de eso al brir cualquier otra carpeta aparece problemas de permisos 

este se puede resolver con este comando,
cd /home
sudo chown -R name:name name (where username is you username, ofcourse :) 

 pero deja el problema principal de que volvera a pasar lo mismo si se vuelve a correr sudo dolphin

2.no se como surgio este pero cuando copeo un documento del escritorio a una unidad ntfs que tengo montada me aparece que no se pudieron cambiar los permisos, creo que es por el fstab, para corregirlo puse esto enseguida de la unidad a montar con problemas, pero tengo la duda de si paso este problema por haber corrido sudo dolphin

3.cuando se corta una cosa del escritorio a otra parte nunca se corta enverdad, solo se copea, repito esto solo pasa en el escritorio, y no he podido encontrar como arreglarlo

si me pueden ayudar con estos problemas

---

