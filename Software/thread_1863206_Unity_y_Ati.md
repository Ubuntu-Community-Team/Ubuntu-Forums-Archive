---
title: "Unity y Ati"
date: 2011-10-17
forum: Software
---

### Post by Apipote on 2011-10-17
Hola a todos.

Hoy hice un "upgrade" de 11.04 a 11.10 y Oh sorpresa...!! luego de actualizar los drivers propietarios ATI me desaparecieron las barras y el panel lateral de Unity. No puedo hacer absolutamente nada. Solo se ve Nautilus. Hice todo los pasos de recover por la consola pero nada...
Lei que a varios les paso lo mismo pero no encontré ninguna solución.
Algún consejo...?
Gracias por adelantado.

---

### Post by fmsismo on 2011-10-17
Probaste entrar a unity2D?  Te anduvo eso?

Si eso falla, probaste entrar con el usuario visita?

Si eso anda (purga la configuración del compiz y volvé al default la configuración de unity):
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
unity --reset

---

