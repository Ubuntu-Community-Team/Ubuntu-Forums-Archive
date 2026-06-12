---
title: "Quiero editar el grub dentro de WUBI. El archivo menu.lst dentro de /boot/grub no exi"
date: 2012-03-14
forum: Software
---

### Post by sonhadorpr on 2012-03-14
¡Saludos amigos Ubunteros!
Soy un novato, desde 2006 :-)
Acabo de instalar el Ubuntu 10.04.4 LTS 64-bit en "formato wubi" a una portátil.
Sony VAIO VPCEB490X
corriendo Windows 7 Pro 64 bit
Intel i3 Dual Core
6GB RAM
Blue-Ray
500GB HDD.
La situación es que dicha portátil es de mi esposa, y no quiero interferir con su Windows, por tanto pensé, que si algo le pasa al Windows, o al Ubuntu, es mejor hacer la instalación con WUBI, que se desinstala muy fácilmente en Windows, y no tiene problemas con el mbr y etc...

Eso fue lo que pensé, pero ahora, al haber instalado el Ubuntu (Wubi), me salen 2 menús al principio de el boot de la Vaio.
1, un menú que no había visto, que me pide escoger entre Windows 7 y Ubuntu, con un tiempo de espera regresivo de 10 segundos. Al escoger Ubuntu, me tira al GRUB menu tradicional, QUE SE SUPONE ESTÉ localizado en /boot/grub/menu.lst, pero allí no está.

Lo que quiero hacer es:
Editar el primer menú, para eliminar el tiempo...o bajarlo, a 1 ó 2 segundos.
¿Alguien sabe dónde se encuentra el archivo que tengo que editar para el primer menú?
Yo sé que editando el /boot/grub/menu.lst edito el menú segundo, pero...interesantemente, como mencioné arriba, dicho archivo no existe, DONDE SE SUPONE que esté.
¿Qué hago?
¡¡¡Gracias por su ayuda!!!
¡Bendecidos!

ROM

---

### Post by Patriciologico on 2012-05-17
sonhadorpr,

Hace tiempo que el Grub se edita en /etc/default/grub.

Despues de editar:

```
sudo update-grub
```

Saludos,

---

