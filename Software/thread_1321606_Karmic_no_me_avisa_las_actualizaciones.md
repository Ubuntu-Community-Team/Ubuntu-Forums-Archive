---
title: "Karmic no me avisa las actualizaciones"
date: 2009-11-10
forum: Software
---

### Post by alejo_joan on 2009-11-10
Hola, les quiero hacer una pregunta.
Hace poco actualicé mi 9.04 a 9.10 y funciona  a la perfección pero no me avisa las actualizaciones disponibles (que sí lo hacía el 9.04).
Entro al Gestor de actualizaciones y me aparece el listado, le doy actualizar y actualiza. Tengo todo configurado para que lo haga de manera automática.
Saludos.
Alejo.

---

### Post by SLA_leandrin on 2009-11-10
Si, a mi me pasa lo mismo.

De todos modos estoy tan acostumbrado a hacer un 

```
sudo apt-get update && sudo apt-get upgrade
```

que hasta que no leí tu post no me había dado cuenta!
Veremos si alguien tiene una solución.

Saludos...

---

### Post by pablo.s on 2009-11-10
A partir de la Alpha 3 de Karmic Koala
se avisa al usuario de las actualizaciones
de seguridad unicamente.

---

### Post by juancarlospaco on 2009-11-10
Lo que dice pablo.s
:)

---

### Post by guisheca on 2009-11-10
Mirá vos, no sabía de esto, yo también me acostumbré a tirar de comandos. Creo que es una decisión acertada del equipo de ubuntu, ya que las otras actualizaciones pueden traer problemas.
Ya se trató mucho el tema en este foro, y creo que esta es una buena solución.

---

### Post by emiliano_raso on 2009-11-10
Yo me habia acostumbrado con debian hacerlo por consola, pero realmente uqe no se avise mas es una pavada, porque no cuesta nada y a los usuarios nuevos les viene re bien.

Es mas, es uno de los mejores aspectos que hay en Ubuntu.

---

### Post by sebastianabate on 2009-11-11
Esta es una de las pocas cosas que no me gustaron de Karmic, que cambiaran radicalmente la forma de avisar que hay actualizaciones y no exista una forma obvia de volver al viejo sistema.

Me parece bien que realicen cambios para mejorar la experiencia del usuario, pero no me parece nada bien que se haga de forma compulsiva y sin pensar que somos muchos a los que nos gustan las cosas como son (si hace una búsqueda sobre este tema van a ver la cantidad de reclamos que se hicieron), y estamos capacitados para seguir usándolas de esta forma.

Y después de hacer catarsis les paso cómo hacer para volver al viejo sistema de aviso (el icono en la bandeja de sistema en vez de que se abra el Update Manager de golpe); pueden ejecutar este comando (como usuario normal, no con sudo)

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```y santo remedio (aunque sigue avisando únicamente cuando hay actualizaciones de seguridad, y no cuando hay actualizaciones comunes).

PD: ya sé que no era para tanto, que al final existía una forma de volver a poner las cosas como estaban, pero este comando no figura ni en las release notes, ni en la ayuda del Update Manager, lo encontré después de buscar bastante en foros y listas; y es por eso que me molestó tanto.

---

### Post by pablo.s on 2009-11-11
> **sebastianabate said:**
> Me parece bien que realicen cambios para mejorar la experiencia del usuario, pero no me parece nada bien que se haga de forma compulsiva y sin pensar que somos muchos a los que nos gustan las cosas como son (si hace una búsqueda sobre este tema van a ver la cantidad de reclamos que se hicieron), y estamos capacitados para seguir usándolas de esta forma.

Justamente el cambio se hizo por
una catarata de quejas de usuarios
que les molestaba ver actualizaciones
dia por medio.
Mientras esté disponible algún metodo
para actualizar, se va a poder.
Ubuntu está dando grandes pasos hacia
la simplificación de la experiencia del
usuario, y de veras entiendo tu disgusto.
Solamente ver la polémica sobre Software
Center o sobre Ubuntu One.
Pero es un camino necesario para que el
grán público llegue a GNU/Linux.

---

### Post by sebastianabate on 2009-11-11
> **pablo.s said:**
> Justamente el cambio se hizo por
una catarata de quejas de usuarios
que les molestaba ver actualizaciones
dia por medio.
Mientras esté disponible algún metodo
para actualizar, se va a poder.
Ubuntu está dando grandes pasos hacia
la simplificación de la experiencia del
usuario[...]

Y esto me parece perfecto, Ubuntu se transformó en lo que es justamente porque permite que el usuario novel lo pueda utilizar y configurar sin demasiados problemas; pero me parece que se puede simplificar sin quitar opciones.

En este caso puntual la opción más práctica es la de setear como predeterminado el nuevo comportamiento pero agregar una opción dentro de la configuración de Updates para poder elegir entre la apertura automática del Update Manager o el icono en la bandeja de sistema; y esto no es complicado, ya que como vimos es simplemente cambiar una entrada de true a false.

Me parece perfecto que Canonical utilice el feedback que recibe de los usuarios finales para hacer la mejor distribución posible para ellos; pero que no se olviden que existe una gran cuota de usuarios profesionales/corporativos que pretenden seguir teniendo el control fino de sus sitemas, sin perder la maravillosa facilidad a la que nos tiene acostumbrados Ubuntu.

---

### Post by alejo_joan on 2009-11-14
Muchas gracias a todos!

---

