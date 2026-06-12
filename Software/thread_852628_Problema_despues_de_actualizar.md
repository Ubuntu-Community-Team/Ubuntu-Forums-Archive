---
title: "Problema despues de actualizar"
date: 2008-07-07
forum: Software
---

### Post by pelex on 2008-07-07
Hola nuevamente.
Con mi Ubuntu recién estrenado después de una trabajosa instalación, me dispuse a llevar a cabo la actualización del mismo. Como la cosa venía medio lenta y se me hacía tarde para el trabajo, lo dejé trabajando solo. Cuando volví, alguien de mi familia (esposa o hijos), habían cerrado Ubuntu y estaban en Windows.
Reinicié la PC, arranqué en Ubuntu y cuando me dispuse a agregar algunas cosas me encontré con que el Gestor de paquetes Synaptic me daba el siguiente error:

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]


El mismo error me aparece con _Añadir y quitar aplicaciones_, y con el _Gestor de Actualizaciones_.

Como total novato que soy, no tengo ni idea de lo que hay que hacer.
Se agradece una manito.
Saludos :)

---

### Post by Mauro22 on 2008-07-07
Como te dice ahi!

[B]run 'dpkg --configure -a' 

[/B]
O sea, 

sudo dpkg --configure -a

---

### Post by pablo0469 on 2008-07-07
Cuando sufris interrupciones durante el proceso de actualizacion, justamente te pide que corras ese comando desde una terminal (Aplicaciones > Accesorios > Terminal). En esa ventaja tipeas:

sudo dpkg --configure -a
Escribis tu contraseña y listo, el sistema termina de actualizarse solito.

Saludos.

---

### Post by pelex on 2008-07-07
Ja, ja, que nabo ¿no?
Es justo lo que termino de hacer, como está en inglés me abataté y después me di cuenta de lo que decía y le dí padelante, incluso después del primer intento fallido puse "sudo" yo solito y salió. Cuando volví para decir que el problema estaba arreglado encontré tu respuesta, muchas gracias.
Me voy a tener que sacar de encima la costumbre de que en Windows por lo general las ayudas e indicaciones que te da el sistema casi nunca te sirven para algo, pero parece que en Ubuntu si.
Saludos :)

---

### Post by Mauro22 on 2008-07-07
La verdad que es medio estupido ese error. Tranquilamente tendria que ser medio automatico y pedirte la contraseña y ejecutarlo automaticamente.


:lolflag:

---

### Post by sdennie on 2008-07-08
> **pelex said:**
> 
Me voy a tener que sacar de encima la costumbre de que en Windows por lo general las ayudas e indicaciones que te da el sistema casi nunca te sirven para algo, pero parece que en Ubuntu si.


Jeje.  Es la verdad.  Con Ubuntu, si la maquina dice, "Please/Maybe run...", debés hacerlo.  ;)

---

### Post by feche_mza on 2008-07-08
***yo tube un error parecido despues de actualizar al hardy (ya lo solusione pero quiero apuntar a otra cosa) por que despues de actualizar se rompen algunos paquetes?? o se pierden,digo esto por que tive problemas con el firefox, que no me reproducia los videos de macromedia y estaba todo en ingles (ya los solusione a estos problemas) pero mi preguntas es por que borra esos paquetes que no son obsoletos???***

---

### Post by pablo0469 on 2008-07-09
Feche, en tu caso resulto fallida la actualizacion completa de la version de la distro, asi que te aconsejo hacer una instalacion limpia directamente desde un CD de Hardy.

Saludos.

---

### Post by faktorqm on 2008-07-12
Para mi esta bien que te lo diga pero que no lo haga automatico, por que muchas veces te pregunta que queres hacer, o que version borrar, como que te va tirando distintas opciones. Y ahi el user es el que elije digamos. Salu2!

---

