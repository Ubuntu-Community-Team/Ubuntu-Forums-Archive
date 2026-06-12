---
title: "Linux Kernel 2.6.28-14 en el gestor de actualizaciones"
date: 2009-07-28
forum: Software
---

### Post by aledruetta on 2009-07-28
¡Hola Comunidad!

No sé si fue pura casualidad, pero en el momento exacto en que activé el repositorio de Código Fuente para Medibuntu, me saltó el Gestor de Actualizaciones con esa versión del Kernel:
```
Linux Kernel 2.6.28-14
```
La que tengo en uso actualmente es la:
```
Linux Kernel 2.6.28-13
```
¿Qué me aconsejan? ¿Le doy OK.?

Gracias,
Alejandro.

---

### Post by rubioo on 2009-07-28
Yo recien la puse para instalar así que espero que este tudu bem :D

---

### Post by Luca_turicci on 2009-07-29
Lo instalé hace un par de horas, y hace 20 minutos que volví al 2.6.28-13, es que tengo problemas con el driver de alsa en mi HP Mini (110 1020la), revisé en la página y no hay una versión compatible todavía, pero espero que en estos dias la haya, en cuanto esté lista de seguro probaré el nuevo Kernel :D

---

### Post by harryscode on 2009-07-29
Hace una hora reinicié y hasta ahora funciona tudo bem.. tudo legal :).. esperemos siga asi

---

### Post by guillermolisi on 2009-07-29
El tema de actualizar o no la version del kernel esta muy relacionada con la configuracion de hardware que se tenga.

Como se ve, hay casos en donde la actualizacion no es funcional (caso mencionado respecto de la HP Mini) y en otros funciona sin problemas, tal vez porque es una instalacion mas standard al igual que el hardware que se usa.

De todas formas nadie te apura, Ale, asi que tomate tu tiempo, fijate que hardware "especial" podes tener y en funcion de eso y de las experiencias que veas por aqui, planifica la actualizacion.

Esto siempre y cuando no estes en una situacion en la cual la actualizacion sea practicamente obligatoria (algo que no funciona del todo bien, algo que no funciona y que la actualizacion resuelve, etc.)

---

### Post by EnriqueK on 2009-07-29
Tanto en Intrepid como en Jaunty, el reproductor Audacious no me reproducía sonido alguno, lo solucioné actualizando ALSA , el caso es que cuando hubo un cambio del kernel , se volvió a quedar sin sonido, así que tuve que volver a recompilar ALSA , sin embargo, esto no me pasó con esta última actualización del kernel y todo me funciona perfectamente.

---

### Post by rubioo on 2009-07-29
> Hace una hora reinicié y hasta ahora funciona tudo bem.. tudo legal .. esperemos siga asi

 También está todo bien hasta ahora :D

---

### Post by geekman91 on 2009-07-29
todo funciona a la perfeccion

---

### Post by aledruetta on 2009-07-29
Bueno, lo instalé, era como una papa caliente en la mano, no aguantaba más. Todo bien, aparentemente. Sólo tuve que recompilar el modulo del kernel de virtualbox, pero eso es normal cuando actualizo el kernel.

Gracias por los comentarios,
Alejandro.

---

### Post by leosr on 2009-07-29
> **aledruetta said:**
> Bueno, lo instalé, era como una papa caliente en la mano, no aguantaba más. Todo bien, aparentemente. Sólo tuve que recompilar el modulo del kernel de virtualbox, pero eso es normal cuando actualizo el kernel.

Gracias por los comentarios,
Alejandro.
Yo también, fuera de eso todo bien hasta ahora.

Saludos.

---

### Post by alberto71 on 2009-07-29
No aporto mucho, pero hasta ahora, la actualización me va de 10. 

Mi único problema persistente es JDownloader que no "gusta" de mi Nvidia 8600... problema que se mantiene en la nueva actualización de kernel 2.6.28-14 y con JDownloader 0.6.0193

---

### Post by oktubrer on 2009-07-29
No tuve problemas en una HP DV4-1413
Por momentos al apagarla le da un kernel panic y la termino apagando a manopla, pero no recuerdo si me pasaba antes de actualizar el kernel o no.
Todavía no me puse a ver el log para ver que pasa.

De todas formas me quedó una duda: ¿cuando actualizas el kernel, en el grub no siguen quedando las opciones para bootear con los kernels anteriores?
Porque en ese caso no habría problemas en actualizar, reiniciar y probar, ya que la vuelta atrás sería tan simple como elegir el kernel anterior en el grub.

---

### Post by aledruetta on 2009-07-29
> **oktubrer said:**
> De todas formas me quedó una duda: ¿cuando actualizas el kernel, en el grub no siguen quedando las opciones para bootear con los kernels anteriores?
Porque en ese caso no habría problemas en actualizar, reiniciar y probar, ya que la vuelta atrás sería tan simple como elegir el kernel anterior en el grub.

Sí, queda la opción de bootear con las versiones anteriores del kernel.

---

### Post by Luca_turicci on 2009-08-11
._. empiezo a pensar k soy el único al que le falla algo con este kernel nuevo... lo probaré de nuevo...

---

