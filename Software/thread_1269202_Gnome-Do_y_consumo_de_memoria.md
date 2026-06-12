---
title: "Gnome-Do y consumo de memoria"
date: 2009-09-17
forum: Software
---

### Post by alberto71 on 2009-09-17
Hola.

Desde hace un tiempo a ésta parte, utilizo Gnome-Do + Docky + Docklets en lugar de AWN por la practicidad de ejecutar cualquier programa con solo tipear las letras iniciales. Además, tiene un comportamiento bastante fluido y es muy agradable estéticamente.

Sin embargo, vengo notando desde el upgrade a la versión 0.82 que el consumo de ram se me va por las nubes, llegando casi a los 400 mb, lo que me parece excesivo este tipo de aplicación.

Uso 4 de applets: hora - clima - monitor de CPU y papelera de reciclaje mas 9 aplicaciones en el dock.

Alguien sabe si es posible mantener la funcionalidad del programa pero limitar su consumo de recursos? (o es todo culpa de Mono?)

Muchas gracias.

Nota: quienes usan Gnome-DO notaron que si lo sitúan en la parte superior no pueden mover las ventanas desde Expo?

---

### Post by juancarlospaco on 2009-09-18
Mono es un lenguaje lento, muy lento, puede ser por eso...
Pero hay mas Docks disponibles en los repos, usa el que mas se ajuste a tu gusto.

---

### Post by alberto71 on 2009-09-19
Gracias por la recomendación. La intención el post era ver si a alguien más le pasa esto o es que es un problema particular.

---

### Post by Mister X on 2009-09-19
yo tengo una version mas vieja de Gnome-do, ahora me está usando 18 Mb, tal vez tengas muchos plugins activos? o algun plugin en particular que tenga que usar mucha memoria


yo particularmente lo encuentro muuuuuuuy util y usable

---

### Post by alberto71 on 2009-09-24
Hola. Perdón en la demora para contestar.

Estoy probando eso precisamente ahora. Desactivé todos los plugins, no usaba muchos ni muy seguido. Luego desactivé los docklets y solo dejé la papelera. 

Al parecer el docklet de CPU es el que consume.Es un docklet muy útil porque con el color ya indica el consumo de CPU y Ram; además abre el monitor del sistema, es casi perfecto. Pero consume mucha memoria.

Igual, Gnome-DO sigue "escalando" el consumo de Ram, pero no llega de momento (y calculo que le tomará mucho mas tiempo hacerlo), a los exorbitantes 430 mbs :lolflag:

Gracias por la sugerencia.

---

### Post by emiliano_raso on 2009-09-25
Cuanto tenes total de memoria RAM?

Cuando era loquito de los entornos graficos y todos sus chiches usaba Cairo Dock:
[http://packages.ubuntu.com/intrepid/cairo-dock](http://packages.ubuntu.com/intrepid/cairo-dock)

Sinó, si queres ahorrar recursos porque tenes una maquina chompi y ejecutar aplicaciones con pocos pasos, yo uso ahora run commands de metacity.
Tengo todas las aplicaciones configuradas con <Shift>Fx donde x es el numero de cada una de las teclas funcion.
Si queres fijarte que onda:
1) Alt+F2
2) Tipeá "gconf-editor"
3) Desplegá "apps"
4) Desplegá "metacity"
5) En "global_keybindings" configuras las teclas de acceso rapido para cada "run_command"
6) En "keybinding_commands" elegís que hace cada cosa.

Espero que te sirva.

Saludos.

---

