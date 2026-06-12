---
title: "Problema con Blender y Gutsy"
date: 2007-10-24
forum: Software
---

### Post by kk_furtiva on 2007-10-24
Hola gente, escribo para preguntar si alguien tiene el mismo problema q yo:

Blender, simplemente no funciona con Gutsy!!!

Estuve investigando bastante y vi q ya han cargado esto como bug en launchpad, pero no encuentro por ningun lado el motivo del error.

Segmentation fault (core dumped)

A alguien le sucede lo mismo? Es algo del driver open para ATI? 

Yo sospechaba q era mi placa de video (ATI Mobility Radeon M6 LY) ya que en Feisty tampoco funcionaba (bah,...funcionaba mal) cosa q se solucionaba utilizando la version Mesa Static. Pero en Gutsy no funciona ninguna version ni 2.44, ni 2.44static, ni 2.45, ni 2.45static. 

Alguna idea? Alguien conoce algun workaround?

Saludos y gracias...

---

### Post by leo_rockway on 2007-10-24
a mi blender me funciona y tengo ati, pero con los drivers propietarios (los libres no funcionan con mi placa) asi que quizas el problema ande por los drivers libres

---

### Post by GGsalas on 2007-10-25
A mi me funciona pero sólo en modo de pantalla completa, no se por que sucede eso. Tengo placa de video Nvidia FX 5200 con los drivers propietarios

---

### Post by JoACoV on 2007-10-25
> **GGsalas said:**
> A mi me funciona pero sólo en modo de pantalla completa, no se por que sucede eso. Tengo placa de video Nvidia FX 5200 con los drivers propietarios
Exactamente lo mismo... ***pero funciona***

---

### Post by leo_rockway on 2007-10-25
a mi me funciona en modo pantalla completa y en ventana.

---

### Post by m4v on 2007-10-30
que blender estás usando? el oficial de Blender o el que viene con los repos de ubuntu?

---

### Post by leo_rockway on 2007-10-31
el de los repos de ubuntu gutsy; es decir la 2.44 (dynamic) y no la 2.45

---

### Post by kk_furtiva on 2007-10-31
Yo estoy usando el 2.44 de los repos y el 2.45 y 2.45-static de blender.org.

Igualmente ayer jugando un rato descubri q si deshabilito DRI ([https://wiki.ubuntu.com/Bugs/AtiDriver](https://wiki.ubuntu.com/Bugs/AtiDriver)) el problema se soluciona. Asi q supongo q esto está relacionado a DRI...

Saludos

---

### Post by leo_rockway on 2007-10-31
yo tengo ati y no tuve que desabilitar dri para que funcione... que raro.

---

### Post by Offoffoff on 2007-11-02
I have the same problem with my Blender at IGP Radeon 345 in my laptop. How to solve it?

---

### Post by Katarozem on 2008-09-16
A mi tampoco me funciona el blender ni en fullscreem ni en windowed, tengo una tarjeta (o placa) ATI, supongo que con los driver  de propietario funcionara. pero si ya tengo los drivers libres, como hago para sustituirlos por los de propietarios!? O.o?

---

