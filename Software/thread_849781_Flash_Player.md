---
title: "Flash Player"
date: 2008-07-04
forum: Software
---

### Post by ramiro_md on 2008-07-04
Muchachos ando necesitando el flash player para gusty, instale desde synaptic el paquete flashplugin-nonfree, pero algunas paginas me piden el flash player todavia =S...estuve buscando y no encontre ningun paquete para mi arquitectura (64 bits).Si saben donde lo consigo bienvenidos sean xD.Un saludo

---

### Post by leo_rockway on 2008-07-04
swfdec funciona con 64.

---

### Post by ramiro_md on 2008-07-05
AAun asi firefox me sigue pidiendo que instale el flash  player  =S

---

### Post by leo_rockway on 2008-07-06
¿Firefox te lo pide o alguna página en particular te lo pide?

---

### Post by ramiro_md on 2008-07-06
peginas en particulares..

---

### Post by leo_rockway on 2008-07-07
Eso pasa porque swfdec no es una implentación completa de Adobe Flash, porque se logró con ingeniería inversa (aunque ahora Adobe liberó las especificaciones). Si una página chequea qué versión de Adobe Flash tenés swfdec quizás informe que es equivalente a Adobe Flash 9.0.100 y la página puede requerir una versión posterior. Las opciones que tenés son:

0) Usar swfdec y aceptar que algunas veces no funcione.
1) Intentar usar Adobe Flash (que está sólo disponible para 32b). Sé que se puede hacer, pero no sé que tan bien funciona el resultado final.
2) Probar Gnash (yo probé swfdec y Gnash y me quedo con swfdec).
3) Cambiar a 32b e instalar Adobe Flash.

Tené en cuenta que Adobe Flash es una muy mala implementación de Flash porque consume muchísimos recursos. Por otro lado, Gnash y swfdec no son implementaciones completas, pero están trabajando para mejorarlas. En base a eso decidí que preferís hacer.

---

