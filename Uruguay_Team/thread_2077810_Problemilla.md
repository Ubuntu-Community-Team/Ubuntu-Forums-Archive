---
title: "Problemilla"
date: 2012-10-29
forum: Uruguay Team
---

### Post by dalepo on 2012-10-29
Buenas a todos, soy nuevo en el tema de Ubuntu, no tengo mucha idea y quiero aprender.

Instalé Ubuntu 12.04 desde un live CD. En el disco duro tengo 2 particiones, una para windows 7 y otra para para las cosas que bajo, instalaciones, etc. Cuando comencé a instalar Ubuntu booteando desde CD, instalé de la forma "Algo más". Creé 2 particiones de más, una para el "swap" (8 gigas), y otro para el S.O. (15 gigas aprox). 

El problema es que no me carga el grub, me inicia por predeterminado el Windows 7 y no me da la opción para cargar Ubuntu. Intenté instalar grub siguiendo una guía ( [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB) ), pero sigue igual. También bajé wingrub pero no sé como usarlo bien.

Cualquier ayudita se agradece mucho.

Saludos

---

### Post by jerrrys on 2012-10-29
Si se trata de un problema de comida, trate de reparar yannubuntu arranque. Es muy fácil de usar.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Además, no es necesario instalar manualmente partitons. Usted puede elegir la opción de instalación lateral lado y esto también va a crear la partición swap.

Este anuncio ha sido traducido por google.  :)

---

### Post by danielmato on 2012-11-05
Con la respuesta de Jerry, seguro se te complica el panorama, muy buena onda, pero el traductor de G... todavía deja que desear.

Antes que nada una pregunta ¿8 gb de swap? es una locura, 4 es el máximo necesario, de ahí para arriba, es desperdicio de disco.

Normalmente, la recomendación para un novato es, dejá que el instalador de Ubuntu se haga cargo.

En el caso del 12.04 dice clarito, instalar junto a win... dejá que el haga particiones, que le salen bárbaras.

Y sino, si te gusta tocar, y sabés por dónde vas.

Inicias el live.

Buscás en el Dash el gParted (herramienta de discos), y desde ahí y en forma gráfica, editas las particiones.

Recomendación, achicás la partición de win, y dejás el espacio que quieras usar en Ubuntu sin particionar.

Cerrás la aplicación.

Dos clic a instalar Ubuntu, y a instalar.

Si querés cuando llegás a la parte de particiones, podés dar clic en "algo más" ahí vas a ver una partición ntfs, esa no la toques, es win, y otra que dice espacio libre, arrancá a hacer ahí particiones.

No te olvides que como mínimo necesitas hacer 3 particiones-

1 - 4 gb - area de intercambio
2 - 15 a 20 gb - ext4 - / (raíz del sistema)
3 - resto del disco - ext4 - /home.

Cualquier cosa, chiflá y vemos como darte una mano.

Saludos

---

