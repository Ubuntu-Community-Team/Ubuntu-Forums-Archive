---
title: "[SOLVED] IndentationError: unexpected indent (Python)"
date: 2008-06-07
forum: Software
---

### Post by madelaki on 2008-06-07
Tengan en cuenta que nunca habia programado nada excepto ejemplos en mi vida, y cuando lo intente, paso esto. De donde viene este error? No encontre nada claro con Google, y muchisimo menos en español. Lei que podia ser un problema con el formato del codigo, que no tengo para nada claro. Me lo tira con un if bajo un raw_input. Estan asi:

```
xx = raw_input("x")
 if x
```

Tambien probe con esto pero devuelve el mismo error.

```
x = raw_input("x")
             if x
```

Si alguien tiene alguna idea de por que me tira este error y/o como solucionarlo, le voy a estar agradecido de por vida.

---

### Post by marcosconio on 2008-06-07
Deberias ponerlo a la misma altura que la linea anterior, asi:

xx = raw_input("x")
if x

y __exactamente__ a la misma altura de la linea anterior, sino python se quejara.... suerte con ese hermoso lenguaje.!

---

### Post by madelaki on 2008-06-07
Hm... no creo que sea asi. Me devuelve un syntax error.

---

### Post by marianom on 2008-06-08
Mucho me temo que así como está ese código no tiene sentido.

Los 2 lugares donde podés usar un if en python son:

 1- estructura condicional normal
    ```
if x == 0:
    doSomething()
else:
    doThisOtherThing()
```

 2- en un list comprehension
    ```
x = [y for y in v if y == 0]
```

Ergo, o a ese snippet le falta texto luego del if o es un list comprehension mal escrito. Si podés tirar más código, lo puedo ver e intento darte una mano.

Sea dicho de paso que el error de Indentación inesperada lo da cuando - :) - escribís un bloque sin la identación correcta (esto es: para cada nivel anidado de código tiene que existir la misma cantidad de espacios de sangrado ya que es lo que usa python para reconocer bloques de código -notese que no tiene {} como otros lenguajes). Por lo tanto, el error quiere decir algo pero lo que mostrás no tiene sentido en sí por lo tanto el error "debería" estar en otro lado que no estamos viendo.

---

### Post by madelaki on 2008-06-08
Obviamente falta codigo, pero son prints. Tengo que definir una funcion para los prints? No puedo ponerlos directamente?

---

### Post by leo_rockway on 2008-06-08
Para usar print debería ser algo así:

```
xx = raw_input("x")
if xx == foo:
    print "foo"
elif xx == bar:
    print "bar"
else:
    print "not foo nor bar"

```

Por cierto, es altamente recomendable la lista de correo de Python Argentina.

---

### Post by madelaki on 2008-06-08
Solved, gracias. 
> 
Por cierto, es altamente recomendable la lista de correo de Python Argentina. 

No me gusta la idea de que mi primer mensaje sea un pedido de ayuda.

---

### Post by marcosconio on 2008-06-08
> No me gusta la idea de que mi primer mensaje sea un pedido de ayuda.

Tu primer mensaje puede ser un "Hola mundo" presentandote, y el segundo el grito de ayuda :)

---

### Post by leo_rockway on 2008-06-08
> **madelaki said:**
> 
No me gusta la idea de que mi primer mensaje sea un pedido de ayuda.

Igual yo recomendaba la lista en general, no para este caso en particular. Yo básicamente estoy de lurker ahi, porque entiendo poco y nada, pero de vez en cuando pesco algo que más o menos entiendo y que me hace aprender.

> **marcosconio said:**
> Tu primer mensaje puede ser un "Hola mundo" presentandote, y el segundo el grito de ayuda :)

No sé si estás en la lista, pero el "Hola, mundo." es realmente imprescindible y es una competencia para ver quién manda la versión más creativa, jaja.

---

### Post by marianom on 2008-06-08
Ohh yeah, la lista de pyar es de lujo. Muchos que saben mucho están ahí.

---

