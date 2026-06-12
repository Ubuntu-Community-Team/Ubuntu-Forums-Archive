---
title: "Problema al arrancar Ubuntu 9.10"
date: 2010-07-03
forum: Software
---

### Post by renekert on 2010-07-03
Estimados:
Sin que yo crea haber cambiado nada, mi laptop muestra, junto con el cuadro de "login", un cartel abajo que dice:
"Problema de instalación. No se ha instalado correctamente  la configuración predeterminada para el gestor de energía"
Tanto si espero que se cierre este cartel, como si lo cierro yo y continuo con el Login, la máquina entra en un ciclo y repite el cartel sin terminar de arrancar nunca.
El problema sigue siendo el mismo en cualquier Kernel anterior.
No se como usar bien el "recovery mode", pero el tratar de reparar paquetes rotos no resultó en ningún cambio.
No se como salir de este círculo ¿Podrán ayudarme?

---

### Post by biale on 2010-07-03
Lo unico que se me ocurre...
Provisoriamente y para intentar salir del ciclo editaria las sentencias del arranque normal del Grub añadiendo acpi=off.

---

### Post by renekert on 2010-07-04
Gracias Biale. No me siento seguro de saber como hacer lo que sugerís. ¿te molestaría darme algunos detalles o lugares donde buscar?
Gracias,
Renekert

---

### Post by guillermolisi on 2010-07-04
Lo primero que sugiero averiguar es si estas usando Grub 1 o Grub 2 ya que depende de la version el procedimiento a seguir.

---

### Post by renekert on 2010-07-04
Michas gracias Guillermolisi. Tengo Grub1.

---

### Post by elraulo on 2010-10-10
[COLOR=#000000][FONT=Times New Roman][FONT=Bitstream Vera Sans]Como va gente,
Necesito de su ayuda con un problema que tengo en notebook. Un dia me estaba andando re bien, despues cuando la encendi, me surgio este mensaje:
"No de ha unstalado correctamente la configuracion predeterminada para el gestor de Energia"
Y pongo la contraseña y pinta como que quiere entrar, pero vuelve a la misma pantalla.
Revisando he visto que esto le paso a mucha gente, algunos dicen que es un BUG, otros que se lleno la parte particionada en donde esta la configuracion del sistema, sin embargo no entiendo las soluciones que les dieron. Me reconozco ignorante.
Agradeceria que alguien si sabe como solucionarlo, me indique _paso por paso_, que debo hacer
Muchas gracias
El Raulo[/FONT][/FONT][/COLOR]

---

### Post by elraulo on 2010-10-10
Hola yo tambien tengo el mismo inconveniente, me podrian decir como hacer para solucionarlo.


Gracias.

---

