---
title: "Dudas sobre KWin"
date: 2009-02-10
forum: Software
---

### Post by fgl82 on 2009-02-10
¡Buenas!

Estuve leyendo un poco acerca de Kwin y me picó el bichito de la curiosidad.

Por loque ví, KDE no se lleva bien con Compiz y Kwin se convertiría entonces en una opción mejor.

sin embargo, buscando en google "Compiz vs Kwin" no encontré nada y, por tanto, preferí venir a preguntar acá algunas cosas.

Veamos:

1) ¿KWin se basa en compiz? Porque vi muchos efectos similares: el cubo, la animación tipo "genio de la lámpara" para minimizar evntanas, etc.
2) ¿Cuál es más liviano?
3) ¿KWin es el compositing manager de KDE 4.2 o bien KDE 4.2 ya integra algún compositing por default?
4) Cualquier información extra sobre a KWin y diferencias a destacar respecto a Compiz será bienvenida

Disculpen las preguntas, sé que quizá varias podría googlearlas, pero estoy en el laburo ¡y la curiosidad ataca!:lolflag:

---

### Post by fgl82 on 2009-02-10
> **fgl82 said:**
> ¡Buenas!

Estuve leyendo un poco acerca de Kwin y me picó el bichito de la curiosidad.

Por loque ví, KDE no se lleva bien con Compiz y Kwin se convertiría entonces en una opción mejor.

sin embargo, buscando en google "Compiz vs Kwin" no encontré nada y, por tanto, preferí venir a preguntar acá algunas cosas.

Veamos:

1) ¿KWin se basa en compiz? Porque vi muchos efectos similares: el cubo, la animación tipo "genio de la lámpara" para minimizar evntanas, etc.
2) ¿Cuál es más liviano?
3) ¿KWin es el compositing manager de KDE 4.2 o bien KDE 4.2 ya integra algún compositing por default?
4) Cualquier información extra sobre a KWin y diferencias a destacar respecto a Compiz será bienvenida

Disculpen las preguntas, sé que quizá varias podría googlearlas, pero estoy en el laburo ¡y la curiosidad ataca!:lolflag:
Bueno me contesto solo que en el almuerzo pude buscar info:

1) no
2) no hay conclusión
3) es el window manager de KDE que le agregaron capacidades de compositing. No se desarrollo de 0 como Compiz sino que se le incorporó la funcionalidad.

---

### Post by Hei Ku on 2009-02-10
KDE no se lleva bien con Compiz porque su manera de ver los escritorios es diferente. Compiz se adapta bien a gnome porque usan paradigmas similares.
KDE habla de escritorios y Compiz de viewports. Podes encontrar varios flamewars al respecto de esto.

---

### Post by clasificado on 2009-02-11
En las épocas de kde 3.5 se usaba el paquete compiz-kde, que traia configuraciones específicas para matar a kwin y reemplazarlo por el equivalente compiz (emerald, creo). Compiz sobre KDE, por decirlo asi.

> 1) ¿KWin se basa en compiz? 
Nope. KWin y Compiz son iniciativas independientes que implementan el concepto de Compositing.

Al principio se los acusaba de estar duplicando el trabajo (y el código) ya que en cierto punto los dos estan implementando las mismas características de maneras incompatibles.

Por otra parte, el propósito puede ser el mismo (efectos de escritorio) pero las diferencias en la implementación hace que cada uno vaya por su lado: Compiz es bien independiente del sistema de escritorio, cuando KWin está aprovechando todas las características KDE.

clasificado

---

