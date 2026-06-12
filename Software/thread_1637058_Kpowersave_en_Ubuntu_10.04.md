---
title: "Kpowersave en Ubuntu 10.04"
date: 2010-12-03
forum: Software
---

### Post by donmatas on 2010-12-03
Estimad@s:

instalé la última versión disponible de [kpowersave (0.7.3-5) ]("https://launchpad.net/ubuntu/lucid/i386/kpowersave/0.7.3-5ubuntu1") en mi laptop Dell 1545 con Lucid Lynx. La ejecuté y configuré maravillosamente.
El problema es que al reiniciar el laptop el ícono característico aparece opacado y ya no son accesibles las funciones ni configuraciones del bendito gestor de energía de KDE. Adjunto un pantallazo para explicarme mejor.

¿alguna sugerencia?

gracias de antemano
DM

---

### Post by hectorivand on 2010-12-04
> **donmatas said:**
> Estimad@s:

instalé la última versión disponible de [kpowersave (0.7.3-5) ]("https://launchpad.net/ubuntu/lucid/i386/kpowersave/0.7.3-5ubuntu1") en mi laptop Dell 1545 con Lucid Lynx. La ejecuté y configuré maravillosamente.
El problema es que al reiniciar el laptop el ícono característico aparece opacado y ya no son accesibles las funciones ni configuraciones del bendito gestor de energía de KDE. Adjunto un pantallazo para explicarme mejor.

¿alguna sugerencia?

gracias de antemano
DM

Hola DonMatas... Proba algo, una vez que arranca el sistema y vez que te aparece opaco, suspende el equipo y volvelo a activar. A ver si aparece de vuelta habilitado.

Hay una extraña razón que algunas cosas, tipo control de brillo, volumen y demas relacionadas con la energía en Toshiba y Dell no funcionan si primero no suspendes el equipo.

Saludos
Nacho

---

### Post by donmatas on 2010-12-07
> **hectorivand said:**
> Hola DonMatas... Proba algo, una vez que arranca el sistema y vez que te aparece opaco, suspende el equipo y volvelo a activar. A ver si aparece de vuelta habilitado.

Hay una extraña razón que algunas cosas, tipo control de brillo, volumen y demas relacionadas con la energía en Toshiba y Dell no funcionan si primero no suspendes el equipo.

Saludos
Nacho

Gracias Nacho por la respuesta, 
te cuento que no me funciona que lo me propones. Sin embargo, sí funciona lo siguiente. Instalé el Xfce4-power-manager (que está a medio camino entre el patético gnome-power-manager y el fabulantásitco kpowersave) y lo puse como aplicación que arranca al inicio. Lo curioso es que si está corriendo el Xfce4PM y arranco el kpowersave funciona. Es más, si cierro el Xfce4PM y luego arranco el kpowersave, también funciona. El problema es que si lo pongo como gestor de energía por defecto, para que arranque junto con la sesión, no funciona.

agradezco cualquier ayuda u orientación

salud
DM

---

