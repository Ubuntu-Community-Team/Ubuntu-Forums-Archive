---
title: "duda instalar ubuntu con windows xp"
date: 2009-06-07
forum: Software
---

### Post by pennyhume on 2009-06-07
bueno..yo ya estuve dejando algunos mensajes por ahi con algunos problemitas que tenia, debido a que soy nueva en ubuntu...

ahora tengo una duda, distinta..tenia instalado ubuntu con wubi desde windows, y por diversas cuestiones, formatie windows, volando tambien ubuntu...reinstale windows ahora..y queria reinstalar ubuntu, pero me gustaria no hacerlo con wubi, sino en una particion o maquina virtual..la pregunta es...que me recomiendan?

y algunas otras dudas...

- si yo tengo una particion con windows y otra con los archivos y documentos..necesito una tercera para ubuntu?

-si lo instalo en una particion como hago para que me reconozca los archivos de un sistema a otro como hacia con wubi? es automatico?

-si lo instalo en una maquina virtual, como hago para que me reconozca archivos de uno a otro..es automatico??

---

### Post by sajnox on 2009-06-08
> **pennyhume said:**
> que me recomiendan?

Lo mejor es instalarlos por separado y que Ubuntu no dependa de windows, pero si por ahora te sentis mas comoda con Windows wubi es mas que una buena opcion, no creo sinceramente que puedas notar perdida de rendimiento en el equipo, lo digo por lo menos desde mi experiencia de uso

y algunas otras dudas...

> - si yo tengo una particion con windows y otra con los archivos y documentos..necesito una tercera para ubuntu?

Si, la necesitas. En realidad necesitas dos mas ya que la primera es para la particion donde instalas el sistema y la otra es para el swap (normalmente no usa mas de 1gb y te lo hace automaticamente el sistema)

> -si lo instalo en una particion como hago para que me reconozca los archivos de un sistema a otro como hacia con wubi? es automatico?

No pero casi, lo mejor y mas simple es darle desde la instalacion el punto de montaje, sino lo haces ahi despues a mano a mano lo podes hacer y es muyy simple

> -si lo instalo en una maquina virtual, como hago para que me reconozca archivos de uno a otro..es automatico??

mmmm, a mi no es la opcion que mas me gusta. Si pensas usar ubuntu a diario la MV es medio boba y tiene algunas limitaciones en cuanto a la parte grafica y respecto a compartir archivos no es automatico pero no es para nada dificil

---

### Post by Tosh78 on 2009-06-08
Sajnox, me parece que se referia a si instalarlo en VM o directo en otra particion.
Con respecto a cual opcion de estas, mi recomendacion es que uses una particion. Como bien dijo Sajnox, con la maquina virtual vas a tener bastantes limitaciones.

---

### Post by josecuervo86 on 2009-06-08
A pesar de las limitaciones, crear una maquina virtual es un buen metodo para probar un SO sin modificar absolutamente nada. Pero al igual que mis compañeros, recomiendo la instalación en una partición aparte.

---

