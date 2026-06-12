---
title: "firefox incia en &quot;Trabajar sin conexion&quot;"
date: 2008-04-28
forum: Software
---

### Post by atatiducken on 2008-04-28
hola amigos, instale hardy y tengo un problema q no es para nada grave pero muy molesto, cada vez q inicio firefox este lo hace con la opcion "Trabajar sin conexion", asi q debo desactivarla. Lo mismo pasaba con Firefox 3 Beta 4 en Ubuntu 7.10, alguna idea de lo q puede estar pasando? 
Estoy conectado con Arnet a traves del modem maldito Huawei mt810
gracias

---

### Post by srmantis on 2008-04-28
Tengo el mismo problema.
En teoria uno deberia escribir en el propio navegador:
about:config
y configurar la opcion browser.offline y dejarla en falso.
Pero no da resultados. Una solucion que encontre, pero que es temporal es instalar el otro Firefox (que trae la opcion false por defecto, o sea esta online) que aparece en añadir y quitar. Por lo menos en hardy aparacen dos firefox.

Mientras sea una version beta creo que seguira existiendo el problema, pero hay que reconocer que fue muy facil instalar el flash y el java.

Si encuentras una mejor solucion, postea para tenerla en cuenta.

---

### Post by atatiducken on 2008-04-28
muchas gracias, por el momento voy a hacer lo q me dijiste, pero voy a seguir intentando solucionarlo, si averiguo como hacerlo lo posteo
un saludo

---

### Post by MeduZa on 2008-04-28
creo que el problema es que el archivo de configuracion no tiene permisos de escritura! me paso hace unos dias que el FF arracaba siempre igual y no me guardaba las configuraciones que le hacia.
entonces cuando fui a ~/.mozilla/firefox/oykqbzym.default/ (esto ultimo deberia cambiar)
el archivo prefs.js tenia un candado.

prueven eso.

Saludos

---

### Post by atatiducken on 2008-04-28
gracias por la ayuda, pero mi archivo prefs.js si tenia los permisos de escritura y lectura, es mas entre a verlo y en la seccion  de "browser.offline" decia **false**, en teoria deberia arrancar bien, no se lo q pasa, seguire buscando, cualquier cosa q encuentre lo posteo
saludos

---

### Post by cheyo on 2010-10-08
Disculpen por resucitar un tema viejo...

Después de buscar mucho por la red, descubrí por qué firefox 3.6 (en ubuntu 10.04) siempre me iniciaba en modo "trabajar sin conexion"

[B]solución rápida:

Poner en la barra de direcciones de firefox:

```
about:config
```

Ignorar el aviso de seguridad.

Buscar la siguiente cadena:

```
toolkit.networkmanager.disable
```

doble click en ella y cambiar su valor a "true"

¡Listo![/B]

Explicación para curiosos:

El problema es que yo uso WICD para administrar mis redes inalámbricas y firefox utiliza la interfaz de network-manager para saber si nos encontramos conectados a internet, de manera que al no hallar dicha interfaz, se pone en modo sin conexion. Esta solución vale tambien para quienes usan módem. ¡Saludos!

---

