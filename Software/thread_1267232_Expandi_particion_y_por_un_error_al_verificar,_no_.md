---
title: "Expandi particion y por un error al verificar, no actualizo espacio para utilizacion"
date: 2009-09-15
forum: Software
---

### Post by crynof on 2009-09-15
Hola como estan?
Miren, quize expandir la particion de mi ubuntu con el gparted desde el Live cd, le saque un poco de espacio a una particion NTFS y se al agregue a la ext2, entonces, el gparted empezo a mover las particiones y redimensionarlas, pero ya cuando quedaba el ultimo proceso en la parte donde verificaba, dio error, pero la particion NTFS si se redujo, y la EXT2 si se expandio, solo que la muestra como si tuviese el mismo espacio que antes, y no me deja utilizar el resto, y esto lo sé por que en el Gparted del Livecd, si me muestra la particion EXT2 de 10gb, con 6GB utilizados, y antes esa particion era de 6GB con 6GB utilizados.
Al utilizar ubuntu, me aparecen los 6GB de antes y los 4GB q se expandio no los actualizo.

Alguien sabe como hacer de que la particion actualize su espacio nuevo?, por q por lo visto no actualizo el espacio final.

Espero que puedan ayudarme
Saludos y muchas grax

---

### Post by Carlos C on 2009-09-16
Hola, una posibilidad es que uses testdisk. Está en los repositorios así que lo puedes instalar con apt-get. Es bastante intuitivo y no debieras tener problemas para usarlo. puede trabajar con particiones ext2 y ntfs.

Saludos.

---

