---
title: "Problemas con el AMSN"
date: 2009-10-19
forum: Software
---

### Post by santiago79 on 2009-10-19
hola gente tengo un problema que siempre me pasa y nose porque es.
yo recien estaba usando el amsn re bien de 10 lo cerre y lo vuelvo a iniciar y cuando apreto inicar secion o el boton de idioma se cierra de una y nose porque? alguien sabe porque pasa?:(
gracias por su tiempo

---

### Post by mama21mama on 2009-10-19
Seguramente un bugazo, es lindo el amsn pero hay que reconocer que no esta del todo estable. A mi me a pasado varias veces en diferentes versiones, pero igual lo sigo usando.

Lo que puedes hacer es mover momentaniamente la config.

Proba en terminal:

> mv ~/.amsn ~/.amsn.old
analicemos que hace este comando, mueve la config .amsn a .amn.old
para mas informacion:

> man mv

Espero que te ande luego de mover la config.

---

### Post by santiago79 on 2009-10-19
no amigo sigue igual se reinicia la configuracion pero se sigue cerrando :(
encima ahora estoy desde kubuntu y el emesene no me detecta la webcam todo mal:(

---

### Post by mama21mama on 2009-10-20
Para la webcam debes abrir un puerto en amsn.

Debes remover y purgar el amsn. Funciona muchas veces.

> sudo apt-get remove --purge amsn
Remmueve la aplicacion, y borra todo dato de su configuracion

> 
sudo apt-get install amsn
Instala la aplicacion


Si esto no funca [instala este]("http://mamalibre.eshost.com.ar/?q=content/amsn-messenger-con-videollamada")

Saludos

---

### Post by santiago79 on 2009-10-20
no :( sigue igual que ****** muchos bug el amsn

---

### Post by luks911 on 2009-10-20
Ejecutalo en una terminal, corriendo
```
amsn
```
De ese modo, cuando se cierra te va a devolver algún error y vas (y vamos) a tener más datos para saber qué pasa.

---

### Post by santiago79 on 2009-10-20
mira me salia error de segmentacion
pero ahora tratando de volver a una version anterior porque tenia la 99b me sale esto ahora

there's a problem loading a module of aMSN (TkCImage): version conflict for package "tcl:have 8.5.6, ned exactly

---

### Post by mama21mama on 2009-10-20
Usa [este amsn v0.99b]("http://mamalibre.eshost.com.ar/?q=content/amsn-messenger-con-videollamada")

---

### Post by santiago79 on 2009-10-20
> **mama21mama said:**
> usa [este amsn v0.99b]("http://mamalibre.eshost.com.ar/?q=content/amsn-messenger-con-videollamada")


claro ese uso y con ese me paso el problema con la que abrí  esta rama del foro

alguien tiene una manera facil de instalar el tk/tcl porque no me los detecta ahora

---

