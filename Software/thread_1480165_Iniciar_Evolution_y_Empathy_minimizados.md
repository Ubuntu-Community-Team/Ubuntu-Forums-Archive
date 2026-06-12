---
title: "Iniciar Evolution y Empathy minimizados"
date: 2010-05-11
forum: Software
---

### Post by JoniJnm on 2010-05-11
Hola, 

Saben qué comando tengo que poner para ejecutar Evolution y Empathy minimizados? Es para ponerlo en la lista de aplicaciones de inicio

Es que no me entero cuando están abiertos o no, como el icono siempre está en la bandeja del sistema...

Saludos!

---

### Post by juancarlospaco on 2010-05-11
*empathy &*

Tengo yo... y por el otro uso Gmail Notification

---

### Post by guillermon on 2010-05-13
> **JoniJnm said:**
> Hola, 

Saben qué comando tengo que poner para ejecutar Evolution y Empathy minimizados? Es para ponerlo en la lista de aplicaciones de inicio

Es que no me entero cuando están abiertos o no, como el icono siempre está en la bandeja del sistema...

Saludos!
Hola, yo no entiendo bien la pregunta... Los comandos serían evolution y empathy, respectivamente. Sugerencia, yo como lego que soy cuando no sé cuál sería el comando uso alt+F2, que a medida que vas escribiendo te sugiere aplicaciones... Otra opción es en la consola, cuando escribes una primera parte de la palabra, aprietas dos veces la tecla Tab, y te sugiere todas las variantes...
Respecto de saber si están siendo ejectuados, se supone que tienes una lista de ventanas, por cada aplicación. Otra opción es usar un docky, como gnomedo o AWN.
Espero ayudarte. Cualquier duda no dudes en preguntar. Saludos

---

### Post by spydeyrch on 2010-05-13
> **JoniJnm said:**
> Hola, 

Saben qué comando tengo que poner para ejecutar Evolution y Empathy minimizados? Es para ponerlo en la lista de aplicaciones de inicio

Es que no me entero cuando están abiertos o no, como el icono siempre está en la bandeja del sistema...

Saludos!

Creo que entiendo bien. Quieres un icono que podrias usar para abrir evolution y Empathy a la misma vez pero que estan minimizados en la barra de programas, cierto? Dejame averiguar y ahorita vengo para darte las noticias que encuentro, sale.

-Spydey :guitar:

EDIT: todavia estoy buscando pero creo que empezaria algo asi: 

```

evolution && empathy -???????
```

Solo que no se cuales serian las opciones (los ???????) para empezarlos minimizados. Voy a buscar un poco mas.

---

### Post by JoniJnm on 2010-05-14
Gracias por tu respuesta, spydey

Sólo quería hacer que se iniciaran con ubuntu, pero minimizados.

He añadido en las "Aplicaciones de inicio" los dos:
evolution &
empathy &

Aunque eso que comentas es una buena idea. Si lo consigues avisa :-P

---

### Post by guillermolisi on 2010-05-14
> **JoniJnm said:**
> Gracias por tu respuesta, spydey

Sólo quería hacer que se iniciaran con ubuntu, pero minimizados.

He añadido en las "Aplicaciones de inicio" los dos:
evolution &
empathy &

Aunque eso que comentas es una buena idea. Si lo consigues avisa :-P
Y asi funciona tal como vos querias ?

---

### Post by xavipv on 2012-05-26
> **JoniJnm said:**
> Hola, 

Saben qué comando tengo que poner para ejecutar Evolution y Empathy minimizados? Es para ponerlo en la lista de aplicaciones de inicio

Es que no me entero cuando están abiertos o no, como el icono siempre está en la bandeja del sistema...

Saludos!

Hola,

Si lo que quieres es que las aplicaciones que se ejecutan al inicio se queden minimizadas, puedes usar "Alltray":

```
sudo apt-get install alltray
```

Después en la ventana de "Aplicaciones al inicio", done pones la aplicación que se va a ejecutar, delante de la orden pones "alltray", ejemplo:

```
alltray turpial
```

Espero que te sirva.

---

