---
title: "Dudas sobre compilar un kernel"
date: 2010-12-30
forum: Software
---

### Post by asterix77 on 2010-12-30
Cada vez que arranco mi sistema (Lucid AMD64), aparece el siguiente error por algunas milésimas de segundo.

[   26.983298] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)

Buscando por google se trataría de un bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843)

Mi sistema arranca en forma normal sin problemas, pero me ha sucedido en forma más o menos continua que cuando trabajo con alguna aplicación que requiere aceleración gráfica (tanto con compiz activado como no activado), esta se cierra al ejecutar alguna acción específica (exportar a PDF, vista previa, imprimir). Los mensajes de errores que muestra la aplicación tienen relación a este problema.

Leí por algún post que este error estaba fijado en un nuevo kernel. Revisando [www.kernel.org](www.kernel.org) ya está disponible la versión estable 2.6.36.2, y mi sistema está actualizado recién a la 2.6.32-27. Quisiera compilar el último kernel, uno por curiosidad, y lo otro a ver si de paso soluciono este pequeño inconveniente.

La consulta es (y creo que si) a pesar de compilar un kernel, los otros que están instalados se mantienen, porque tengo entendido que si un kernel tiene problemas al arrancar, simplemente se escoge otra versión y no debería haber problemas (¿o si?)

¿ es un proceso seguro?


Saludos

---

### Post by Carlos C on 2010-12-30
Hola. El kernel que tienes instalado no se perderá (a menos que tú lo borres voluntariamente). No debieras tener problemas por ese lado. Efectivamente, siempre puedes escoger con cuál iniciar el sistema. Si el nuevo kernel no apareciera en el menú de GRUB2 puedes ejecutar el comando:
```
update-grub
```para asegurarte que el archivo */boot/grub/grub.cfg* se actualice. No debes editar a mano ese archivo, en vez de ello puedes agregar entradas personalizadas al GRUB2 en el archivo */etc/grub.d/40_custom*.
Si al iniciar el sistema no puedes ver el menú prueba mantener presionada la letra SHIFT.

Puedes leer más información aquí:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Saludos.

---

### Post by asterix77 on 2010-12-30
Ok.

Gracias por responder Carlos

Me voy a animar a hacerlo entonces, pero ya será hasta el próximo año  [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG][IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG][IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

Hasta entonces les cuento.


Saludos

):P

---

