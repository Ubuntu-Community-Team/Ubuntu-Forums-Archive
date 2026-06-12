---
title: "No puedo ni actulizar mi ubuntu a la 10.04 ni hacer una instalación nueva"
date: 2010-05-03
forum: Software
---

### Post by Jeivo on 2010-05-03
hola a todos, en primer lugar me presento, soy Jeivo y soy nuevo en este foro.

Os comento mi problema. Resulta que yo tengo ubuntu 9.10, pues bien, cuando intenté actualizar, me da fallo en el paso de instalación cuando faltan unos 14 minutos.

Intenté hacer una copia nueva (ya que me fastidió lo que tenía al intentar actualizar), y cuando voy a hacer una copia nueva, cuando llega a la parte de las particiones, no me detecta ninguno de los dos discos duros que tengo.

En resumen, que no tengo manera de pasarme a la 10.04. Lo he intentado ya varias veces y nada.

¿saben que puedo hacer?

Un saludo y muchas gracias.

---

### Post by clasificado on 2010-05-03
Bienvenido!


**¿Será que podés agregar las especificaciones de tu pc?**

CPU, discos, si tenes Ventanas y Ubuntu va al lado, memoria, etc.

si sabés que discos tenés, mejor (sata o ide).

**Por lo que veo, **todavía tenés una combinación más para probar: [actualizar con el CD ALTERNATE]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

- El cd Live te sirve para instalar desde cero desde el cd y probar el operativo, pero no actualizar desde el cd

- el [cd Alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") podés hacer una actualización de un ubuntu preexistente e instalar desde cero, pero no podés probar el operativo

Bajate el alternate del 10.04 y ponelo con el ubuntu 9.10 encendido que te ofrece actualizar desde el cd.

**Por último, **en este foro practiamente no se usa la raiz, sino que los ordenamos en software, hardware y comunidad. Para la próxima, problemas de software como éste ponelos dentro de software asi le ahorrás trabajo al moderador :D

---

### Post by Jeivo on 2010-05-03
en primer lugar, mil gracias por responder.

ahora te comento lo que me has preguntado.

Tengo un pIV a 3.2 ghz. Tengo un disco duro con ubuntu 9.10 y otro con lo mismo. (también probé la instalación dejando un solo disco). Los dos discos son SATA, uno de 320gb y otro de 500gb. 3gb ram y grafica ati de 512mb saphire 3650 hd. la placa es asus.

El cd alternate lo he probado, pero no de la manera que me dices. Probé a hacer una instalación nueva con ese cd y no funcionó, asi que voy a probar a meter ese cd con mi 9.10 arrancado e intentar actualizarlo.

Muchas gracias, probaré eso y te lo comentaré.

---

### Post by Jeivo on 2010-05-04
Nada,no ha funcionado, me sale el mismo problema, se queda en configurando memtest86+.

Creen que kubuntu funcionaria?

---

### Post by guillermolisi on 2010-05-05
No termino de entender el problema.

El sistema esta funcionando con 9.10 ?
Si es asi, probaste de iniciarlo con un CD de 10.04 en modo Live ?

Si probaste, como te fue ? Anduvo bien ?
Si no probaste, probalo y hace tus comentarios.

---

### Post by Jeivo on 2010-05-05
Probé con el Live del 10.04 y en principio parecia ir bien, pero empezó a hacer cosas raras.

Pulsaba por ejemplo, la letra "a" y ahora aparecía en la pantalla como si estuviese pulsada la letra.

y cosas así raras hasta el punto que no podia dominarlas y en el el caso de Kubuntu no me dejaba ni instalarlo.

la 9.10 me funciona perfectamente.

---

### Post by guillermolisi on 2010-05-08
Para estos casos nada mejor que leer los logs para ver que eventos registra en el inicio.
Los clasicos son /var/log/dmesg (sistema en general) y /var/log/Xorg.0.log (interfaces humanas: video, teclado, mouse, tabletas, etc.)

---

