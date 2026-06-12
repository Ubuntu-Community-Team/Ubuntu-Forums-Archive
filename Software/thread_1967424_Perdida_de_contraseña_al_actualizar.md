---
title: "Perdida de contraseña al actualizar"
date: 2012-04-28
forum: Software
---

### Post by Brath-ga on 2012-04-28
Tengo un equipo de sobremesa con Ubuntu 10.10.

Al actualizar a Ubuntu 12.04, logicamente opté por la acción de actualizar sin tocar los ficheros de /home.

Cuando finalizó la instalación, reinicié y al introducir mi contraseña ( la misma que tuve siempre ), de dió un pantallazo y volvió a la pantalla de login, así, varias veces.

Arranqué en modo seguro e intenté actualizar la contraseña como root, pero tampoco me dejaba e indicaba un error.

Volví a reiniciar y le indiqué que arrancara la versión anterior de Ubuntu, pero al llegar al login, volvía a pasarme lo mismo con la contraseña. No me indica que sea incorrecta, solo que vuelve a la misma pantalla.

No os parece extraño?

Le pasó a alguien más o es un caso de "polstergeis" mio?.

Salud@s

---

### Post by juancarlospaco on 2012-04-28
Algo, posiblemente de la Grafica esta fallando, y matando la X,
proba iniciar en modo 2D, o seguro y fijate como resulta...

---

### Post by Brath-ga on 2012-04-29
Probé a matar las X y nada.

Lo peor es que la cosa se complicó posteriormente y al intentar iniciar Ubuntu se reseteaba.

Al final, despues de 4 intentos tuve que cargarme /home en donde tenía mis configuraciones e instalar desde 0 formateando todo.

El caso es que creo saber cual era el problema:

Cuando lo instalé por vez 1ª,2ª y 3ª, la partición en donde estaba Ubuntu me la reconocía como "sdb". En la definitiva estaba como "sda".

Cuando instalara la versión 10.10 ya me localizaba los discos cambiados y puse un "thread" con un aviso. Por eso cuando empezé a instalar la 12.04 y vi que Ubuntu estaba en "sdb" que fuera en donde lo instalara y pensé que habían corregido el problema.

A lo peor me pasa a mi solo al tener 2 discos, en un netbook en la que lo actulicé sin perder nada, me lo hizo perfectamente.

---

### Post by jandry on 2012-04-29
Disculpen mi ignorancia pero este post figura como solved, cual fue la solucion? formatear todo? es este un bug que se arrastra desde la version 10? Abrazo Ubuntero

---

### Post by guillermolisi on 2012-04-30
> **Brath-ga said:**
> .......
El caso es que creo saber cual era el problema:

Cuando lo instalé por vez 1ª,2ª y 3ª, la partición en donde estaba Ubuntu me la reconocía como "sdb". En la definitiva estaba como "sda".

Cuando instalara la versión 10.10 ya me localizaba los discos cambiados y puse un "thread" con un aviso. Por eso cuando empezé a instalar la 12.04 y vi que Ubuntu estaba en "sdb" que fuera en donde lo instalara y pensé que habían corregido el problema.

A lo peor me pasa a mi solo al tener 2 discos, en un netbook en la que lo actulicé sin perder nada, me lo hizo perfectamente.

Creo que lo dieron por resuelto por el citado comentario. Es decir, no era lo que parecia, era un problema de identificacion de particiones.

---

