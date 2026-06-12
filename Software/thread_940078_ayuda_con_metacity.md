---
title: "ayuda con metacity"
date: 2008-10-06
forum: Software
---

### Post by darkarcangel_sam on 2008-10-06
miren mi problema es q instale el froztwire y no consigo ver sus opsiones ni menus solo aparecen en blanco y m meti a una pagina q decia q si usaba beryl lo cambiara al gestor metacity pero no se endonde se encuantra el mentado gestor , o como se abre dicho gestor,lo busq en el menu pero no encuentro nada de gestores , nomas m aparecenel gestor de paquetes synamptic o algo asi y gestor de actualizaciones o algo asi jeje pero no me aparece el gestor de ventanas ni nada x el estilo 

asi q si son tan amables de explicarme como se hace eso les sere eternamente agradecido
 no utilizo ninguna targeta grafica 
y lo tengo en efectos visuales : normal

gracias 

Sam

---

### Post by faktorqm on 2008-10-06
si mal no recuerdo el comando es (presionar ALT + F2)

```
metacity --replace
```

Salu2!

---

### Post by valucha on 2008-10-09
[COLOR="DarkOrchid"]El metacity es como el "explorer" en Windows, (aunque no tanto),Es el programa con el que podés ver los archivos, te maneja el escritorio y un par de cosas más.
La cosa es que para manejar las ventanas existen varios programas en Ubuntu, por defecto en Gnome viene "metacity", si vos activas los efectos de escritorios se activa posiblemente Compiz, que te maneja las ventanas de otra forma, por eso las ves gelatinosas y hace esos efectos lindos al cerrarse y abrirse.
Lo que te dicen para el Frostwire es que no uses Compiz (Beryl era el viejo Compiz) y uses el que viene por defecto, metacity. 
Como es algo que te maneja todo, que se inicia al principio de ubuntu, no lo vas a encontrar en el menú, entonces tenés que remplazarlo en la consola. Porque ahora estás usando Compiz (porque dijiste que tenias los efectos de escritorio), entonces no hay que hacer otra cosa que sacar los efectos de escritorio (es decir, sacar compiz) y dejar metacity.

Entrás a la consola: (aplicaciones-> accesorios -> terminal) y tipeas metacity --replace , tu pantalla probablemente se ponga negra o parpadee por unos segundos y después vuelve todo a la normalidad sin usar los efectos.

Espero quie te sirva algo, Saludos.[/COLOR]

---

