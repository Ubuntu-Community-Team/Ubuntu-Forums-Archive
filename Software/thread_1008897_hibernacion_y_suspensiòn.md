---
title: "hibernacion y suspensiòn"
date: 2008-12-12
forum: Software
---

### Post by lucasfava on 2008-12-12
Alguien sabe como activar la hiberaciòn y la suspensión en ubuntu, en mi caso solo tengo en el menú gráfico apagar o reiniciar. Si tengo que meter mano en la terminal, recuerden que soy novato y de la terminal estoy en foja cero :popcorn:

---

### Post by sdennie on 2008-12-12
Capaz que la maquina tuya no puede usar hibernacion o suspension.  Igual, usa:

```

gconf-editor

```

Anda a /apps/gnome-power-manager/general y poner "can_suspend" y "can_hibernate".  Asi deben aparecer en el menu.

---

### Post by euzkoarima on 2008-12-12
mirate [este link]("http://ubuntuforums.org/showthread.php?t=329902&highlight=hibernate+command") que hablan justo de eso.

Saludos.
Eduardo

---

### Post by lucasfava on 2008-12-12
> **vor said:**
> Capaz que la maquina tuya no puede usar hibernacion o suspension.  Igual, usa:

```

gconf-editor

```

Anda a /apps/gnome-power-manager/general y poner "can_suspend" y "can_hibernate".  Asi deben aparecer en el menu.

Tienen que estar marcado con una v, o no tienen que estar marcado para que funcionen. :confused:
pues fui y estaban marcados con la v

---

### Post by sdennie on 2008-12-13
Capaz que el BIOS no lo tiene y Ubuntu sabe.  Que dice:

```

cat /proc/acpi/sleep

```

---

### Post by lucasfava on 2008-12-14
Lo de hibernar y suspender me lo pone ha la entrada pero no aparece cuando dejo de usar el S.O . :confused:

Una cosa mas, como puedo hacer para, entrar sin poner contraseña o usuario, pues mi viejo quiere probar el sistema, pero se quejo de que puse usuario y contraseña :popcorn:, pues el loco que empeso con el tema de probar esta escribiendo aca :lolflag:

---

### Post by Hei Ku on 2008-12-14
Por que no le creas un usuario a tu viejo? Asi el se puede personalizar su escritorio como quiera.

---

### Post by lucasfava on 2008-12-26
> **vor said:**
> Capaz que el BIOS no lo tiene y Ubuntu sabe.  Que dice:

```

cat /proc/acpi/sleep

```

me dice que no existe el fichero o directorio

---

