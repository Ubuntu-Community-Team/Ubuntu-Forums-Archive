---
title: "No puedo activar el corrector ortográfico en español para Epiphany"
date: 2009-06-17
forum: Software
---

### Post by GGsalas on 2009-06-17
Hola, avancé bastante buscando una solución [(1)]("http://crunchbang.org/archives/2007/12/27/epiphany-and-firefox-on-ubuntu/") | [(2)]("http://ubuntuforums.org/showpost.php?p=2572757&postcount=10") pero pude terminar, sólo pude activar el corrector ortográfico en inglés, no pude cambiar el idioma.

La activación se hace llendo a la dirección **about:config** desde epiphany y cambiando los siguientes valores:

**layout.spellcheckDefault **debe cambiarse a 1
**spellchecker.dictionary** : acá se debe colocar el idioma español (probé con es-ES, con es-AR) pero no lo acepta, en cambio pone (en-US).

Aparentemente existe un BUG y no se pueden cambiar los valores numéricos, tuve que editar el archivo de preferencias con el siguiente comando e ingresar el valor a mano:
```
gedit ~/.gnome2/epiphany/mozilla/epiphany/prefs.js
```

el dato que ingresé es:
```
user_pref("layout.spellcheckDefault", 1);
```

Como no funcionaba el diccionario tampoco en _Tomboy_ entonces fui a Synaptic e instalé el paquete **aspell-es**, y luego de reiniciar la sesión verifiqué que Tomboy verifica bien la ortografía.
[B]
El resultado es que ahora tengo corrección ortográfica para Tomboy, pero para epiphany tengo en inglés, no es español.[/B]

No estoy seguo si el consumo de memoria es mucho menos que firefox, pero la verdad Epiphany me gusta mucho.

Saludos

---

