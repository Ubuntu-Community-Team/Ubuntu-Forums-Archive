---
title: "Problema con flash y la pantalla"
date: 2011-04-09
forum: Software
---

### Post by nemodot on 2011-04-09
Hola gente, tengo el siguiente inconveniente al ver videos flash como desde youtube o cuevana. Luego de 15 minutos más o menos, la pantalla de mi monitor se oscurece como si se tratara del protector de pantalla.

Aunque lo configure para que se inicie una hora luego de inactividad esto me sigue ocurriendo, lo que no pasa cuando veo videos desde el VLC o cualquier reproductor de video.

Parece ser que no se trata del protector y que en realidad el problema proviene del monitor. No tengo idea como puedo evitarlo más que moviendo el mouse con un palo desde lejos.

Es como si el monitor comenzara a hibernar automaticamente, independientemente, y el boton de encendido comienza a parpadear.

---

### Post by juancarlospaco on 2011-04-10
No se si sea algo del Hardware, ...pero proba ejecutar:

**xset dpms force on**

y mira la Peli  :)

---

### Post by nemodot on 2011-04-10
Gracias, che, ahora lo pruebo y confirmo. 
Googlé el comando que me pasaste y me morí de risa con esta solución poco ortodoxa:


> I get this too and it's frugging annoying.

[COLOR="Red"]**The only thing I've been able to do is set up a small reservoir that drips water into a ballast tank that then uses a pulley system to slowly pulls a lead weight up over the keyboard and then drop it once the ballast gets to a certain weight (tipping the water into a secondary reservoir below)**[/COLOR]. 

For a while I thought I'd invented a perpetual motion machine until I remembered I have to fill the main reservoir up about once every few hours.

I'm sure a software fix would be easier. :(

Por cierto, en GNOME se puede resolver si vas a **Sistema -> Preferencias -> Gestor de Energía** y bajo "**Pantalla**" poner la pantalla en reposo si está inactivo durante: **NUNCA**

---

