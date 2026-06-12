---
title: "Se corto la luz y ZAS!."
date: 2010-10-09
forum: Software
---

### Post by Cacique1 on 2010-10-09
Hola. El otro día estaba trabajando en Ubuntu 10.04 y de pronto se corto la luz eléctrica. Cuando volví a encender la PC y querer abrir cualquier programa de OpenOffice.org 3.2, me salía el siguiente mensaje:
   
  Otra instancia de OpenOffice.org está accediendo a su configuración personal o la configuración personal está bloqueada. 
  Un acceso simultáneo puede provocar incoherencias en la configuración personal. Antes de continuar asegúrese de que el usuario “cierre OpenOffice.org en el ordenador”.
  ¿Está seguro de desear continuar?.
   
  Como soy nuevo en Ubuntu, no quise continuar. Mis dudas son:
  1) ¿A qué se debe este problema y como se soluciona?.
  2) ¿Existe algún procedimiento a seguir cuando Ubuntu no se cierra adecuadamente (corte de luz, por ejemplo)?.
  Desde ya, agradezco cualquier respuesta.

---

### Post by alfplayer on 2010-10-09
Probablemente quedó mal algún archivo de OpenOffice, habría que corregir ese archivo. Hiciste la búsqueda en Google?

---

### Post by scrooge_74 on 2010-10-09
> **Cacique1 said:**
> Hola. El otro día estaba trabajando en Ubuntu 10.04 y de pronto se corto la luz eléctrica. Cuando volví a encender la PC y querer abrir cualquier programa de OpenOffice.org 3.2, me salía el siguiente mensaje:
   
  Otra instancia de OpenOffice.org está accediendo a su configuración personal o la configuración personal está bloqueada. 
  Un acceso simultáneo puede provocar incoherencias en la configuración personal. Antes de continuar asegúrese de que el usuario “cierre OpenOffice.org en el ordenador”.
  ¿Está seguro de desear continuar?.
   
  Como soy nuevo en Ubuntu, no quise continuar. Mis dudas son:
  1) ¿A qué se debe este problema y como se soluciona?.
  2) ¿Existe algún procedimiento a seguir cuando Ubuntu no se cierra adecuadamente (corte de luz, por ejemplo)?.
  Desde ya, agradezco cualquier respuesta.

Hola,

1) Open Office a veces da lata si se cierra mal, cuando reinicia trata de recuperar los archivos. Puede ser que en el /temp quedó algún lock file.

2) Método es que te compres un UPS barato y te ahorres los problemas. Porque el tema no es sólo que se va a luz y paf! te quedas a mitad de algo importante, es que al no tener una batería/regulador de voltaje las fluctuaciones o ese micro apagón empiezan a dañar tu PC, ya sea la fuente de poder o la misma placa madre y/o eventualmente el disco y la data. 

Una batería de USD 45 te ahorra como $150 a $250 en piezas de recambio eventualmente.

---

### Post by biale on 2010-10-10
Además, y si recuerdo bien, el punto debil del formato de archivos ext4 refiere justamente a los cortes de energía eléctrica.Pero si se tratara de una notebook y con la batería puesta ese problema potencial desaparece.

---

### Post by Cacique1 on 2010-10-14
Estimados ubunteros, gracias por sus respuestas. Aclaro que ya busque en Google y Bing, pero no encontre la respuesta. Y como soy novato en informatica, quisiera saber que es un lock file. :confused:

---

### Post by scrooge_74 on 2010-10-14
[http://www.gnu.org/s/libc/manual/html_node/File-Locks.html](http://www.gnu.org/s/libc/manual/html_node/File-Locks.html)

---

### Post by Cacique1 on 2010-11-24
Hola. Estimados amigos ubunteros, el problema era el lock file del que hablaba scrooge_74. Después de que lo borre, todo volvio a andar bien. También pido disculpas por el tiempo que tarde en responder, pero estaba en una zona que casi no tenia conexión a Internet. Hasta la proxima.

---

### Post by Cacique1 on 2010-11-24
Hola. Estimados amigos ubunteros, el problema era el lock file del que hablaba scrooge_74. Después de que lo borre, todo volvio a andar bien. También pido disculpas por el tiempo que tarde en responder, pero estaba en una zona que casi no tenia conexión a Internet. Hasta la proxima.

---

