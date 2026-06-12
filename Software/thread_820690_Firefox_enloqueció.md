---
title: "Firefox enloqueció"
date: 2008-06-06
forum: Software
---

### Post by fgl82 on 2008-06-06
Gente tengo un grave problema.

No sé si habrá sido luego de los upgrades de kernel que llevó a cabo hardy ayer, pero firefox directamente se volvió loco!

Les explico los signos del enfermo:

1) En la barra de direcciones no aparece la direccion del sitio que está siendo explorado, sólo lo que yo escribo queda ahí.
2) El plugin de "firegestures" dejó de andar. Al ejecutar cualquier gesture dice en la barra de estado: Gesture Failed: DR (TypeError: gPrefService is null)
3) Las pestañas quedan con la animación de "cargando" aún después de haber completado la carga de la página
4) No aparece más la barra de progreso de carga de los sitios en la barra de estado

¡¡¡No entiendo nada!!!

¿A alguien más le pasó esto?

---

### Post by clasificado on 2008-06-06
porahi se te rompió el perfil. ¿Probaste iniciando un perfil nuevo?

clasificado

---

### Post by fgl82 on 2008-06-06
uhhh no pero no tenia ganas de hacer semejante lio....

porque en un perfil nuevo netbeans por ejemplo no me aparece instalado... tengo que crear yo el acceso... y... aplicar los temas de vuelta y... llevarme todo del home al otro home y..... pufffffffffffffffffffff!!!! :lolflag:

lo que si, voy a probar con uno que ya tengo creado de antes a ver como funciona, gracias por la idea!

---

### Post by fgl82 on 2008-06-06
uhh si tal cual, en el otro perfil me anda!!! :S

pucha que lo tiró... y bueh, será cuestión de crear uno nuevo.......

gracias...

---

### Post by clasificado on 2008-06-06
> **fgl82 said:**
> 
pucha que lo tiró... y bueh, será cuestión de crear uno nuevo.......

Mirá que no me refiero a otro usuario de ubuntu eh!!!

Es que Firefox tiene su propio sistema de perfiles.

Probá ejecutando en una consola

```
killall firefox-bin
./firefox -profilemanager
```

El primero es para cerrar el firefox, el segundo para abrir el profilemanager. Con eso podes crear un nuevo perfil sin cambiar el usuario

clasificado

---

### Post by fgl82 on 2008-06-06
uh barbaro!!!no saqbia eso, gracias!

me voy a fijar y te aviso. :D

gracias!!!

---

### Post by fgl82 on 2008-06-06
sos un capo, borré el default profile, lo creé de vuelta y listo. 

gracias! Eran errores tan raros y todos juntos que ya no sabía qué hacer! 

:D:D:D:D:D:D

---

