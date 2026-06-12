---
title: "Reponer permisos"
date: 2009-08-26
forum: Software
---

### Post by EnriqueK on 2009-08-26
El caso es que tenía una partición en FAT32 de unos 90 gigas, descidí respalñdar toda la información allí guardada y formatearla en EXT4 m los problemas empezaron al montar esta partición , lo hice en /media/E , estuve modificando los permisos entrando como administrador, logré nontarla, pero se me presentaron dos problemas uno es que en el directorio raíz / todas las carpetas presentan candados , o sea no tengo permisos de escritura como usuario , claro que eso no serñia novedad, de hecho así debe ser siempre, lo raro es que me muestre candados que antes no mostraba, pero esto no deja de ser un detalla estético si se quiere, pero no interfiere para nada en la operatoria del sistema. El otro problema es que muchas veces documentos generados en esa partición , lo hacen con root como propietario t además con el ya mencionado candado, voy zafando de este problema usando el comando 
sudo chown enrique:enrique -R /media/E
El mencionado comando solo es una solución temporal. por que al querer generar otro archivo, se presenta el problemam asñi que para zafar aú mas, al comando lo metí en algunos Scripts que ejecuto con frecuencia, pero al menos a mi no me convence esta solucuion xhapucera, quisiera algo definitivo, dejo la parte pertinente del **fstab**
#Entry for /dev/sda6 :
UUID=3dba5e6c-9533-4f38-8666-b1e330994906	/media/E	ext4	defaults	0	0
Utra cosa, también noté que se generó una papelera oculta dentro del directorio raiz / , la descubtí al notar que el espacio de / aumentaba sin motivos aparentes.
Resumiendo, lo que quiero es reponer los permisos de root y así dejarlo como debe ser y luego veré como hago para lograr el montaje adecuado.

---

