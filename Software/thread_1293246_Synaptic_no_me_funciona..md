---
title: "Synaptic no me funciona."
date: 2009-10-16
forum: Software
---

### Post by Hadso on 2009-10-16
Hola a todos. No encontré info sobre este tema en el foro. 
Resulta que acabo de formatear mi disco e instalar Ubuntu 9.04 que tenía quemado en un CD desde hace unos meses. 
El tema es que ahora quiero instalar algunos programas y Synaptic no me funciona.
Cuando crea el árbol de dependencia, se cuelga en el 50%, se queda ahí y no sale. 

Bueno, qué puedo hacer? Muchas gracias!

Saludos, 

Hadso.

---

### Post by guillermolisi on 2009-10-16
> **Hadso said:**
> Hola a todos. No encontré info sobre este tema en el foro. 
Resulta que acabo de formatear mi disco e instalar Ubuntu 9.04 que tenía quemado en un CD desde hace unos meses. 
El tema es que ahora quiero instalar algunos programas y Synaptic no me funciona.
Cuando crea el árbol de dependencia, se cuelga en el 50%, se queda ahí y no sale. 

Bueno, qué puedo hacer? Muchas gracias!

Saludos, 

Hadso.
Proba con ```
sudo apt-get update
``` en una consola/terminal a ver que te dice.

Para instalar paquetes especificos tambien podes usar ```
sudo aptitude
``` y una vez ahi podes usar la funcion Search para ubicar el paquete a instalar.

---

### Post by Hadso on 2009-10-17
Perfecto! Muchas gracias. Creo que lo había probado, pero no me había funcionado porque no podía terminar el proceso anterior de Synaptics donde había detectado el error. 
Y ya que estamos en esto, me podría alguien contar cuál es la diferencia entre "sudo apt-get install" y "sudo aptitude"?

Muchas gracias!

---

### Post by guillermolisi on 2009-10-17
> **Hadso said:**
> Perfecto! Muchas gracias. Creo que lo había probado, pero no me había funcionado porque no podía terminar el proceso anterior de Synaptics donde había detectado el error. 
Y ya que estamos en esto, me podría alguien contar cuál es la diferencia entre "sudo apt-get install" y "sudo aptitude"?

Muchas gracias!
[En este thread]("http://ubuntuforums.org/showpost.php?p=8104430&postcount=2") se habla algo sobre el tema

---

### Post by Hadso on 2009-10-17
OK. Gracias. Tonces ya se puede cerrar este hilo. 
Muy agradecido.

---

