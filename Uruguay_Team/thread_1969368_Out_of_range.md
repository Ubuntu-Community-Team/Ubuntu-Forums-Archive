---
title: "Out of range"
date: 2012-04-30
forum: Uruguay Team
---

### Post by xGrp on 2012-04-30
Buenas gente, actualice a la version 12.04 y me encontre al reiniciar con la pantalla negra sin posibilidad de elegir que SO arrancar (en realidad no  vemos los caracteres pero están allí)

si alguno le pasa lo mismo la solución que encontré fue

una vez que arranca Ubuntu editamos el archivo de configuración del grub


$ sudo gedit /etc/default/grub


descomentamos la linea (quitando el #)


GRUB_GFXMODE=800x600


por defecto aparece 640x480
yo le puse 800x600

guardan los cambios y actualizan el grub


$ sudo update-grub


reinician y a mi al menos me funciono de maravilla

otro problemita que tuve luego de actualizar fue que mi escritorio ya logeado en ubuntu estaba completamente negro

lo solucione saliendo a la ventana de login con ctrl+alt+sup
luego elegi Ubuntu 2D y ya andaba normal de nuevo supongo que sera un tema de mi tarjeta grafica

bueno si algún novatillo como yo le sucede así solucione el tema
saludos

---

