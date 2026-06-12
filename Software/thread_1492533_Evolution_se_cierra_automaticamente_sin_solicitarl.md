---
title: "Evolution se cierra automaticamente sin solicitarlo"
date: 2010-05-24
forum: Software
---

### Post by renzo.martinez.friz on 2010-05-24
Estimados:

Hoy debi buscar un correo con una informacion especifica y este era de hace dos meses atras, cuando quise abrirlo el programa Evolution se cerro sin que se lo pidiera, pense que lo habia hecho por error, pero al reintentarlo... se cerro nuevamente.

Pense que, como me tenia acostumbrado Windows, con reiniciarlo se arreglaria, pero no fue asi, aun sigo seleccionando varios correos, tanto antiguos como los de hoy para poder leerlos y en muchos casos vuelve a cerrarse nuevamente.

¿A alguien le ha ocurrido esto? ¿Como pudo solucionarlo?  No puedo leer todos mis correos hoy.

No me habia ocurrido antes, corro con Ubuntu 10.04.

Saludos.

Renzo Martinez Friz

---

### Post by renzo.martinez.friz on 2010-05-27
> **renzo.martinez.friz said:**
> Estimados:
 
Hoy debi buscar un correo con una informacion especifica y este era de hace dos meses atras, cuando quise abrirlo el programa Evolution se cerro sin que se lo pidiera, pense que lo habia hecho por error, pero al reintentarlo... se cerro nuevamente.
 
Pense que, como me tenia acostumbrado Windows, con reiniciarlo se arreglaria, pero no fue asi, aun sigo seleccionando varios correos, tanto antiguos como los de hoy para poder leerlos y en muchos casos vuelve a cerrarse nuevamente.
 
¿A alguien le ha ocurrido esto? ¿Como pudo solucionarlo? No puedo leer todos mis correos hoy.
 
No me habia ocurrido antes, corro con Ubuntu 10.04.
 
Saludos.
 
Renzo Martinez Friz
 
Parece que no me queda otra que aplicar lo mismo que cuando tenía Windows, formateo y reinstalación de sistemas.

---

### Post by asterix77 on 2010-05-27
¿has intentado lanzar evolution desde la terminal?
 
#evolution
 
Si hay un error debiera mostrarlo en la terminal.
 
 
Saludos

---

### Post by renzo.martinez.friz on 2010-05-27
> **asterix77 said:**
> ¿has intentado lanzar evolution desde la terminal?
 
#evolution
 
Si hay un error debiera mostrarlo en la terminal.
 
 
Saludos
 
Nop.  No se me había ocurrido.  Lo peor es que ahora al seleccionar un correo, incluso de aquellos que antes sí podía leer, también se cierra, arroja un pantallazo negro y termina enviándome a la pantalla de ingreso de usuarios.
 
¿Me habré topado con el único virus de Linux?  ¿Como tanta "suerte"?

---

### Post by adux on 2010-05-28
a mi igual me paso, nunca sube bien que fue, lo tire de terminal y todo pero no me daba un error. lo solucione haciendo purge a todo evolution nomas y reinstalando :S despues de limpiar, talvez alguna paquete que no haya quedado bien o bug no se. pero se soluciono

---

### Post by Carlos C on 2010-05-28
¿"dmesg" no te entrega alguna pista?

---

### Post by renzo.martinez.friz on 2010-05-30
> **Carlos C said:**
> ¿"dmesg" no te entrega alguna pista?

Mi conocimiento es solo usuario, recién salido de Windows.  Aún es chino para mi...

---

### Post by asterix77 on 2010-05-31
dmesg es un comando que se corre en consola, simplemente lo digitas de la siguiente forma (sin el #), y luego lo pegas acá.

#dmesg | more

Lo que despliega es muy grande por lo que no cabe todo en la terminal, por eso se agrega lo de "| more".

Cuando hay algún tipo de errores generalmente aparecen acá.

¿no has intentado haciendo lo que sugirió adux?

#sudo apt-get remove evolution
#sudo apt-get purge evolution

Eso si, si tienes correo respalda la carpeta oculta  "/home/usuario/.evolution

Para ver las carpeta oculta ve a tu carpeta personal con nautilus (navegador de archivos por defecto), mantén apretado la tecla shift+H y la vas a ver.

y después 

#sudo apt-get install evolution

Una alternativa a evolution es thunderbird por si lo quieres probar.

Saludos

---

### Post by renzo.martinez.friz on 2010-06-01
> **asterix77 said:**
> dmesg es un comando que se corre en consola, simplemente lo digitas de la siguiente forma (sin el #), y luego lo pegas acá.
 
#dmesg | more
 
Lo que despliega es muy grande por lo que no cabe todo en la terminal, por eso se agrega lo de "| more".
 
Cuando hay algún tipo de errores generalmente aparecen acá.
 
¿no has intentado haciendo lo que sugirió adux?
 
#sudo apt-get remove evolution
#sudo apt-get purge evolution
 
Eso si, si tienes correo respalda la carpeta oculta "/home/usuario/.evolution
 
Para ver las carpeta oculta ve a tu carpeta personal con nautilus (navegador de archivos por defecto), mantén apretado la tecla shift+H y la vas a ver.
 
y después 
 
#sudo apt-get install evolution
 
Una alternativa a evolution es thunderbird por si lo quieres probar.
 
Saludos
 
Gracias, Asterix77 (y aprovecho de agradecer a todos).  Pero como no caché qué me quisieron decir con "Purge" y me seguía dando problemas, además que se demoraba casi un minuto en partir... opté por formatearlo y reinstalar el sistema 10.04 de nuevo.   (Me diplomé formateando Windows cientos de veces :P)
 
Pude respaldar el Evolution por la opción dentro del la sección "Archivo" del menú y lo reinstalé quedando OK una vez que ya había reinstalado.
 
El problema que me ocurrió fue que el Wifi de mi Compaq no se activó, pero después tuve que reinstalarle los "drivers" propietarios y también se arregló.
 
No sé si Adux se refiera a lo mismo, pero ahora recuerdo que hace algunas semanas utilicé un comando de limpieza, pero asumí que era similar a programas de mantención que utilizaba anteriormente donde, por ejemplo, borraba los archivos temporales de internet, *.tmp, que quedaban al utilizar algo en Windows... quizás en realidad estaba eliminando programas instalados y en eso eliminé algún componente de Evolution que generó los problemas subsiguientes.
 
Por favor, no crean que soy "vaca" en hacerles perder el tiempo en responderme, sólo que tuve que hacerla corta porque dependo bastante del email y no sabía como arreglarlo.  Les estoy muy agradecidos a todos por su ayuda.
 
(Quizás este tema no deba ser marcado como solucionado, por cuanto fue media Tarzanística la solución y, finalmente, salvo para mí, no creo que sea una solución válida para el resto que pudiera tener el mismo problema).

---

