---
title: "Problema con la calculadora de gnome"
date: 2009-02-06
forum: Software
---

### Post by rubioo on 2009-02-06
Hola a todos, resulta que viendo que cosas tenia de diferente la calculadora de gnome. Probando las cosas que tenia descubri que al hacer la tangente de 90º me daba un resultado :S (ahora no les escribo desde ubuntu, despues les pongo una captura de pantalla si quieren). Viendo esto, fui al menu ayuda y ahi hay una opcion reportar problema y ahi es a donde fui, pero queria saber si con eso era suficiente, o si tengo que hacer otra cosa, para estar seguro que en la proxima version va a estar solucionado en bug. Si no es que es un problema de mi calculadora y a ustedes les funciona bien.

      Saludos

---

### Post by feche_mza on 2009-02-08
no es un error en la calculadora, es un problema matematico, la tangente de 90 te da un numero muy grande (o mui chico no me acuerdo) por eso te lo tira en una exprecion con el numero e, si vos te fijas en casi todas las calculadoras cientificas (las de mano que llevas a la facu) si tratas de calcular la tangente de 90 te va a decir "math error", y lo primero que uno piensa es math=matematico, pero no, es un error de mantisa, el numero es tan grande que no lo llega a calcular la maquinita

---

### Post by Hei Ku on 2009-02-08
No es que el número sea un poco grande para las calculadoras. La tangente de 90° te da un límite infinito.
[http://es.wikipedia.org/wiki/Cosecante#Valor_de_las_funciones_trigonom.C3.A9tricas](http://es.wikipedia.org/wiki/Cosecante#Valor_de_las_funciones_trigonom.C3.A9tricas)

Si tienen que rendir análisis, preparense para el recuperatorio. :lolflag:

---

### Post by Air23 on 2009-02-08
Un error hay, por mas que la funcion tangente tienda a infinito cuando el ángulo tiende a 90° al hacer tangente de 90° en la calculadora debería dar un error. 

Tan(x)=sen(x)/cos(x)

Luego el coseno de 90° es cero y la división por cero no esta definida

---

### Post by Hei Ku on 2009-02-08
Es cierto, debería tirar error, o mostrar un infinito o algo. Qué es lo que da en este caso?

---

### Post by Air23 on 2009-02-08
> **Hei Ku said:**
> Es cierto, debería tirar error, o mostrar un infinito o algo. Qué es lo que da en este caso?

El resultado que arroja es:
```
-8,618206661e+214
```

---

### Post by Hei Ku on 2009-02-08
Sip, eso se merece un bug. Pueden fijarse en launchpad si hay algo relacionado a ese paquete.

---

### Post by rubioo on 2009-02-08
:O descubri un bug xd. Ya lo reporte asi que espero que lo puedan solucionar para la proxima version 




           Saludos

---

### Post by faktorqm on 2009-02-09
<no quiero quedar como un nerd asqueroso>

Les recuerdo que tiende a infinito por izquierda, ya que "en el valor" hay una asintota y por derecha es menos infinito.}
Como bien dijo air23, la tangente de 90 no tiene solucion, si el limite como explique antes, pero aca nadie tomo limite ;)

</no quiero quedar como un nerd asqueroso>

bueno, no lo pude evitar... salu2!!!!

---

### Post by rubioo on 2009-02-09
> **faktorqm said:**
> <no quiero quedar como un nerd asqueroso>

Les recuerdo que tiende a infinito por izquierda, ya que "en el valor" hay una asintota y por derecha es menos infinito.}
Como bien dijo air23, la tangente de 90 no tiene solucion, si el limite como explique antes, pero aca nadie tomo limite ;)

</no quiero quedar como un nerd asqueroso>

bueno, no lo pude evitar... salu2!!!!

 Jaja, el intento es lo que cuenta :P
 Volviendo al tema, ayer agarre un live cd de ubuntu 7.10 que tenia por ahi, i al hacer la misma operación, dice "Error en operación matemática" o algo parecido (que es lo que tendría que aparecer)

      Saludos

---

