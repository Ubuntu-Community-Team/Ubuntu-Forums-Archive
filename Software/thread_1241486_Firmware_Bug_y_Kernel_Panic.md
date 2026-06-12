---
title: "Firmware Bug y Kernel Panic"
date: 2009-08-16
forum: Software
---

### Post by FB91 on 2009-08-16
Hace un rato pude hacer andar internet en mi Kubuntu (gracias a Hei Ku) y ni bien pude hice lo que dice este tutorial [http://tuxarena.blogspot.com/2009/08/how-to-install-kde-43-in-ubuntukubuntu.html](http://tuxarena.blogspot.com/2009/08/how-to-install-kde-43-in-ubuntukubuntu.html) para agregar los repositorios para tener KDE 4.3 

Después hice un sudo apt-get update y luego sudo apt-get upgrade

Una vez finalizado con éxito reinicio la PC y...

:shock: :shock: :shock: 

Luego del grub, cuando aparece la pantalla negra que dice Starting up...
debajo sale un mensaje de este estilo:

[    0.004000] ACPI: Aborted because bad gzip magic numbers
[    2.762482] [Firmware Bug]: powerow-k8: Your BIOS does not provide ACPI_PS objects in away that Linux understand.
[    2.8864174] Kernel panic - hot syncing: VFS: Unable to mount root on Unknow block (0,0)

Intento entrar desde el Recovery modo y no puedo, sale un mensaje como el anterior y no puedo teclear nada.

Lo primero que pienso es: SE MURIO! 

¿Estoy errado?

---

### Post by Hei Ku on 2009-08-16
proba poner en la linea del boot las opciones:

noapic nolapic

---

### Post by FB91 on 2009-08-16
ingreso al setup de la bios pero no encuentro nada para "meter codigo"

Leí por internet que para modificar el boot.ini hay que acceder al primer disco rígido, y que éste archivo está oculto. Pero como dije antes lo único que puedo hacer es entrar al menú de la bios (apretando Supr. al inicio)

EDIT: Ya entendí como poner  eso del noapic nolapic en este comentario [http://ubuntuforums.org/showpost.php?p=3831313&postcount=4](http://ubuntuforums.org/showpost.php?p=3831313&postcount=4) pero igualmente sigue sin andar, salen los mismos errores

---

### Post by Hei Ku on 2009-08-16
Cuando te aparecen las opciones para arrancar, las de los kernels, fijate que abajo te dice que tecla apretar para editarla

No es en la BIOS, ni en el boot.ini (que es de windows)

---

### Post by FB91 on 2009-08-16
Cuando me aparecen las opciones para arrancar me dá 2 opciones (aparte del enter, claro), presionar la letra C que sale la línea de comandos... en la que se vé:

grub>

y la E que la verdad nose bien que hace, a las opciones que tengo para elegir como que les cambia el nombre... ni idea, para mí que es la C la que tengo que apretar... 

Entonces, una vez que presiono la C, en la línea de comandos escribo noapic nolapic y me muestra este error, diciendo que no reconoce el comando: Unrecognized command

en que le estoy errando?

---

### Post by Hei Ku on 2009-08-16
Tenes que apretar la e, para editar la linea de booteo. Despues tenes que apretar de vuelta la e, y elegis la linea que tiene el kernel.
Al final de esa linea agregas noapic nolapic

Despues apretas b para bootear.

---

### Post by FB91 on 2009-08-16
Ya lo hice, y ahora me tira otros errores.

ACPI: Aborted because bad gzip magic numbers
BIOS bug, Local APIC #0 not detected!
...forcing use of dummy APIC emulation (tell your hw vendor)
powernow-k8: BIOS error_ no PSB or ACPI _PSS objets
y también lo del kernel panic

---

### Post by sergiom99 on 2009-08-16
Y que hardware tenes?

Cuando estas en el GRUB, eligiendo los kernels mas viejos que aparecen debajo de todo, podes bootear normalmente?

---

### Post by FB91 on 2009-08-16
tengo una MB Asus M2N68 / AMD 8650 Phenom x3 / 4 GB RAM / 320 GB HDD / NVIDIA GeForce 9500GT / 19" AOC
> 
Cuando estas en el GRUB, eligiendo los kernels mas viejos que aparecen debajo de todo, podes bootear normalmente?

cuando estoy en el GRUB tengo 3 opciones, al que entro normalmente, el de recovery mode y otro que si mal no recuerdo dice algo de "otro sistema operativo" (?)

---

### Post by FB91 on 2009-08-16
esto que me sucedió pudo haber afectado a mis archivos del /home ? porque de última instalo de nuevo kubuntu

---

### Post by Hei Ku on 2009-08-16
No, no los afecta.

---

