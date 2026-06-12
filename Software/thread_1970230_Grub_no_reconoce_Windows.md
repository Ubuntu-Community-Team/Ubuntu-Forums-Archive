---
title: "Grub no reconoce Windows"
date: 2012-04-30
forum: Software
---

### Post by ketzelleshelle on 2012-04-30
Instalé 12.04 junto a W7. 
Cuando en Grub voy a la opción de W7, en lugar de ir a este me vuelve a cargar el grub. 
Alguna ayuda o sugerencia? 
Muchas gracias.

---

### Post by guillermolisi on 2012-05-01
Ingresa en una consola/terminal de Ubuntu:```
sudo update-grub
``` Volve a iniciar y comentanos como resulto.

---

### Post by ketzelleshelle on 2012-05-01
> **guillermolisi said:**
> Ingresa en una consola/terminal de Ubuntu:```
sudo update-grub
``` Volve a iniciar y comentanos como resulto.

Gracias por la respuesta... no resultó.

Me sigue sucediendo lo mismo...

---

### Post by EnriqueK on 2012-05-01
Ejecuta
sudo -i
grub-mkconfig && grub-install /dev/sda  && update-grub
sto asumiendo que sda sea el DD en donde tienes instalado a windows

---

### Post by ketzelleshelle on 2012-05-01
> **EnriqueK said:**
> Ejecuta
sudo -i
grub-mkconfig && grub-install /dev/sda  && update-grub
sto asumiendo que sda sea el DD en donde tienes instalado a windows

No resulta... evidentemente algo hice mal cuando instalé?

Ninguna ayuda más para intentar resolver el problema?


-------------------------------------------------------------------------

Lo solucioné de la siguiente manera con Testdisk:

```
sudo apt-get install testdisk
   sudo testdisk
```

Luego:

```
 Primera pantalla:  Selecccionar "No Log" y luego presionar Enter.
  Segunda pantalla:  Seleccionar el disco duro que contiene la partición con Windows y elegir "proceed" .
  Tercera pantalla:  "intel"
  Cuarta pantalla:  "advanced",
  Quinta pantalla:  Seleccionar la partición de Windows y elegir "boot"
  Sexta pantalla:  "BackupBS"
  Séptima pantalla:  type "Y" to confirm
```

Luego presionar "q" varias veces hasta salir de testdisk.

Entonces Rebootee y pude entrar en Windows.

Luego volví a Ubuntu para hacer

```
sudo update-grub
```

---

