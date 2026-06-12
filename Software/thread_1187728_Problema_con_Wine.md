---
title: "Problema con Wine"
date: 2009-06-14
forum: Software
---

### Post by tinoq3 on 2009-06-14
Hola, los molesto para ver si alguien tiene idea de porque wine emite el siguiente error:

[I]fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x23
  Serial number of failed request:  9758
  Current serial number in output stream:  9758[/I]

Copié la carpeta del soft a ejecutar bajo wine en la carpeta *'Archivos de programa'*, me posiciono en ella y ejecuto *wine soft.exe* y arroja ese error...

Gracias y saludos.

---

### Post by josecuervo86 on 2009-06-15
Es con el único programa que te tira ese error? o te lo hace con otros tambien.
Por lo que se ve parece haber un problema con ALSA

---

### Post by tinoq3 on 2009-06-15
Me lo tira con varios, todos los que probé. Leí googleando que debía añadir la línea *“Audio”=”alsa”* dentro del archivo config de wine, pero el error continúa. Alguna idea?

---

### Post by josecuervo86 on 2009-06-15
Se me ocurre que no estas usando AlSA, puede ser? Anda a **Sistema > Preferencias > Sonido** y fijate cual esta usando como salida

---

### Post by tinoq3 on 2009-06-15
Te adjunto la ss :S

---

### Post by josecuervo86 on 2009-06-15
Y si probas cambiando en **pistas predeterminadas del mezclador** (abajo de todo) la opcion que tenes marcada (Pulseaudio) por otra? Te da alguna opcion? Esta alsa entre ellas?

---

### Post by leonardomdq on 2009-06-16
en pista predeterminadas del mesclador proba de ponerlo en  HDA ATI (alsa mixer) , nose si tendras esa opcion.

---

### Post by tinoq3 on 2009-06-16
OK, hoy cuando llegue pruebo y les aviso. De todas formas ya probé con otras opciones, no recuerdo bien cuales, y el resultado fue el mismo.

Más tarde edito y les comento. Gracias de ante mano.

---

