---
title: "[SOLVED] Evitar la transparencia de Metacity usando el Compiz"
date: 2009-01-07
forum: Software
---

### Post by kornykyano on 2009-01-07
No encuentro info de como evitar la transparencia de la ventana cuando uso Metacity y el Compiz. 

Sin el Compiz queda muy bien, probé con Emerald pero es muy pesado e inestable, también con otro theme y sucede es lo mismo.

No quiero dejar de usar el Compiz por lo agradable que es. Espero que alguien tenga alguna idea.

Saludos.
imagen actual
[ATTACH]99054[/ATTACH]
inagen deseada
[ATTACH]99053[/ATTACH]

---

### Post by Hei Ku on 2009-01-07
Sacale el efecto de opacity.

---

### Post by kornykyano on 2009-01-07
> **Hei Ku said:**
> Sacale el efecto de opacity.

No esta activado. 

Me gustaria saber si el que usa el compiz, le pasa lo mismo?

Gracias x la respuesta.

---

### Post by Hei Ku on 2009-01-07
Hay un par de efectos mas que estan vinculados a la transparencia, en particular de ventanas que no estan en foco.
Y eso es configurable, lo podés sacar si queres. Que plugins tenes activados?

---

### Post by kornykyano on 2009-01-07
Aparentemente el Compiz funciona asi, por mas que desactive..."completamnete todo"... sigue igual.

Yo lo vengo usando desde 7.04 y siempre fue asi. Convengamos que es una bolu#$% lo mio porque es solo estético.

Saludos y gracias nuevamente :)

---

### Post by kornykyano on 2009-01-08
Bueno...encontre la solución!!!!
simplemete habia que cambiar en gconf-editor las opciones de opacidad de las ventana de Metacity:
[COLOR="Blue"][LIST]/apps/gwd/metacity_theme_opacity[/LIST][/COLOR] se lo cambia por el valor "1"

\\:D/

PD:**Hei Ku** algo de razón tenias :)

---

