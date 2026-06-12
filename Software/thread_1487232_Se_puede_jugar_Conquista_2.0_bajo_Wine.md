---
title: "Se puede jugar Conquista 2.0 bajo Wine????"
date: 2010-05-18
forum: Software
---

### Post by dam1977 on 2010-05-18
Como ven, estamos intentando instalar algunos juegos para que mis muchachos no extrañen demasiado el Windows!! Instalamos el Conquista 2.0 y logramos hasta cargar los parches, pero cuando queremos que arranque, se corta y se cierra. Alguien habrá logrado vencer estos obstáculos? Gracias!!!

---

### Post by clasificado on 2010-05-19
Conquista conquista? el conquista.91.com?

no todavía. Tengo entendido que es Ventanas compatible, lo estas mandando a través de wine?

probá ejecutando el EXE desde la consola
```

wine nombre.exe

```

---

### Post by guillermolisi on 2010-05-19
Que version de Wine estas usando para correr ese juego ?

---

### Post by dam1977 on 2010-05-19
Tenemos instalada la versió de Wine que viene por defecto en Ubuntu 10.04....

---

### Post by guillermolisi on 2010-05-19
> **dam1977 said:**
> Tenemos instalada la versió de Wine que viene por defecto en Ubuntu 10.04....
Te recomiendo, aunque aun sigue siendo una version beta, que instales y uses la que esta en los repositorios de Wine-HQ.

Para agregar sus repositorios tenes que abrir la opcion de Origenes del Software, luego ir a la pestaña Software de Terceros, Agregar y en el campo que se habilita copia y pega > ppa:ubuntu-wine/ppaluego click sobre el boton Agregar y listo.
Solo te queda recargar/refrescar el cache local y ahi te aparecera que tenes actualizaciones de Wine para aplicar.

Si no recuerdo mal tambien te bajara WineTricks que es un paquete de mejoras para Wine que hace magia :)

Proba y comenta que tal te fue.

---

### Post by DrKenobi on 2010-05-19
Esta pagina esta muy buena: [http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by dam1977 on 2010-05-28
Instalé WineTricks, agregué los repositorios de Wine, todo eso bien. pero sigo sin poder jugar a Conquista....

---

### Post by dam1977 on 2010-05-29
Instalé el juego, pero al iniciarlo aparece el siguiente mensaje:
[IMG]http://i47.tinypic.com/14k8c3c.png[/IMG]
Estuve mirando la página de appdb.winehq. pero no entiendo que es lo que hay que hacer.

---

### Post by albert0 on 2011-04-23
> **dam1977 said:**
> Instalé el juego, pero al iniciarlo aparece el siguiente mensaje:
[IMG]http://i47.tinypic.com/14k8c3c.png[/IMG]
Estuve mirando la página de appdb.winehq. pero no entiendo que es lo que hay que hacer.

Podrías intentar ejecutar el Conquer.exe directamente con el parametro "BLACKNULL"

Yo voy a instalar de nuevo ubuntu a ver que tal me va! :D

Intenta corre en la consola el juego así:
"wine Conquer.exe BLACKNULL"

Ouch!, no me dí cuenta de la fecha del post.

---

### Post by dam1977 on 2011-04-25
no hay problema, albertO. Seguimos sin poder jugar Conquista con Wine... vamos a probar lo que dijiste y te contamos..

---

### Post by jdandrader on 2012-01-06
HOla chicos, pues dejenme contarles que yo instale el wine en ubuntu 11.10 y el juego me corrio sin problema, la cuestion es q cuando se abre la ventana del juego no puedo elegir el servidor en cual jugar, no me aparecen, pero si ingreso mi id y contraseña puedo jugar sin problemas en el servidor galaxia, servidor que aparece por defecto seleccionado, alguien a tenido el mismo problema_?

---

