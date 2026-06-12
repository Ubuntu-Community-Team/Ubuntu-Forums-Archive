---
title: "activar metasse"
date: 2009-11-06
forum: Software
---

### Post by joseluis on 2009-11-06
amigos, tengo ubuntu 9.10 en una notebook un tanto antigua, tiene tarjeta nvidia integrada, pero no es muy polenta. No importa, quisiera probar metacity, efectos de escritorios, que no sea compiz, porque se que compiz no anda acá. ¿como hago? ¿como se si está isntalado? ¿como lo instalo ? o como lo activo?
gracias

EDIT: bueno..lo pude activar. Por favor, quisiera saber si puedo activar el AWN con metacity. Lo intento pero no hay caso. No me gusta y no me queda bien el Cairo-Dock y estuve viendo en [http://www.tuxapuntes.com/drupal/node/1356](http://www.tuxapuntes.com/drupal/node/1356) que se puede hacer.Teniendo activado metacity, como lo tengo en la actualidad..

---

### Post by juancarlospaco on 2009-11-06
AWN necesita aceleracion, Cairo Dock 2 no necesita aceleracion,
podes instalarte el Engine de Murrine que permite trasparencias dentro de las ventanas,
podes habilitar el Composite de Metacity desde el 
gconf-editor--->Apps--->Metacity--->tildar "Composite"
Todo esta en los Repos, asi que no necesitas buscarlo en internet,
te recomiendo estes usando la ultima Version de Ubuntu, la 9.10.
:)

---

### Post by joseluis on 2009-11-06
si..lo activé así tal como me decís. Es decir, lo tengo activado el metacity. Por eso quisiera saber si puedo meter el AWN. Quizás no entendí lo que expresaste y me estás diciendo que necesito compiz, pero no me la maquina para el compiz.

---

### Post by juancarlospaco on 2009-11-06
Pero no podes usar AWN, por que usa aceleracion OpenGL, por hardware.
el Compisote de Metacity corre sin aceleracion, por software.
Usa Cairo Dock que tiene la opcion de correr sin aceleracion.

---

### Post by joseluis on 2009-11-06
Si...lo intenté..pero Cairo Dock no me anda bien. Se traba, se arrastra. En fin..una lástima...porque me gusta tender un dock, es muy práctico y además son vistosos...

---

### Post by josecuervo86 on 2009-11-06
Probaste con wbar? No es AWN pero es un dock al fin

---

### Post by joseluis on 2009-11-08
si...probé con wbar. Está bueno. Pero poca o nada personalización. 
Pero al final pude resolverlo de esta manera, que es lo que mejor me quedó:
1. activé metacity
2. bajé el Docky, sin necesidad de poner todo el Gnome-Do. 
Lo hice siguiendo la indicación de uno de los hilos, post, que es LO QUE HAY QUE HACER DESPUES DE INSTALAR KARMIC KOALA. En donde dice qué comando poner para instalar solo Docky.

Y la verdad me queda bárbaro: efectos de metacity, con dock de Docky, sin perder demasiados recursos. Está ok asi.
GRACIAS

---

### Post by goldenfox on 2009-11-08
AWN puede correr con composite pero te ba a consumir mucho
creeme antes tenia un pc con 512 de ram y una targeta onboard prosavage y andaba muy lagoso si tenia muchas cosas abiertas

---

