---
title: "Dos ubuntu y un Xp es posible en un solo grub?"
date: 2009-02-19
forum: Software
---

### Post by david_mza on 2009-02-19
Buenas... tengo ubuntu funcionando sin problemas en una pc :D. Hay una persona que trabaja conmigo y quiere un usuario y obviamente me pone contento que quiera usar linux pero el problema es que le tengo que dar un usuario administrador y conociendolo se que va a empezar a instalar paquetes a loco y que tarde o temprano va a degradarlo o algo terrible va a pasar :???:... Pensé en instalarle otro ubuntu independiente para el en otro disco de la pc y manejarlo con el boot del bios. **La pregunta es si el grub es capaz de administrarme dos ubuntu en discos distintos para no utilizar el boot del bios, es decir como va reaccionar el grub si le instalo un sistema nuevo en otro disco (el ubuntu que funciona actualmente esta en un disco tambien con windows XP. ¿Se entiende? ¿Alguna sugerencia?**

---

### Post by guillermolisi on 2009-02-19
> **david_mza said:**
> Buenas... tengo ubuntu funcionando sin problemas en una pc :D. Hay una persona que trabaja conmigo y quiere un usuario y obviamente me pone contento que quiera usar linux pero el problema es que le tengo que dar un usuario administrador y conociendolo se que va a empezar a instalar paquetes a loco y que tarde o temprano va a degradarlo o algo terrible va a pasar :???:... Pensé en instalarle otro ubuntu independiente para el en otro disco de la pc y manejarlo con el boot del bios. **La pregunta es si el grub es capaz de administrarme dos ubuntu en discos distintos para no utilizar el boot del bios, es decir como va reaccionar el grub si le instalo un sistema nuevo en otro disco (el ubuntu que funciona actualmente esta en un disco tambien con windows XP. ¿Se entiende? ¿Alguna sugerencia?**
Si, Grub puede administrar los sistemas operativos tal como pensas, sin importar que sean dos Ubuntu y un XP.

Primero tenes que instalar XP (si aun no esta hecho) y luego cada uno de los Ubuntu que necesites.

Si alguno de los Ubuntu va en un disco fisico adicional, revisa que Grub grabe la informacion de booteo en el disco primario (donde esta el XP - supongo que sera disco 0 particion 0) asi no necesitas recurrir al F8 del BIOS (que podria ser una alternativa al multiple booteo via Grub).

---

### Post by david_mza on 2009-02-19
Muchas gracias!!! Funcionó perfecto, ahora voy a ver si lo oredeno un poco al grub para que se vea mas prolijo y entendible.

Saludos :P



> **guillermolisi said:**
> Si, Grub puede administrar los sistemas operativos tal como pensas, sin importar que sean dos Ubuntu y un XP.

Primero tenes que instalar XP (si aun no esta hecho) y luego cada uno de los Ubuntu que necesites.

Si alguno de los Ubuntu va en un disco fisico adicional, revisa que Grub grabe la informacion de booteo en el disco primario (donde esta el XP - supongo que sera disco 0 particion 0) asi no necesitas recurrir al F8 del BIOS (que podria ser una alternativa al multiple booteo via Grub).

---

