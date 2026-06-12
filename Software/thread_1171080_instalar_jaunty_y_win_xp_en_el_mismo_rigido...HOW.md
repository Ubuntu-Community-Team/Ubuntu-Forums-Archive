---
title: "instalar jaunty y win xp en el mismo rigido...HOW?"
date: 2009-05-27
forum: Software
---

### Post by leonardo83 on 2009-05-27
Buenas, se que seguro ya se habra hecho un thread sobre esto pero no lo pude encontrar.

Tengo un rigido sata de 320 Gb donde instale recien win xp (por cuestiones que mi vieja quiere aprender a usar la compu y bueno, quiere emezar con windows), a esto quiero instalarle una particion para Jaunty, es decir, coo muuucho le dejaria 30 gb para windows y el resto para Linux jeje, lo que no se hacer es la particion, llego al paso de donde elijo particion manual pero despues no se que hacer, en un lugar lei que habia que descontar 5gb de lo que estaba en windows :(.
Es decir, para que se entienda, me gustaria tener por ejemplo 30 gb o 50 gb que se mantengan para windows, y el resto (casi casi 280 gb) todo para Jaunty.
Alguien me diria como lo particiono? me pierdo con eso de ntfs, swap o lo de la parte "/".
Cualquier ayuda bienvenida sea, gracias!

;)

---

### Post by staar on 2009-05-27
la forma más fácil es instalar windos en una partición del tamaño que quieras (vos querés 30 Gb? bueno dale) y dejar el espacio destinado a ubuntu como espacio libre sin particionar...

después, en el instalador de ubuntu, seleccionar para que haga el particionado automático en el espacio libre (creo que la opción dice algo así como 'Usar espacio libre')

si ya creaste una partición para windos, que ocupa todo el disco, y no tenés ganas de volver a instalar windos, con el Editor de particiones del livecd (Sistema > Administración) podés achicar esa partición, y dejar el espacio libre destinado a ubuntu sin particionar...

saludos

---

### Post by leonardo83 on 2009-05-27
gracias!!
mira, entre en paticiones y como espacio para win deje 40000 (Mib)
en donde dice espacio libre precedente escribo algo o ya elijo "redimensionar" ?
perdon, es que no quiero hacer macana :(

Gracias y espero respuesta

---

### Post by staar on 2009-05-27
arriba tenés una representación en forma de barra del disco, con el mouse agarrá la parte derecha y correla hacia la izquierda, hasta que la partición quede del tamaño deseado, con espacio libre precedente 0 y espacio libre posterior igual al espacio que le querés dejar a ubuntu, después poné redimensionar, y luego aplicá los cambios (el cambio no se hace hasta que no pones 'Aplicar' en la barra principal del editor, no te hagas drama)

saludos

---

### Post by leonardo83 on 2009-05-27
> **staar said:**
> arriba tenés una representación en forma de barra del disco, con el mouse agarrá la parte derecha y correla hacia la izquierda, hasta que la partición quede del tamaño deseado, con espacio libre precedente 0 y espacio libre posterior igual al espacio que le querés dejar a ubuntu, después poné redimensionar, y luego aplicá los cambios (el cambio no se hace hasta que no pones 'Aplicar' en la barra principal del editor, no te hagas drama)

saludos

ok ok hasta ahora va todo bien.
Mira me quedo win con 31.9 b y dice free space 259 gb
ahora para instalar en todo elresto jaunty elijo "usar el mayo espacio libre continuo" o "manualmente"  ? :(



gracias por la ayuda

---

### Post by staar on 2009-05-27
"usar el mayo espacio libre continuo" y sale con fritasss....

saludos

---

### Post by Tosh78 on 2009-05-27
La otra que podes hacer es particionar 8GB para / en ext4.
Con respecto a la swap dependiendo de cuanto tenes de ram deberias asignar el doble de la ram si tenes menos de 1gb (si tenes 256 de ram, la haces de 512, si tu ram es 512, entonces 1gb). Si tenes 1gb, la dejas de 1gb, y si tenes mas de 1gb, le asignas la mitad de la ram (si tenes 2gb de ram, le asignas 1gb). No se si alguien tendra algun comentario mejor sobre esto, pero siempre lo use asi y funciono perfectamente.
El resto lo dejas para /home en ext4.
Cualquier cosa pregunta.

---

