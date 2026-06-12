---
title: "[SOLVED] Programas se quedan detrás al abrir fichero"
date: 2008-11-05
forum: Software
---

### Post by electronpositivo on 2008-11-05
Buenos días, 

Me sucede lo siguiente en ubuntu 810 con Compiz y Emerald activados:

Cuando tengo un programa abierto y desde natilus abro un fichero asociado a ese programa, se me queda delante nautilus en lugar de pasar delante el programa con el fichero que acabo de abrir.

Por ejemplo:
1. Abro nautilus y localizo el documento que quiero abrir.
2. Abro el documento con el OpenOffice y me aparece abierto delante de todo.
3. Vuelvo a nautilus y abro otro documento.
4. Parece que no se ha abierto.
5. Busco las ventanas abiertas y veo que el documento sí que se ha abierto.

Me gustaría que tras el paso 3 OpenOffice hubiera pasado delante como lo hace cuando el programa estaba cerrado y se abría por primera vez (paso 2).

Espero haberme explicado con claridad.

¿Existe alguna forma de cambiar esto?

Gracias :)

**[COLOR="DarkGreen"]SOLUCIÓN (Por santiagoward2000): Abrí compizconfig-settings-manager, andá a General Options, y abajo de Focus & Raise Behaviour y poné el Focus Prevention Level en Off.[/COLOR]**

---

### Post by sdennie on 2008-11-06
Probá:

```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/focus_prevention_level 0

```

---

### Post by electronpositivo on 2008-11-07
Gracias vor, pero me parece que no sirve. 

¿Otra idea :confused:

> **vor said:**
> Probá:

```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/focus_prevention_level 0

```

---

### Post by sajnox on 2008-11-07
> **electronpositivo said:**
> Gracias vor, pero me parece que no sirve. 

¿Otra idea :confused:

Por que te parece que no sirve?

Que error te tira? Cambio en algo el comportamiento?

---

### Post by santiagoward2000 on 2008-11-07
Hola!
No estoy seguro de eso, pero creo que el gconftool no anda si usa Compiz. Abrí **compizconfig-settings-manager**, andá a **General Options**, y abajo de **Focus & Raise Behaviour** y poné el **Focus Prevention Level** en Low u Off. Creo que eso tendría que arreglarlo.
Saludos!

---

### Post by Tosh78 on 2008-11-07
Hola! Anda a Sistema -> Preferencias -> Administrador de opciones de Compiz config y fijate si tenes tildado "Opacidad", si lo tenes, quitaselo y proba. Cuando yo lo instale, me lo tildo por defecto y era bastante molesto. El efecto puede llegar a ser algo parecido a lo que vos decis.

---

### Post by electronpositivo on 2008-11-08
> **sajnox said:**
> Por que te parece que no sirve?

Que error te tira? Cambio en algo el comportamiento?

Ningún error, y ningún cambio en el comportamiento...

---

### Post by electronpositivo on 2008-11-08
> **santiagoward2000 said:**
> Hola!
No estoy seguro de eso, pero creo que el gconftool no anda si usa Compiz. Abrí **compizconfig-settings-manager**, andá a **General Options**, y abajo de **Focus & Raise Behaviour** y poné el **Focus Prevention Level** en Low u Off. Creo que eso tendría que arreglarlo.
Saludos!

¡Diste en el clavo! =D> 

Tenía el Focus Prevention Level en Low, lo cambié a Off y ya lo tengo como quería.

Muchísimas gracias a ti y a todos los que me habéis echado una mano. :guitar:

---

### Post by santiagoward2000 on 2008-11-08
> **electronpositivo said:**
> ¡Diste en el clavo! =D> 

Tenía el Focus Prevention Level en Low, lo cambié a Off y ya lo tengo como quería.

Muchísimas gracias a ti y a todos los que me habéis echado una mano. :guitar:

De nada! Igual me parece raro que en low haga eso. Yo lo tengo en low y no me pasa...

---

