---
title: "Problemas Con Compiz Emerald!!!"
date: 2009-10-19
forum: Software
---

### Post by checudero on 2009-10-19
Hola a todos. Tengo un problema con el Compiz Emerald, se lo instale a una netbook wind u100 con ubuntu 9.04 netbook remix.
El tema es el siguiente, active unos efectos y el problema que ocurrio por ejemplo, que cuando cierra una ventana queda en donde estubo esa ventana, quede negro y en defenitiva me queda toda la pantalla en negro y no puedo usar el menu para desactivarlo.
Ya busque y busque mucho, lo unico que encontre fue poner en la consola:
 **"metacity --replace"** para cambiar el entorno y no me anda.
La verdad ya no se que hacer, me da pena formatear la pc.
Si sirve de algo, tengo winxp como sistema secundario, tal vez pueda entrar desde ahi y borrar o modificar algo.
Espero que me ayuden y si es posible, que me expliquen el por que de ese problema asi aprendo algo mas.
Saludos a Todos

---

### Post by pablo.s on 2009-10-19
Lo que tenés que hacer es
lo siguiente:
Cuando entra en la sesión y
se pone la pantalla en negro
pasas con CTRL+Alt+F1 a la
consola 1. Ahi vas a tener que
poner tu nombre de usuario y
luego esto:

```
sudo apt-get remove compiz compiz-wrapper emerald
```

y luego presioná CTRL+Alt+Del.
Cuando vuelvas a entrar en tu
sesión vas a tener Metacity.

---

### Post by checudero on 2009-10-19
Wiiii!!\\:D/ jajaja, me alegraste el dia, me sirvio y ahora mismo lo estoy usando, estaba muy preocupado por ese tema, es que soy casi nuevo en todo esto y no entiendo bien esto de los comandos.
Una ultima consulta, de que manera puedo aprender desde 0 el uso de los comandos, encontre manuales, pero ya dan cosas por sabido o estan dedicados a temas especificos, en definitiva busco algo explicado de una manera que sea para tontos, por asi decirlo.
La verdad muchas gracias.:P
Hay sistema de puntos aca?, por que si lo hay, te quiero dar mis puntos.

---

### Post by guillermolisi on 2009-10-19
> **checudero said:**
> Wiiii!!\\:D/ jajaja, me alegraste el dia, me sirvio y ahora mismo lo estoy usando, estaba muy preocupado por ese tema, es que soy casi nuevo en todo esto y no entiendo bien esto de los comandos.
Una ultima consulta, de que manera puedo aprender desde 0 el uso de los comandos, encontre manuales, pero ya dan cosas por sabido o estan dedicados a temas especificos, en definitiva busco algo explicado de una manera que sea para tontos, por asi decirlo.
La verdad muchas gracias.:P
Hay sistema de puntos aca?, por que si lo hay, te quiero dar mis puntos.
Fijate que hay unos sticky threads en el area de Normal Threads que te pueden servir de inicio para lo que consultas.

Tambien en la seccion Comunidad hay dos threads, uno referido a un grupo de estudios y otro referido a "Un comando por dia". Date una vuelta por ellos que es una buena forma de empezar.

Y para proximas veces, trata de mantener el foco en el tema del hilo. Si se te ocurren consultas sobre otros temas primero busca con la herramienta Search si ya fue tratado el tema, si no lo fue abri otro hilo pero no mezcles los tantos, asi quienes buscan soluciones y quienes quieren responder les resulta mas facil, claro, conciso y practico.

---

### Post by SLA_leandrin on 2009-10-19
> **checudero said:**
> 
Hay sistema de puntos aca?, por que si lo hay, te quiero dar mis puntos.

OT de onda: JUAAAA esto no es Taringa che...

---

### Post by pablo.s on 2009-10-19
> **checudero said:**
> Hay sistema de puntos aca?, por que si lo hay, te quiero dar mis puntos.

Si hubiera sistema de puntos
no podría manejar, porque he
cometido todos los pecados
posibles en este foro. Si señor.

---

