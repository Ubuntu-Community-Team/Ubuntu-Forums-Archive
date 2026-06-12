---
title: "No puedo imprimir en red"
date: 2009-11-06
forum: Software
---

### Post by cajimas on 2009-11-06
Cuando instalo la impresora(brother 5240), conectada a otro equipo con xp sp3, me aparece un mensaje de "authenticacion" y me solicita nombre de usuario, nombre de red y contraseña...no entiendo a que se refiere...

---

### Post by Carlos C on 2009-11-06
> **cajimas said:**
> Cuando instalo la impresora(brother 5240), conectada a otro equipo con xp sp3, me aparece un mensaje de "authenticacion" y me solicita nombre de usuario, nombre de red y contraseña...no entiendo a que se refiere...

Hola cajimas. Por favor recuerda publicar tus dudas en el subforo adecuado. En caso de que tengas dudas puedes leer los [sticky]("http://ubuntuforums.org/showthread.php?t=1162708") que hemos dispuesto con la intención de clarificar lo que corresponde publicar en cada subforo. Procedo a mover este hilo a "Software".

En caso de dudas puedes leer [aquí]("http://ubuntuforums.org/showthread.php?t=1162750").

Respecto a tu problema, faltan datos así que tendré que suponer muchas cosas. Supongo que estás usando samba para conectarte con el equipo con xp. Si no tienes samba instalado [deberás hacerlo]("http://blockdeubuntu.blogspot.com/2008/07/cmo-configurar-samba-en-ubuntu.html"). Supongo que, después de configurar samba, lo que hiciste fue ir a Sistema -> Administracion -> Impresoras y escogiste "Impresora nueva". Luego elegiste la opción "Impresora de red" y seleccionaste "Impresora Windows (SMB)". Cuando te pide el nombre de usuario se refiere al login y el password del usuario de ubuntu que estas usando en esa sesión. Sobre el nombre de la red, me imagino que se refiere al nombre del grupo de trabajo, que si no lo has cambiado es "WORKGROUP" o "GRUPO_TRABAJO".


Saludos.

---

