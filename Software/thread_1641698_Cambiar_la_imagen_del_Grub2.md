---
title: "Cambiar la imagen del Grub2"
date: 2010-12-09
forum: Software
---

### Post by diegolaboranti on 2010-12-09
Hola a todos, espero que puedan ayudarme. 
Quiero cambiar la imagen del grub2, para eso primero instalé unas imágenes con este comando

[COLOR="Red"]sudo apt-get install grub2-splashimages[/COLOR]

lo que me agregó imágenes en [COLOR="Red"]/usr/share/images/grub[/COLOR]
luego con el comando sudo gedit [COLOR="Red"]/etc/grub.d/05_debian_theme[/COLOR] traté de modificar la imagen en las líneas que están en negrita 

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="**/usr/share/images/desktop-base/moreblue-orbit-grub.png**"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

y allí pongo la dirección de una de las imágenes que instalé, hasta acá todo bien pero en cuanto quiero cambiarla por una mía que modifiqué con el gimp, la redimencioné a 640*480, le cambié la extención a .tga y la copié en la misma carpeta no lo hace, es más, toma al azar cualquier otra imagen o no pone ninguna.
La única diferencia que vi en las dos imágenes (la descargada y la mía) es que una pertenece al root y la otra a mí, ¿tendrá esto que ver?
Espero que puedan ayudarme. Gracias!:p

---

### Post by guillermolisi on 2010-12-11
Adecuale a tu archivo de imagen los permisos tal como estan los otros archivos (los descargados) de imagenes que usa el grub2.

---

